# GDPR — Name Protection Process

_Companion to `GDPR_Compliance.md` (read that first for the principles). This
document describes the **end-to-end process** by which a natural person's name is
kept out of plaintext at every stage of the data platform. It uses generic terms
and names no internal schema, procedure, host or service._

---

## 1. Purpose

Personal names enter the platform inside third-party sports data and news. This
process ensures that from the moment a name is resolved to a person, it exists
only as ciphertext — while the platform can still **deduplicate** people and
**retrieve** a name for display when authorised.

---

## 2. The process end to end

```mermaid
flowchart TD
    subgraph STG["Staging (transient)"]
        RAW["Incoming record<br/>name in plaintext<br/><i>backup-excluded, purged per batch</i>"]
    end

    subgraph PROM["Resolve & protect step"]
        MK["Derive match key<br/>(lossy, one-way form of the name)"]
        MKH["Hash the match key"]
        DEDUP{"A person with this<br/>match-key hash<br/>already exists?"}
        REUSE["Reuse existing<br/>identity record"]
        NEW["Create identity record<br/><b>no name held</b> — id + public attributes only"]
        ENC1["Encrypt the name → names vault<br/>(AES-256) + store its hash"]
        ENC2["Encrypt the match key → fingerprint-alias store<br/>(AES-256) + store its hash"]
    end

    subgraph INT["Internal analytics database"]
        IDREC["Identity record — no readable name"]
        VNAME["Names vault — ciphertext"]
        VALIAS["Fingerprint-alias store — ciphertext + hash"]
        LINKS["Event data (line-ups, results, stats)<br/>references the identity record by id only"]
    end

    subgraph PUBP["Publish step"]
        PUSH["Copy to production:<br/>identity record (no name),<br/>names vault + alias store (ciphertext + hashes)<br/><i>ids kept identical across databases</i>"]
    end

    subgraph PROD["Production database"]
        PIDREC["Identity record — no readable name"]
        PVNAME["Names vault — ciphertext"]
        PVALIAS["Fingerprint-alias store — ciphertext"]
    end

    subgraph GET["Retrieve (on demand)"]
        SVC["Decrypt service — single entry point,<br/>authorisation enforced"]
        DEC["Decrypt by certificate<br/>(no passphrase held by any app)"]
        DISP["Return name for immediate display<br/><i>not cached, not logged, not written back</i>"]
    end

    RAW --> MK --> MKH --> DEDUP
    DEDUP -- yes --> REUSE
    DEDUP -- no --> NEW
    REUSE --> ENC1
    NEW --> ENC1 --> ENC2
    NEW --> IDREC
    ENC1 --> VNAME
    ENC2 --> VALIAS
    REUSE --> LINKS
    NEW --> LINKS

    IDREC --> PUSH
    VNAME --> PUSH
    VALIAS --> PUSH
    PUSH --> PIDREC
    PUSH --> PVNAME
    PUSH --> PVALIAS

    PVNAME --> SVC --> DEC --> DISP

    style NEW fill:#e6f4ea,stroke:#137333
    style VNAME fill:#fce8e6,stroke:#c5221f
    style VALIAS fill:#fce8e6,stroke:#c5221f
    style PVNAME fill:#fce8e6,stroke:#c5221f
    style PVALIAS fill:#fce8e6,stroke:#c5221f
```

---

## 3. Why a fingerprint alias

Deduplication needs to recognise that two incoming records describe the same
person. It does this with a **match key** — a lossy, one-way reduction of the
name (it cannot be reversed to the name).

Rather than keep that match key as a readable value on the identity record, the
process **encrypts it** and stores it — with its hash — alongside the name in the
protected stores, tagged as a distinct kind of alias. Matching then runs against
the **hash**, so deduplication keeps working while no name-derived text sits on
the identity record itself.

The same store also holds other alias forms of a name (e.g. an initial-plus-
surname variant seen in one source), each encrypted and hash-indexed the same
way.

---

## 4. What never holds a readable name

- The identity record — in the internal database and in production.
- Event data (line-ups, results, statistics) — references people by id only.
- The production database, other than as ciphertext in the protected stores.
- Application configuration and source control — no decryption passphrase exists
  to hold; decryption is authorised through the database's own certificate chain.
- Logs — the decrypt service does not log the values it returns.

Non-personal entities (clubs, teams, racehorses, syndicates) are not personal
data and are stored normally.

---

_Last reviewed: 2026-08-30._
