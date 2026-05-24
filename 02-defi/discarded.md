# Discarded DeFi ideas

Candidates considered for category 02 but cut. Reason codes match `DISCARDED.md` in repo root:

- **CR-1** — Pitch needs DeFi context
- **CR-2** — Pitch is incremental
- **CR-3** — Already shipped or in the air
- **CR-4** — Pitch needs unpacking
- **CR-5** — Too infra-y / not productable
- **CR-6** — Niche audience
- **CR-7** — Mathematically beautiful, no demo

---

## Exotic options

### Asian-Settled DEX
*"Strike at the average price over 30 days. Whales can't pin you on expiry day."*
**Cut: [CR-1]** — Already in repo's DISCARDED.md. DeFi-niche; "MEV-proof options by averaging" lands for traders only.

### Lookback Vault
*"A vault that retroactively buys ETH at its 30-day low."*
**Cut: [CR-2 / CR-3]** — Intuitive but the premium-paid rebuttal flattens the wow. Already cut in repo's DISCARDED.md.

### Rainbow Vault
*"Deposit ETH. Earn whichever of {ETH, BTC, SOL, gold} performed best this month."*
**Cut: [CR-2]** — Stulz pricing is well-trodden; rebuttal ("you pay a premium that prices in hindsight") flattens the wow. Already cut in repo's DISCARDED.md.

### Variance Swap Perp
*"A perp on realised volatility. Long vol without buying options."*
**Cut: [CR-6]** — Niche audience. Pitch requires understanding "realised vs implied vol." Already cut in repo's DISCARDED.md.

### Power Perps
*"Long the square of ETH. If ETH doubles, you 4x."*
**Cut: [CR-3]** — Squeeth (Opyn) shipped this years ago. Not Orbital-fresh.

---

## Yield & Lending innovations

### Pendle for Restaking Points
*"Tokenize your EigenLayer points before they exist."*
**Cut: [CR-3]** — Pendle V3, Ether.fi, and several others have shipped points-tokenization since 2024. Incremental.

### Risk-Tranched Lending (CLO Waterfall)
*"Senior tranche earns 4%. Junior tranche earns 18%, eats first loss."*
**Cut: [CR-1, CR-6]** — Requires "CLO" + "waterfall" + "subordination" knowledge. Lands for credit traders, not generalist judges.

### Cross-Protocol Netting
*"Offset your Aave borrow against your Morpho lend."*
**Cut: [CR-2]** — Operational efficiency, not paradigm shift.

### Insurance-Backed Undercollateralized Lending
*"Borrow $10K with $2K collateral. An insurer takes the rest of the risk."*
**Cut: [CR-2]** — Already attempted (Goldfinch, TrueFi). Pitch is recycled.

---

## AMMs

### Regime-Switched AMM
*"Our AMM doesn't have a curve. It has 4096 curves, and the order picks one."*
**Cut: [CR-4]** — Requires explaining "regime switching" + "volatility" before payoff. Adjacent to Orbital but weaker.

### Reactive AMM (dynamic-vol curve)
*"An AMM whose curve mutates based on order flow."*
**Cut: [CR-2, CR-7]** — "Curve adapts to volatility" sounds like an incremental Curve tweak; demo is hard to show in 60s.

### Blind FHE AMM
*"A Uniswap where nobody — not even the LP — sees the trade."*
**Cut: [CR-7]** — FHE demo runs at ~5 swaps/min vs Uniswap at hundreds/sec; numbers undercut the wow.

### Frequent Batch Auction DEX
**Cut: [CR-1]** — Lands for MEV-aware crowd. Outside DeFi, "frequent batch" is meaningless.

---

## Bonding curves & Harberger LP

### Self-Funding Harberger LP
*"Set your own LP fee. Anyone can buy your position at that price."*
**Cut: [CR-3]** — Already in repo's FRONTIER.md as Harberger NFTs (#3). Applying it to LP positions is incremental — the universal Harberger pitch already exists.

### Harberger Bonding Curve
*"Buy the token. Anyone can take it from you at the price you set."*
**Cut: [CR-3]** — Same family as Harberger NFTs.

---

## Yield tokenization & restaking extensions

### Restaking Futures
*"Restake the proof you'll be restaked."*
**Cut: [CR-1]** — Lands only if you know EigenLayer well. Already cut in repo's DISCARDED.md.

### LRT-of-LRTs Vault
*"A token backed by every restaking token, weighted by yield."*
**Cut: [CR-2, CR-3]** — Yearn-style aggregator; not new.

---

## Insurance / Cat / Credit

### Parametric Cat Pool (DeFi-only framing)
*"Underwrite hurricanes onchain. Settle in 30 seconds."*
**Cut: [Reserved for category 07 — Real-World]** — Already in FRONTIER.md as #24; better fit for real-world category.

### Music-Royalty Variance Swap
**Cut: [CR-5, CR-6]** — Royalty oracle doesn't exist clean; niche audience.

### Longevity Swap Pool
**Cut: [CR-5]** — Population-mortality index oracle fatal in 3 weeks.

---

## Oracles & MEV defense (DeFi flavor)

### Oracle-Free Lending (Endogenous Reporting)
*"Game theory replaces Chainlink."*
**Cut: [CR-7]** — Beautiful idea but the demo is "see, nothing happens for a week, then a bonded report comes in." Not visually compelling.

### Distribution Oracle
**Cut: [CR-3]** — Same paper as Distribution Markets (in FRONTIER.md).

### Functional Encryption Oracle
**Cut: [CR-4]** — Pitch needs "functional encryption" context.

---

## Stablecoins / macro

### Flatcoin
*"A stablecoin that tracks consumer prices, not the dollar."*
**Cut: [CR-3]** — Nuon failed. Pitch is "yet another stablecoin design."

### Inflation Range Bond
*"Earn 8% if US inflation stays between 2% and 4%."*
**Cut: [CR-2]** — "Bond + condition" is incremental.

### CMS Spread Range Accrual
*"A bond that pays 12% every day the yield curve is steep."*
**Cut: [CR-1]** — Requires fixed-income knowledge.

---

## Cuts at a glance

| Reason | Count |
|---|---|
| CR-1 (DeFi context) | 4 |
| CR-2 (incremental) | 6 |
| CR-3 (already shipped) | 6 |
| CR-4 (needs unpacking) | 2 |
| CR-5 (too infra-y) | 1 |
| CR-6 (niche audience) | 1 |
| CR-7 (no demo) | 3 |
