# Idea 10: Cliquet Ratchet Vault

## Pitch
*"An ETH vault that locks in your gains every month. It can only ratchet up."*

## What it is
A vault that holds a strip of forward-start at-the-money options on ETH. Each month, the strike resets to the prevailing spot price and the previous month's gain (if any) is locked in as paid coupon. You bank the upside whenever it happens; you never give it back. Cliquet/ratchet options are a $40B+ TradFi market (especially in EU retirement products), with zero clean DeFi version.

## How it works
Vault sells a deposit-side receipt token; pays out monthly the maximum of zero and (spot_t − strike_{t-1})/strike_{t-1}, then resets strike_t = spot_t. Mathematically each leg is a forward-start ATM call; the vault hedges by buying a strip of these from an option AMM (Lyra, Premia, Aevo). Pricing in Stylus: integrate Black-Scholes for forward-start with stochastic-vol correction (Heston model preferred — needed because forward-start IV is non-trivial). Total premium is locked in upfront via the option-AMM strip purchase.

## Why it lands (Orbital filter)
"Lock in gains every month, only ratchets up" sounds like a perpetual-motion machine until you hear the trade-off: depositor pays the upfront premium for the strip. Universal hook — every retail saver wants "the gains stay locked in." The fact that the rebuttal is a single sentence (you pay for the ratchet via lower initial deposit value) means the pitch lands clean.

## Future utility
1-year: retirement-style DeFi product (long-dated holders sleep better with locked-in gains). 3-year: every yield-bearing vault offers a cliquet wrapper. 5-year: structured-cliquet replaces the entire DOV (DeFi Options Vault) covered-call category because users prefer ratcheted upside to capped upside.

## Business model
2% management + 20% performance on locked-in gains. At $300M TVL (realistic given ETH+BTC together are $2T+ retail-addressable), historical 12-18% annual capture → $60M annual gains, $12M perf fee + $6M management = $18M revenue. TAM: $40B annual TradFi cliquet issuance (mostly EU). Comparable: TradFi cliquet desks charge 4-6% drag; we charge 50 bps + perf — 10× cheaper.

## Sponsor / track fit
**Robinhood Chain $30K** primary — retirement-flavored vault for retail crowd. **Overall $70K** secondary. **Stylus** — Heston model forward-start integration is intensive math; Solidity fixed-point can't price this without 10× gas.

## 3-week MVP scope
- Week 1: Stylus Heston forward-start option pricer; vault contract (ERC-4626) with monthly reset hook.
- Week 2: option-AMM strip buy logic (Lyra/Premia integration); coupon distribution.
- Week 3: demo — backtest 12 months ETH 2024, show locked-in gains vs HODL; live deposit, simulate 3 months forward with mock spot moves.

## Risks
- **Option-AMM IV mispricing** — forward-start IV is hard to source clean. Mitigation: TWAP IV smoothing; cap IV bounds.
- **Roll basis** — monthly resets eat 1-2% in spread costs. Mitigation: longer reset cadence (quarterly) as v2 option.
- **Volatility crush** — low-vol regimes make the vault drag negative. Mitigation: variable management fee tied to realized vol.

## Sources
- Heston, *A Closed-Form Solution for Options with Stochastic Volatility* (1993) — [pages.stern.nyu.edu](https://pages.stern.nyu.edu/~ealtman/3-%20HestonOriginalPaper.pdf)
- Wikipedia Cliquet Option — [en.wikipedia.org/wiki/Cliquet_option](https://en.wikipedia.org/wiki/Cliquet_option)
- Wilmott on cliquets (FAQs in Quantitative Finance) — [wilmott.com](https://wilmott.com/)
