# Idea 11: Quanto Perp DEX

## Pitch
*"A perp where you bet on BTC but get paid in ETH at a fixed exchange rate."*

## What it is
A "quanto" perpetual: the underlying is one asset, the payoff is denominated in another at a fixed conversion. BTC-quanto-in-ETH means $1 of BTC move pays you 1 ETH-denominated unit, no matter what ETH/USD does. Two simultaneous bets in one position. CEXes (BitMEX classic XBTUSD was quanto) never re-shipped it for crypto natives; no clean DeFi version exists.

## How it works
Standard perp clearinghouse where the funding rate has an *extra* quanto adjustment term derived from the correlation between underlying and payoff currencies. Math from Carr & Lee (UChicago) quanto pricing: futures price = `F_X * exp(-ρσ_Xσ_Y T)`, where ρ is BTC-ETH correlation, σs are vols. Funding rate captures this drift permanently. Stylus contract computes rolling correlation + funding adjustment per block. Reference-asset oracle (Pyth BTC/USD) + payoff-asset oracle (ETH/USD) feed independent prices; margin posted in payoff asset.

## Why it lands (Orbital filter)
"Bet on BTC, settle in ETH at fixed rate" trips the brain in 13 words. Standard perp = 1D bet. Quanto perp = 2D bet (asset × currency). Same Orbital N-D shape: you're not just adding leverage to BTC, you're decomposing the bet into "BTC view" and "BTC/ETH cross-currency view." Universal-enough for crypto-natives: every trader has wished they could be "long BTC but earn ETH yield from it."

## Future utility
1-year: ETH-margined traders who want pure-BTC directional exposure without conversion. 3-year: quanto becomes default settlement for derivatives whose underlying isn't the natural collateral (tokenized SPX paid in USDC; FX perps paid in stables). 5-year: every cross-asset perp on Hyperliquid-style venues uses quanto math; spot conversion becomes legacy plumbing.

## Business model
Standard perp fee: 2 bps maker / 5 bps taker on volume. At $500M daily quanto volume (5% of Hyperliquid mid-term volume), $20-50M annual fee, $2-5M after rebates. Plus funding-rate take of 10%. Comparable: dYdX v4 revenue $50M/yr at $30B daily volume on vanilla perps; quanto is the high-margin specialty. TAM: cross-asset speculation is ~30% of crypto-derivatives flow.

## Sponsor / track fit
**Overall $70K** — clean unbuilt primitive in DeFi. **Robinhood Chain $30K** — RH retail wants "long BTC without leaving USDC" / "long tokenized SPX paid in USDC." **Stylus** — rolling correlation matrix + funding-rate adjustment per block is gas-prohibitive in Solidity (saves 20×).

## 3-week MVP scope
- Week 1: Stylus quanto-adjusted funding rate engine; rolling correlation oracle.
- Week 2: perp clearinghouse contract with margin in payoff asset; matching engine (or OCB integration).
- Week 3: demo with two markets — BTC-paid-in-ETH and SPX-paid-in-USDC; show funding rate diverges from vanilla equivalent by the correlation term.

## Risks
- **Correlation breakdown** — flash decorrelation invalidates funding model. Mitigation: stressed-correlation circuit breaker.
- **Wide bid-ask** — early liquidity is thin without market makers. Mitigation: in-house MM bot for first month.
- **Margin liquidation cascades** — payoff-asset crashes while underlying moves. Mitigation: portfolio-margin overlay (see idea 04).

## Sources
- Carr & Lee, *Robust Replication of Volatility Derivatives* — [math.uchicago.edu/~rl/rrvd.pdf](https://math.uchicago.edu/~rl/rrvd.pdf)
- Wikipedia Quanto — [en.wikipedia.org/wiki/Quanto](https://en.wikipedia.org/wiki/Quanto)
- BitMEX XBTUSD legacy quanto contract spec — [bitmex.com/app/seriesGuide/XBT](https://www.bitmex.com/app/seriesGuide/XBT)
