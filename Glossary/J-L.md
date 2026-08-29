# Glossary — J–L

**Index:** [A–C](A-C.md) · [D–F](D-F.md) · [G–I](G-I.md) · J–L · [M–O](M-O.md) · [P–R](P-R.md) · [S–U](S-U.md) · [V–Z](V-Z.md) · [about](README.md)

### Just-in-time authorisation

Delivery permission requested one file at a time, at the moment of transfer, and
short-lived — so there is never a stockpile of reusable upload
**[permits](P-R.md#permit-upload)** and a leaked one is worthless within moments.

### Kruskal–Wallis

A rank-based statistical test for whether several groups differ in level. The
default choice when the quantity being measured is skewed, as betting-price moves
usually are.

### LDB3

The private, on-site SQL Server holding Sportgramme's operational record —
fixtures, runners, results. The analytics layer reads from it and never writes
to it. Analysis-ready copies live in **[sg_bi](S-U.md#sg_bi)**.
