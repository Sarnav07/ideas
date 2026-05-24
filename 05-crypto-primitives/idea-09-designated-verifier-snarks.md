# Idea 09: Designated-Verifier SNARKs — Proofs That Are Worthless If Leaked

## Pitch
*"Prove something to your bank that's worthless if your bank leaks it."*

## What it is
A SNARK where only the designated verifier — holding a secret verification state — can be convinced. To everyone else, the proof is unverifiable garbage. *Strong* designated-verifier (DV) SNARKs go further: the verifier can themselves *simulate* an indistinguishable proof, so even if they leak it, no third party can tell the original from a fake. Cryptographic non-transferability.

## How it works
*Designated-Verifier zk-SNARKs Made Easy* (IACR 2024/1153) defines and constructs strong DV-SNARKs from two-party ring signature techniques — no encryption layer needed. The verifier holds a private key; the prover produces a proof that the verifier can check, and the verifier can also generate a *fake* proof that passes their own check. Anyone the verifier shows the proof to has zero reason to believe it (could be a fake the verifier made).

Onchain demo: a private credit-bureau API. Borrower wants to prove to Aave that their off-chain credit score is ≥700 without anyone else verifying. Aave holds a DV verification key; borrower produces a DV-SNARK. Aave is convinced. If Aave forwards the proof to Compound, Compound cannot verify it — and even if Compound trusts Aave, the proof is *simulatable by Aave*, so it carries zero attestation outside the original session. Credentials that cannot be replayed.

## Why it lands (Orbital filter)
"Prove something to one party that's worthless if they leak it." Every credentialing system today has the leak-and-replay problem — once you prove your salary to one lender, the proof is portable. DV-SNARKs sever that link with math. Anti-coercion, anti-replay, anti-data-broker. Single sentence shocks anyone who has had a credit-bureau experience.

## Future utility
- **1 yr:** private DeFi underwriting (lenders verify creds without re-exposing them); confidential KYC.
- **2-3 yr:** anti-coercion voting (voter can fake their own proof to anyone demanding evidence); whistleblower auth (prove identity to one journalist, fakeable to the world).
- **3-5 yr:** every credential issued in the ecosystem ships with DV mode as default — public proofs become opt-in, not default. Big shift in onchain ID.

## Business model
Per-verification fee paid to the credential issuer (insurance, banks, employers). Premium tier: DV-verifier-as-a-service for institutions that don't want to manage verification keys. Stylus precompile for L2s offering native DV verification.

## Sponsor / track fit
- **Arbitrum Stylus** — DV-SNARK verifier compiles cleanly to Stylus; less expensive than full Groth16.
- **Privacy / Wallets track** — the canonical demo (prove to a lender, fakeable elsewhere).
- **Cryptography track** — first onchain strong-DV-SNARK deployment.

## 3-week MVP scope
- **W1:** Port the IACR 2024/1153 construction (Circom impl exists). Verify the strong-DV property end-to-end.
- **W2:** Build the credit-underwriting demo — borrower produces a DV-SNARK of "credit score ≥ 700" against an off-chain attested dataset; Aave-style lender verifies on Arbitrum.
- **W3:** Live demo: borrower proves to lender, lender accepts; lender publishes the proof to a second lender; second lender's verifier rejects (different DV key).

## Risks
- **Technical:** strong-DV vs ordinary-DV is a subtle distinction; for true non-transferability you need strong-DV (the verifier-simulation property). Use only the IACR 2024/1153-class constructions.
- **Key management:** verifier private keys are sensitive — loss = inability to verify; theft = adversary can fake proofs to themselves but not impersonate.
- **Adoption:** DV-mode requires UX changes (verifiers must hold keys); not all credential consumers will adopt fast.

## Sources
- *Designated-Verifier zk-SNARKs Made Easy* — [IACR 2024/1153](https://eprint.iacr.org/2024/1153) / [Springer](https://link.springer.com/article/10.1007/s10207-025-01199-6)
- *Adaptively Sound Zero-Knowledge SNARKs for UP* — [IACR 2024/227](https://eprint.iacr.org/2024/227) (DV-SNARK for UP from sub-exp LWE)
- *Strong Designated-Verifier zk-SNARKs* — [Springer chapter](https://link.springer.com/chapter/10.1007/978-981-95-3182-0_23)
- *Fast and designated-verifier friendly zk-SNARKs in the BPK model* — [Cybersecurity journal](https://link.springer.com/article/10.1186/s42400-025-00432-y)
