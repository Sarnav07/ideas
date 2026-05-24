# Category 8 — Multi-Domain (Cross-Cutting Primitives)

10 primitive-layer ideas that don't belong to any single category. Each enables apps across **at least 3 distinct domains** (DeFi + AI + governance + privacy + DePIN + insurance + identity), and the cross-cutting power is the pitch.

**Selection rule applied:** every idea must pass the Orbital filter *and* its README "Cross-domain applications" section must list 3+ specific use cases across 3+ distinct domains. Generic platform claims ("usable for anything") were cut.

---

## Index

| # | Idea | Domains touched (≥3) | Pitch |
|---|---|---|---|
| **01** | [tlock-as-a-Service](idea-01-tlock-as-a-service.md) | DEX/MEV · Governance · AI agents · NFT/auctions · Prediction markets (5) | *"One API. Encrypt anything to any future block. Every app inherits MEV resistance."* |
| **02** | [Slashable Bond Market](idea-02-slashable-bond-market.md) | Oracles · AI · DePIN · Insurance · Governance · Compliance (6) | *"Post ETH. Make any claim. If you lie, the chain takes your ETH."* |
| **03** | [Atomic Cross-Rollup Bundles](idea-03-atomic-cross-rollup-bundles.md) | DeFi arb · Lending · AI agents · Governance · NFT · Bridges (6) | *"Send one tx. It either lands on five rollups together or nowhere."* |
| **04** | [Historical State SQL](idea-04-historical-state-sql.md) | Credit · Governance · AI agents · Insurance · Airdrops · Analytics (6) | *"Run SQL across five years of Ethereum history. Get one proof. Trust nothing."* |
| **05** | [TEE Compute Bus](idea-05-tee-compute-marketplace.md) | AI · Dark pools · Governance · Oracles · Gaming · Compliance (6) | *"A smart contract that runs code no one can see, including the operator."* |
| **06** | [Verifiable Randomness Bus](idea-06-drand-randomness-bus.md) | Gaming/NFT · DAO sortition · DeFi lotteries · AI agents · DePIN · Insurance (6) | *"Every smart contract on Arbitrum shares the same provably-fair dice."* |
| **07** | [Universal Attestation Bus](idea-07-universal-attestation-bus.md) | Lending · AI agents · Governance · DePIN · Identity · Compliance (6) | *"Any address. Any claim. Any chain. One attestation graph."* |
| **08** | [Programmable Shielded Pool](idea-08-programmable-shielded-pool.md) | DeFi · Voting · Inheritance · Payroll · Bearer cash · Subscriptions · Compliance (7) | *"A private bank account whose every transaction runs a custom program."* |
| **09** | [Intent Solver Bus](idea-09-intent-solver-bus.md) | DEX · NFT · AI agents · Bridges · Governance · Subscriptions (6) | *"Write what you want. Solvers race to make it happen. Pay only on success."* |
| **10** | [Witness Encryption Vault](idea-10-witness-encryption-vault.md) | AI agents · Inheritance · Bug bounties · Prediction markets · Insurance · Escrow · Whistleblowing (7) | *"Encrypt a secret that unlocks only if the chain reaches a specific state."* |

---

## Top 3 picks for this category

These are the three primitives whose cross-cutting power is most legible *and* whose 3-week MVP is realistic.

### 🥇 #01 — tlock-as-a-Service
**Why first:** the primitive ships today (drand is production for Filecoin), the verifier fits in Stylus, and the pitch hits five domains in one breath. Sealed-bid trading, sealed votes, sealed agent prompts, sealed auctions, sealed predictions — all from one library. Closest mapping to a "drop this Solidity import and your dApp inherits a superpower" demo.

**Why it wins as a hackathon project:** Stylus-canonical (BLS12-381 pairing in Rust), drand integration is one HTTP relay call, and we can ship three meaningfully different demo apps in three weeks.

### 🥈 #10 — Witness Encryption Vault
**Why second:** strictly more general than tlock (tlock is WE keyed to drand rounds; this is WE keyed to *any* predicate). Powers FRONTIER #9 (witness-encrypted agent wallet) and FRONTIER #17 (dead-man-switch inheritance) *and* opens new applications (auto-release bug bounties, conditional whistleblowing). 7 distinct domains.

**Why it slots second:** cryptographic novelty is higher (SWE constructions <2 years old), so demo polish is harder. Strong story but more risk than tlock.

### 🥉 #02 — Slashable Bond Market
**Why third:** generalizes the *entire* EigenLayer/AVS thesis into a single product. Every restaked-ETH-backed claim — oracle, AI, DePIN, insurance, governance, compliance — lives in one bond pool. The Hyperliquid HIP-3 proof-of-concept (permissionless perp listing with bonded oracles) shows the pattern already works in one vertical; this generalizes it.

**Why third:** depends on EigenLayer / Symbiotic / Karak liveness on Arbitrum, which is real but newer than drand. Bigger sponsor surface (EigenLayer grants) compensates.

---

## What makes a primitive "cross-cutting"

A genuinely cross-cutting idea has three properties:

1. **The primitive is asset-agnostic.** It doesn't care whether the payload is a swap, a vote, a prediction, or an AI prompt. It operates on `bytes`.
2. **Three or more domains have a specific demo use case.** Not "it could be useful for AI someday" — but "agent X calls library Y at line Z to do specific thing W".
3. **Network effects compound across domains.** More apps adopting → cheaper / faster / more secure → more apps adopt. Same flywheel works whether the next adopter is a DEX, a DAO, or an oracle.

Every idea here clears all three bars. Ideas that fail any bar (e.g., "encrypted mempool", which only really matters for DEX/MEV, not for AI or inheritance) were cut to a single-domain category.

---

## Sponsor-track resonance

Every primitive here is **Stylus-canonical** — they all involve BLS pairings, STARK verifiers, or heavy cryptographic verification where Stylus delivers 5-10x cost reduction over Solidity. This makes the whole category a natural Arbitrum Stylus showcase.

Additionally:
- **#02 Slashable Bonds** → EigenLayer ecosystem grant
- **#03 Atomic Bundles** → Espresso / Robinhood Chain
- **#07 Attestation Bus** → Robinhood Chain (regulated attestations), ERC-8004 ecosystem
- **#08 Shielded Pool** → first port of Goldberg et al. 2026 to Arbitrum (mirrors Aegis THESIS angle)
- **#09 Intent Bus** → cross-DEX + ERC-8004 + Robinhood Chain trifecta

---

## See also

- [discarded.md](discarded.md) — ideas considered but cut for this category
- [/FRONTIER.md](../../FRONTIER.md) — main shortlist of 30 Orbital-tier ideas
- [/THESIS.md](../../THESIS.md) — winning project framework (Aegis as primary)
