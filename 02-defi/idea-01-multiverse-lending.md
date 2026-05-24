# Idea 01: Multiverse Lending

## Pitch
*"Borrow against assets that only exist if Trump wins."*

## What it is
A lending protocol that lets you collateralize and borrow conditional tokens — assets scoped to a future outcome (election, FDA approval, war). Liquidations only fire inside the matching "verse," so a conditional borrow is liquidation-proof until the world picks a branch.

## How it works
Probability-lattice algebra over Polymarket-style YES/NO conditional tokens. The protocol implements push-down/pull-up maps so a position in `notFiredETH` can be borrowed against `notFiredUSD` with zero cross-verse liquidation risk — both legs collapse together or neither does. Oracle resolution merges the verses back into base ETH/USD. Math follows Dave White's *Multiverse Finance* (Paradigm, May 2025): each verse is a measure-theoretic event, and the lending market clears separately in each leaf of the event tree.

## Why it lands (Orbital filter)
Eight-word pitch that breaks a generalist's brain. Lending × prediction markets is a new primitive — same author as Orbital Pool, so credibility transfers automatically. The rebuttal ("liquidations only fire in the verse where the event resolves") is the punchline that closes the deal.

## Future utility
1-year: hedge fund desks borrow stablecoins against "Fed cuts in Q3" tokens. 3-year: every macro view is a conditional collateral position. 5-year: insurance premiums priced as multiverse lending spreads — pay $0.95 to receive $1 if hurricane hits.

## Business model
Standard lending take-rate of 10% of interest spread. At $500M conditional-TVL (5% of current Polymarket OI, conservative), 8% blended borrow rate → $40M annual interest, $4M protocol revenue. Tokenomic kicker: governance token captures verse-resolution fees (mint/burn dust on each branch collapse). Comparable: Aave v3 at $25B TVL generates ~$80M/yr; conditional-margin segment is greenfield with no incumbent.

## Sponsor / track fit
**Overall $70K** primary — strongest "novel financial primitive" pitch in the pool. **Robinhood Chain $30K** secondary — Robinhood owns prediction-market distribution post-Kalshi acquisition; conditional-margin is the natural credit-layer extension. Arbitrum-native (Stylus for probability-lattice math). Pairs with Paradigm's research narrative.

## 3-week MVP scope
- Week 1: fork Polymarket conditional-token (ERC-1155 outcome shares); Stylus contract for verse algebra (push-down/pull-up).
- Week 2: lending pool with verse-scoped LTV; UMA-style optimistic oracle for resolution.
- Week 3: liquidation bot that respects verse boundaries; demo: borrow USDC against "Bitcoin > $200K by Dec" YES tokens, simulate both resolutions.

## Risks
- **Oracle resolution** — disputed verses (UMA-style) freeze liquidations. Mitigation: per-verse circuit breaker.
- **Adoption** — needs prediction-market liquidity depth; cold-start risk solved by piggy-backing Polymarket.
- **Regulatory** — conditional collateral on political events is CFTC-adjacent.

## Sources
- White, *Multiverse Finance* — [paradigm.xyz/2025/05/multiverse-finance](https://www.paradigm.xyz/2025/05/multiverse-finance)
- Gnosis Conditional Tokens framework — [docs.gnosis.io/conditionaltokens](https://docs.gnosis.io/conditionaltokens/)
