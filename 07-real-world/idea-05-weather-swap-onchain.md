# Idea 05: Weather Swap — HDD/CDD Onchain

## Pitch
*"Hedge your gas bill against a warm winter. Settle on NOAA's number, not Goldman's quote."*

## What it is
A permissionless HDD/CDD (heating-degree-day / cooling-degree-day) swap pool that lets utility companies, farmers, ski resorts and natural-gas traders hedge weather exposure directly against retail liquidity providers — bypassing the CME's $20-multiplier institutional contracts that lock out anyone below a $5M ticket.

## How it works
Underwriters deposit USDC into seasonal tranches keyed `(city, month, HDD/CDD_strike, payoff_per_degree)`. Buyers buy a swap leg paying $X per degree above/below a strike (e.g., NYC Nov-2026 HDD strike 600). Pricing follows Alaton-Djehiche-Stillberger Ornstein-Uhlenbeck temperature modelling with seasonal-mean-reverting drift. Oracle dependency: **Chainlink-relayed NOAA NCEI daily weather observations** (already on-chain via Chainlink Functions; per-city public-record temperature with T+24h finality). Settlement at month-end: cumulative degree days × multiplier × notional.

## Why it lands (Orbital filter)
$15B+ OTC weather-derivatives market (Speedwell Settlements 2024), CME volume up 4× to 42K monthly contracts in 2023. **"You can hedge a warm winter the same way you hedge BTC volatility"** is conceptually new to a generalist. The pitch sells itself once you frame *"a farmer can buy crop insurance from a Tokyo retail trader"*.

## Future utility
**1-yr:** Indian rice farmers buy monsoon swaps directly from Web3 LPs (1B+ underinsured agricultural workers). **3-yr:** utility companies hedge gas-load via decentralized swaps (vs being held hostage to JP Morgan desk pricing). **5-yr:** climate-risk hedging becomes a $100B+ retail-accessible asset class; insurance integrators bundle weather swaps with property cover.

## Business model
TAM: $15B annual notional in OTC weather derivatives (2009 baseline; growing). Capture 2% of OTC + new retail-accessible volume → **$300M notional**. Take rate: 0.3% per swap + 1% premium fee on swap pricing → **$3M ARR** at conservative early traction. Network effects: more underwriters = tighter pricing = more buyers; classical two-sided liquidity flywheel.

## Sponsor / track fit
**Robinhood Chain ($30K reserved seat)** — natural RWA derivatives extension; Robinhood already owns macro-retail distribution post-Kalshi. **Overall $70K** secondary — "weather swap" lands in the same way as the cat pool but with a different demo (recurring monthly settlement vs single-event payout). Stylus for the temperature-model pricer (Ornstein-Uhlenbeck simulation is gas-heavy in Solidity).

## 3-week MVP scope
- **Week 1:** Chainlink Functions adapter pulling NOAA NCEI daily mean temperature for 5 reference cities (NYC, Chicago, LA, Tokyo, Mumbai). Solidity swap contract with cumulative-degree-day accumulator.
- **Week 2:** Stylus contract for Alaton temperature pricer (mean-reverting OU process with seasonal drift). Underwriter tranches keyed by (city × month × strike).
- **Week 3:** demo: short Nov-2026 NYC HDD at strike 600; simulate a warm month via mocked oracle; see retail underwriter pool earn premium. Frontend with city-by-city heatmap of open interest.

## Risks
- **Basis risk** — NOAA city-station mismatched with insured asset (e.g., farm 80km away). Mitigation: multi-station weighted average + radius-based hedging.
- **Oracle gaming** — NOAA revisions are rare but real (rounding edge cases). Mitigation: T+7 settlement window with dispute path.
- **Adverse selection** — insiders with private weather forecast data front-run swaps. Mitigation: encrypted-mempool tlock orders (composes with Tier S idea #15).
- **Regulatory** — CFTC swaps reporting requirements may apply at scale. Mitigation: KYC underwriter side via zkPassport; retail-only hedger side.

## Sources
- [CME Weather Products](https://www.cmegroup.com/markets/weather.html)
- [GARP: Hedging Weather Risk](https://www.garp.org/risk-intelligence/sustainability-climate/how-weather-derivatives-250220)
- Alaton et al., *On Modelling and Pricing Weather Derivatives* — [KTH 2002](https://www.math.kth.se/matstat/fofu/reports/weather.pdf)
- [CME HDD/CDD contract spec](https://www.cmegroup.com/trading/weather/files/weather-fact-card.pdf)
