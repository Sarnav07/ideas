# Idea 04: Futarchy — Decision Markets Choose DAO Policy

## Pitch
*"Vote on values. Bet on policies. The market chooses."*

## What it is
A DAO governance system where token holders vote only on *what to maximize* (a single welfare metric like ARR, treasury, or active-user count), and conditional prediction markets price each candidate policy's expected effect on that metric. The highest-priced policy auto-executes; the loser's market refunds.

## How it works
- For each proposal P, two conditional markets open: "metric in 12 months | P passes" and "metric in 12 months | P fails."
- Traders deposit; LMSR quotes both conditional expectations.
- After a fixed bidding window, the policy whose conditional expectation exceeds the alternative by ≥ ε auto-executes via a timelock.
- Non-winning markets settle to the realized metric on the non-realized branch via refund; winning market settles at expiry.
- Hanson's theorem: under risk-neutral, well-informed traders, the chosen policy maximizes expected welfare.

## Why it lands (Orbital filter)
Hanson published in 2000, Vitalik publicly endorsed it in Nov 2024, and *nobody has shipped a clean version* — the pitch lands precisely because it's 25 years overdue.

## Future utility
- 1 yr: DAO treasury allocation, grant program triage, parameter changes.
- 3 yr: protocol-fee setting, validator-set changes, fork decisions.
- 5 yr: corporate boards (Robin Hanson's original target).

## Business model
- 0.5% take rate on conditional-market volume.
- $1M+/yr from a single $100M-treasury DAO running monthly futarchy votes.
- Optional governance-token fee discounts.

## Sponsor / track fit
Overall. Pattern-match for *any* DAO sponsor (Arbitrum DAO, Optimism Collective, Uniswap Foundation). Robinhood track if extended to corporate-decision markets.

## 3-week MVP scope
- Conditional-LMSR pair in Stylus.
- Timelock executor that reads market prices and routes to a target Safe.
- Demo on a fake DAO with three live proposals.

## Risks
- Liquidity bootstrap on conditional markets (thin order books defeat the mechanism).
- Manipulation by traders who can move the metric post-execution.
- Welfare-metric selection becomes the new political battleground.

## Sources
- Hanson, *Futarchy: Vote Values, But Bet Beliefs* — https://mason.gmu.edu/~rhanson/futarchy.html
- Buterin, *From Prediction Markets to Info Finance* — https://vitalik.eth.limo/general/2024/11/09/infofinance.html
- Hanson, *Decision Markets* (IEEE Intelligent Systems, 1999) — https://mason.gmu.edu/~rhanson/decisionmarkets.pdf
