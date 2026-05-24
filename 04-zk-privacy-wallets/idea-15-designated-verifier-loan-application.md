# Idea 15: Designated-Verifier Loan Application

## Pitch
*"Show your credit score to one lender. The proof is useless to everyone else."*

## What it is
A credit-application primitive where the borrower's reputation / income / on-chain history proof is cryptographically usable only by the specific lender it was generated for. Shopping rates across 5 lenders means generating 5 separate proofs — and even if one leaks, no other lender (or data broker) can use it.

## How it works
The borrower computes a ZK proof over their on-chain credit history (income receipts via zkTLS, repayment history via Lagrange coprocessor, etc.) using a Designated-Verifier SNARK bound to the lender's pubkey. The lender verifies the proof, but the proof has the *non-transferability* property: the lender could have forged it themselves, so the proof is meaningless to any third party.

## Why it lands (Orbital filter)
"Apply for credit without your data ever leaving your wallet for someone else's use" lands instantly with anyone who's been credit-shopped or had data brokers harvest their score.

## Future utility
1-year: anti-data-broker credit shopping for crypto loans. 3-year: standard credit-decisioning primitive for institutional DeFi (Maple, Goldfinch). 5-year: regulatory mandate in jurisdictions like the EU (GDPR data-minimization).

## Business model
- Per-proof fee: $0.50 per submitted application (borrower pays).
- Lender SaaS: $10k/mo per institution for the verifier+blocklist API.
- Insurance: 5bps on funded loans (covers verifier-side mis-decisioning). $5B/yr funded loans × 5bps = $2.5M.

## Sponsor / track fit
- **Lagrange** — ZK coprocessor for on-chain credit-history queries.
- **Arbitrum Stylus** — DVS verifier + lender API.
- **DeFi / lending track** — pairs with [[idea-02-anti-sybil-personhood-bond]] for full undercollateralized credit stack.

## 3-week MVP scope
- DVS proof circuit over a synthetic credit object (repayment history merkle root + income oracle attestation).
- Stylus lender-side verifier.
- Demo: alice has 12 months of repayments + Stripe-zkTLS payslip. She applies to lender-A and lender-B with two separate DVS proofs. Lender-A leaks her proof; lender-B's verification of the same bytestring fails because pubkey-binding mismatches.
- Bonus: borrower can revoke + re-issue a proof if a lender mis-uses it (the leak proves it was lender-A, since only lender-A could have produced the convincing proof).

## Risks
- **Technical:** DVS proof generation is heavier than standard SNARK (~3-5× constraint count).
- **Lender adoption:** lenders prefer transferable proofs (resell to data brokers). Counter: regulation will force this in 2-3 years.
- **Repudiation defense:** the "lender could have forged it" property cuts both ways — borrowers can deny they sent the proof, weakening contract enforcement.

## Sources
- Li & Zhang, *Designated-Verifier SNARKs Revisited* (IACR 2024/1153) — https://eprint.iacr.org/2024/1153
- Lagrange ZK Coprocessor — https://www.lagrange.dev/
- DECO zkTLS (Zhang et al., CCS 2020) — https://arxiv.org/abs/1909.00938
- See also: [[idea-07-designated-verifier-credentials]], [[idea-02-anti-sybil-personhood-bond]]
