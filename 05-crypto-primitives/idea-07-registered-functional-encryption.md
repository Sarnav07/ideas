# Idea 07: Registered Functional Encryption — One Ciphertext, A Million Different Answers

## Pitch
*"Encrypt once. Every viewer sees only the slice they paid for."*

## What it is
Functional Encryption (FE) lets a ciphertext be decrypted *into a different function of the plaintext* depending on which key you hold — `f₁(x)`, `f₂(x)`, … but never `x` itself. *Registered* FE replaces the trusted-key-generator with a *key curator* who holds zero secrets — users register their own keys, the curator just publishes a Merkle-style aggregation. Onchain, the curator is the contract.

## How it works
Datta, Pal, Waters and others' line of work (IACR 2024/177, 2024/327, ASIACRYPT 2024) builds *Registered FE* for inner-product and quadratic functions from pairings + MDDH. Users post a public key; the contract aggregates into a master PK; subscribers receive function-specific keys that decrypt the FE ciphertext only to `⟨w, x⟩` for the weights `w` they hold. No private-key generator. No subpoena target. No escrow.

Onchain demo: a paid data feed. A weather provider publishes one FE-encrypted ciphertext per hour containing `(temp, humidity, wind, pressure, ...)`. Subscribers buy function-keys for the slices they want — agronomists pay for `(temp, humidity)` weighted average; energy traders pay for `(temp - threshold)·1{wind>X}`; nobody else can see the raw vector. The contract handles registration, payments, and key issuance permissionlessly.

## Why it lands (Orbital filter)
"One ciphertext. A million viewers. Each one sees a different answer." Decryption keys that compute *functions* — not reveal data — is a brain-bend for anyone who treats encryption as binary. The *registered* variant kills the key-escrow objection ("but who holds the master?") in one move.

## Future utility
- **1 yr:** premium data feeds (oracles, weather, financial), per-buyer slicing.
- **2-3 yr:** GDPR-compliant analytics — ad networks publish FE-encrypted user profiles; advertisers buy keys for the predicates they need. Raw data never leaves the source.
- **3-5 yr:** every API becomes function-encrypted by default. "Read access" gives way to "function access" — pay per query type, not per query.

## Business model
Per-key-issuance fee (one-time). Per-decryption fee (recurring). Marketplace for function-keys — sell "give me the 7-day moving average" key as an NFT. Stylus precompile licensing for L2s wanting native registered-FE verification.

## Sponsor / track fit
- **Arbitrum Stylus** — pairing-based FE verifier is Stylus-native; registration math fits cleanly into a Rust contract.
- **Lit Protocol / FHE / privacy stacks** — natural complement to threshold encryption; covers the "compute on encrypted data with sublinear key cost" gap.
- **Cryptography track** — first onchain registered FE deployment with a real revenue model.

## 3-week MVP scope
- **W1:** Implement Reg-IPFE (Datta–Pal–Waters from pairings) in Stylus. Inner-product is enough for v1 — weighted averages cover 80% of useful functions.
- **W2:** Build the data-feed marketplace contract — providers publish ciphertexts, subscribers register, contract issues function-keys for purchased weight vectors.
- **W3:** Demo: weather provider publishes a 10-dimensional FE ciphertext; three subscribers buy three different weight vectors; each sees only their function output, none sees the raw vector.

## Risks
- **Technical:** Reg-FE is limited to inner-product and quadratic functions today; circuit-class registered FE is bounded-collusion-resistant only (ASIACRYPT 2024). Don't oversell expressiveness.
- **Performance:** registration cost grows with the user set; periodic compaction needed.
- **Adoption:** new mental model — devs need clear docs explaining the function-key vs. decryption-key distinction.

## Sources
- Zhu, Datta, Pal, Waters — *Registered Functional Encryptions from Pairings* — [IACR 2024/327](https://eprint.iacr.org/2024/327)
- *Registered Functional Encryption for Quadratic Functions from MDDH* — [IACR 2024/177](https://eprint.iacr.org/2024/177)
- Francati, Friolo, Maitra, Malavolta, Rahimi, Venturi — *Registered (Inner-Product) Functional Encryption* (ASIACRYPT 2023) — [IACR 2023/395](https://eprint.iacr.org/2023/395)
- *Bounded Collusion-Resistant Registered Functional Encryption for Circuits* (ASIACRYPT 2024) — [Springer](https://dl.acm.org/doi/10.1007/978-981-96-0875-1_2)
