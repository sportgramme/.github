# sportgramme 
The fundamental proposition is:

> **Sportgramme enables creators to create,collaborate and enhance reputation as well as reaching far wider syndicate markets for their content.** 
  
> **Sportgramme gives fans a richer, better connected, single view of the sports and athletes they want to follow.**
  
> **Sportgramme delivers high quality sports content to syndication partners to distribute trusted, enriched content and data to wider audiences and markets.**


## The single source of truth for world sport data, media, market intelligence, unified and syndicated globally.
> More than **half** of the world's population engages with sports content. Premium sporting events remain among the largest media audiences ever recorded.
[Sports Viewership Statistics 2026 (Cometoplay)](https://blog.cometoplay.co.uk/sports-viewership-statistics/)

> "Global sports advertising market valued at $62.3 billion in 2025."
[Sports Advertising Market Research Report 2034 (DataIntelo)](https://dataintelo.com/report/sports-advertising-market).

> "The Global Sports Media Market reached USD 150 billion in 2025."
[Global Sports Media Market Size, Share & Forecast(Ken Research)](https://www.kenresearch.com/industry-reports/global-sports-media-market).

--- 


## The Product

```mermaid
flowchart TD

    S((Sportgramme))

    C(Content)
    D(Data)
    T(Technology)

    SUB[Subscription Products]
    FEE[Fee-Based Services]

    MRR[Recurring Revenue]
    TR[Transactional Revenue]

    S --> C
    S --> D
    S --> T

    C --> SUB
    D --> SUB

    D --> FEE
    T --> FEE

    SUB --> MRR
    FEE --> TR

    class S platform
    class C,D,T domain
    class SUB,FEE revenue
    class MRR,TR money

    classDef platform fill:#E8EDE3,stroke:#2D3C21,color:#2D3C21,stroke-width:3px;
    classDef domain fill:#FAFBF8,stroke:#556B42,color:#2D3C21;
    classDef revenue fill:#F5F0E3,stroke:#B89B5E,color:#2D3C21,stroke-width:2px;
    classDef money fill:#FBF8F0,stroke:#A88D57,color:#2D3C21,stroke-width:2px;
    
```
sportgramme is a global concern with the stated aim of holding sports data for all sports competed under  governance or a National governing body affilated with/to an internatonal governing body.

 ### The Landscape
 
```mermaid
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

    Experience
      Web Hub
      Content Consumption
      Content Creation
      Contributor Dashboards
      Subscriptions

    Integration
      Internal APIs
      Rate Limiting
      Authentication
      Security

    Intelligence
      NLP
      LLM
      RAG
      Translation

    Data
      SQL Server
      Neo4j
      Qdrant
      Apache

    Infrastructure
      AWS
      Compute
      Storage
      Security

    Enterprise Services
      Ingestion
      Historical Archive
      Reporting
      Statistics

    External Services
      Google Geo
      Apple Weather
      Meta
      Twitch
      SubStack
      X
    Revenue
      Syndication
      Subscription
      Data Licensing
```
## Inputs and outputs.

```mermaid
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
    "lineColor":"#556B42"
  }
}}%%

mindmap
  root((Sportgram))

    Input Channels

      In-House
        Editorial
        Journalists
        Analysts
        Photographers
        Contributors

      Regulatory Bodies
        Governing Bodies
        Registrars
        Federations
        Sporting Authorities

      Leagues Teams & Athletes
        Leagues
        Teams
        Clubs
        Athletes

      API Vendors
        Sports Data
        Results
        Statistics
        Betting Data
        Weather Data

      Social Media
        X
        Instagram
        Facebook
        YouTube
        TikTok

    Distribution Channels

      Owned Channels
        Website
        Mobile Apps
        Newsletters
        Notifications
        Social Media
          sportgramme@instagram
          sportgramme@tiktok
          youtube Sportgramme
          facebook Sportgramme
          twitch
          substack

      FutureVision
         Broadcast rights
            SportgrammeTV
               CH UK EU AUS NZ HK

      Commercial Partners
        Syndication
        Publishers
        Broadcasters
        Sponsors

      Betting Partners
        Odds Providers
        Betting Operators

      Data Consumers
        API Customers
        Data Licensing
        Analytics Partners
```
