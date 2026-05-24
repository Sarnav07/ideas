# Idea 10: EUA Variance Pool — Carbon Vol Without Carbon

## Pitch
*"Trade EU carbon-price volatility without holding a single offset. The vol, not the credit."*

## What it is
A variance-swap protocol over the **EU Allowance (EUA) spot price** — the world's largest compliance-carbon market ($380B in 2025, EU ETS). Solves the problem that carbon-credit ETFs (KRBN, GRN) give you 1× exposure but you can't isolate the volatility from the directional bet. This trades the vol surface, not the price.

## How it works
Variance swap referenced to daily EUA spot (ICE Endex EUA front-month future). Buyers go long realized variance; LPs short the variance via Carr-Madan replication. Pricing engine consumes implied-vol surface from EUA options market + historical realized variance over rolling windows. Oracle dependency: **Pyth Network EUA front-month future price feed + ICE Endex daily settlement adapter** (Pyth has EU-carbon coverage; ICE Endex publishes daily settlements in a public bulletin). Cross-validation via Climate Impact X (Singapore) for the parallel voluntary-carbon market.

## Why it lands (Orbital filter)
"Carbon vol, not carbon" inverts a $380B market that retail can't currently touch in any sophisticated way. Variance is invisible to most ETF buyers; isolating it is a sophisticated TradFi trade (CITI desk only) that becomes 1-tap on-chain. Same Orbital-shape as the Dispersion Pool — extract a specific Greek from a broad market.

## Future utility
**1-yr:** crypto-native macro funds use it as a hedge against ETF carbon exposure. **3-yr:** corporates (steelmakers, airlines, cement) hedge their EU-ETS compliance cost via on-chain variance — cheaper than buying options through a Goldman desk. **5-yr:** every emissions-trading scheme (UK ETS, California CCA, RGGI, China ETS, Korea K-ETS) has a corresponding on-chain variance market — a unified "global carbon vol surface."

## Business model
TAM: EU ETS spot turnover ~$680B/yr at 2025 prices; broader carbon-credit market $686B in 2025 (GMInsights) projected $9.4T by 2035 at 30% CAGR. Capture 0.01% as variance notional → **$70M annual variance notional**. Take rate 0.5% on variance traded → **$350K ARR Year 1, scales to $5M ARR by Year 3** as compliance buyers join.

## Sponsor / track fit
**Overall $70K** — TradFi-mirror + climate angle plays well to a global-narrative judging panel. **Robinhood Chain ($30K)** — RWA + derivatives extension. The variance-swap math is the same Carr-Madan replication as the Dispersion Pool (Frontier #14), so it shares the Stylus-killer-demo angle.

## 3-week MVP scope
- **Week 1:** Pyth EUA price-feed integration + ICE Endex daily-settlement parser. Solidity variance-swap contract (fork dispersion-pool scaffold).
- **Week 2:** Stylus implementation of realized-variance accumulator + Carr-Madan replication pricer. LP-pool with seasonal-volatility tranches.
- **Week 3:** demo theatre: 2-year historical replay of EUA vol regime (2022 Russia-gas spike, 2024 cooler regulation). Show vol-of-vol surface visualization in 3D — visceral "this is the missing market" frame.

## Risks
- **Oracle quality** — EUA spot has thin overnight liquidity; settlement-windows games possible. Mitigation: T+1 TWAP from ICE official close.
- **Concentration** — EU compliance buyers cluster at quarter-end; squeezes vol. Mitigation: dynamic LP-fee adjustment + concentration caps.
- **Regulatory** — EU MiFID II and EU ETS Regulation may classify on-chain carbon-derivatives as regulated. Mitigation: launch as a non-EU-resident pool; cross-validate with voluntary-carbon (Climate Impact X) market in jurisdiction-free territory.
- **Underlying liquidity collapse** — carbon-price collapse (post-2030 phaseout uncertainty) zeros vol surface. Mitigation: tranche-by-vintage hedging.

## Sources
- [GMInsights Carbon Credit Market — $686B 2025 → $9.4T 2035](https://www.gminsights.com/industry-analysis/carbon-credit-market)
- [CarbonCredits.com — EU ETS & VCM Live Prices](https://carboncredits.com/carbon-prices-today/)
- Bossu, *Variance Dispersion and Correlation Swaps* — [arXiv 1004.0125](https://arxiv.org/pdf/1004.0125)
- [Pyth Network EUA price feed](https://pyth.network/price-feeds)
- [ICE Endex EUA Futures](https://www.ice.com/products/197/EUA-Futures)
