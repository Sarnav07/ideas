# Idea 06: Self-Slashing EOTS Bond Wallet

## Pitch
*"Sign two conflicting messages and your wallet automatically pays your bond to the victim."*

## What it is
A DeFi safety primitive: any oracle, validator, sequencer, or LP that posts data signs each statement with an Extractable One-Time Signature (EOTS). If they equivocate (sign two different things from the same nonce), the algebraic structure of the signature *reveals their full private key*. Anyone can extract the key, drain the bonded wallet, and pay the victim — *permissionlessly*. Slashing without governance, challenge periods, or honest watchers.

## How it works
Babylon's Schnorr-EOTS construction: signature is `s = r + cx` for nonce `r`, challenge `c = H(msg, R)`, private key `x`. Sign twice on different messages → two equations `s₁ = r + c₁x`, `s₂ = r + c₂x` → solve for `x = (s₁ - s₂)/(c₁ - c₂)`. Wallet contract holds the bonded stake; key extraction lets anyone permissionlessly sign the withdrawal. Stylus contract verifies the secp256k1 EOTS scheme; on equivocation proof posted on-chain, the bond drains to the proof submitter who routes 90% to the victim.

## Why it lands (Orbital filter)
Distinct from "slash by governance vote" (every existing system): EOTS slashing is mathematical, instant, anyone-can-trigger. The pitch lands because "wallet pays itself out the moment you cheat" feels like sci-fi — the rebuttal ("you only lose if you actually equivocate") sells the asymmetry. Crypto's first true *automatic* punishment primitive.

## Future utility
1-year: every oracle (Chainlink-style price posts), every sequencer (Arbitrum-like order claims), every LP committing to quotes uses EOTS bonds. 3-year: insurance-grade DeFi requires EOTS commitments on counterparty actions. 5-year: EOTS becomes the default signing scheme for any "I will only say one thing about X" claim onchain — replaces challenge-period slashing entirely.

## Business model
Protocol layer: 50 bps of every bonded action posted through the EOTS verifier. At $10B annual notional flowing through bonded oracles/sequencers (a realistic mid-term DeFi number — Babylon staking alone hit $5B), $50M annual fee pool, $5M protocol share. Pure-infra revenue: every dApp using the verifier pays for the gas-and-protocol bundle. TAM: every slashing event in DeFi — currently fragmented across LSTs, EigenLayer AVS, oracle networks.

## Sponsor / track fit
**Overall $70K** — fundamental primitive that ships across many sponsors. **Stylus canonical** — secp256k1 algebra for EOTS extraction is the kind of cryptographic verifier Stylus exists for (30× cheaper than Solidity precompile chaining). **Robinhood Chain $30K** — RH retail wants bonded oracle pricing for tokenized equities; this is the credibility layer.

## 3-week MVP scope
- Week 1: Stylus secp256k1 EOTS verifier (Schnorr + extraction proof); test vectors from Babylon.
- Week 2: bonded oracle template (post-price-with-EOTS); equivocation-proof aggregator.
- Week 3: live demo with two adversarial oracles, equivocation detected, bond drained on-chain in one tx.

## Risks
- **Nonce-management UX** — accidental nonce reuse blows up benign signers. Mitigation: deterministic nonce (RFC 6979) + counter sharding per topic.
- **Adoption gap** — needs first integrator (oracle vendor) to commit. Mitigation: partner with one Pyth/RedStone-like network for launch.
- **Stylus precompile churn** — Arbitrum precompile changes. Mitigation: pure-Rust fallback path.

## Sources
- Babylon BTC Staking Litepaper (Schnorr-EOTS) — [docs.babylonlabs.io/papers/btc_staking_litepaper(EN).pdf](https://docs.babylonlabs.io/papers/btc_staking_litepaper(EN).pdf)
- Maxwell, Poelstra, Seurin, Wuille, *Simple Schnorr Multi-Signatures* — [IACR 2018/068](https://eprint.iacr.org/2018/068)
- RFC 6979 deterministic ECDSA — [tools.ietf.org/html/rfc6979](https://tools.ietf.org/html/rfc6979)
