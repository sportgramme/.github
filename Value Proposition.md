# Sportgramme — The Three Pillars

Sportgramme is built around **three essential pillars: The Fan, The Creator and The Syndication Partner**.

Each is essential to the success of the ecosystem.

**The Fan creates demand and engagement.**
**The Creator creates knowledge, content and insight.**
**The Syndication Partner creates reach and distribution.**

Sportgramme connects them, adding the data, metadata, technology and infrastructure that allows each pillar to create greater value for the others.

> **Creators create. Fans engage. Syndication Partners extend the reach. Sportgramme connects them.**

```mermaid
flowchart TB

    FAN["THE FAN<br/><br/>Demand<br/>Attention<br/>Engagement"]

    CREATOR["THE CREATOR<br/><br/>Knowledge<br/>Content<br/>Expertise<br/>Insight"]

    PARTNER["THE SYNDICATION PARTNER<br/><br/>Distribution<br/>Reach<br/>Markets<br/>Audiences"]

    SG(("SPORTGRAMME<br/><br/>THE CONNECTED<br/>SPORTS ECOSYSTEM"))

    FAN -->|"Consumes<br/>Engages<br/>Follows"| SG
    SG -->|"Content<br/>Data<br/>Experience"| FAN

    CREATOR -->|"Creates<br/>Reports<br/>Insight<br/>Media"| SG
    SG -->|"Metadata<br/>Data<br/>Tools<br/>Audience"| CREATOR

    SG -->|"Enriched Content<br/>Structured Data<br/>Syndication"| PARTNER
    PARTNER -->|"Distribution<br/>Audiences<br/>Markets"| SG

    CREATOR -.->|"Stories • Media • Expertise"| FAN
    FAN -.->|"Demand • Engagement • Audience"| CREATOR

    FAN -.->|"Audience • Demand"| PARTNER
    PARTNER -.->|"Greater Reach • Access"| FAN

    classDef fan fill:#DCE5D5,stroke:#2F4A32,color:#263526,stroke-width:3px;
    classDef creator fill:#C9DCC5,stroke:#3F6043,color:#263526,stroke-width:3px;
    classDef partner fill:#B7CEB3,stroke:#506F50,color:#263526,stroke-width:3px;
    classDef sg fill:#2F4A32,stroke:#1F3021,color:#FFFFFF,stroke-width:5px;

    class FAN fan;
    class CREATOR creator;
    class PARTNER partner;
    class SG sg;
```

### The ecosystem flywheel

The relationship creates a continuous cycle of value:

```mermaid
flowchart LR

    A["CREATORS<br/>Create"]
    B["SPORTGRAMME<br/>Connect + Enrich"]
    C["FANS<br/>Consume + Engage"]
    D["SYNDICATION PARTNERS<br/>Distribute"]
    
    A --> B
    B --> C
    C --> D
    D --> C
    D --> A
    C --> A
    B --> D
    D --> B

    classDef node fill:#DCE5D5,stroke:#2F4A32,color:#263526,stroke-width:2px;
    classDef centre fill:#2F4A32,stroke:#1F3021,color:#FFFFFF,stroke-width:4px;

    class A,C,D node;
    class B centre;
```

The fundamental proposition is:

> **Sportgramme enables creators to create and collaborate, gives fans a richer and more connected sports experience, and enables syndication partners to distribute trusted, enriched content and data to wider audiences and markets.**

**Each pillar strengthens the others.**

That interconnectedness is the foundation of the Sportgramme business model.
