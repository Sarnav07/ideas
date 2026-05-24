# Idea 08: Permissionless Perp Factory + EOTS Oracle Bond

## Pitch
*"Anyone can launch a perp market. List a bad oracle and the market burns your bond."*

## What it is
Uniswap made spot listing permissionless. Perp listing has stayed gatekept — Binance committee, dYdX governance, Hyperliquid HIP-3 deployer whitelist. This is HIP-3 + EOTS bonds: deploy a perp market on any reference asset by bonding stake; each oracle price post must be an EOTS-signed claim. Equivocate, lose your bond. Automatically.

## How it works
Builder bonds 100k+ USDC, deploys a permissionless perp contract with a custom oracle (Pyth, Redstone, a TEE attestation, anything). Each price post is an EOTS over `(market_id, slot, price)`. Two conflicting posts under the same nonce → permissionless key extraction → bond drained by whoever proves the equivocation, with 80% routed to traders harmed by the bad price. Market list-and-launch in one tx. Margin/funding/clearing inherits Hyperliquid's HIP-3 architecture; the EOTS layer is the slashing primitive.

## Why it lands (Orbital filter)
Two-beat killer pitch: (1) "anyone can launch a perp market" — lands like Uniswap-V2-for-perps. (2) "list a bad oracle and the market burns your bond" — the mathematical-slashing punchline that closes it. Inverts the *trust* assumption of perp listing: instead of "the protocol vets the listing," it's "the listing vets itself."

## Future utility
1-year: long-tail asset perps (every meme, every tokenized equity, every NFT floor) without governance. 3-year: tokenized-real-world-event perps (oil futures, weather, election odds) all use the same factory. 5-year: perp launching is invisible plumbing — any DeFi app embeds a perp launch in two lines.

## Business model
Listing bond capture: 1% of bond as protocol take ($1k per launch, $1M annual at 1000 launches). Trading fee share: 2 bps of all perp volume routed through factory markets. At $50B annual notional through long-tail perps (10% of Hyperliquid's volume in 2 years), $100M fee pool, $10M protocol revenue. TAM: $1T+ annual notional in cross-CEX perp volume, ~30% addressable for long-tail / tokenized assets that CEXes won't list.

## Sponsor / track fit
**Overall $70K** — clean primitive, fresh narrative (HIP-3 + EOTS is unbuilt). **Stylus canonical** — secp256k1 EOTS verifier + perp margining math. **Robinhood Chain $30K** — Robinhood Chain wants permissionless tokenized-equity perps; this is the launcher. Strong "Hyperliquid is on Arbitrum" narrative.

## 3-week MVP scope
- Week 1: HIP-3-style perp factory contract (Stylus); EOTS verifier (shares lib with idea 06).
- Week 2: minimal CLOB matching engine + funding rate; oracle binding per market.
- Week 3: deploy 3 demo markets (one normal, two adversarial); equivocate one oracle on-stage; bond drains; markets close out.

## Risks
- **Bad oracle gaming** — sophisticated adversary equivocates with profit > bond. Mitigation: bond size proportional to OI; circuit breaker on oracle price-jump.
- **Liquidity fragmentation** — too many markets, no depth. Mitigation: shared insurance fund across factory markets.
- **Regulatory** — permissionless perps face SEC/CFTC scrutiny. Mitigation: KYC-gated frontend; factory primitive itself is base-layer infra.

## Sources
- Hyperliquid HIP-3 — [hyperliquid.gitbook.io/hyperliquid-docs/hyperliquid-improvement-proposals-hips/hip-3-builder-deployed-perpetuals](https://hyperliquid.gitbook.io/hyperliquid-docs/hyperliquid-improvement-proposals-hips/hip-3-builder-deployed-perpetuals)
- Babylon EOTS — [docs.babylonlabs.io/papers/btc_staking_litepaper(EN).pdf](https://docs.babylonlabs.io/papers/btc_staking_litepaper(EN).pdf)
- dYdX v4 perp clearinghouse — [docs.dydx.exchange](https://docs.dydx.exchange/)
