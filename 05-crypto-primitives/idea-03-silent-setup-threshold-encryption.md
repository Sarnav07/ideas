# Idea 03: Silent-Setup Threshold Encryption — Decrypt Committees Without Ceremonies

## Pitch
*"A 1,000-validator decryption committee that never had a ceremony."*

## What it is
A threshold encryption (TE) primitive where the joint public key is a *deterministic function* of each party's locally-generated key. No DKG, no rounds of communication, no trusted dealer — every validator posts one public key once and the system has a working t-of-n decryption committee forever. Threshold and signer set can be chosen dynamically *after* the silent setup.

## How it works
Garg–Kolonelos–Policharla–Wang's *Threshold Encryption with Silent Setup* (CRYPTO 2024) and the companion *hinTS: Threshold Signatures with Silent Setup* (IEEE S&P 2024) build this from BLS + a single succinct "hint" each party posts at registration. Aggregation produces a master public key; decryption requires t-of-n partial decryptions that anyone can combine. Dynamic membership: validators rotate in/out by posting/revoking hints — no global ceremony.

Onchain demo: a sealed encrypted mempool on Arbitrum where every L2 validator is implicitly a decryption committee member. Users encrypt transactions to the aggregated public key. After block N is sealed, validators post their partial decryptions; anyone aggregates. New validators can join the committee mid-epoch with a single tx — no coordinated DKG, no liveness assumption on the existing set.

## Why it lands (Orbital filter)
Every threshold scheme in production today (drand, Distributed Validator Tech, FROST) requires a multi-round DKG ceremony — *the* operational nightmare. "What if the ceremony was unnecessary" sounds impossible to anyone who has run one; the *hint* mechanism makes it true. Inverts the "trusted setup" mental model.

## Future utility
- **1 yr:** encrypted mempools that don't need bespoke validator sets; sealed-bid auctions with dynamic juries.
- **2-3 yr:** every L2 ships with a native silent-setup decryption oracle. New validators join trustlessly; offboarding is a single tx.
- **3-5 yr:** silent-setup becomes the default for *any* multi-party crypto on chains — randomness, decryption, signatures. DKGs disappear from production cryptography.

## Business model
Toll bridge — per-decryption fee paid to participating validators (Lit Protocol model, but without the centralized PKP coordinator). Premium tier: SLA-backed decryption service for institutional clients (auction operators, custody flows). Stylus precompile licensing.

## Sponsor / track fit
- **Arbitrum / Stylus** — silent-setup verifier is BLS pairings + a polynomial-commitment check; Stylus-native.
- **EigenLayer** — restaked operator mesh becomes the validator set; slashing for non-decryption.
- **Cryptography track** — first deployment of silent-setup TE on a public L2.

## 3-week MVP scope
- **W1:** Port hinTS / silent-setup TE to Stylus. Reuse Hedera's reference impl ([hinTS PDF](https://hedera.com/wp-content/uploads/2025/11/hinTS_Threshold_Signatures_with_Silent_Setup.pdf)) as a starting point.
- **W2:** Stand up a sealed encrypted mempool: encrypt-to-aggregated-PK at submit time; validators post partial decryptions after block close.
- **W3:** Live demo — 100 simulated validators, dynamic add/remove mid-epoch, encrypted tx volume of 1k/min.

## Risks
- **Technical:** security proven in the algebraic group model — audit-grade deployments need disclosure. Forward security claims require validator key rotation.
- **Performance:** aggregation is `O(n)` group ops at decrypt time; for 1k-validator sets needs precomputation.
- **Adoption:** integrating with existing validator sets requires governance; smaller L2s adopt first.

## Sources
- Garg, Kolonelos, Policharla, Wang — *Threshold Encryption with Silent Setup* (CRYPTO 2024) — [IACR 2024/263](https://eprint.iacr.org/2024/263) / [Springer](https://link.springer.com/10.1007/978-3-031-68394-7_12)
- Garg, Jain, Mukherjee, Sinha, Wang, Zhang — *hinTS: Threshold Signatures with Silent Setup* (IEEE S&P 2024) — [IACR 2023/567](https://eprint.iacr.org/2023/567)
- IACR artifact archive — [artifacts.iacr.org/crypto/2024/a4](https://artifacts.iacr.org/crypto/2024/a4/)
- Walkthrough — [Silent Threshold Encryption Simplified](https://hackmd.io/@guruvamsi-policharla/S1WuMrAFxe)
