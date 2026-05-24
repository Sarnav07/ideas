# Idea 05: HyperNova Folding — The Infinite Rollup in Your Browser

## Pitch
*"Fold a billion executions into one proof. Live, in the user's browser."*

## What it is
A folding scheme (Nova / HyperNova / NeutronNova family) where each new step of computation is "folded" into a running accumulator — the prover never has to re-prove old steps, and the resulting IVC (Incrementally Verifiable Computation) lets you prove arbitrarily long executions with constant-size state and one final SNARK. Critically: client-side. The math is light enough to run in a browser, on a phone, on a watch.

## How it works
Nova (Microsoft Research) introduced folding for R1CS in 2022. HyperNova (Kothapalli & Setty, CRYPTO 2024) generalized to CCS (which covers Plonkish, R1CS, AIR simultaneously) — the prover's per-step cost is a single MSM proportional to circuit width. NeutronNova (Kothapalli et al, IACR 2024/1606) folds *everything reducible to zero-check*, the most expressive folding scheme yet.

Onchain demo: a privacy-preserving payment-stream app. Every transfer the user makes locally folds into a personal IVC accumulator on their phone. At any point they can produce a single SNARK proving "I have transferred ≤$10k this month" or "I paid these merchants" — no recomputation, no trusted setup, no server. Settlement contract verifies one constant-size proof for an arbitrarily long history.

## Why it lands (Orbital filter)
"You can prove a million steps of computation in your browser" sounds like a violation of Big-O. The folding insight — that you don't need to re-prove, only to *combine* — is the same flavor of paradigm leap as Orbital's geometric generalization. Cheap recursion is the math people didn't think was possible.

## Future utility
- **1 yr:** browser-side ZK identity wallets (every claim folded into one proof); private payment streams; client-side rollup provers.
- **2-3 yr:** zkVMs where the prover runs on the user device, not a sequencer farm. Costs collapse 100×.
- **3-5 yr:** every meaningful onchain interaction comes with a folded proof attached. The "prove this happened" cost approaches zero.

## Business model
SDK and tooling — Nova-as-a-library for app devs (think "Stripe but for client-side ZK"). Premium tier: managed proving service for teams that don't want to ship WASM provers. Stylus precompile for the final HyperNova verifier — gas-optimized aggregation.

## Sponsor / track fit
- **Arbitrum Stylus** — final HyperNova verifier in Stylus is a clean win (BN254 ops, MSM batching).
- **Aztec / Aleo / privacy tracks** — folding is the prover for the next generation of privacy stacks.
- **Cryptography track** — first end-to-end IVC demo running on consumer hardware with onchain verification.

## 3-week MVP scope
- **W1:** Wire up Nova (`microsoft/Nova`) or Sonobe (Nova-family aggregator framework) compiled to WASM. Verify it runs in browser at 10+ folds/sec on a laptop.
- **W2:** Build the payment-stream app. Each user transfer folds into a personal accumulator. Periodic final SNARK published onchain.
- **W3:** Demo — user folds 10,000 transfers on a MacBook in <60s, posts a 5KB SNARK to Arbitrum, Stylus verifier accepts it.

## Risks
- **Technical:** folding accumulator must commit to opening polynomials — needs a clean Pedersen/IPA stack. Sonobe and Microsoft Nova both ship working implementations.
- **Performance:** per-step prover is fast (single MSM) but the *final* compression to a SNARK is heavy — needs Spartan or HyperPlonk on top. Budget the compression cost realistically.
- **Audit complexity:** folding security proofs are subtle; multiple papers have had bugs in their soundness arguments. Use audited libraries.

## Sources
- Kothapalli & Setty — *HyperNova: Recursive arguments for customizable constraint systems* (CRYPTO 2024) — [IACR 2023/573](https://eprint.iacr.org/2023/573)
- Kothapalli et al — *NeutronNova: Folding everything that reduces to zero-check* — [IACR 2024/1606](https://eprint.iacr.org/2024/1606)
- Kothapalli, Setty, Tzialla — *Nova: Recursive Zero-Knowledge Arguments from Folding Schemes* — [github.com/microsoft/Nova](https://github.com/microsoft/Nova)
- Mova variant — [IACR 2024/1220](https://eprint.iacr.org/2024/1220)
