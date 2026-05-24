# Cat 5 — Discarded Primitives

Primitives that were considered but didn't pass the Orbital filter (pitch ≤15 words, capability surfaces in one beat, concrete onchain application). Same cut codes as `/Open-House/DISCARDED.md`.

---

## Cut Codes
- **[CR-5] Too infra-y / not productable** — pitch is plumbing, not user-facing magic
- **[CR-7] Mathematically beautiful, no demo** — primitive is exotic but no 60-sec demo
- **[CR-3] Already shipped or in the air** — better-pitched variant elsewhere in FRONTIER.md
- **[CR-4] Pitch needs unpacking** — requires 2+ sentences before the lean-in
- **[CR-1] Pitch needs domain context** — lands only for crypto/math insiders

---

## Cuts

### Indistinguishability Obfuscation (iO) — JLS 2021+
**Pitch attempted:** *"A smart contract whose source is encrypted but still runs."*
**Cut: [CR-7]** — S-tier pitch but iO at any meaningful throughput is impossible today; even Jain-Lin-Sahai 2021 schemes are millions of orders of magnitude too slow for a 3-week MVP. Will be revisited in 5 years.
- Jain, Lin, Sahai — [IACR 2020/1003](https://eprint.iacr.org/2020/1003)

### Plain BLS Aggregate Signatures
**Pitch attempted:** *"Combine 1,000 signatures into one."*
**Cut: [CR-3]** — already in production (Ethereum consensus, Cosmos, drand). Not Orbital-fresh.
- Boneh, Lynn, Shacham — original BLS paper

### Lattice Verifiable Delay Functions
**Pitch attempted:** *"Slow-computed randomness that even a quantum adversary can't shortcut."*
**Cut: [CR-5]** — already cut in `/Open-House/DISCARDED.md`. Application is just "fair lottery," which idea #04 (Wesolowski VDF) covers with a deployable primitive.

### Generic FROST DKG / Threshold Schnorr
**Pitch attempted:** *"Sign with N parties, none of whom hold the full key."*
**Cut: [CR-3, CR-5]** — Squads, Lit, Sodium all ship variants. Not novel; idea #03 (silent setup) is the upgrade angle.

### Snake-Eye Resistant PKE (standalone)
**Pitch attempted:** *"A public key that lets you send a message but not prove you sent one."*
**Cut: [CR-5]** — flagged in master DISCARDED.md as plumbing for OMR. Without an OMR-specific application demo, the user-facing pitch is too abstract.
- Liu, Sotiraki, Tromer, Wang — [IACR 2024/510](https://eprint.iacr.org/2024/510)

### Statement-Oblivious Witness Encryption
**Pitch attempted:** *"A committee decrypts your message but never learns the condition."*
**Cut: [CR-4, CR-7]** — already cut in master DISCARDED. Beautiful primitive, demo is hard to make visceral.
- Bormet et al. — [IACR 2023/668](https://eprint.iacr.org/2023/668)

### Cassiopeia (puzzle-witness encryption)
**Pitch attempted:** *"An oracle that publishes the answer only if you prove you solved a puzzle."*
**Cut: [CR-3]** — same witness-encryption family as idea #01 (KZG WE), less universal application.
- Madathil, Scafuro, Seemakhupt — [IACR 2023/635](https://eprint.iacr.org/2023/635)

### Verifiable Homomorphic Secret Sharing
**Pitch attempted:** *"Two servers split your data, compute on it, and prove the answer is right."*
**Cut: [CR-5]** — already in master DISCARDED. Pure infra primitive.

### Traceable VRFs
**Pitch attempted:** *"If a validator leaks their VRF key, the leak traces back to them."*
**Cut: [CR-1, CR-6]** — already in master DISCARDED. Validator-internal; niche.
- Boneh, Partap, Rotem — [IACR 2025/312](https://eprint.iacr.org/2025/312)

### TFHE primitives (bootstrapping, programmable bootstrap)
**Pitch attempted:** *"Run a logic gate on encrypted bits — fast enough to be practical."*
**Cut: [CR-5]** — pure plumbing. The interesting product layers (FHE AMM, FHE perp, FHE vault) all sit on it but each is independently CR-7 due to latency. Better as a building block, not as a standalone Cat-5 pick.

### Beaver Triples / Replicated Secret Sharing (MPC primitives)
**Pitch attempted:** *"Two parties compute on a secret neither can see."*
**Cut: [CR-3, CR-5]** — every MPC stack has these. Not a fresh primitive.

### Hardware-attested primitives (Intel TDX, SEV-SNP, Nvidia confidential H100)
**Pitch attempted:** *"Compute on a server even the server can't peek into."*
**Cut: [CR-3]** — TEE-based primitives are well-trodden (Marlin, Phala, Oasis). Covered as deployment infra in other categories (#22 Forecasting Cohort, #28 TEE Dark Pool).

### Pietrzak VDF
**Pitch attempted:** Same as Wesolowski VDF.
**Cut: [CR-3]** — Wesolowski (idea #04) has shorter proofs and cleaner verification; Pietrzak is the runner-up in the same family.

### Recursive STARK aggregation (Plonky3, Boojum)
**Pitch attempted:** *"Aggregate a million STARK proofs into one."*
**Cut: [CR-5]** — infrastructure for rollup provers (Polygon zkEVM, zkSync); not user-facing. The IVC/folding angle (idea #05) is the more pitch-friendly cousin.

### Sumcheck-based proof systems (standalone)
**Pitch attempted:** *"A proof system where the verifier checks one polynomial identity."*
**Cut: [CR-1, CR-5]** — sumcheck is *infrastructure* for Spartan, HyperPlonk, Jolt — covered by idea #06 (which uses Lasso, which uses sumcheck). Standalone pitch doesn't land.

### Programmable Cryptography Manifestos (PCD, IVC philosophy)
**Pitch attempted:** *"The math layer of programmability."*
**Cut: [CR-4, CR-5]** — too abstract; the *specific instantiations* (idea #05 folding, #06 zkVM) are the demoable artifacts.

### Falcon / Dilithium (post-quantum signatures)
**Pitch attempted:** *"Sign your transactions in a way that survives quantum computers."*
**Cut: [CR-3]** — NIST standardized; multiple wallet projects shipping. PACTs (FRONTIER #5) is the pitch-friendly version. Standalone PQ-sigs is incremental.

### Anonymous Liquid Democracy / Copy-Robust Voting
**Pitch attempted:** *"Your delegate's delegate's delegate votes for you — and can't betray you."*
**Cut: [CR-4]** — already in master DISCARDED. Better fit for Cat 6 (Governance) if revived.

---

## If you want to argue back

Most legit candidates for re-promotion:
- **iO** if a meaningful subset (compact-FE-style iO from LWE, IACR 2024 line of work) becomes hackathon-buildable — pitch is too good to leave parked forever.
- **Snake-eye Resistant PKE** if paired with a clean OMR demo — has the right paradox shape if the application surfaces.
- **Traceable VRFs** if pitched as "validator-grade anti-collusion" — niche but rising in importance with restaking.
