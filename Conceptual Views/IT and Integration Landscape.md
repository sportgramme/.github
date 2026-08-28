# Sportgramme — Conceptual IT Landscape

Sportgramme combines cloud-based infrastructure with **on-premise AI capabilities**, allowing the platform to use dedicated AI processing alongside its cloud application and data environment.

Moving on prem ensures 
- stability
- cost prudency
- security of proprietory  processes and  knowledge

### The AI model

The conceptual structure is now:

**On-Prem AI → LLM + NLP + Image Training + Harvest Training**

This makes **On-Prem AI** the capability, rather than treating an individual LLM as the entire AI environment.

It also provides a clean place for future AI capabilities to be added without changing the overall conceptual architecture.

The on-premise AI environment becomes a distinct capability within the Sportgramme technology landscape.

---

```mermaid id="8q4m2x"
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

    Application
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

    On-Prem AI
      LLM
      NLP
      Image Training
      Harvest Training

    Cloud
      AWS
        Lambda
        Compute
        Storage
      Microsoft Azure
      Google Cloud

    Integration
      Internal APIs
      External APIs
      Data Exchange
      Services

    Distribution
      Sportgramme Web
      Social Media
        TikTok
        Instagram
        YouTube
        Twitch
        X
      Video
      Still Imagery
      Syndication Partners
        API
        FTP
        Email
```

