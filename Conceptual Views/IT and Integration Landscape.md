# Sportgramme — Conceptual IT Landscape

Sportgramme is a **cloud and web-based application** supported by a connected technology environment for ingesting, storing, processing, analysing and distributing sports information and media.

The conceptual IT landscape shows the principal technology hubs without moving into detailed technical architecture.

```mermaid id="k2p6vz"
%%{init: {
  "theme":"base",
  "themeVariables": {
    "background":"#FFFFFF",

    "primaryColor":"#FAFBF8",
    "primaryTextColor":"#2D3C21",
    "primaryBorderColor":"#2D3C21",

    "secondaryColor":"#F3F5F0",
    "secondaryTextColor":"#2D3C21",

    "tertiaryColor":"#E8EDE3",
    "tertiaryTextColor":"#2D3C21",

    "lineColor":"#556B42",

    "clusterBkg":"#FBFCFA",
    "clusterBorder":"#8A9B7A",

    "mainBkg":"#FAFBF8",
    "nodeBorder":"#556B42"
  }
}}%%

mindmap
  root((Sportgramme))

    Web & Cloud Application
      Web Platform
      User Experience
      APIs

    Ingestion Hub
      Sports Data
      Content
      Media
      External Feeds

    Data Hub
      MSSQL Server
      Sports Database
      Metadata

    Analysis & Reporting Hub
      Apache BI
      Analytics
      Statistics
      Reporting

    AI & Language
      On-Prem LLMs
      NLP
      Enrichment
      Translation

    AWS
      Lambda Compute
      Storage
      Cloud Services

    Distribution
      Sportgramme Web
      Social Media
      Video
      Still Imagery
      TikTok
      Instagram
      Shorts
```

### The conceptual technology flow

**Ingest → Store → Analyse → Enrich → Publish → Distribute**

The major hubs are deliberately shown as **capabilities**, with the principal technologies identified beneath them.

The **Ingestion Hub** brings data, content, media and external feeds into Sportgramme.

The **Data Hub** provides the core structured sports information, supported by **MSSQL Server**.

The **Analysis & Reporting Hub** turns the accumulated data into statistics, analysis and reporting, supported by **Apache BI**.

The **AI & Language** capability uses on-premise **LLMs and NLP** to enrich, interpret and translate information.

**AWS** provides the cloud compute, storage and supporting environment, including **Lambda**.

Finally, Sportgramme distributes information and media through its own web platform and external channels including **video, still imagery, TikTok, Instagram and Shorts**.

> **A simple technology principle: Sportgramme ingests the world of sport, builds and enriches its data, applies intelligence, and distributes the resulting information and media wherever the audience is.**
