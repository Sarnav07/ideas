# Idea 02: Parametric Cat Pool

## Pitch
*"Underwrite hurricanes onchain. Settle in 30 seconds when USGS says magnitude ≥7."*

## What it is
A permissionless reinsurance pool where stablecoin underwriters back catastrophe-bond–style policy NFTs (lat, long, radius, magnitude trigger). When a USGS / NOAA / Chainlink-attested event crosses the trigger, payout settles **in the next block** — vs Bermuda SPV cat bonds that take 60–90 days.

## How it works
Underwriters deposit USDC into per-peril tranches (Atlantic hurricane, California earthquake, Tokyo typhoon). Buyers mint policy NFTs encoding `(lat, long, radius, triggerMagnitude, payout, expiry)`. Pricing uses **Wang Copula-POT** on historical USGS / NHC event data (multi-event triggered cat bond model). Oracle dependency: **Chainlink-relayed USGS earthquake feed + NOAA NHC hurricane center coordinates** (both are public-record APIs with sub-15-minute latency; Chainlink pushes to chain). Settlement: a keeper calls `claim(policyId)`; contract reads the latest oracle event, checks geographic + magnitude predicates, transfers payout.

## Why it lands (Orbital filter)
$45B+ global cat-bond market currently routed through Bermuda SPVs with 90-day settlement and 5–7% management fees. **"Insurance you can buy in your wallet that pays the moment the earthquake happens"** is visceral; it sells itself on the latency inversion alone. Every Floridian or LA resident gets it instantly.

## Future utility
**1-yr:** Caribbean small-businesses and Indonesian SMBs buy $1K hurricane policies without a broker. **3-yr:** muni governments (Mexico City, Manila) issue parametric cat bonds onchain to retail underwriters globally — pension funds buy yield, the city gets instant liquidity post-quake. **5-yr:** the cat-bond market shifts onchain; Bermuda SPVs become a relic.

## Business model
TAM: $63.9B outstanding cat-bond market (Artemis Q1 2026 record). Capture even 1% → **$640M underwritten**. Pool take rate: 1.5% of premium (vs 5–7% TradFi mgmt fee) → **$10M ARR** at 1% share. Secondary revenue: policy-NFT secondary market fees (0.5% on resale — cat bonds trade actively in TradFi).

## Sponsor / track fit
**Robinhood Chain ($30K reserved seat)** — RWA narrative is direct (insurance is the largest unbuilt RWA category onchain). **Overall $70K** secondary — cleanest "real-world settlement" demo in the pool, lands on judges who saw 2025 hurricane news. Pairs naturally with Chainlink CCIP for cross-chain underwriting.

## 3-week MVP scope
- **Week 1:** Chainlink USGS adapter (mainnet feeds already exist for earthquake; build NOAA NHC parser for hurricane lat/long/category). Solidity policy-NFT (ERC-1155) with geographic predicate.
- **Week 2:** Stylus implementation of Wang Copula-POT pricer (matrix math is gas-prohibitive in pure Solidity). Underwriter tranches with cliff-payoff curves.
- **Week 3:** demo theatre: replay 2024 Hurricane Helene + 2025 Turkey quake; show 30-second on-chain settlement with policy NFTs minted on the day before. Frontend with risk map (Mapbox + tranche heatmap).

## Risks
- **Basis risk** — parametric trigger fires but insured suffers no loss, or vice versa. Mitigation: layered triggers (magnitude + radius + population density).
- **Oracle quality** — USGS revises magnitudes for up to 30 days post-event. Mitigation: settle at T+24h frozen value; revision triggers separate dispute window.
- **Regulatory** — selling unlicensed insurance is illegal in most jurisdictions. Mitigation: structure as a parametric **swap** (CFTC-cleaner than insurance) and KYC underwriters via Aegis/zkPassport.
- **Concentration** — single mega-event drains pool. Mitigation: per-peril tranches + global diversification math.

## Sources
- Wang, *Pricing Multi-event Triggered Catastrophe Bonds* — [arXiv 2302.00462](https://arxiv.org/pdf/2302.00462)
- [Wharton Cat Bond Primer](https://impact.wharton.upenn.edu/wp-content/uploads/2023/08/Cat-Bond-Primer-July-2021.pdf)
- [Artemis Cat Bond Market Dashboard — Q1 2026 $63.9B outstanding](https://www.artemis.bm/dashboard/)
- [Chainlink USGS earthquake feed](https://docs.chain.link/data-feeds)
