# Idea 07: Baltic Pool — Freight Derivatives Onchain

## Pitch
*"Hedge Suez Canal shipping rates from your phone. The Baltic Exchange just got Uniswap'd."*

## What it is
A perpetual swap on the **Baltic Dry Index (BDI)** and major dry-bulk + container-shipping routes (Capesize, Panamax, Supramax). The $XB Forward Freight Agreement (FFA) market is currently broker-intermediated, $1M+ ticket size, and entirely opaque to anyone but a Maersk / Glencore. This is a permissionless retail-accessible version.

## How it works
Perpetual contract referenced to daily BDI value (and route-specific subindices). Funding rate à la Hyperliquid — long pays short when perp > spot index. Oracle dependency: **Pyth Network + Chainlink Functions adapter for daily Baltic Exchange assessments** (Baltic publishes daily fixings as a paid feed; commercial license required at scale, free historical / 24h-delayed feed adequate for retail derivatives). Mark price = TWAP of fixings over 24h to prevent single-fixing manipulation.

## Why it lands (Orbital filter)
"You can short global shipping from your phone" is brain-tickle territory — most people don't realize freight rates *trade* as a derivative; the $XB FFA market is a Wall Street insider thing. Lands on anyone who read the *Ever Given Suez headline 2021* — *"how do you make money when shipping breaks?"* now has a 1-tap retail answer.

## Future utility
**1-yr:** crypto-native commodity hedge funds replace their FFA broker desks with onchain perps (lower-latency, no T+2 settlement). **3-yr:** SMEs that ship containers (Shopify-tier exporters) buy freight-rate floors as part of their treasury-management; agents auto-hedge ETA-discounted invoices. **5-yr:** Baltic Exchange itself onboards on-chain settlement; FFA broker desks consolidate or vanish.

## Business model
TAM: FFA market notional ~$30B/yr cleared (LCH ForexClear FFA data 2024) + ~$50B OTC. Capture 0.5% → **$400M notional**. Hyperliquid-style perp fee = 0.025% maker / 0.05% taker → **$10M ARR** at conservative 3× annualized notional turnover.

## Sponsor / track fit
**Robinhood Chain ($30K reserved seat)** — RWA + global-macro-derivatives angle; Robinhood is positioning as the retail-commodities chain. **Overall $70K** — pairs cleanly with the Hyperliquid HIP-3 *permissionless perp factory* narrative (#27); a freight perp launched on HIP-3 is the proof-point that HIP-3 enables exotic markets.

## 3-week MVP scope
- **Week 1:** Baltic Exchange historical-data adapter (free 24h-delayed feed). Pyth/Chainlink push of daily BDI + Cape-5TC route average. Solidity perp scaffold (fork Hyperliquid HIP-3 reference).
- **Week 2:** Stylus oracle-bond contract (EOTS over daily fixings; equivocation drains bond — composes with Frontier #25/#27). Funding-rate engine + liquidation queue.
- **Week 3:** demo: short BDI perp at 2,800; simulate spike to 4,000 (May-2024 historical); show LP P&L + funding accumulation. Frontend with route-by-route OI heatmap and Bermuda-Triangle-area mention for narrative juice.

## Risks
- **Oracle quality** — Baltic fixings are subjective panel assessments (broker-survey). Mitigation: aggregate Baltic + Drewry + S&P Global feed with median-of-three.
- **Liquidity bootstrapping** — perp markets need LP depth before traders show up. Mitigation: AMM-style virtual liquidity for first 90 days; capped notional.
- **Regulatory** — FFA is a regulated derivative under MiFID/CFTC. Mitigation: jurisdictional gating (block US IPs initially) + structure perpetual as a *cleared swap* not an FFA.
- **Manipulation** — single dominant carrier (Maersk) could push fixing. Mitigation: TWAP + dispute window + spot-cargo cross-check via shipping AIS data.

## Sources
- [Baltic Exchange Dry Services](https://www.balticexchange.com/en/data-services/market-information0/dry-services.html)
- [ICE Baltic Dry Index BDI Future](https://www.ice.com/products/83048584/Baltic-Dry-Index-BDI-Future)
- [Baltic Exchange GMB Guide v8.3 (Apr 2026)](https://www.balticexchange.com/content/dam/balticexchange/consumer/documents/data-services/documentation/ocean-bulk-guides-policies/GMB.pdf)
- [Hyperliquid HIP-3 builder-deployed perpetuals](https://hyperliquid.gitbook.io/hyperliquid-docs/hyperliquid-improvement-proposals-hips/hip-3-builder-deployed-perpetuals)
