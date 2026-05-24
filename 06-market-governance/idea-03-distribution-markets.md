# Idea 03: Distribution Markets

## Pitch
*"Bet on the number, not the side. One pool, infinite outcomes."*

## What it is
A continuous-outcome prediction market — instead of YES/NO at a threshold, traders take positions on any *interval* of a real-valued outcome (BTC price on Dec 31, election margin, hurricane wind speed). One pool prices the entire probability distribution.

## How it works
- Continuous-outcome Logarithmic Market Scoring Rule (CLMSR) over a finely discretized real line.
- A segment-tree backing store gives O(log n) cost for arbitrary-interval bets; liquidity is shared across the whole distribution.
- Each trade reshapes the implied PDF; the AMM's loss is bounded by `b · ln(N)` where `b` is the liquidity parameter and `N` the number of buckets.
- Settlement reads a single real-valued oracle at expiry and pays the bucket containing the realized value.

## Why it lands (Orbital filter)
Literal "Uniswap V3 of prediction markets" — same conceptual leap as Orbital (binary → continuous, 1D → N-D), and the pitch lands without a single line of math.

## Future utility
- 1 yr: macro markets (CPI, FOMC dot-plot, GDP), sports point-spreads.
- 3 yr: any continuous-outcome insurance — temperature, rainfall, AQI.
- 5 yr: replaces binary-options markets entirely.

## Business model
- 0.25% per interval trade.
- 5 bp liquidity-provider fee on PDF reshaping.
- At Polymarket-scale volumes ($1B/yr), $2.5M+ in fees.

## Sponsor / track fit
Overall (Paradigm). Robinhood — tokenized macro markets. Arbitrum Stylus for segment-tree updates at low gas.

## 3-week MVP scope
- CLMSR engine in Stylus with segment-tree storage.
- Market on BTC end-of-month price with hourly liquidity refresh.
- UI showing live implied PDF + interval-trade slider.

## Risks
- Bucket granularity vs. gas cost trade-off.
- Tail-bucket manipulation (low liquidity at extremes).
- Oracle precision must match bucket width.

## Sources
- White, *Distribution Markets* — https://www.paradigm.xyz/2024/12/distribution-markets
- Dudík, Lahaie, Pennock, *A Tractable Combinatorial Market Maker (CLMSR)* — https://arxiv.org/pdf/2102.07308
- Hanson, *Logarithmic Market Scoring Rules* — https://mason.gmu.edu/~rhanson/mktscore.pdf
