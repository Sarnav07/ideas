# Idea 15: LiquiBid — Sealed-Bid AI Liquidator Auctions

## Pitch
*"Liquidators are AI agents. They bid in sealed envelopes. The lowest-loss bid wins."*

## What it is
A liquidation venue where AI agents compete to liquidate distressed positions via sealed-bid tlock auctions. Each agent submits an attested bid `(price, route)`; the auction picks the bid minimizing borrower loss. Winning agent executes; bond covers shortfall from attested execution price.

## How it works
1. Lending protocol triggers liquidation, posts position to LiquiBid.
2. N agent operators each submit tlock-encrypted bid to next-block drand: `(execution_price, route_via_DEXes, attestation_hash)`. Each agent is a small RL/LLM model in TDX.
3. Block N+1: bids decrypt. Stylus contract picks lowest-loss bid (maximum returned to borrower above debt). Winner executes via attested routing; if slippage > attested, bond drains.
4. Borrower receives surplus pro-rata. Repeat-defaulting agents lose reputation; consistent winners accumulate it.

## Why it lands (Orbital filter)
Liquidation today is a winner-take-all MEV scrum: fastest bot takes the full discount, borrower loses the rest. "Sealed-bid AI auction where the borrower captures the slack" inverts the entire MEV food chain — agents *compete to leave more on the table for the borrower*.

## Future utility
1-yr: Aave/Morpho fork integrates LiquiBid; borrowers retain 5-20% more in distressed exits. 3-yr: default standard for liquidations. 5-yr: borrower-protection layer becomes a regulated insurance product.

## Business model
30bp on liquidation notional, of which 50% to winning agent. At $5B annual liquidation volume across integrated protocols, $15M/yr fee pool.

## Sponsor / track fit
Best Agentic AI $15K + DeFi + Overall $70K. tlock (FRONTIER #15 sister) + ERC-8004 + Aave/Morpho integration. EigenLayer slashing + Lagrange zkML for execution-proof bonuses.

## 3-week MVP scope
- Week 1: Stylus auction + reputation contract
- Week 2: 4 agent operators (different routing strategies) running in TDX, integrating Uniswap V3 + Curve + 1inch routes
- Week 3: 50 simulated liquidations on testnet vs naive auction, dashboard of borrower-surplus captured

## Risks
- tlock latency adds 1-block delay (~2s). Acceptable for most liquidations; for extreme moves, fall back to fastest-bonded-agent.
- Agents could collude. Mitigate by sealed-bid + minimum N=3 distinct operators + reputation slashing for correlated bidding.
- Initial agent operator count thin. Bootstrap by partnering with existing MEV searchers + offering rep onboarding.

## Sources
- [drand tlock](https://docs.drand.love/docs/timelock-encryption/)
- [tlock — IACR 2023/189](https://eprint.iacr.org/2023/189)
- [Aave liquidation mechanism](https://docs.aave.com/developers/guides/liquidations)
- [Marlin Oyster CVM](https://docs.marlin.org/oyster/protocol/cvm/)
