# Idea 14: Onchain Credit Default Swap Pool

## Pitch
*"Buy insurance against any DeFi protocol getting hacked. Premium is consensus risk."*

## What it is
A market-priced credit-default-swap on any onchain reference entity — Aave, Lido, EigenLayer, a specific stablecoin, a tokenized treasury issuer. Buyers pay a stream of premium; sellers earn the stream and pay out the full notional when a verifiable "credit event" (hack, depeg, insolvency) fires. The premium is the consensus market view of next-12-month risk — a real risk-pricing primitive DeFi has never had.

## How it works
Reference event defined by a Stylus contract predicate: e.g., "Aave aUSDC peg drift > 5% for 24 hours" or "Lido stETH peg < 95% TWAP for 1 hour." Buyers pay quarterly premium in USDC; sellers post 100% notional collateral in USDC; clearing through a CDS-pool contract that nets buyer streams against seller payouts. Pricing follows ISDA-style fixed-recovery CDS: premium PV = sum of discount * survival_prob * accrual. Survival probability marked from a Polymarket-style binary market on the same credit event — the prediction-market price *is* the implied default probability.

## Why it lands (Orbital filter)
"Insurance against a specific DeFi protocol getting hacked" is what every Curve-hack, Euler-hack, Mango-hack victim has wished for. The Orbital twist: the *premium itself* is the market view of the risk, set continuously by a paired prediction market. So buying CDS doesn't just hedge — it tells you the market's read on the protocol's safety. Insurance + risk-disclosure in one primitive.

## Future utility
1-year: every DAO treasury holds CDS on its top 3 DeFi exposures (Aave, Lido, Uniswap). 3-year: CDS-on-stablecoin becomes the standard treasury hedge (USDC depeg, USDT depeg). 5-year: a yield curve of DeFi-credit emerges — risk-free DeFi rate vs credit-spread to Aave, Lido, Maker.

## Business model
Premium-stream take rate: 5%. At $2B notional outstanding (1% of US CDS market, conservative), 100 bps average premium → $20M annual premium flow, $1M protocol take. Plus prediction-market spread on the paired survival-probability market. TAM: ISDA reports $9.5T global CDS notional; even 0.01% capture is $1B notional, $100M premium pool. Comparable: Nexus Mutual peaked at $250M cover-active; CDS structure is more capital efficient (sellers post 100% rather than the buyer paying upfront).

## Sponsor / track fit
**Overall $70K** primary — major missing primitive. **Robinhood Chain $30K** secondary — credit insurance on tokenized-corporate-bonds is the natural extension (this is what TradFi CDS *is*). **Stylus** — predicate evaluator + premium-accrual schedule (daily compounding) is Stylus-canonical math.

## 3-week MVP scope
- Week 1: CDS-pool contract (Stylus) with ISDA-style premium accrual + predicate evaluator.
- Week 2: 3 reference predicates (Aave aUSDC depeg, Lido stETH depeg, generic price-oracle drift); Polymarket-style prediction market binding.
- Week 3: live demo — buy CDS on stETH, simulate depeg event (force oracle), payout fires; show premium tracking prediction-market price.

## Risks
- **Predicate ambiguity** — what counts as a "hack" vs governance pause. Mitigation: precise on-chain measurable triggers only (peg drift, TVL drop, frozen function selectors).
- **Capital efficiency** — sellers must lock 100% notional. Mitigation: tranching (seniors lock less notional, juniors absorb first loss).
- **Adverse selection** — buyers know more than sellers when they hedge. Mitigation: paired prediction market keeps premium honest.

## Sources
- Wikipedia Credit Default Swap — [en.wikipedia.org/wiki/Credit_default_swap](https://en.wikipedia.org/wiki/Credit_default_swap)
- ISDA Credit Derivatives Definitions (2014) — [isda.org/2014/12/26/2014-isda-credit-derivatives-definitions](https://www.isda.org/2014/12/26/2014-isda-credit-derivatives-definitions/)
- Nexus Mutual claims history — [nexusmutual.io](https://nexusmutual.io/)
