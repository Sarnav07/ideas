# Idea 04: Witness-Encrypted Agent Wallet

## Pitch
*"An AI agent wallet whose private key only exists if it does its job."*

## What it is
A smart-account wallet whose signing key is *not stored anywhere*. Instead, it is encrypted under a signature-based witness-encryption scheme such that the decryption key only materializes when the drand beacon publishes the BLS signature that attests "the agent completed task T at block N." If the agent fails, the wallet remains a dead address — funds can't be spent, scammers can't drain it.

## How it works
- User defines a task predicate `T` (e.g., "deliver this email," "settle this trade," "publish this report").
- An attestation contract on Arbitrum will emit `done(T)` only when the predicate verifies (zkTLS receipt, oracle, or peer-attestation).
- drand publishes a deterministic BLS signature per block; we encrypt the agent's signing key to *"the drand signature for the first block after `done(T)` is emitted."*
- Before completion: no signature exists → key uncomputable → wallet inert.
- On completion: signature publishes → anyone can decrypt → agent signs once → wallet drains and the agent gets paid.

## Why it lands (Orbital filter)
Everyone's mental model of a wallet is "a key inside a vault." Inverting that — *the wallet has no key until it earns one* — breaks the model in 12 words. Beats every "agent wallet with policy guardrails" pitch on the market.

## Future utility
**1 year:** Replaces the dev-painful "AI agent has a hot key in a TEE" pattern. **3 years:** Default custody for any autonomous agent paid for work. **5 years:** Universal pattern for outcome-bonded payments — freelance contractors, DAO bounties, agent-to-agent commerce.

## Business model
- 25 bps protocol fee on every witness-encrypted withdrawal.
- Bonded agent vault TAM: project agent-managed assets reach **$50B by 2027** (Citi GPS Forecast, agentic web). 25 bps of 5% turnover = **~$6M/year**.
- Premium tier: structured-outcome composition (e.g., "release 30% on milestone 1, 70% on milestone 2") at $20–500/setup.

## Sponsor / track fit
- **Best Agentic ($15K)** — direct ERC-8004 + ERC-4337 composition.
- **Robinhood Chain ($30K)** — payment-rail flavor; consumer-facing "set and forget" agent payouts.
- **Overall ($70K)** — sci-fi pitch with a working demo.

## 3-week MVP scope
- ERC-4337 smart wallet that delegates signature derivation to a Drand watcher Stylus contract.
- Signature-based witness encryption library (port from Glaeser/Madathil 2025 IACR 2025/1064 reference impl).
- Single-task predicate: agent must post a zkTLS-attested HTTPS-200 to a target URL.
- Demo: deploy wallet pre-funded with USDC, run an agent, watch the wallet drain only after the target URL returns the magic string.

## Risks
- **Drand dependency** — drand is currently the only multi-curve threshold beacon. Mitigation: support multiple beacons (drand + EigenLayer-restaked).
- **Race conditions** — once the witness signature publishes, anyone can compute the key. Front-running mitigated by Schnorr nonce + agent-only co-signer in the predicate.
- **WE library maturity** — uses pairing-friendly curves only available via Stylus precompile (BLS12-381). Acceptable in 2026.

## Sources
- Glaeser, Madathil, Scafuro, *T+1-eWEB* — https://eprint.iacr.org/2025/1064
- *Secure Autonomous Agent Payments* — https://arxiv.org/abs/2511.15712
- Burdges et al., *tlock* — https://eprint.iacr.org/2023/189
- drand specification — https://docs.drand.love/
