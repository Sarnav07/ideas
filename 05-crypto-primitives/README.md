# Category 5 — Crypto Primitives (10 Ideas)

Pure cryptographic primitives that enable *new applications* — not full products, but the math layer that makes a new product class possible. Every entry pairs a primitive with a concrete onchain demo so the *capability* sells itself (not the math).

**Curation rule:** the pitch must surface the *capability* in ≤15 words to trigger "wait, how?" Plumbing-only entries (silent setup as infra, generic FROST DKGs, generic adaptor sigs) were rejected — see `discarded.md`. The remaining 10 each ship a demo a smart generalist can grok in one beat.

---

## Index

| # | Idea | Pitch | Primitive | Sponsor sweet spot |
|---|---|---|---|---|
| 01 | [KZG Witness Encryption — Conditional Payments](./idea-01-kzg-witness-encryption-conditional-payments.md) | *"Encrypt money that unlocks itself the instant a public proof exists."* | KZG extractable WE | Arbitrum Stylus, Lagrange |
| 02 | [Tempora-Fusion Homomorphic Time-Lock](./idea-02-tempora-fusion-homomorphic-timelock.md) | *"Sum encrypted bids while they're still locked."* | Verifiable homomorphic TLP | Flashbots, MEV defense |
| 03 | [Silent-Setup Threshold Encryption](./idea-03-silent-setup-threshold-encryption.md) | *"A 1,000-validator decryption committee that never had a ceremony."* | hinTS / silent-setup TE | Arbitrum, EigenLayer |
| 04 | [Wesolowski VDF Lottery](./idea-04-wesolowski-vdf-uncheatable-lottery.md) | *"Randomness that costs an hour to produce and a millisecond to verify."* | Wesolowski / class-group VDF | Arbitrum Stylus, NFT mints |
| 05 | [HyperNova Folding — Infinite Rollup in the Browser](./idea-05-hypernova-folding-infinite-rollup.md) | *"Fold a billion executions into one proof. Live, in the user's browser."* | Nova / HyperNova / NeutronNova IVC | Arbitrum, privacy stacks |
| 06 | [Jolt zkVM — Prove Any Rust Program in Seconds](./idea-06-jolt-zkvm-instant-rust-proofs.md) | *"Run a Rust program. Prove it ran. In one second."* | Jolt + Lasso lookups | Arbitrum Stylus, a16z |
| 07 | [Registered Functional Encryption](./idea-07-registered-functional-encryption.md) | *"Encrypt once. Every viewer sees only the slice they paid for."* | Reg-IPFE from pairings | Oracle / data-feed tracks |
| 08 | [Homomorphic Signatures — Aggregates Without Rows](./idea-08-homomorphic-signatures-subset-proofs.md) | *"Sign a million numbers. Later, prove the average without revealing any."* | Linearly homomorphic signatures | Audit, proof-of-reserves |
| 09 | [Designated-Verifier SNARKs](./idea-09-designated-verifier-snarks.md) | *"Prove something to your bank that's worthless if they leak it."* | Strong DV-SNARKs | Privacy / identity tracks |
| 10 | [Publicly Verifiable Deletion](./idea-10-publicly-verifiable-deletion.md) | *"Anyone can verify your data was deleted — even a future quantum computer."* | LWE-based PVD | Privacy, regulatory tracks |

---

## Top 3 (if forced to pick)

### #01 — KZG Witness Encryption
**Why:** the cleanest "money that unlocks itself" pitch. Single pairing per op, audit-grade impl already exists ([rot256/research-we-kzg](https://github.com/rot256/research-we-kzg)), Stylus-native. The bug-bounty demo is universal — no DeFi knowledge required. Same paper family as FRONTIER #6 (Sealed Model) but a different *application slice* (conditional payments vs. ML weight escrow), so co-builds cheaply.

### #06 — Jolt zkVM
**Why:** the closest crypto has to "the SQL moment for ZK" — devs write Rust, get a proof, ship onchain. EUROCRYPT 2024 best paper energy. Arbitrum Stylus is a perfect host (Rust on both sides). The "submit any pricing function in Rust, settle onchain" demo is hackathon catnip and points at a real billion-dollar future.

### #05 — HyperNova Folding (Browser IVC)
**Why:** folding is the inflection that ends the "ZK is for sequencer farms" mindset — proving moves to the client. CRYPTO 2024 paper, NeutronNova follow-up adds expressiveness. The 60-second demo ("fold 10k transfers on a MacBook → 5KB proof → Stylus verifier accepts") is mathematical reality and audience whiplash.

---

## Domain spread

- **Witness / time-lock encryption family**: 01, 02
- **Threshold cryptography**: 03
- **Verifiable computation / IVC / zkVM**: 04 (VDF as verifiable compute), 05, 06
- **Functional encryption**: 07
- **Signature primitives**: 08
- **Proof systems with secrecy properties**: 09
- **Post-quantum / deletion**: 10

Spread is intentionally heavy on the *next-wave* primitives (WE, registered FE, PVD) the FRONTIER.md applications depend on, with one foundational pick from each major proof-system family (Jolt = lookup-based; HyperNova = folding-based).

---

## Coordination notes

- **Cat 4 (ZK/Privacy/Wallets) overlap avoided:** FRONTIER #5 (PACTs), #15 (tlock sealed-bid), #17 (Dead-Man-Switch), #19 (Traceable Ring Sigs), #9 (Witness-Encrypted Wallet) are likely Cat 4 picks — distinct from these 10 primitives, which sit one layer below.
- **Cat 4 may also want:** Designated-Verifier (idea #09) as a privacy wallet feature, or PVD (#10) as an identity hygiene feature. If so, this README defers — pick the layer where each shines hardest.
- **Stylus showcase potency:** #04, #06, #08 are all Stylus-native pairing/MSM workloads; ideal Arbitrum demos.

---

## Sources index (master list)

- [IACR ePrint 2024/264](https://eprint.iacr.org/2024/264) — KZG Witness Encryption (Fleischhacker et al)
- [arXiv 2406.15070](https://arxiv.org/abs/2406.15070) — Tempora-Fusion (Abadi)
- [IACR 2024/263](https://eprint.iacr.org/2024/263) / [IACR 2023/567](https://eprint.iacr.org/2023/567) — Silent-setup TE / hinTS
- [Stanford VDF survey](https://crypto.stanford.edu/~dabo/pubs/papers/VDFsurvey.pdf) — Wesolowski VDF
- [IACR 2023/573](https://eprint.iacr.org/2023/573) — HyperNova
- [IACR 2024/1606](https://eprint.iacr.org/2024/1606) — NeutronNova
- [IACR 2023/1217](https://eprint.iacr.org/2023/1217) — Jolt zkVM
- [IACR 2024/327](https://eprint.iacr.org/2024/327) — Registered FE from pairings
- [IACR 2023/1499](https://eprint.iacr.org/2023/1499) — Linearly homomorphic sigs
- [IACR 2024/1153](https://eprint.iacr.org/2024/1153) — Strong DV-SNARKs
- [IACR 2024/1596](https://eprint.iacr.org/2024/1596) — Secret Sharing with PVD
