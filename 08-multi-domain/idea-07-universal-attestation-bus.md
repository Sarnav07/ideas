# Idea 07: Universal Attestation Bus — EAS as a Cross-Domain Reputation Spine

## Pitch
*"Any address. Any claim. Any chain. One attestation graph."*

## What it is
A productized Ethereum Attestation Service (EAS) deployment on every Arbitrum Orbit chain plus a cross-chain attestation indexer. Anyone — KYC providers, oracles, AI auditors, DePIN operators, DAOs — issues structured, schema-typed attestations against any subject (address, contract, off-chain hash). Consumer contracts query the bus for "show me all attestations of schema X about subject Y from issuers in set Z" and compose policies on top.

## How it works
- EAS contracts deployed on every target chain; schemas are content-addressed (`bytes32 schemaUID`).
- Attestations are signed payloads stored either on-chain (revocable, public) or off-chain (Merkle-committed).
- A LayerZero/Wormhole-backed indexer aggregates attestations across chains under each subject identifier.
- Consumer contracts use the bus via standard library calls; no per-issuer custom integration.

## Why it lands (Orbital filter)
Soulbound tokens promised reputation; they delivered isolated NFTs. EAS already shipped >40M attestations in 2025 (Optimism Citizens, Coinbase Verifications, Gitcoin Passport). Saying "the reputation primitive already exists, it just needs a *bus*" tells the audience the substrate is ready — the missing piece is composition.

## Cross-domain applications
- **DeFi lending**: combine "passed KYC" (Coinbase issuer) + "no Aave defaults" (zk-coprocessor issuer) + "GitHub contributor" (Gitcoin issuer) for tiered rates.
- **AI agents**: ERC-8004 agents accrue attestations from job completions, customer reviews, audit firms; reputation is queryable cross-chain.
- **Governance**: weighted voting where each attestation type contributes a coefficient (e.g., "Citizen House membership" + "long-term holder").
- **DePIN**: nodes attest to uptime / location; insurance protocols read the same attestation graph.
- **Identity**: passport/age/jurisdiction attestations from zkPassport / Anon Aadhaar consumed by *every* downstream protocol.
- **Compliance**: regulators issue allow-list attestations; permissioned pools check inclusion without re-running KYC.

## Future utility
1-yr: 50+ attestation schemas standardized via EAS schema registry. 3-yr: cross-chain attestation graph is the de facto "social layer" of crypto. 5-yr: governments issue attestations directly (e.g., EU eIDAS-anchored age proofs); on-chain compliance becomes a database lookup.

## Business model
- Free read; paid write (per-attestation listing fee for high-traffic schemas).
- Premium: indexed cross-chain query API ($USDC-metered), reputation-as-a-service for protocols too small to run their own indexer.
- TAM: KYC + credit + identity verification is a $20B/yr industry off-chain; even 1% of that routed through a crypto-native attestation bus = $200M.

## Sponsor / track fit
- **Arbitrum** — already has EAS on Arb One; this productizes it across Orbit + Robinhood Chain.
- **Robinhood Chain** — natural home for regulated attestation schemas (KYC, accreditation, broker-eligibility).
- **ERC-8004 ecosystem** — agent reputation is a flagship attestation-graph use case.

## 3-week MVP scope
- Deploy EAS contracts to Arbitrum Sepolia + Robinhood Chain testnet + 1 Orbit testnet.
- LayerZero-backed indexer that mirrors attestations into a shared graph.
- `AttestationLib.sol` (Stylus) with `query(subject, schema, issuerSet) → Attestation[]`.
- Three demo apps:
  1. **Tiered lending**: Aave fork that gives borrowers rate cuts based on stacked attestations from 3 issuers.
  2. **Cross-chain agent reputation**: ERC-8004 agent with attestations from jobs on 2 different rollups, queried atomically.
  3. **Quadratic-eligible voting**: DAO that only allows votes from addresses with `IsHuman` attestation from World ID or zkPassport.

## Risks
- **Issuer-side adoption** — schemas only matter if respected issuers (Coinbase, Gitcoin, World) opt in. Mitigate by starting with already-EAS-active issuers.
- **Sybil resistance of issuers** — anyone can issue attestations; we need *issuer reputation* recursively. Use stake-weighted issuer rankings.
- **Cross-chain consistency** — LayerZero delays. Acceptable for reputation; not for trade execution.

## Sources
- [Ethereum Attestation Service (EAS) docs](https://docs.attest.org/)
- [Coinbase Verifications via EAS](https://www.coinbase.com/onchain-verify)
- [Optimism Citizen House attestations](https://atlas.optimism.io/)
- [Gitcoin Passport on EAS](https://docs.passport.xyz/)
- [zkPassport circuits](https://github.com/zkpassport/circuits)
- [Anon Aadhaar](https://github.com/anon-aadhaar/anon-aadhaar)
