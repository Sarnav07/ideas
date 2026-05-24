# Idea 03: Dispersion Pool

## Pitch
*"One pool. Long the parts, short the whole. Profit if stocks decorrelate."*

## What it is
A permissionless dispersion-trading vault: simultaneously sells variance on a basket index and buys variance on each constituent. Net P&L equals the realized-correlation slice — the same trade that Citadel, Susquehanna, and Optiver run as a $XB prop strategy with zero retail access. Onchain via tokenized equities.

## How it works
Index variance literally decomposes: `σ²_index = Σwᵢ²σᵢ² + 2ΣΣwᵢwⱼρᵢⱼσᵢσⱼ`. Carr-Madan replication writes each variance leg as a log-payoff portfolio of options. Cholesky-decomposed vega weighting (Jacquier & Slaoui 2010) builds a static portfolio that isolates pairwise correlation. Implementation: Stylus contract holds option strikes from Hegic/Lyra-style AMMs on each constituent + the index, computes the Cholesky-weighted basket, rebalances daily. Settles in USDC.

## Why it lands (Orbital filter)
Literal Orbital-shape pitch — variance is 1D, dispersion is N-D correlation. The CBOE DSPX Index made this a measurable, daily-quoted thing in TradFi 2023, but no DeFi access exists. "Profit if stocks decorrelate" is a generalist-hookable inversion: a smart non-trader hears it and asks "wait, can I bet on whether the market moves together?"

## Future utility
1-year: hedge against correlation spikes during crises (everything-down-together protection). 3-year: tokenized-equity correlation desk for stable-coin treasuries. 5-year: cross-asset dispersion (crypto basket vs equity basket) becomes the dominant macro vol trade onchain.

## Business model
Vault take rate: 2% management + 20% performance on a strategy that historically earns 4-8% annual Sharpe-1 returns (Bossu data on CBOE DSPX). At $200M TVL (realistic given tokenized-equity growth), $4M management + ~$3M perf = $7M annual. Comparable: Volatility Shares (TradFi) charges 95 bps on $300M AUM; we're addressing a $XB hedge-fund strategy with retail access. TAM: $45B+ of US tokenized equity TVL exposure that needs vol hedges.

## Sponsor / track fit
**Robinhood Chain $30K** — primary fit. Robinhood Chain launched tokenized US equities as flagship — dispersion is the canonical strategy on a stock basket. **Overall $70K** secondary. **Stylus** — Cholesky decomposition on a 50×50 covariance matrix is the kind of math that justifies Rust over Solidity (saves ~$500 per rebalance).

## 3-week MVP scope
- Week 1: Stylus Cholesky + log-payoff replication math; mock 5-stock basket using Robinhood Chain tokenized equities (AAPL, MSFT, GOOG, AMZN, NVDA).
- Week 2: option-strip vault integration (Lyra-style or in-house); daily rebalance keeper.
- Week 3: live demo with 5-stock dispersion vs S&P-mini index, real Chainlink option-IV oracle, P&L attribution UI.

## Risks
- **Tokenized-equity liquidity** — Robinhood Chain volumes early. Mitigation: launch with crypto-basket (BTC/ETH/SOL/AVAX vs total-cap index) as fallback.
- **Option AMM depth** — log-payoff strip needs deep option book per constituent. Mitigation: discrete-strike approximation.
- **Roll risk** — monthly variance roll exposes basis. Mitigation: ladder maturities.

## Sources
- Jacquier & Slaoui, *Variance Dispersion and Correlation Swaps* — [arXiv 1004.0125](https://arxiv.org/abs/1004.0125)
- CBOE DSPX Dispersion Index — [cboe.com/us/indices/dispersion](https://www.cboe.com/us/indices/dispersion/)
- Carr & Madan, *Towards a Theory of Volatility Trading* (1998)
