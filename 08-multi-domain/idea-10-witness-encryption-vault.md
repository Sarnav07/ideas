# Idea 10: Witness Encryption Vault — Encrypt to Any Future On-Chain Condition

## Pitch
*"Encrypt a secret that unlocks only if the chain reaches a specific state."*

## What it is
A productized witness-encryption layer: any contract publishes a ciphertext keyed to an arbitrary on-chain predicate (BLS signature emitted, transaction included, oracle price crossed, ERC-8004 attestation issued). The ciphertext is decrypted automatically — by anyone — once that predicate is satisfied. No committee, no trusted dealer, no time-lock; the *event itself* is the key.

## How it works
- Uses signature-based witness encryption (SWE) — encrypt-under-statement, decrypt-under-witness (a BLS signature satisfying the statement).
- Statement examples: "drand emits round R" (composes with Idea #01), "Pyth feed X crosses Y", "ERC-8004 agent A receives attestation Z from issuer I".
- Anyone who observes the witness signature can decrypt; the predicate is the discriminator.
- Avitabile et al. (2024) brought ciphertext size to ~constant; Glaeser et al. (2025) added on-chain efficient verifiers for the SWE family.

## Why it lands (Orbital filter)
Time-lock encryption is "the future will decrypt me". Witness encryption is *"a specific future event will decrypt me — and only it"*. That distinction is huge: bug-bounty payouts that auto-release on exploit confirmation; inheritance that triggers on attested death; insurance that pays the second the oracle fires; agent wallets that activate on job completion (FRONTIER #9 generalized).

## Cross-domain applications
- **AI agents**: agent wallet's signing key is encrypted to "ERC-8004 attestation `job_complete` exists" — the key materializes the moment the agent earns it (FRONTIER #9).
- **Inheritance**: ciphertext containing heirs' decryption key, encrypted to "no heartbeat from owner in N days" (FRONTIER #17 generalized to any heartbeat oracle).
- **Bug bounties**: full exploit details encrypted to "patched code hash X deployed at block ≥ Y"; auto-decrypts post-fix.
- **Prediction markets**: outcome data encrypted to "UMA finalizes proposal P"; eliminates race conditions on settlement.
- **Insurance**: payout key encrypted to "USGS attestation of magnitude ≥ 7 at coord (lat,long)"; instant release on event.
- **Escrow**: deal terms encrypted to "both signatures present on attestation A"; no escrow agent needed.
- **Whistleblowing**: leaks encrypted to "court order on docket D"; revealed only with judicial witness.

## Future utility
1-yr: 3-5 high-profile WE applications shipped (inheritance, bug bounties, agent wallets). 3-yr: WE becomes the default for any "if/then" off-chain payload. 5-yr: legal contracts cite WE encryption hashes as enforceable conditional-disclosure clauses.

## Business model
- Per-ciphertext registration fee + per-decryption gas reimbursement to relayers.
- Premium: hosted ciphertext storage (IPFS / Arweave / Filecoin pinning).
- TAM: niche per-app but cumulative. Inheritance alone is a $X trillion intergenerational transfer problem; capturing 0.001% in fees = $10M+/yr. Bug bounty market is $1B/yr; even 1% = $10M.

## Sponsor / track fit
- **Arbitrum Stylus** — BLS pairing-heavy verifier; Stylus is mandatory for cost-effective WE.
- **Overall track** — sci-fi-grade primitive with multiple visceral demos (inheritance, bug bounty).
- **Robinhood Chain** — conditional disclosure of regulated documents (M&A escrow, IPO docs released on SEC filing).

## 3-week MVP scope
- `WitnessVault.sol` (Stylus) — ciphertext registry + BLS-aggregate verifier for SWE.
- SDK: `witness-encrypt-cli` for encryption against a JSON predicate.
- Three demo apps sharing the vault:
  1. **Witness-encrypted agent wallet** (FRONTIER #9): agent's signing key auto-materializes on `job_complete` attestation.
  2. **Dead-man-switch inheritance** (FRONTIER #17): heir key auto-decrypts on missed heartbeat round.
  3. **Auto-release bug bounty**: full PoC code released to bounty hunter on confirmed patch deployment.
- README: cite Avitabile, Glaeser, Madathil/Scafuro.

## Risks
- **Cryptographic novelty** — SWE constructions are <2 years old; corner cases possible. Mitigate by using audited primitives only (Avitabile 2024 + Glaeser 2025) and limiting predicates to BLS-verifiable.
- **Predicate expressiveness** — not every condition has a clean BLS witness. Scope MVP to drand rounds, ERC-8004 attestations, Pyth feed crossings.
- **Latency** — decryption requires the witness signature to be observable. For instant payouts, rely on always-online relayers.

## Sources
- [Avitabile et al., *SWE with Compact Ciphertext* — IACR 2024/1477](https://eprint.iacr.org/2024/1477)
- [Glaeser/Madathil/Scafuro, *T+1-eWEB* — IACR 2025/1064](https://eprint.iacr.org/2025/1064)
- [Madathil/Scafuro/Seemakhupt, *Cassiopeia* — IACR 2023/635](https://eprint.iacr.org/2023/635)
- [Fleischhacker/Hall-Andersen/Simkin, *Extractable WE for KZG* — IACR 2024/264](https://eprint.iacr.org/2024/264)
- [*Secure Autonomous Agent Payments* — arXiv 2511.15712](https://arxiv.org/abs/2511.15712)
- [BqETH whitepaper](https://bqeth.com/) — production reference for WE-based escrow
