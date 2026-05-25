# Idea 2: SIGMA

**Name origin:** Σ — the mathematical symbol for the covariance matrix that is the literal primitive at the heart of the product. One Σ matrix, two products on top of it.

## Pitch
*"Bring Hyperliquid's cross-margin to spot Apple and Tesla. Plus their hedge fund's favorite trade."* *(14 words)*

**Generalist-only version (10 words):** *"Same basket. 25% more borrowing. Plus a built-in hedge."*

**Pitch reframe note:** The original "Covariance OS" pitch failed the generalist test because the word "covariance" is a deal-breaker. This pitch deliberately **never says "covariance" or "Cholesky" or "Mahalanobis" in the headline.** Math judges still get the math (heat-map demo + Stylus benchmark). Generalist judges hear *"Hyperliquid for spot stocks"* — vocabulary everyone in 2026 already understands.

## Spine
DeFi math / cross-margin.

## What it is
A portfolio-margin lending protocol that uses the full **covariance matrix** of your basket — not per-asset isolation — to price LTV. The same matrix powers a second product: a **dispersion vault** that profits when stocks decorrelate.

One Stylus contract. Two unrelated DeFi products. Same math.

In numbers: deposit BTC + ETH + SOL + tokenized AAPL + MSFT on Aave → borrow 63% LTV (capped by the weakest asset). Deposit the same basket on SIGMA → borrow 83% LTV (the full basket is genuinely less risky than its weakest leg). That 20 percentage-point spread is the killer demo on stage.

## How it works
**Lending leg — N-dimensional portfolio margin.**
- Position risk computed as Mahalanobis distance over a rolling 30-day covariance matrix Σ: position risk = xᵀ Σ x (where x is the position vector).
- Stylus implements Cholesky factorization at every healthcheck (~30× cheaper than Solidity per author).
- Ledoit-Wolf shrinkage estimates Σ from Chainlink price feeds (handles the small-sample noise that breaks naive sample-covariance).
- Liquidation triggers on **portfolio risk**, not per-asset price floor. Dutch auction over the marginal-risk component (sell the position that reduces xᵀΣx fastest).

**Dispersion vault — Cholesky-weighted variance basket.**
- Sells variance on an index basket (σ²_index), buys variance on constituents (Σ wᵢ² σᵢ²).
- Cholesky decomposition isolates the realized-correlation slice from the variance term: σ²_index = Σ wᵢ² σᵢ² + 2 Σ Σ wᵢ wⱼ ρᵢⱼ σᵢ σⱼ.
- Carry-Madan log-payoff replication builds a static portfolio of option strikes per constituent.
- Daily rebalance keeper. Profits if stocks decorrelate (or vol-of-correlation moves in your favor).

**Same Σ matrix powers both.** The 20×20 covariance estimator updated once per block is reused by:
1. The lending pool healthcheck (to score LTV)
2. The dispersion vault rebalancer (to weight the option strip)

Two products, one numerical engine.

## Why it lands (Orbital filter)
The pitch reframe ("Hyperliquid for spot Apple and Tesla") clears the generalist test because by mid-2026 *Hyperliquid* is generalist vocabulary. The on-stage demo is two browser tabs side-by-side: judge picks a basket, Aave's tab shows 63% borrow, SIGMA's tab shows 83% borrow. Then judge adds *"short ETH perp as collateral"* → Aave's borrow drops (it doesn't understand the hedge), SIGMA's borrow rises (the matrix knows the basket got market-neutral). Audible reaction.

For math judges: the live heat-map of the 20×20 correlation matrix is visually striking and the falsifiable Stylus benchmark (*"180k gas for 5×5 Cholesky, 320k gas for 20×20"*) is concrete.

## Future utility (2026 market thesis)
**Who buys:**
- DeFi power traders capped by Aave's isolation limits (real public Twitter thread: *"I've been trying to lever a hedged basket and Aave won't let me"*).
- Crypto-native quant desks (Wintermute, GSR, Cumberland) who want a dispersion-trading venue but won't touch the Volmex stack.
- DAO treasurers hedging tokenized-equity positions on Robinhood Chain.

**Why mid-2026 (not 2025, not 2027):**
- Hyperliquid portfolio margin shipped Dec 2025 → the design is now mainstream-trader-accepted with *zero* spot-lending implementation. SIGMA is the spot version of the perp primitive everyone now wants.
- Robinhood Chain tokenized equity launch (Feb 2026) is the first time you can actually do an on-chain dispersion trade with AAPL, MSFT, GOOG, AMZN, NVDA. Pre-2026 there were no real tokenized US equities with chain-native liquidity.
- Stylus maturity in 2026 makes 20×20 Cholesky at every healthcheck cheap.
- None of these were jointly true in 2025.

## Business model
- **Lending leg:** 10% take rate on borrow interest spread.
- **Dispersion vault:** 2/20 (2% management fee + 20% performance fee).
- **Day-30 realistic revenue:** $50K/month if 5-10 quant deposits land (market-2026's number — clearest revenue projection of all three options).

Compounding revenue: the same TVL that pays interest spread is the same TVL that pays vault fees. One acquisition cost, two revenue streams.

## Sponsor / track fit
- **Primary: Stylus showcase.** **Single best Stylus case study in the entire fusion set.** Cholesky on a real-time covariance matrix is exactly the kind of math that loses to Solidity gas costs. The numerical pitch is concrete and falsifiable: *"180k gas for 5×5 Cholesky, 320k gas for 20×20."*
- **$30K Robinhood Chain (reserved seat).** Tokenized-equity dispersion + spot cross-margin are the canonical first strategies on a tokenized-stock chain. Robinhood retail wants Hyperliquid-grade cross-margin honesty.
- **$70K Overall.** Clean mathematical primitive with Paradigm-lineage research narrative. judge-wow gave it 6.5 for the *original* covariance-OS pitch; with the reframe ("Hyperliquid's cross-margin for spot stocks") the generalist axis recovers because Hyperliquid is now generalist vocabulary — estimated ~8.0.
- **Best Agentic ($15K)** — not a fit. Skip.

**Max reserved-seat reach:** ~$50K (Overall + RH Chain).

## 3-week MVP scope
**Week 1 — Math core.**
- Days 1-2: Stylus Cholesky + Ledoit-Wolf shrinkage + Mahalanobis distance routine. Foundry fuzz on numerical stability.
- Days 3-4: Chainlink price-stream covariance pipeline (rolling 30-day Σ for 20 assets: BTC/ETH/SOL + tokenized AAPL/MSFT/GOOG/AMZN/NVDA + gold + others).
- Days 5-7: Portfolio-margin lending pool with Σ-driven healthcheck. Dutch-auction liquidation over the marginal-risk component.

**Week 2 — Dispersion vault + UI.**
- Days 8-10: Carr-Madan log-payoff replication + Cholesky-vega-weighted basket construction. Option-strip integration (Lyra-style on deep names, discrete-strike approximation on long-tail).
- Days 11-12: Daily rebalance keeper. P&L attribution dashboard.
- Days 13-14: Live heat-map UI of 20×20 correlation matrix + side-by-side Aave-vs-SIGMA borrowing-power widget + dispersion P&L chart.

**Week 3 — Trial + ship.**
- Days 15-17: Recruit 20 quant testers (DeFi Twitter, Bankless, ex-TradFi desks). Tasks: (1) deposit mixed crypto-equity basket and beat Aave's borrowing quote, (2) deposit into dispersion vault during a low-correlation week, measure realized P&L. Benchmark: ≥20% more borrowing capacity vs. Aave on median tester basket; dispersion vault Sharpe ≥1 over 14-day backtest.
- Days 18-19: Live demo: judge picks a basket on stage, two tabs show Aave's quote vs. SIGMA's quote. Then judge adds a short ETH perp as collateral → Aave's borrow drops, SIGMA's borrow rises.
- Days 20-21: Pitch deck (Hyperliquid comparison front-and-center, dispersion as "the Citadel trade you can't normally do"), 3-min video, submit Overall + Robinhood Chain + Stylus.

## Risks
**The one that could kill this:** Robinhood Chain tokenized-equity option liquidity is too thin to make the dispersion leg work. The lending leg ships regardless; the dispersion leg needs deep option books per constituent.

**Mitigation:**
- v1 dispersion runs on a crypto basket fallback (BTC/ETH/SOL/AVAX vs. total-cap index) so the demo isn't dependent on option-AMM depth that doesn't exist yet.
- Acknowledge in pitch: *"v1 dispersion on crypto; tokenized-equity dispersion is v2 conditional on RH-Chain option-AMM depth."*

**Secondary risks:**
- Ledoit-Wolf shrinkage convergence on small samples could be unstable in low-data regime (mitigate with bootstrap stress tests).
- Numerical instability in Cholesky for near-singular matrices (mitigate with regularization + Foundry fuzz on adversarial Σ).

## Lens verdicts
- **market-2026 (8/10 — class leader):** *"Clear buyer with real capital, two compounding revenue streams, genuinely hard to copy. Risk: niche market (quants only) caps TAM unless retail wrapper is added. Day 30 runway: $50K/month if 5-10 quant deposits land."*
- **judge-wow (6.5/10 original → ~8.0/10 with reframe):** *"Beautiful primitive, fails the generalist test. The pitch demands covariance literacy. Smart but flat for half the room."* — **fixed by the reframe above.**
- **staleness-detector (mixed):** N-Dim Lending inherits Hyperliquid HIP-3 freshness (Dec 2025). Dispersion Pool 5/10 — *"core math is 2010, Robinhood Chain dependency is the 2026 hook."* True. We lean on Hyperliquid-portfolio-margin-as-spot (the genuinely 2026 framing) and the RH-Chain tokenized-equity dependency (the genuinely 2026 distribution).

**Honest framing:** judge-wow and market-2026 are *both right about the original framing* — the math is commercially superior and pitch-fragile. The reframe is the resolution: hide the word "covariance," lead with "Hyperliquid for spot stocks + the hedge fund trade." Same product, half the generalist friction.

## Sources
- `ideas/02-defi/idea-04-ndim-portfolio-lending.md` — N-Dimensional Portfolio-Margin Lending
- `ideas/02-defi/idea-03-dispersion-pool.md` — Dispersion Pool
- Hyperliquid portfolio margin docs (Dec 2025)
- Ledoit, O. & Wolf, M. — *Honey, I Shrunk the Sample Covariance Matrix* (2003)
- Carr, P. & Madan, D. — *Towards a Theory of Volatility Trading* (1998)
- CBOE — DSPX (Dispersion Index) methodology (2023)
- Arbitrum Stylus production benchmarks (2025-2026)
