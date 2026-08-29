# Glossary — P–R

**Index:** [A–C](A-C.md) · [D–F](D-F.md) · [G–I](G-I.md) · [J–L](J-L.md) · [M–O](M-O.md) · P–R · [S–U](S-U.md) · [V–Z](V-Z.md) · [about](README.md)

### p-value

The chance of seeing a result at least this extreme if the claim under test were
true. Small means "surprising if nothing is going on". Always read next to an
**[effect size](D-F.md#effect-size)**, never alone.

### Permit (upload)

A short-lived, single-purpose token authorising the transfer of exactly one file
to cloud storage. Issued by **[just-in-time authorisation](J-L.md#just-in-time-authorisation)**;
expires shortly after use and cannot be reused. A transfer that tries to send
anything beyond what its permit covers is rejected at the storage layer.

### Proofing area

The staging store a feature and its lead image land in first, before
**[feed assembly](D-F.md#feed-assembly)** builds them into the public feeds. A
failed publish never loses the contributor's work and never leaves the feeds
half-updated.

### Quantum

The *size* of a single price move, measured in
**[implied-probability](G-I.md#implied-probability)** terms. One of the two axes
of **[volatility](V-Z.md#volatility)**; the other is how *often* moves happen.

### Quarantine

The holding area probationary media contributions sit in until the
**[moderation gate](M-O.md#moderation-gate)** approves them. Blocked or
unapproved material is held, never published.

### Resampling

Estimating uncertainty by repeatedly reshuffling or re-drawing the data
(permutation, bootstrap) instead of relying on a textbook formula. The house
default, always done by **[block](A-C.md#block-permutation--bootstrap)** (race or
day).

### Reversal

A price move in the opposite direction to the one before it. Reversals are what
make a market *volatile* rather than merely trending, and are counted as the core
event in volatility analysis.

### Role

A named bundle of **[capabilities](A-C.md#capability)** ("editor", "approver")
granted as one unit and scoped to a **[division](D-F.md#division-organisational)**.
Tightening or retiring a role changes it everywhere it is held. A requested role
expands into its capability scopes under a single grant, so approval and
revocation act on the whole thing at once.
