# Sportgramme Business Intelligence

**A hands-off analytics layer.** Ask a question in plain language, from anywhere.
The answer arrives on the Sportgramme website — no dashboards to build, no queries
to write, no software to open.

---

## The idea

```mermaid
flowchart LR
    U["Remote user<br/>plain-language prompt"] --> A["BI agent"]
    A --> H["Hypothesis<br/>a precise, testable question"]
    H --> R["Run the analysis"]
    R --> P[("Postgres BI store")]
    P --> S["Apache Superset<br/>charts"]
    S --> W["Sportgramme website<br/>result in the right place"]
    W -.->|"link + notification"| U
```

You send a question. The system turns it into a repeatable analysis, runs it
against the betting-market data, stores the result, draws it, and drops it into
the right spot on the site. You get a link when it is ready.

---

## Why three data tiers

```mermaid
flowchart TD
    subgraph LOCAL ["On site - private"]
        SS["SQL Server LDB3<br/>source of record<br/>fixtures, runners, results"]
        CAP["Capture files on the NAS<br/>raw betting price ticks"]
    end
    subgraph MID ["NAS - cloud reachable"]
        PG[("Postgres sg_bi<br/>analysis-ready facts<br/>plus every result we produce")]
    end
    subgraph TOP ["Cloud reachable"]
        SUP["Apache Superset<br/>charts and dashboards"]
    end
    WEB["Sportgramme website"]

    SS --> PG
    CAP --> PG
    PG --> SUP
    SUP --> WEB
```

| Tier | Holds | Why it is separate |
|---|---|---|
| **SQL Server `LDB3`** | the operational truth — fixtures, runners, results | stays on-site and private; analysis never writes to it |
| **Postgres `sg_bi`** | analysis-ready data and every result we produce | reachable from the cloud, so tools and the website read results here — not from the private database |
| **Apache Superset** | the charts people actually look at | cloud-hosted; embeds straight into web pages |

---

## Asynchronous by design

```mermaid
sequenceDiagram
    actor User as Remote user
    participant BI as BI system
    participant Site as Sportgramme site
    User->>BI: Does market volatility change day to day?
    BI-->>User: acknowledged, working on it
    Note over BI: picks or writes a hypothesis,<br/>runs it, checks the result<br/>against a fixed decision rule
    BI->>Site: publish result (chart plus verdict)
    BI-->>User: done, here is the link
```

Ask, walk away, get told when it lands.

---

## What a "hypothesis" is

A **precise, testable question**, written down once so the exact same analysis can
be re-run any time new data arrives.

```mermaid
flowchart LR
    Q["A clear claim<br/>to test"] --> D["Which data"]
    D --> T["Which statistical test"]
    T --> DR["Decision rule<br/>what counts as proven"]
    DR --> V{{"Verdict"}}
    V --> S1["supported"]
    V --> S2["refuted"]
    V --> S3["inconclusive"]
```

The verdict is decided by a **fixed rule set in advance** — significance *and*
real-world size — never a judgement call after the fact. If there is not enough
data yet, the honest answer is *inconclusive*.

**Example — H001:** *"There is no day-to-day variation in market volatility —
every day's racing churns about the same amount."* The system measures how much
each race's prices swing back and forth, groups the races by day, and tests
whether the days genuinely differ.

---

## A hypothesis over its life

```mermaid
stateDiagram-v2
    [*] --> draft
    draft --> ready: question, data and test agreed
    ready --> running: analysis executed
    running --> supported
    running --> refuted
    running --> inconclusive
    supported --> archived
    refuted --> archived
    inconclusive --> running: more data arrives
```

---

## Where answers appear

Every analysis is tied to a home on the website — a dashboard, a panel on a race
page, or a standing report. When a run finishes, that spot updates on its own and
you are sent the link.

---

## Glossary

Every term used across these docs is defined in the repo-wide
**[Glossary](../Glossary/)**, split alphabetically (A–C, D–F, …). Quick links:
[tick data](../Glossary/S-U.md#tick-data) ·
[hypothesis](../Glossary/G-I.md#hypothesis) ·
[verdict](../Glossary/V-Z.md#verdict) ·
[volatility](../Glossary/V-Z.md#volatility) ·
[sg_bi](../Glossary/S-U.md#sg_bi) ·
[LDB3](../Glossary/J-L.md#ldb3) ·
[Superset](../Glossary/S-U.md#superset)
