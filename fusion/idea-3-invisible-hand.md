# Idea 3: INVISIBLE HAND

## Pitch
*"An AI agent whose wallet doesn't exist until it does its job — and whose model doesn't either."* *(15 words)*

**Tighter (12 words):** *"The AI agent has no wallet and no model — until it earns them."*

## Spine
AI-agent / cryptographic commerce.

## What it is
The **first end-to-end zero-trusted-coordinator agent commerce protocol.** An autonomous AI agent has no model weights, no signing key, and no wallet — until a single cryptographic primitive (witness encryption keyed on outcomes) releases all three *only* upon verifiable task completion.

Today's "agent wallet" is: hot key in a TEE + policy guardrails + hope. INVISIBLE HAND replaces every trust assumption with cryptography: **no completion → no key → no theft.** ERC-8004 reputation rides on top.

The on-stage demo: judge clicks "verify and decrypt" → zkML proof posts → model weights download AND agent wallet drains AND ERC-8004 reputation updates, all from the *same* witness-extracted secret.

## How it works
Two layers, both built on the same Rust Stylus port of KZG witness encryption (IACR 2024/264).

**Layer 1 — Sealed Model.**
- AI model weights are KZG witness-encrypted under a public-test-set capability predicate ("accuracy ≥ 0.85 on CIFAR-10 test set" or "passes safety benchmark X").
- Buyer runs the encrypted blob through a Lagrange DeepProve-1 zkML proof generator → submits proof on-chain → Stylus verifier releases the witness → witness decrypts weights.
- No zkML proof = no decryption, forever. No trusted enclave anywhere in the loop.

**Layer 2 — Witness-Encrypted Agent Wallet.**
- ERC-4337 smart-account wallet's signing key is **signature-based witness-encrypted** (T+1-eWEB, Glaeser-Madathil IACR 2025/1064) under a task-completion predicate.
- Predicate: *"drand signs the first block after `done(T)` is emitted by oracle X"* (where `done(T)` is a zkTLS-attested HTTPS-200 to a target URL, or any other verifiable outcome).
- drand-watcher Stylus contract holds the encrypted key.
- Task completes → drand signature exists → signature extracts the witness → witness decrypts the signing key → wallet can pay the agent operator (and the model seller, atomically).
- If task fails → drand never signs → signing key never exists → no funds can move.

**The fusion punchline.** Both layers share the *same* KZG-WE Stylus library. The agent has no key, no weights, and no wallet **until and unless** it proves the capability and delivers the task. ERC-8004 reputation update is signed by the same witness extraction that unlocks the wallet — one secret, four consequences.

## Why it lands (Orbital filter)
*"An AI agent whose wallet doesn't exist until it does its job"* is a 12-word self-contained paradox. A generalist judge grasps the inversion: today's agents are *trusted* to spend; this agent *cannot* spend until the cryptography agrees. The on-stage demo is theatrical in a way nothing else in the portfolio is — a wallet that visibly appears out of nothing the instant a zkML proof posts.

Falsifiable benchmarks for the math judges: *"verifier gas < 5M, proof time < 60s on Gemma3-class model."* Citations across IACR 2024 + IACR 2025 + Lagrange DeepProve + ERC-8004 + drand mature beacon stack make the technical credibility undeniable.

## Future utility (2026 market thesis)
**Who buys:**
- **Regulated AI procurement** (defense contractors, big-pharma R&D, fintech credit-model buyers) who today rely on SOC-2 reports because they have no way to verify *"is this the model you said it was?"* — sealed-model is the cryptographic alternative.
- **Every builder of an autonomous AI agent paid for work** (freelance contractors, DAO bounty workers, agent-to-agent commerce) who today accepts hot-key-in-TEE risk.
- **Protocol designers** who want outcome-bonded payment rails without a trusted coordinator.

**TAM (per source ideas):**
- Regulated AI model market: ~$25-35B by 2026.
- Agent-managed AUM forecast: $50B by 2027 (Citi GPS).
- Take rate: 0.5% of model marketplace transactions + 25bp of WE withdrawals → low-to-mid eight figures annual at modest market share.

**Why mid-2026 (not 2025, not 2027) — strongest of the three options on this axis:**
- **Lagrange DeepProve-1 launched late 2025** — literally the enabling infrastructure for proving CNN-class model capability cheaply enough to demo.
- **T+1-eWEB paper (IACR 2025/1064, Glaeser-Madathil 2025)** — signature-based witness encryption only became buildable in 2025; no production implementations exist.
- **BLS12-381 Stylus precompiles** matured at scale in 2025 — without them the WE wallet costs $500K/op.
- **ERC-8004 mainnet (Jan 2026)** — the agent identity standard tying reputation updates to a registered entity.
- **drand mature beacon.**
- **None of these primitives were simultaneously production-ready before mid-2026.** staleness-detector verdict: *"the most 2026-native idea in the vault."*

## Business model
- **0.5% take rate** on sealed-model marketplace transactions.
- **25bp** on every witness-encrypted withdrawal from an agent wallet.
- Day-30 numbers depend on hand-building one model-marketplace launch partner (B2B drag is the real revenue risk).

## Sponsor / track fit
- **Primary: $15K Best Agentic.** Canonical Best Agentic build — ERC-8004 + ERC-4337 + WE cryptography is *exactly* what Best Agentic was carved out to reward. Marlin / Phala TEE bounties adjacent.
- **$70K Overall.** First deployed witness-encryption + zkML composition on Arbitrum. Falsifiable benchmark: *"verifier gas < 5M, proof time < 60s on Gemma3-class model."* The sci-fi pitch makes Overall a real shot.
- **Stylus showcase.** Pairing-friendly curve operations (KZG verifier + BLS12-381) are textbook Stylus territory.
- **$30K Robinhood Chain** — weak fit; not a flagship use case for Robinhood. Skip.

**Max reserved-seat reach: ~$85K — only one of the three options where BOTH Best Agentic AND Overall are realistically in play.** Asymmetric prize math.

## 3-week MVP scope
**Week 1 — WE Stylus library + sealed-model PoC.**
- Days 1-2: Rust port of KZG witness encryption (IACR 2024/264). **High-risk infra, start Day 1.** Foundry + cargo-stylus integration.
- Days 3-4: Lagrange DeepProve verifier contract in Stylus. Encrypt a small CNN (CIFAR-10, ~100K params) under predicate "accuracy ≥ 0.85" on a public test set.
- Days 5-7: End-to-end test: post zkML proof → verifier releases witness → witness decrypts blob → cleartext weights download. Also wire the "fake model" denial case (no proof → no decryption, forever).

**Week 2 — WE Agent Wallet + drand integration.**
- Days 8-10: Signature-based WE library (port Glaeser-Madathil IACR 2025/1064) sharing KZG primitives with the model side.
- Days 11-12: ERC-4337 smart wallet + drand-watcher Stylus contract. Single-task predicate: zkTLS-attested HTTPS-200 to a target URL. Wallet's signing key is encrypted to "drand signature for the first block after `done(T)` is emitted."
- Days 13-14: ERC-8004 reputation hookup — successful completions ratchet up the agent's registry score; same witness extraction that unlocks the wallet signs the reputation update.

**Week 3 — Unified demo + trial + ship.**
- Days 15-17: 5-10 user trial — developer builds a toy agent that buys a sealed model, runs it, and gets paid through the WE wallet. Measure: end-to-end zero-trusted-coordinator flow completion rate; mean witness-extraction-to-payment latency.
- Days 18-19: On-stage demo: judge buys a sealed model live, an agent uses it to complete a task (post verifiable HTTPS-200), the agent's wallet drains paying both the model seller and the agent operator — all driven by one zkML proof + one drand signature.
- Days 20-21: Pitch deck citing IACR 2024/264 + IACR 2025/1064 + DeepProve-1 + Citi GPS agentic AUM forecast. 3-min video. Submit Overall + Best Agentic + Stylus.

## Risks
**The one that could kill this:** **WE library maturity.** Both Sealed Model and WE Agent Wallet source ideas explicitly note this — KZG witness-encryption and signature-based WE constructions are research-grade with no production Rust ports. We are shipping the ports. If the Stylus implementation slips past Day 10, the unified demo collapses. This is the most technically aggressive option of the three and the most likely to fail in a way invisible to judges (because *"the WE library isn't working"* doesn't make a good demo).

**Mitigation:**
- **Day-1 spike** to evaluate library risk: spend day 1 attempting a minimal KZG WE encryption + decryption round trip in cargo-stylus. If blocked, fall back to a Phala-TEE-based "trusted enclave decryption" stand-in for the model side (clearly labeled as a v1 trust-assumption), keeping the wallet side cryptographic.
- **Team-size constraint:** 3-person tight; 2-person infeasible. KZG-WE port + DeepProve verifier + ERC-4337 wallet is too much WE-crypto specialization for two people. **Do not pick this option with a 2-person team.**

**Secondary risks:**
- DeepProve-1 proof time on Gemma3-class model exceeds 60s → fall back to smaller model class for demo.
- BLS12-381 Stylus precompile costs higher than projected → batch operations + amortize.

## Lens verdicts
- **staleness-detector (9 + 8 — class leader):** *"The most 2026-native idea in the vault. Cannot be confused with any prior Bengaluru winner. Requires Lagrange DeepProve-1, T+1-eWEB, BLS12-381 Stylus, ERC-8004, drand maturity — none simultaneously production-ready before mid-2026. This would be the first end-to-end cryptographic agent commerce protocol — no trusted coordinator at any step."*
- **market-2026 (not directly scored — outside the original 8; estimated 6-7/10):** Regulated AI procurement TAM is real but B2B-slow; agent-managed AUM forecast is real but speculative; revenue model is clean but Day-30 numbers depend on hand-building one model-marketplace partner.
- **judge-wow (not directly scored; estimated 8.5-9.0):** *"An AI agent whose wallet doesn't exist until it does its job"* clears the Orbital bar — a 12-word self-contained paradox. Demo is theatrical (judge watches a wallet appear from nothing) but requires explaining KZG WE in the pitch, costing 5-10 seconds of bandwidth.

**Honest framing:** the three lenses *don't* directly disagree on this option — they weren't all asked. The staleness lens (which surveyed the whole catalog) treats this as the strongest 2026-native fusion available. Market and wow weren't asked because the components fall outside the original 8 — inherited estimates put market at 6-7 (B2B drag) and wow at 8.5-9.0 (sci-fi pitch).

The honest read: **2026 hard-tech moat is strongest of the three. Wow factor is high but not class-leading. Commercial story is real but slowest to monetize. This is the only option that can simultaneously win Best Agentic AND Overall reserved seats** — a property neither OMNIVERSE nor SIGMA has.

## Sources
- `ideas/01-ai-agents/idea-01-sealed-model.md` — Sealed Model
- `ideas/01-ai-agents/idea-04-witness-encrypted-agent-wallet.md` — Witness-Encrypted Agent Wallet
- IACR 2024/264 — KZG witness encryption
- IACR 2025/1064 — *T+1-eWEB: Signature-Based Witness Encryption* (Glaeser, Madathil, 2025)
- Lagrange — DeepProve-1 (late 2025)
- ERC-8004 — Agent Identity Standard (Jan 2026 mainnet)
- ERC-4337 — Account Abstraction
- drand — distributed randomness beacon
- Citi GPS — *Agentic AI: The Next Investment Frontier* (agentic AUM forecast)
- Marlin / Phala TEE infrastructure (fallback option)
