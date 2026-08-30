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
| [**sportgramme-on-prem**](https://github.com/sportgramme/sportgramme-on-prem) | The restricted back office — the platform-wide access-control model and its operator console |
| [**sportgramme-on-prem**](https://github.com/sportgramme/sportgramme-on-prem) | The restricted back office — the platform-wide access-control model and its operator console |

## Dig deeper

The platform hub — **[sportgramme/sportgramme](https://github.com/sportgramme/sportgramme)** — holds:

- [**ARCHITECTURE.md**](https://github.com/sportgramme/sportgramme/blob/main/ARCHITECTURE.md) — how the four surfaces fit together, and why the repositories were consolidated
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
