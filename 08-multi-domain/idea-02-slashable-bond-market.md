# Idea 02: Slashable Bond Market — Restaked-ETH Insurance for Any Off-Chain Claim

## Pitch
*"Post ETH. Make any claim. If you lie, the chain takes your ETH."*

## What it is
A generalized AVS-on-EigenLayer (or Symbiotic / Karak) that lets anyone open a *bond market* against an arbitrary off-chain assertion — "this oracle price is right", "this LLM output is unmanipulated", "this server has 99.9% uptime", "this address is not a sanctions hit". Restaked operators stake ETH against the claim; a challenge-and-prove game slashes losers permissionlessly.

## How it works
- Claim deployer writes a `Claim` Solidity struct: `{ predicate, evidenceFormat, challengePeriod, slashAmount }`.
- Operators opt in by restaking ETH via EigenLayer/Symbiotic; their stake backs the claim.
- Anyone can challenge with on-chain evidence (zkTLS proof, Merkle proof against L1 state, drand-attested timestamp, etc.).
- If challenge succeeds inside the period, operator's restaked ETH transfers to the challenger.
- Reusable across domains: same bond, different predicate.

## Why it lands (Orbital filter)
Sounds tautological ("of course people stake to back claims") until you realize the *same restaked ETH* now backs hurricane insurance, oracle prices, AI safety claims, and SLA contracts simultaneously. One pool, infinite assertions — capital efficiency for trust itself.

## Cross-domain applications
- **DeFi oracles**: any token can launch with a permissionless oracle whose ETH-backed bond exceeds the manipulation profit (HIP-3 style).
- **AI**: agents post bonds against "I will not exfiltrate funds" or "my output is not prompt-injected"; bonds slash on proof of misbehavior.
- **DePIN**: nodes post bonds against location/bandwidth claims (Witness Chain shape); slash on triangulation failure.
- **Insurance**: parametric cat bonds where underwriter ETH backs payout; slashed when USGS/NOAA trigger fires.
- **Governance**: delegate posts bond against "I will vote per my published policy"; voter slashes if delegate deviates.
- **Compliance**: KYC providers bond against "this address is not OFAC-listed"; slashable on Chainalysis attestation.

## Future utility
1-yr: 5-10 vertical AVSs collapse into one general market. 3-yr: restaked ETH becomes "underwriting capital" of crypto — comparable to Lloyd's syndicates. 5-yr: traditional reinsurers (Munich Re, Swiss Re) buy slashable bonds as cheap reinsurance for parametric risks.

## Business model
- Per-claim listing fee + take rate on slashed amounts (10-20% to protocol, rest to challengers).
- Operator-side: subscription to claim filters (an operator who only backs "weather claims under $1M" pays per match).
- TAM: EigenLayer has $14B restaked as of 2026; even 1% rerouted to generalized claims = $140M backing → conservative $10-30M/yr protocol take rate.

## Sponsor / track fit
EigenLayer ecosystem grants — this is literally what EigenLayer pitches but generalized. Arbitrum Stylus for the slashing/verifier engine (BLS sig aggregation in Rust). Robinhood track via tokenized-asset SLA insurance.

## 3-week MVP scope
- Generic `BondMarket.sol` (Stylus) with pluggable predicate verifier interface.
- EigenLayer AVS registration (Holesky → Arbitrum bridge).
- Three demo claims sharing the same bond pool:
  1. **Oracle bond**: BTC price claim challengeable via Pyth pull oracle disagreement > 1%.
  2. **SLA bond**: `s3.amazonaws.com` uptime claim challengeable via 3-of-5 zkTLS probe failures.
  3. **Agent bond**: ERC-8004 agent claim challengeable via on-chain receipt of forbidden action.
- Demo: spin up all three, run a slash live on stage.

## Risks
- **Adoption**: needs operators willing to back arbitrary claims. Mitigate with initial $50K bonded liquidity from sponsor grants.
- **Predicate complexity**: not every off-chain claim has a clean on-chain verifier. Scope MVP to claims with existing oracles (Pyth, Chainlink, zkTLS).
- **Slashing griefing**: malicious challengers spam claims. Mitigate with challenger bonds and per-claim cooldowns.

## Sources
- [EigenLayer Economic System (2025)](https://p2p.org/economy/2025-the-year-eigenlayer-became-an-economic-system/)
- [Symbiotic restaking docs](https://docs.symbiotic.fi/)
- [Karak network whitepaper](https://karak.network/)
- [Witness Chain Proof of Location AVS](https://docs.witnesschain.com/depin-coordination-layer/proof-of-location-testnet)
- [Hyperliquid HIP-3 builder-deployed perpetuals](https://hyperliquid.gitbook.io/hyperliquid-docs/hyperliquid-improvement-proposals-hips/hip-3-builder-deployed-perpetuals) (proves bond-backed permissionless markets work)
