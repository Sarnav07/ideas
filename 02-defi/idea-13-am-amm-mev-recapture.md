# Idea 13: Auction-Managed AMM (am-AMM)

## Pitch
*"An AMM where arbitrageurs pay the LPs to play. MEV flows backwards."*

## What it is
A Uniswap-style pool whose right to set the swap fee — and to be the front-of-queue swapper — is auctioned every block to the highest bidder. The arb who would otherwise extract LVR from LPs has to pay the LPs first to get the privilege. MEV is recaptured at the source, not after the fact via Flashbots.

## How it works
Adams & Moallemi (arXiv 2403.03367) "am-AMM": each pool runs a censorship-resistant English auction every N blocks for a pool-manager role. The winning manager sets the swap fee and gets to execute arb trades — but pays the auction price into the LP pool. Equilibrium analysis shows the auction revenue equals the LVR the manager extracts, so LPs end up neutral against the perfectly-rebalanced benchmark. Pricing model from Milionis et al. (LVR paper) used to set auction reserve. Stylus contract handles the auction state machine and dynamic-fee setting per slot.

## Why it lands (Orbital filter)
The inversion lands: in a normal AMM, arbitrageurs take from LPs (LVR). Here, LPs take from arbitrageurs. "MEV flows backwards" is the punchline. Distinct from previous attempts because (a) the auction is on-chain and trustless, (b) Stylus makes it cheap enough to actually run, and (c) no governance committee picks pool managers.

## Future utility
1-year: Uniswap V4 hooks adopt am-AMM as the canonical anti-LVR pattern. 3-year: am-AMM replaces vanilla constant-product as the default AMM construction across DeFi. 5-year: LP returns *outperform* HODL on volatile pairs because of recaptured arb revenue.

## Business model
Pool-protocol take rate: 10% of auction revenue. At $5B TVL (5% of Uniswap V3), $1B daily volume, conservative 4 bps of recaptured LVR = $40M annual auction flow, $4M protocol revenue. Plus governance-token capture of auction-management seat fees. TAM: estimated $1-2B annual LVR extracted from LPs across DeFi today (Milionis 2022); we recapture that flow.

## Sponsor / track fit
**Overall $70K** — clean academic primitive (Columbia's Moallemi) shipping on Arbitrum. **Stylus** — auction state machine + dynamic-fee math + LVR accounting is gas-prohibitive in Solidity (am-AMM hasn't shipped at scale because of this). **Robinhood Chain $30K** secondary — better LP economics on tokenized-equity pools.

## 3-week MVP scope
- Week 1: Stylus am-AMM auction state machine; English auction per N-block window; LVR-pricing oracle.
- Week 2: hook into Uniswap V4-style pool; dynamic fee setter; manager-trade priority queue.
- Week 3: demo: side-by-side am-AMM vs vanilla V3 on the same pair; show LP P&L delta over 24h simulated volume.

## Risks
- **Auction griefing** — adversary bids high then refuses to trade. Mitigation: bond + slashing for inactivity.
- **Centralization** — large MMs dominate auctions, LPs get small share. Mitigation: tier-based auction with retail-LP minimum cut.
- **Implementation gaps vs paper** — am-AMM in real-world conditions hasn't been proven. Mitigation: backtest against Uniswap V3 historical data first.

## Sources
- Adams & Moallemi, *am-AMM: An Auction-Managed AMM* — [arXiv 2403.03367](https://arxiv.org/abs/2403.03367)
- Milionis et al., *Automated Market Making and Loss-Versus-Rebalancing* — [arXiv 2208.06046](https://arxiv.org/abs/2208.06046)
- *Rebalancing-versus-Rebalancing* (LVR fidelity update) — [arXiv 2410.23404](https://arxiv.org/abs/2410.23404)
