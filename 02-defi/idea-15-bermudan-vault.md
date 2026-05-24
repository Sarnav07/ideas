# Idea 15: Bermudan Optimal-Exit Vault

## Pitch
*"You can sell on 12 specific days a year. The chain decides which day was optimal."*

## What it is
A yield vault that issues a Bermudan-option position to depositors: redemption is allowed only on N pre-specified dates per year. The vault runs a Longstaff-Schwartz optimal-stopping algorithm onchain to determine the *theoretically optimal* exit date — if a depositor exits earlier, they forfeit the option value, which the vault captures as carry.

## How it works
Vault holds ETH (or yield-bearing collateral) earning baseline yield. Depositors receive ERC-721 positions that can be redeemed only on observation dates t₁, t₂, … tₙ. Stylus contract runs Longstaff-Schwartz regression (the standard quant-finance solver for optimal-stopping problems) on simulated price paths to value the position. The vault sells the *optimal-exercise option* as a tradeable instrument: a holder can sell "the right to exercise on the optimal day" as a separate token. Optimal-stopping math is the heart of American/Bermudan option pricing and has never shipped onchain because Solidity can't run the Monte Carlo + regression efficiently.

## Why it lands (Orbital filter)
"The chain decides the best day to sell" lands as a brain-tickle: optimal-stopping is a famously hard math problem (the Secretary Problem, organ allocation, marriage proposals). Solving it onchain and making it tradeable inverts the user-decision model: instead of "you choose when to exit, you probably mistime it," it's "the math finds the optimal exit, you trade the right to it."

## Future utility
1-year: long-term holders use Bermudan vaults as a "smart HODL" — yield + structured exit. 3-year: every yield-bearing vault has a Bermudan wrapper. 5-year: tradeable optimal-exercise rights become a new asset class (American-option secondary market).

## Business model
1% management + 10% of captured-option-value (the spread between optimal-exit P&L and naive-exit P&L). At $400M TVL, 6-10% annual return from yield, ~3% additional from optimal-exit capture → $4M management + $1.2M perf = $5.2M revenue. Plus secondary-market take on tradeable exercise rights. TAM: any yield vault (Pendle YT market is $5B+) where the user benefits from timed exit.

## Sponsor / track fit
**Overall $70K** primary — Longstaff-Schwartz onchain is a Stylus *flagship* demo (literally the kind of math people thought would never run onchain). **Stylus** canonical — Monte Carlo + regression in Rust on Arbitrum is the kind of compute-heavy task Stylus exists for. **Robinhood Chain $30K** — retail users want "timed exits without overthinking."

## 3-week MVP scope
- Week 1: Stylus Longstaff-Schwartz solver (Monte Carlo path simulator + polynomial regression).
- Week 2: vault contract with ERC-721 redemption rights; observation-date keeper.
- Week 3: demo — ETH Bermudan vault with 12 quarterly observation dates; show solver-computed optimal-exercise schedule; tradeable exercise-right tokens.

## Risks
- **Monte Carlo gas** — even Stylus may struggle at large N. Mitigation: pre-computed solver results cached on-chain; only verify proofs onchain.
- **Path-dependency oracle requirements** — need clean price feeds for the simulation calibration. Mitigation: Chainlink-VWAP feeds with stale-checks.
- **User confusion** — optimal-stopping is unintuitive. Mitigation: UI that shows "if you exit today, you forfeit $X of option value."

## Sources
- Longstaff & Schwartz, *Valuing American Options by Simulation: A Simple Least-Squares Approach* — [anderson.ucla.edu](https://escholarship.org/uc/item/43n1k4jb)
- Wikipedia Bermudan Option — [en.wikipedia.org/wiki/Bermudan_option](https://en.wikipedia.org/wiki/Bermudan_option)
- Glasserman, *Monte Carlo Methods in Financial Engineering* (Springer 2003)
