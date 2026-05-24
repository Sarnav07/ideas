# Idea 14: RLN Airdrop Faucet

## Pitch
*"Claim airdrops anonymously. Greed past the rate limit and your wallet self-doxxes."*

## What it is
A Sybil-resistant token-claim faucet using Rate-Limit Nullifiers: claim anonymously up to the per-epoch limit, but the moment you try to over-claim, the cryptographic construction *automatically* leaks your identity and bans your nullifier forever.

## How it works
Each user's claim consists of a Semaphore-style ZK membership proof + an RLN polynomial share. The protocol fixes a degree-K polynomial; each anonymous claim posts a new (x, y) share. Claiming K+1 times within an epoch lets *anyone* interpolate the polynomial and recover the user's secret key. Over-claimers expose themselves; honest users stay anonymous forever.

## Why it lands (Orbital filter)
"Anonymous airdrops where greed self-dox" is the perfect 8-word paradox. Same Orbital DNA as [[idea-02-anti-sybil-personhood-bond]] but applied to the most-mocked broken primitive in crypto: airdrops.

## Future utility
1-year: anti-Sybil claim mechanism for major token launches ($XXM airdrops). 3-year: standard primitive replacing snapshot-and-vouch Sybil filters. 5-year: foundational rate-limited-anonymity layer for Web3 chat, DAO voting, and reputation faucets.

## Business model
- Airdrop SaaS: 0.5% of airdrop notional managed via RLN claim.
- Anti-Sybil consultancy: $25k engagement for projects setting custom rate-limits.
- Open-source core, paid managed-relay. With ~$2B/yr in airdrop volume across major launches, even 5% market share at 0.5% = $500k/yr.

## Sponsor / track fit
- **Privacy track** — anchor application of RLN beyond messaging (where it was originally designed for Status chat).
- **Arbitrum Stylus** — efficient polynomial-interpolation slasher in Rust.
- **Token-launch / community track** — direct ecosystem value.

## 3-week MVP scope
- RLN circuit (reuse Vac/Privacy & Scaling Explorations RLN-v3) compiled to Groth16.
- Stylus claim contract: verifies proof + stores polynomial share; auto-detects K+1th share and slashes.
- Demo airdrop: 1000 ETH pool, 10 ETH per claim, K=1 per epoch. 5 Sybil attempts → 5 nullifiers leaked + permanently banned.
- Integration: drop-in replacement for Merkle-Distributor.

## Risks
- **Technical:** RLN-v3 polynomial-share leakage is computational; need careful selection of K and epoch parameters.
- **UX:** users don't understand "rate limit" until they hit it — clear in-wallet messaging required.
- **Coordinator risk:** RLN typically needs an off-chain coordinator for share aggregation; can be replaced with on-chain mempool in cheap-gas Stylus environment.

## Sources
- *Rate-Limiting Nullifier: A Spam-Protection Mechanism for Anonymous Environments* (IACR 2025/1030) — https://eprint.iacr.org/2025/1030
- Privacy & Scaling Explorations / RLN repo — https://github.com/Rate-Limiting-Nullifier
- Semaphore — https://semaphore.pse.dev/
- See also: [[idea-02-anti-sybil-personhood-bond]], [[idea-06-traceable-ring-signatures]]
