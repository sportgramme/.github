# Glossary — A–C

**Index:** A–C · [D–F](D-F.md) · [G–I](G-I.md) · [J–L](J-L.md) · [M–O](M-O.md) · [P–R](P-R.md) · [S–U](S-U.md) · [V–Z](V-Z.md) · [about](README.md)

### AnalysisFrame

The single tidy table shape every statistical test consumes. Its columns are
fixed *roles* (`value`, `group`, `block`, …), not domain names. Turning raw data
into one of these is the only bespoke step in an analysis — everything after is
shared code.

### Arbitrage

Backing every outcome of a race, each at the best price offered across
bookmakers, so that the total **[implied probability](G-I.md#implied-probability)**
is below 1.0 — a guaranteed profit whichever runner wins.

### Atom / atom cube

The lowest-level fact row of an analysis (for example one horse × one bookmaker ×
one day). Atoms store *additive* components, so every higher level of a
drill-down — market, day, week — is just a sum of atoms.

### Block (permutation / bootstrap)

Resampling at the level of a whole race or day rather than an individual price
change. Betting data is clustered (many ticks per race), so resampling by block
stops statistical significance being overstated. See
**[resampling](P-R.md#resampling)**.

### Book percentage

The sum of **[implied probabilities](G-I.md#implied-probability)** across a race's
runners for one bookmaker. Above 1.0 is the bookmaker's margin (the *overround*);
below 1.0 is an **[arbitrage](#arbitrage)**.

### Churn

Price movement that goes back and forth rather than trending one way. Churn is
the essence of **[volatility](V-Z.md#volatility)** as defined for these markets.
