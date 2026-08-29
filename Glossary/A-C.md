# Glossary — A–C

**Index:** A–C · [D–F](D-F.md) · [G–I](G-I.md) · [J–L](J-L.md) · [M–O](M-O.md) · [P–R](P-R.md) · [S–U](S-U.md) · [V–Z](V-Z.md) · [about](README.md)

### Access matrix

The single per-user record of *role × division × capability* that says what
everyone may do. Every change is stamped with who made it and when. The
[site-administration](https://github.com/sportgramme/sportgramme-on-prem/tree/main/site-administration)
console edits it and the platform's runtime guards read it — one source of truth,
not an admin copy and a runtime copy. See **[capability](#capability)**,
**[role](P-R.md#role)**, **[division](D-F.md#division-organisational)**.

### Accreditation / accredited contributor

A contributor who holds a named, sport-scoped **[role](P-R.md#role)** granting
specific authoring **[capabilities](#capability)**. Live match scoring is open to
any registered contributor; creating fixtures and publishing features is gated by
accreditation for that sport.

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

### Capability

A single named action a user can be permitted to perform. Capabilities are the
shared vocabulary of the access model — referenced by **[roles](P-R.md#role)**,
by **[trust levels](S-U.md#trust-level--trusted--untrusted)**, and by the runtime
guards. New ones are added deliberately in the
**[capability dictionary](#capability-dictionary)**, not invented ad hoc in code.

### Capability brief

The house documentation format across the showcase repositories: an *As a / I
want / So that* statement plus a conceptual diagram, describing **what a
capability does and the value it delivers** — never endpoints, feeds, hosting, or
internal system names ("**described, not disclosed**").

### Capability dictionary

The controlled list of every **[capability](#capability)** in the platform,
maintained in one place so permissions are always expressed in one vocabulary.

### Channel (syndication)

A configured **[delivery mechanism](D-F.md#delivery-mechanism)** belonging to a
**[syndication partner](S-U.md#syndication-partner)** — its type, purpose, target
environment and priority, plus connection details whose secrets are held
encrypted and never displayed back.

### Churn

Price movement that goes back and forth rather than trending one way. Churn is
the essence of **[volatility](V-Z.md#volatility)** as defined for these markets.

### Consolidated feed

The pooled, newest-first stream of editorial output across every sport, assembled
alongside each sport's own feed and used to drive the public home page and the
news / quotes ticker. See **[feed assembly](D-F.md#feed-assembly)**.

### Core API

The internal API surface every browser **[surface](S-U.md#surface-platform)**
consumes. Its contracts are catalogued in
[`sportgramme-api/internal-api-landscape`](https://github.com/sportgramme/sportgramme-api/tree/main/internal-api-landscape)
— described, not disclosed.
