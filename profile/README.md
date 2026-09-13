# Sportgramme

**The single source of truth for world sport — data, media and market
intelligence — unified and syndicated globally.**

Sportgramme brings together three capabilities — **content, data and technology** —
and turns them into three ways to monetise: **subscriptions, syndication and
fee-based services**. One platform, three revenue streams, each capability feeding
more than one.

```mermaid
flowchart LR
    A1["DATA VENDORS<br/>deliver facts+ content"] --> B(("SPORTGRAMME<br/>connect + validate <br/>+ enrich"))
    A["CREATORS<br/>create + deliver content"] --> B
    A2["Public domain<br/>historical facts + content"] --> B
    A3["Social Media<br/>generate trends + content"] --> B
    B --> K["ACCREDITATIONS<br/>Media Access to events"]
    A <--> K
    B --> C["Site Visitors<br/>consume + engage"]
    B --> E["REPORTERS · MEDIA · RESEARCHERS<br/>ADVERTISING AGENCIES · BROADCASTERS"]
    B --> D["SYNDICATE PARTNERS<br/>distribute"]
    D --> F["ADVERTISING AGENCIES · BOOKS<br/>BROADCASTERS"]
    C --> H["SUBSCRIED"]
    C --> H1["ANONYMOUS"]
    H["SUBSCRIBED"] --> H2["PERSONALIED DASHBOARDS <br/> Focus + Follow "]
    J["EXCLUSIVE<br/>media + content + datasets"] --> A
    J1["GOVERNING SPORTS BODIES<br/>media + content + datasets"] --> A1
    J2["OFFICIAL TOURNAMENT <br/>press releases and content"] --> A1
    J3["OFFICIAL TEAMS <br/>press releases and content"] --> A1
    classDef n fill:#DCE5D5,stroke:#2F4A32,color:#263526,stroke-width:2px;
    classDef c fill:#2F4A32,stroke:#1F3021,color:#FFFFFF,stroke-width:4px;
    class A,A1,,A2,A3,C,D,E,F,H,H1,H2,J,J1,J2,J3 n; class B c;
```

## The platform, by surface

| Surface | What it is |
|---|---|
| [**sportgramme-web**](https://github.com/sportgramme/sportgramme-web) | The browser surface — public site, embeddable widgets, and the contributor tools for authoring, match-day and media |
| [**sportgramme-api**](https://github.com/sportgramme/sportgramme-api) | The internal API landscape every surface consumes, and the syndication channels that distribute content to partners |
| [**sportgramme-cloud**](https://github.com/sportgramme/sportgramme-cloud) | The cloud landscape — media pipeline, storage, CDN, and the delivery / moderation / brokering functions |
| [**sportgramme-on-prem**](https://github.com/sportgramme/sportgramme-on-prem) | The restricted back office — the platform-wide access-control model, its operator console, generative services AI and ML processes|

## Ingestion to federation, at scale

Behind the single source of truth is a highly sophisticated **batch-processing
and monitoring architecture** — not a handful of scheduled scripts. Purpose-built
pipelines ingest, validate, enrich and federate content and data from many
providers and tenants at once, spanning everything from daily editorial content
down to **sub-second, tick-level sporting data**, with full operational
visibility into every run, every dependency, and every delivery, end to end.

Data protection is not a step bolted on afterwards — **GDPR is applied from the
instant data lands in our landscape.** Personal identifiers are converted to
**encrypted fingerprints at the point of ingestion** and carried in that
protected form through every validation, enrichment and transformation stage
that follows — raw personal data is never exposed downstream of the moment it
entered. See [Data protection](#data-protection) below.

```mermaid
flowchart LR
    subgraph Ingestion["Ingestion — multi-tenant, high volume"]
        direction TB
        I1["Data vendors"]
        I2["Creators"]
        I3["Tick-level sporting data"]
    end
    Ingestion --> G["Encrypted fingerprint<br/>GDPR applied on entry"]
    G --> V["Validate + enrich"]
    V --> F[("Federation<br/>one unified, governed dataset")]
    F --> M{{"Scheduling + monitoring<br/>every run audited"}}
    F --> C1["Consumption — web & apps"]
    F --> C2["Consumption — syndication partners"]
    F --> C3["Consumption — analytics & BI"]
    classDef n fill:#DCE5D5,stroke:#2F4A32,color:#263526,stroke-width:2px;
    classDef c fill:#2F4A32,stroke:#1F3021,color:#FFFFFF,stroke-width:4px;
    classDef g fill:#F5F0E3,stroke:#B89B5E,color:#2D3C21,stroke-width:2px;
    class I1,I2,I3,V,C1,C2,C3 n; class F c; class G g;
```

**Reaching in from the web, without opening a door.** On-prem has no inbound
access at all — the engine only ever calls out. A queue sitting in the same
remote database the website uses lets an admin's click become a run here,
and status flows back the same way.

```mermaid
flowchart LR
    Web["Admin web page"] --> Queue[("Remote trigger queue")]
    Engine["On-prem engine"] -- "poll (outbound only)" --> Queue
    Engine -- "mirror status back" --> Queue
    Queue --> Web
```

Described further in **[SgOrchestrator](https://github.com/sportgramme/SgOrchestrator)**
(the scheduling/execution engine) and
**[FtpQueueMonitor](https://github.com/sportgramme/FtpQueueMonitor)** (its
operator console) — what it does and why, not its internals.

## Dig deeper

The platform hub — **[sportgramme/sportgramme](https://github.com/sportgramme/sportgramme)** — holds:

- [**ARCHITECTURE.md**](https://github.com/sportgramme/sportgramme/blob/main/architecture/ARCHITECTURE.md) — how the four surfaces fit together, and why the repositories were consolidated
- [**Value Proposition**](https://github.com/sportgramme/sportgramme/blob/main/Value%20Proposition.md) · [**Business Models**](https://github.com/sportgramme/sportgramme/tree/main/Business%20Models) · [**Business Case**](https://github.com/sportgramme/sportgramme/tree/main/Business%20Case)
- [**Conceptual Views**](https://github.com/sportgramme/sportgramme/tree/main/Conceptual%20Views) — information flows, content landscape, IT & integration landscape
- [**Business Intelligence**](https://github.com/sportgramme/sportgramme/tree/main/Business%20Intelligence) — the analytics framework and statistics catalogue
- [**Glossary**](https://github.com/sportgramme/sportgramme/tree/main/Glossary) — shared platform, distribution and analytics terms

> Every capability is documented as *As a / I want / So that* briefs with
> conceptual diagrams — what it does and the value it delivers, not its internals.

## Data protection

**[sportgramme/GDPR-Compliance](https://github.com/sportgramme/GDPR-Compliance)** —
how personal data (the names of people appearing in sports data and news) is kept
safe: encryption at rest, decrypt-on-demand through a single authorised service,
right to erasure, and the journalism exemption for editorial free text. Written
for reviewers and partners — principles and process, no internals.
