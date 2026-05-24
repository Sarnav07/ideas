# Idea 08: Homomorphic Signatures — Prove Any Aggregate Without Revealing Rows

## Pitch
*"Sign a million numbers. Later, prove the average without revealing any of them."*

## What it is
A *linearly homomorphic signature* lets a signer sign each `xᵢ` once, and *anyone* (without the signing key) can produce a signature on `Σ wᵢ·xᵢ` for any chosen weights `w`. The verifier checks the aggregate signature against the original public key — proving the linear combination is genuine — without ever seeing individual `xᵢ`. Onchain, this is "prove this aggregate came from these signed rows" in one constant-size signature.

## How it works
Pointcheval & Sanders-style structure-preserving linearly homomorphic signatures (IACR 2023/1499) sign per-row with BLS-flavored randomizable signatures. Combiner publishes `σ = Π σᵢ^wᵢ`; verifier checks one pairing equation. Recent work (arXiv 2412.01641) gives tight-security lattice variants — post-quantum-ready.

Onchain demo: a CEX proof-of-solvency that doesn't dump the whole liability tree. Exchange signs each user's balance individually. To prove "we owe ≤ $10B aggregate," the exchange publishes a single homomorphic signature on `Σ balanceᵢ` — verifier checks one pairing equation, sees `total ≤ 10B`, never learns any individual balance. Subset proofs: "we owe ≤ $X to *these* users" without revealing the rest.

## Why it lands (Orbital filter)
"Sign a database. Later, prove any aggregate without revealing any row." Signatures usually authenticate the *exact* signed thing. Homomorphic sigs let *anyone* authenticate any linear combination they want — the verifier still believes it. Closest thing crypto has to "trust this query result."

## Future utility
- **1 yr:** proof-of-reserves that doesn't leak per-user balances; verifiable analytics ("our app's median load time is X").
- **2-3 yr:** ZK-coprocessor co-feature — Lagrange-style coprocessors return aggregate results with a homomorphic signature attached, no SNARK needed.
- **3-5 yr:** every signed dataset (sensor, census, financial filing) ships with a linearly-homomorphic signing key; downstream consumers compute any aggregate they want, free of the publisher.

## Business model
Per-aggregation fee (combiner is permissionless; the *attestor* who signs the raw rows charges). Subscription tier for downstream analytics consumers who want sub-query authentication. Stylus precompile for the verifier.

## Sponsor / track fit
- **Arbitrum Stylus** — pairing verifier in Rust; subset-randomization SNARK in Stylus.
- **Lagrange / EigenLayer** — natural pair with ZK coprocessors; replaces SNARK proofs of SUM/AVG with a one-pairing check.
- **Privacy / Audit tracks** — exchange proof-of-reserves is the canonical demo.

## 3-week MVP scope
- **W1:** Implement Pointcheval–Sanders-style linearly homomorphic sigs over BLS12-381 in Stylus.
- **W2:** Build the proof-of-solvency contract — exchange signs each user balance, posts aggregate sig + Pedersen commitment to the row set.
- **W3:** Demo — exchange with 100k simulated users posts a single signature proving total liabilities ≤ X; auditor verifies in one pairing; no per-user data leaked.

## Risks
- **Technical:** linearly homomorphic ≠ fully homomorphic. Only sums/weighted-averages — multiplicative aggregates (variance, products) need a different primitive (BBS+, mercurial signatures).
- **Forgery boundary:** signer must use independent randomness per row (otherwise key-recovery attacks via linear combinations). Need a hardened HSM workflow.
- **Adoption:** auditors trained on standard signatures need education; new tooling needed.

## Sources
- Bourse, Pointcheval, Sanders — *Linearly-Homomorphic Signatures for Short Randomizable Proofs of Subset Membership* — [IACR 2023/1499](https://eprint.iacr.org/2023/1499)
- *Linearly Homomorphic Signature with Tight Security on Lattice* — [arXiv 2412.01641](https://arxiv.org/pdf/2412.01641)
- *Towards Tightly Secure Short Linearly Homomorphic Signatures* — [ResearchGate](https://www.researchgate.net/publication/382733451_Towards_Tightly_Secure_Short_Linearly_Homomorphic_Signatures)
- Boneh, Freeman — *Linearly Homomorphic Signatures over Binary Fields* (the foundational paper)
