# Idea 12: Reverse Convertible Pool

## Pitch
*"8% monthly coupons in USDC. If ETH drops 30%, your stack converts to ETH at strike."*

## What it is
The most-bought structured product in Asian retail brokerage, never built clean onchain. A vault that accepts USDC, pays a fat monthly coupon, and if the reference asset (ETH, BTC, tokenized AAPL, anything) closes below the knock-in barrier on the final observation date, depositors get the asset at strike — meaning they bought at the high, the market is now lower, and the coupon was payment for taking that risk.

## How it works
Vault sells a strip of cash-settled down-and-in puts on ETH, struck at-the-money, with a 70% barrier. Premium received fund the monthly USDC coupon. At expiry: if ETH never closed below 70% strike, principal returns; if it did, depositors receive ETH at the strike price. Pricing in Stylus: barrier-option Brownian bridge (same kernel as idea 05 autocallable). Distinct from autocallable because (a) no early redemption, (b) the convert-to-asset feature is the *default* outcome, not an edge case, and (c) target audience is "I want to own ETH lower."

## Why it lands (Orbital filter)
The "I get paid to buy ETH cheap" framing trips the bullish-retail brain: it sounds like free money. The catch ("you actually get the asset, at the strike, when it's already down") is the honest punchline. Universal: every accumulator has thought "I'd buy ETH 30% cheaper." Pitch lands in 13 words and the rebuttal is clean.

## Future utility
1-year: accumulation strategy for stables holders who want to step into ETH/BTC at lower prices. 3-year: every tokenized equity has a reverse-convertible vault — RH retail's exact buying behavior. 5-year: structured-accumulation replaces DCA as the rational entry strategy for non-traders.

## Business model
1% mint fee + 15% coupon take. At $200M TVL (RH retail demand at scale), 8-12% coupon yield → $20M coupon flow, $3M protocol revenue. Plus assignment-conversion spread on physical-settlement leg. Comparable: Asian structured-note retail issuance is ~$150B annually; capturing 0.2% is realistic. TAM: every retail accumulator who currently DCAs.

## Sponsor / track fit
**Robinhood Chain $30K** primary — RH retail demographic is *exactly* the target buyer (familiar with "I want to own AAPL at $150" mental model). **Overall $70K** secondary. **Stylus** — Brownian-bridge barrier pricing kernel (shared with idea 05 — bundle for code-reuse story).

## 3-week MVP scope
- Week 1: barrier-pricing Stylus library (shared with idea 05); vault contract with physical-settlement leg.
- Week 2: monthly coupon distribution; barrier-observation keeper bot; option-AMM strip purchase logic.
- Week 3: demo deploy on tokenized-equity reference (AAPL on RH Chain); deposit USDC, simulate 3 months including a barrier-breach scenario.

## Risks
- **Physical-settlement gas spike** — converting all depositors to ETH at expiry is a fat tx. Mitigation: pro-rata claim pattern (depositors pull their ETH).
- **Knock-in cliff communication** — users misjudge tail risk. Mitigation: scenario simulator UI.
- **Reference asset liquidity** — for long-tail tokenized equities, can't source the put strip. Mitigation: launch with ETH/BTC/major-equity only.

## Sources
- Wikipedia Reverse Convertible — [en.wikipedia.org/wiki/Reverse_convertible_securities](https://en.wikipedia.org/wiki/Reverse_convertible_securities)
- Asian structured product market — Goldman primer
- BIS *Structured Products and the OTC Derivatives Markets* — [bis.org/publ/qtrpdf/r_qt0306e.pdf](https://www.bis.org/publ/qtrpdf/r_qt0306e.pdf)
