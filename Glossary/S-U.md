# Glossary — S–U

**Index:** [A–C](A-C.md) · [D–F](D-F.md) · [G–I](G-I.md) · [J–L](J-L.md) · [M–O](M-O.md) · [P–R](P-R.md) · S–U · [V–Z](V-Z.md) · [about](README.md)

### sg_bi

The area of the cloud-reachable Postgres database that holds analysis-ready data
and every result the BI layer produces. Dashboards and the website read from
here — never from the private **[LDB3](J-L.md#ldb3)**.

### Steamer

A runner whose price is getting shorter (smaller odds) — the market backing it
in. Opposite of a **[drifter](D-F.md#drifter)**.

### Superset

Apache Superset, the open-source tool that draws the charts and dashboards. It is
cloud-hosted and embeds directly into Sportgramme web pages.

### Surface (platform)

One of the four axes the showcase repositories are organised on — the place a
capability runs: **Web** (the browser), **API** (internal contracts +
distribution), **AWS** (cloud data & delivery), **On-Prem** (governance). Named
for the surface rather than for Model / View / Controller, because that is what
reads clearly to a first-time visitor. See
[ARCHITECTURE.md](../ARCHITECTURE.md).

### Syndication partner

A named organisation Sportgramme distributes content to commercially, with its
own staff and contacts, billing and legal identity, and one or more
**[delivery mechanisms](D-F.md#delivery-mechanism)**. Moves through a status
lifecycle — active, inactive, historic, blocked, dead — and is never
hard-deleted; a blocked partner is provably excluded from all distribution.

### Tick data

Every individual change in a bookmaker's price, timestamped to the millisecond.
The raw material for all the market analyses.

### Trust level / trusted & untrusted

A per-user, per-**[capability](A-C.md#capability)**, per-content-category marker
set by an administrator. Downstream pipelines route a trusted contributor's work
directly and hold an untrusted contributor's for moderation — the pipeline never
makes that judgement itself. In the media pipeline this appears as the batch
*trust tier* (probationary vs. trusted).
