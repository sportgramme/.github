
# Sportgramme — Conceptual View

At its simplest, Sportgramme is a **connected global sports ecosystem**.

It brings together people, content and data, applies intelligence to that information, connects it across the world of sport, and makes it available through multiple experiences and distribution channels.

The conceptual model deliberately separates **what Sportgramme is**, **what it does**, and **how it creates value**.

```mermaid
%%{init: {
  "theme": "base",
  "themeVariables": {
    "background": "#F7F5EF",
    "primaryColor": "#2F4A32",
    "primaryTextColor": "#FFFFFF",
    "primaryBorderColor": "#233A27",
    "secondaryColor": "#6F8F68",
    "secondaryTextColor": "#FFFFFF",
    "tertiaryColor": "#DCE5D5",
    "tertiaryTextColor": "#263526",
    "lineColor": "#6F8068",
    "fontFamily": "Arial, Helvetica, sans-serif"
  }
}}%%

mindmap
  root((Sportgramme))

    Experience
      Fans
      Creators
      Syndication Partners

    Content
      Reporting
      Media
      Analysis
      Archives
      Broadcast

    Data
      Sports
      People
      Teams
      Competitions
      Events
      Results
      Statistics
      Records

    Intelligence
      Discovery
      Personalisation
      Enrichment
      Translation
      Analysis

    Connectivity
      Global Sports Graph
      APIs
      Metadata
      Integration

    Distribution
      Web
      Mobile
      Social
      Publishers
      Broadcasters
      Syndication

    Revenue
      Subscriptions
      Syndication
      Data Licensing
```

### The conceptual model

The simplest way to understand the platform is:

> **People create → Sportgramme connects and enriches → audiences consume → partners distribute → the ecosystem grows.**

```mermaid
flowchart LR

    P["PEOPLE<br/><br/>Fans<br/>Creators<br/>Syndication Partners"]

    S(("SPORTGRAMME<br/><br/>CONNECTED<br/>SPORTS ECOSYSTEM"))

    C["CONTENT + DATA<br/><br/>Sports<br/>People<br/>Events<br/>Results<br/>Media"]

    I["INTELLIGENCE<br/><br/>Connect<br/>Enrich<br/>Discover<br/>Personalise"]

    D["DISTRIBUTION<br/><br/>Web<br/>Mobile<br/>Publishers<br/>Broadcasters<br/>Syndication"]

    R["VALUE<br/><br/>Engagement<br/>Reach<br/>Revenue"]

    P --> S
    C --> S
    S --> I
    I --> D
    D --> R
    R --> P

    classDef people fill:#DCE5D5,stroke:#2F4A32,color:#263526,stroke-width:2px;
    classDef core fill:#2F4A32,stroke:#1F3021,color:#FFFFFF,stroke-width:4px;
    classDef node fill:#EEF2E9,stroke:#6F8068,color:#263526,stroke-width:2px;
    classDef value fill:#E8DDC5,stroke:#9A814F,color:#3A321F,stroke-width:2px;

    class P people;
    class S core;
    class C,I,D node;
    class R value;
```

### The strategic idea

Sportgramme is therefore **not simply a sports website, media company or data provider**.

It is the **connection layer** that brings together:

**The Fan + The Creator + The Syndication Partner**

around:

**Content + Data + Intelligence**

to create:

**Experience + Distribution + Value**

This is the conceptual foundation on which the more detailed **Fan, Creator, Content, Data, Technology and Revenue ecosystems** can then be built.
