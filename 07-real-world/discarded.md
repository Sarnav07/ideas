# Real-World — Discarded Ideas (cut-reason codes)

Ideas explored during Category 07 hunting that did NOT make the final 10. Cut reasons explained below so future iterations can re-evaluate.

**Cut codes:**
- `[ORBITAL-FAIL]` — pitch needs >15 words or doesn't shock a generalist
- `[ORACLE-WEAK]` — oracle is hand-waved, doesn't exist, or is too low-quality
- `[TAM-WEAK]` — total-addressable-market unverifiable or too small for hackathon-narrative weight
- `[DUPE]` — already represented by another idea in this or another category
- `[REG-DEAD]` — regulatory blocker so severe even a demo is impossible
- `[3WK-IMPOSSIBLE]` — MVP can't be built and demoed in 3 weeks

---

## Cut list

### Tokenized real estate with on-chain rent — `[DUPE]` `[TAM-WEAK in 3wk demo]`
RealT-style fractional real-estate with rent-share streaming. Cut because RealT, Lofty, and Roofstock have shipped this for years; no Orbital-shape pitch. Demo would just be a vault contract — judges have seen it.

### Tokenized treasuries (Ondo / Hashnote variant) — `[DUPE]`
Ondo USDY is at $700M+ already; building "another USDY" is a me-too play. Mention as composability layer for other ideas instead.

### Tokenized private equity (SpaceX / OpenAI shares à la Securitize) — `[REG-DEAD]`
Securitize OpenAI-shares product faced SEC pushback in early 2026; demo would invite immediate cease-and-desist. Skip for hackathon.

### Mortgage-backed securities onchain — `[3WK-IMPOSSIBLE]` `[TAM-WEAK demo-wise]`
Maple Finance and Centrifuge have shipped this; tranche-MBS structuring in 3 weeks is not realistic. Pitch doesn't shock anymore.

### Hawala-style P2P remittance with ZK — `[DUPE]`
Same primitive as zkInvoice (#08) and the Aegis-confidential-reports module. Roll into those rather than ship separately.

### Litigation finance tokenized — `[ORACLE-WEAK]` `[REG-DEAD]`
Legal-outcome oracles don't exist; UMA-style optimistic resolution has 90-day windows. SEC views litigation funding as securities offerings. Skip.

### Genomic data marketplace with HE — `[3WK-IMPOSSIBLE]`
Homomorphic encryption on genomic data is research-grade (FHE), no production-ready stack in 3 weeks.

### Render / Akash compute DePIN — `[DUPE]`
Render and Akash exist and dominate. No Orbital-shape inversion to add.

### DIMO automotive data DePIN — `[ORACLE-WEAK]` `[TAM-WEAK]`
DIMO shipped; building a vertical on top doesn't pass Orbital filter. TAM is "automotive insurance" but insurance angle is better served by SensorBond (#09).

### Power-grid frequency response DePIN — `[ORACLE-WEAK]`
Real-time frequency-response markets are regulated by FERC/ENTSO-E; no public-API oracle that's safe to use in a permissionless protocol. Even Pyth doesn't have grid-frequency feeds.

### Carbon-monitoring satellite oracle — `[3WK-IMPOSSIBLE]` `[ORACLE-WEAK]`
Satellite-attested deforestation / methane-leak oracles are still in R&D (Pachama, MethaneSAT). 3-week MVP would need to fake the upstream. Carbon angle better served by EUA variance (#10).

### Mortality bonds / longevity swaps — `[TAM-WEAK retail]` `[ORACLE-WEAK]`
Actuarial mortality data has 1-2 year lag; on-chain replication needs a credible mortality oracle that doesn't exist. Demo unsatisfying.

### Crack spread (refinery margins) perp — `[ORACLE-WEAK]`
Crack spreads are computed from WTI + RBOB + heating-oil futures; multi-leg arb-pricing oracle bus is fragile. Single-leg freight perp (#07) is cleaner.

### Identity-bound asset markets — `[DUPE]`
Composes with Anti-Sybil Personhood Bond (Frontier #10) and zkInvoice (#08). No standalone Orbital-shape pitch.

### "ZK-Helium" — anonymous device-rewards proof — `[DUPE]`
Self-Resolving DePIN (#03) covers the proof-of-location primitive; this is just a vertical specialization.

### Health-data marketplace with ZK — `[REG-DEAD]` `[3WK-IMPOSSIBLE]`
HIPAA / GDPR-Article-9 special-category data; any demo touching real health records is dangerous. ZK-redaction pipelines aren't mature enough for 3-week ship.

### Power swap onchain (PJM hourly RTLMP) — `[ORACLE-WEAK]`
PJM real-time LMP data is paid feed; FERC compliance is heavy. Weather swap (#05) covers the energy-hedging adjacency more cleanly.

### Trade finance / letters of credit onchain — `[DUPE]` `[3WK-IMPOSSIBLE]`
zkInvoice (#08) is the focused, retail-MVP-able slice of trade finance. Full LC issuance is a 6-month build with corporate-bank partnerships.

---

## What we kept (and why)

10 finalists prioritize the matrix: **shocking pitch × real oracle × hackathon-feasible × Stylus-canonical math × sponsor-track alignment × cross-composability with other categories**.

The 4 reused frontier ideas (Drosera, Cat Pool, Self-Resolving DePIN, SLA Insurance) are pre-validated by FRONTIER.md v2. The 6 new (Weather Swap, Music Variance, Freight Pool, zkInvoice, SensorBond, EUA Variance) all extend the same template: parametric / variance / sensor-attested settlement of a real-world data stream that was previously gated behind brokers, exchanges, or claims adjusters.
