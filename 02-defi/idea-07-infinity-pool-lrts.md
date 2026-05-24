# Idea 07: Infinity Pool — Zero-Slippage LRT Basket

## Pitch
*"A pool with millions of restaking tokens. Every swap quotes at zero slippage."*

## What it is
An AMM with no bonding curve. Every LRT (liquid restaking token) in the pool is priced by querying its underlying stake account's redemption rate — only fees, never slippage, are charged on swaps. Sanctum's Infinity model from Solana, ported to Arbitrum / Ethereum LRTs.

## How it works
Each LRT (rsETH, ezETH, weETH, lsETH, etc.) has a redemption-rate oracle pegged to the underlying ETH staking account. Pool quotes swap price = ratio of the two redemption rates × dynamic fee. The fee adjusts upward as the pool drifts from target basket weights — this is what replaces the slippage curve as the equilibrium mechanism. Pool composition stays balanced because arbitrageurs always find the highest-fee leg most profitable. Sanctum's INF token captures the fee yield; the pool itself is purely a router.

## Why it lands (Orbital filter)
"Zero slippage at any size" sounds like a physics violation until the redemption-rate pricing mechanism lands. Orthogonal inversion to Orbital — instead of generalizing the bonding curve to N dimensions (Orbital), it throws the bonding curve out entirely. Same Orbital-shape paradox: "wait, how is that possible?" Second beat ("we're not pricing the swap, we're pricing the underlying stake") closes the deal.

## Future utility
1-year: LRT routing becomes invisible — wallets just pick "ETH" and the optimal LRT route gets selected by the pool. 3-year: Infinity Pool becomes the *settlement layer* for Ethereum restaking liquidity (a hub-and-spoke replacement for the Curve cross-pool mess). 5-year: every yield-bearing receipt token (LST, LRT, stablecoin yield, RWA yield receipts) routes through redemption-rate pools.

## Business model
Dynamic fee: 1-10 bps depending on basket imbalance. At $5B TVL (Sanctum Infinity on Solana hit $400M; Ethereum LRT TVL is ~$15B — 30% addressable), 100% daily turnover, 4 bps average fee → $73M annual fee, $7M protocol share at 10%. Plus governance-token capture of the long-tail LRT issuance subsidy (LRT issuers pay to be in the pool for distribution). TAM: $15B current Ethereum LRT TVL, growing.

## Sponsor / track fit
**Overall $70K** primary — clean innovation, ships in 3 weeks. **Stylus** secondary — dynamic fee computation across N-asset basket is gas-sensitive at high turnover. **Robinhood Chain $30K** — Robinhood retail buys "ETH yield" without caring which LRT; this routes them.

## 3-week MVP scope
- Week 1: redemption-rate oracle adapter (poll each LRT's underlying stake-account view function); basket weight target spec.
- Week 2: swap router contract with dynamic-fee curve; LP minting (proportional to weighted basket).
- Week 3: demo with 5 mainnet LRTs (ezETH, weETH, rsETH, lsETH, pufETH); show $1M swap at sub-bp slippage; compare to Curve LRT pool slippage at same size.

## Risks
- **Oracle staleness** — redemption rate can lag during un-restaking penalty events. Mitigation: per-LRT staleness halt + dispute window.
- **Long-tail LRT depeg** — one bad LRT contaminates pool. Mitigation: per-asset cap; gated whitelist by underlying restaking operator quality.
- **Sanctum patents** — verify IP clearance. Mitigation: independent implementation; Sanctum has not asserted patents.

## Sources
- Sanctum Infinity announcement — [sanctum.so/blog/infinity-solana-lst-liquidity-pool-by-sanctum](https://sanctum.so/blog/infinity-solana-lst-liquidity-pool-by-sanctum)
- EigenLayer LRT taxonomy — [eigenlayer.xyz](https://www.eigenlayer.xyz/)
- Curve LRT pool postmortems — [resources.curve.fi](https://resources.curve.fi/)
