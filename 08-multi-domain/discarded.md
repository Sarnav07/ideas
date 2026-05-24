# Category 8 — Discarded Multi-Domain Ideas

Candidates considered for Multi-Domain but cut because they failed at least one of:

- **[CR-D1]** Only enables ≤2 distinct domains (so it belongs in a single-domain category, not Multi-Domain).
- **[CR-D2]** Already covered by another category's winners (e.g., FRONTIER #15 tlock — kept as Idea #01 here in primitive form, but app-level tlock sits in MEV/DEX).
- **[CR-D3]** Pure infrastructure plumbing with no user-facing magic (fails Orbital filter on the pitch alone).
- **[CR-D4]** Cross-cutting in theory but no specific demo use case beyond the first domain.
- **[CR-D5]** Already shipped by a single dominant incumbent — first-mover narrative is dead.

---

## Cut

### "A cross-chain message bus that ports state between L2s" — Generalized LayerZero hooks
**Cut: [CR-D3, CR-D5]** — LayerZero, Wormhole, Axelar all ship this. The primitive is real but it's pure plumbing; the user-facing magic lives in the apps on top (which we cover via #03 Atomic Bundles and #07 Attestation Bus indexer).

### "ERC-7715 spending-limit marketplace" — Rent your wallet to an AI
**Cut: [CR-D2]** — Already in FRONTIER as #21 with a sharper pitch. Could fit Multi-Domain framing (wallet rental enables AI agents + subscriptions + gaming), but the FRONTIER pitch is stronger as a standalone product.

### "Generalized threshold-signature network for cross-chain wallets" — TSS marketplace
**Cut: [CR-D3]** — Pure crypto plumbing. The pitch "FROST DKG for arbitrary apps" is already in DISCARDED.md as CR-5. No user-facing inversion.

### "DePIN proof-of-X mesh" — Witness Chain generalized
**Cut: [CR-D2]** — FRONTIER #29 (Self-Resolving DePIN — Proof of Location) is the productized version. The "generalized witness mesh" framing falls into infrastructure plumbing without a sharper pitch.

### "Bayesian Truth Serum as a service" — Self-resolution primitive
**Cut: [CR-D2]** — FRONTIER #1 (Self-Resolving Prediction Market) is the canonical app. Cross-domain framing ("BTS for any disagreement") is interesting but the audience always lands on prediction markets; multi-domain framing adds confusion.

### "Encrypted mempool for any rollup" — Generalized Shutter
**Cut: [CR-D2, CR-D4]** — Covered by FRONTIER #15. The cross-domain framing ("encrypted mempool enables MEV defense + sealed bids + private votes") collapses to MEV defense in practice — the other use cases need additional primitives (which we cover separately via Idea #01 tlock).

### "Soulbound credentials as a primitive" — Generalized SBT
**Cut: [CR-D5]** — Vitalik proposed in 2022. EAS (Idea #07) ate this niche by being non-soulbound and more flexible.

### "Generalized FHE compute layer" — Zama-as-a-service
**Cut: [CR-D3, CR-D4]** — FHE latency in 2026 is still ~5 swaps/min vs Uniswap V3's hundreds/sec. The cross-domain promise is real (private AI + private DeFi + private voting) but the demo doesn't sing under hackathon timing.

### "iO smart contract layer" — Indistinguishability obfuscation
**Cut: [CR-D3]** — Pitch is S-tier; performance is hackathon-fatal. DISCARDED.md CR-7.

### "RGB / client-side-validated tokens" — Off-chain state tokens
**Cut: [CR-D2]** — Already in main DISCARDED.md (CR-4). Cross-domain framing doesn't help.

### "Programmable session keys as a marketplace" — ERC-7715 Marketplace
**Cut: [CR-D2]** — Same as ERC-7715 above; FRONTIER #21 is the sharper version.

### "Account abstraction module registry" — ERC-7579 module marketplace
**Cut: [CR-D3, CR-D4]** — The primitive is real but the user-facing magic lives in *which* modules ship. Without a specific module that hits 3+ domains, this is plumbing.

### "Generalized peer-prediction oracle" — Crowd-sourced truth without ground truth
**Cut: [CR-D2]** — Same family as BTS / Self-Resolving PM (FRONTIER #1).

### "Generic verifiable computation marketplace" — zkVM-as-a-service
**Cut: [CR-D4]** — Real but undifferentiated from Idea #04 (Historical State SQL), which has a sharper "query history" pitch.

### "Cross-chain identity primitive" — Loom-style portable rep
**Cut: [CR-D2]** — THESIS dropped Loom in favor of ConfidentialReports. EAS (Idea #07) is the better primitive for the same job.

### "Generalized sealed-bid auction primitive" — One library for English / Dutch / Vickrey
**Cut: [CR-D2]** — Same primitive layer as Idea #01 (tlock). Adding it as a separate "auction" idea would be a sub-application.

### "Universal nullifier set" — Sybil-resistance primitive
**Cut: [CR-D2]** — Subset of FRONTIER #10 (Anti-Sybil Personhood Bond) and Idea #07 (Attestation Bus).

### "On-chain LLM judge" — Generalized arbitration via LLM agent
**Cut: [CR-D4]** — Real candidate but the cross-domain demo collapses to "LLM does arbitration in DAO disputes" — single-domain in practice.

### "Generalized restaking-secured oracle" — Eigen-Pyth
**Cut: [CR-D2]** — Subset of Idea #02 (Slashable Bond Market). Oracles are one of #02's six use cases, not a separate primitive.

### "Multi-party computation marketplace" — MPC as a service
**Cut: [CR-D3]** — Pure infra. The user-facing magic lives in TEE (Idea #05) or shielded pools (Idea #08), which are easier to demo.

---

## If you want to argue back

If any cuts above feel wrong, pitch the steel-man and we'll re-evaluate. Most likely candidates for resurrection:

- **Generalized FHE compute layer** — if FHE latency improves materially in 2026 (Zama TFHE-rs has 3x throughput gains rumored)
- **On-chain LLM judge** — if we find a sharp cross-domain demo that doesn't collapse to "LLM does X in domain Y"
- **ERC-7579 module registry** — if a specific module that hits 3+ domains emerges (e.g., a passkey + spending-limit + intent-signer triple)

---

## Where the cuts went

Most cuts were redirected to:
- **App-level versions in FRONTIER.md** (e.g., tlock → FRONTIER #15)
- **Single-domain category folders** (e.g., MEV-specific in category 02 DeFi)
- **DISCARDED.md** at the top level if they failed the Orbital filter entirely
