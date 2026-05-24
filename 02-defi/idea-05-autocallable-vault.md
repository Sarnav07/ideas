# Idea 05: Autocallable Vault

## Pitch
*"A vault paying 12% coupons monthly — until ETH drops 30% and you eat the loss."*

## What it is
The onchain version of autocallable structured notes — Europe and Asia's $300B+ annual retail TradFi market. Deposit USDC, the vault sells a strip of barrier-knock-in puts on ETH, you receive a monthly coupon. If ETH stays above 70% of strike, you keep collecting. If ETH ever crosses 100% of strike on a monthly observation, the note auto-redeems early. Zero clean version exists onchain.

## How it works
Vault writes monthly down-and-in puts on ETH (or any reference asset) via Lyra/Premia-style option AMMs. Brownian-bridge calculation in Stylus computes barrier-hit probability between observation dates — the math that lets us price the autocall feature correctly rather than the naive "check only on observation day" approximation that loses 15-30% of the value. Coupon paid in USDC monthly; full principal returned at maturity if barrier never breached; if breached, depositors receive ETH at the strike (now worth less than the USDC they put in). Deng/McCann/Mallett (SSRN 1981308) is the canonical pricing reference.

## Why it lands (Orbital filter)
$300B annual TradFi market — Europeans and Asians have been buying these for 25 years through their bank — and *literally zero clean DeFi version exists*. Pitch lands on the "yield with a catch" intuition that everyone has from CD ladders. The catch (cliff loss on barrier breach) is honest; the Robinhood Chain audience is exactly the retail base that buys these in TradFi.

## Future utility
1-year: yield-hungry stable-treasuries shift from Maker DSR (4%) to autocallable vaults (8-12%). 3-year: every major asset has an autocallable vault with weekly mints. 5-year: structured-product issuance moves onchain because TradFi distribution carries 4% drag; DeFi is 50 bps.

## Business model
Issuance fee: 1% of principal at mint; 20% of coupon spread. At $500M annual issuance (0.2% of TradFi market), $5M issuance + $5-10M coupon take = $10-15M revenue. Comparable: Ribbon Finance v1 hit $300M TVL on simple covered-call vaults; autocallables are 10× the TradFi market because retail prefers structured payoffs to vanilla options. TAM: $300B annual TradFi market.

## Sponsor / track fit
**Robinhood Chain $30K** primary — Robinhood retail is the *exact* demographic buying autocallables in Europe/Asia. **Overall $70K** secondary — clean novel onchain primitive. **Stylus** — Brownian-bridge barrier pricing is non-trivial floating-point math; saves 100× gas vs Solidity fixed-point.

## 3-week MVP scope
- Week 1: Stylus Brownian-bridge barrier pricing; Black-Scholes IV pulled from Lyra/Premia.
- Week 2: vault contract (ERC-4626) that sells the option strip monthly; coupon distribution; barrier oracle.
- Week 3: demo: $100K deposit, 12% APR strike, simulate 12 months with three scenarios (no breach, late breach, autocall early redemption).

## Risks
- **Option AMM depth** — selling monthly puts at scale needs deep counterparty book. Mitigation: launch with capped TVL; widen counterparty mesh in v2.
- **IV mispricing** — wrong IV inputs blow up the coupon. Mitigation: TWAP-based IV smoothing + manual circuit breaker.
- **Communicating tail risk** — users need to understand the cliff. Mitigation: simulator UI that shows realized P&L paths.

## Sources
- Deng/McCann/Mallett, *Modeling Autocallable Structured Products* — [SSRN 1981308](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=1981308)
- Bouzoubaa & Osseiran, *Exotic Options and Hybrids* (Wiley 2010), ch. 8 (autocallables)
- Goldman Sachs structured-products primer — [goldmansachs.com](https://www.goldmansachs.com/insights/pages/structured-products)
