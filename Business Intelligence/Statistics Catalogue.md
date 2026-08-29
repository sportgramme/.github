# Statistical test catalogue (v1)

Every hypothesis declares a `test:` block in its `hypothesis.yaml`. The
framework supports **only** the `question_type` values below; anything else is a
schema-validation error until it is added here deliberately.

The point: hypotheses never hand-roll statistics. An execution script's only
bespoke work is reshaping the atom cube into an **`AnalysisFrame`** (tidy table,
fixed column roles) and naming the `question_type`. Everything after that —
resampling, the test, the effect size, the decision, the result files — is
shared code in `execution/_common/`.

**Implementations are `scipy` / `statsmodels` / `pingouin` only. R is not a
runtime dependency** and nothing in the pipeline shells out to it — see the
project decision (2026-08-29): every v1 test below is covered in pure Python,
and adding R (locally or on the NAS jail) buys no speed at our data scale and
costs a language boundary + fragile deployment. R stays a local, dev-machine
escape hatch for one-off deep dives (GARCH, mixed-effects) that never enter the
register.

## AnalysisFrame column roles

| role | meaning |
|---|---|
| `value` | the numeric metric under test (e.g. `realized_variance`) |
| `group` | categorical factor being compared (e.g. `race_date`, `race_class`) |
| `block` | clustering unit for resampling — **`race` or `day`**, never a raw tick |
| `weight` | optional row weight (e.g. market-life seconds) |
| `pair_id` | pairing key for paired tests |
| `predictor` | numeric predictor(s) for `association` |
| `event` | 0/1 occurrence for `rate_vs_threshold` |
| `exposure` | denominator for a rate (e.g. race-minutes observed) |
| `magnitude` | size of each event (e.g. arb margin) |
| `outcome_cat`, `factor_cat` | categorical columns for `categorical_association` |
| `count` | pre-aggregated cell counts (optional) for contingency tests |
| `series_a`, `series_b`, `t` | aligned time series for `lead_lag` |
| `pred_prob`, `outcome` | for `calibration` (deferred) |

## Supported question types

| `question_type` | Question | Allowed `method` | Required roles | Effect size | Default resampling | Min N |
|---|---|---|---|---|---|---|
| `k_group_level` | Does the metric's **level** differ across a factor? *(H001)* | `kruskal_wallis` (default), `one_way_anova`, `welch_anova` | `value, group, block` | ε² / η² / ω² | block-permute `group` | ≥5 blocks per group |
| `k_group_dispersion` | Does the metric's **spread** differ across a factor? | `bf_permutation` (default), `brown_forsythe`, `levene` | `value, group, block` | variance ratio, ICC | block-permute `group` | ≥5 blocks per group |
| `two_group` | Do two groups differ? | `mann_whitney` (default), `wilcoxon`, `welch_t`, `paired_t` | `value, group[, pair_id], block` | Cliff's δ / Hedges' g | block-permute or sign-flip | ≥10 pairs or ≥5 per group |
| `rate_vs_threshold` | Does an event occur — **how often, how big**? | `bootstrap_rate` (default), `binomial`, `poisson` | `event, exposure, block[, magnitude]` | rate + mean magnitude | block bootstrap by `block` | ≥20 blocks |
| `association` | Does the metric move **with** a predictor? | `spearman` (default), `ols_clustered` | `value, predictor(s), block` | ρ / slope per unit | block-permute `value` | ≥30 blocks |
| `lead_lag` | Does series A move **before** series B? | `xcorr_bootstrap` (default), `granger` | `series_a, series_b, t, block` | lag (seconds), lead-share % | block bootstrap by `block` | ≥30 event pairs |
| `categorical_association` | Is a **categorical outcome** linked to a **categorical factor** (or does a distribution match an expected one)? | `chi2_independence` (default), `g_test`, `fisher_exact`, `chi2_goodness_of_fit` | `outcome_cat, factor_cat, block[, count]` | Cramér's V / odds ratio | permute `factor_cat` by `block` | expected cell ≥5 (else `fisher_exact`); ≥20 blocks |
| `calibration` *(deferred — needs race outcomes from LDB3)* | Do predicted probabilities match reality? | `reliability_binomial`, `brier_decomposition` | `pred_prob, outcome, block` | calibration error, AUC | block bootstrap | ≥200 events |

## The shared resampling engine

All inference routes through:

```
resample(frame, scheme, block, statistic, n, seed) -> null distribution
    scheme in {block_permutation, block_bootstrap, none}
```

- Betting tick data is autocorrelated and clustered (ticks within a race, races
  within a day). Parametric tests that assume iid rows overstate significance,
  so the **default is a block permutation / block bootstrap at the `race`
  (or `day`) level**.
- Parametric methods (`one_way_anova`, `welch_t`, `welch_anova`,
  `chi2_independence`, …) are run **either** on block-level aggregates **or** via
  the permutation form of their statistic. The classical asymptotic p-value
  (`scipy.stats`) is emitted **only** when the spec sets `resampling.scheme: none`.
- `n` (resamples) default 10000, minimum 199. `seed` is recorded in the result.

## TestResult (returned by every method)

```
TestResult{ estimate, ci_low, ci_high, effect_size, effect_label,
            p_value, statistic, n, n_blocks, power_ok, notes[] }
```

`power_ok = false` when the Min N guard fails → `Verdict = inconclusive`
regardless of `p_value`.

## Decision

`apply_decision_rule(decision_rule, TestResult, params, spec) -> Verdict`
`Verdict{ outcome: supported | refuted | inconclusive, reasons[] }`

The YAML `decision_rule` carries prose plus a machine-evaluable `criteria`
block — two lists of `<field> <op> <value>` strings (field = a `TestResult`
attribute; value = a number or a param/test name such as `alpha`) that must ALL
hold. `reject` met → the null (the hypothesis statement) is **refuted**;
`fail_to_reject` met → **supported**; neither, or `power_ok = false` →
**inconclusive**. Rules must combine **significance AND magnitude** — never a
bare p-value. `test.multiple_testing` (`none` | `bh_fdr` | `bonferroni`) governs
correction across the hypothesis register.

## Out of scope for v1

Mixed-effects / hierarchical models, Bayesian estimation, changepoint detection,
survival / hazard on price paths, multivariate models beyond one clustered
regression. Add a row above (and the schema enum) only when a real hypothesis
needs it.
