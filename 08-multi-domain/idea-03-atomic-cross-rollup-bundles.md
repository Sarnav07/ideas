# Idea 03: Atomic Cross-Rollup Bundles — One Transaction, Many Chains

## Pitch
*"Send one tx. It either lands on five rollups together or nowhere."*

## What it is
A shared-sequencer-backed bundle service: a single signed bundle commits to atomic execution across multiple Arbitrum Orbit chains (and Espresso-shared rollups). Either every leg confirms in the same slot or every leg reverts. No bridges, no lockups, no eventual consistency.

## How it works
- Espresso (or Astria) shared sequencer accepts a *bundle* — N transactions, each targeting a distinct rollup that has opted into the same sequencing set.
- Sequencer commits all-or-nothing inclusion via a single ordering proof.
- Each rollup's settlement layer verifies the inclusion proof and finalizes the leg.
- Result: arbitrage, repayment, liquidation, agent coordination — *atomic* across chains.

## Why it lands (Orbital filter)
"Atomic" is what blockchain means within a chain; across chains, we've lived with bridges, optimistic delays, LayerZero hops. Telling someone "one signature, five rollups, no async" inverts the entire multi-chain mental model.

## Cross-domain applications
- **DeFi arbitrage**: flash-buy on Arbitrum One DEX, flash-sell on Robinhood Chain DEX, atomic. No need for cross-chain MEV bots.
- **Lending liquidations**: borrower collateral on rollup A, debt on rollup B — single atomic liquidation, no oracle race.
- **AI agent coordination**: agent on rollup A signs a deal with agent on rollup B; either both sign or neither (escrow-free settlement).
- **Governance**: cross-DAO conditional votes ("DAO-A approves only if DAO-B also approves in the same block").
- **NFT trades**: bundle a Blur listing on Arb One with a Magic Eden purchase on a Magic L3 — atomic swap, no escrow.
- **Bridges**: replace lock-and-mint bridges entirely with atomic burn-on-A / mint-on-B.

## Future utility
1-yr: 3-5 Arbitrum Orbit chains share a sequencer for atomic DeFi. 3-yr: shared sequencing is a baseline expectation; bridges become exception case. 5-yr: "the Arbitrum cluster" feels like one chain with thousands of execution lanes.

## Business model
- Sequencer fee revenue split (Espresso model: ~0.001 ETH per bundle to sequencer set).
- Premium: priority lane for bundles >$10K notional.
- TAM: cross-rollup MEV alone is estimated at $50-200M/yr (Flashbots data); atomic bundles capture the searcher's spread.
- Network effect: more rollups in the set → more atomic pairs → more value.

## Sponsor / track fit
Arbitrum Orbit + Robinhood Chain — atomic bundle between Arb One and RH Chain solves Robinhood's stated "we want our chain to feel native to the Arbitrum cluster". Espresso ecosystem grant. Stylus for the bundle verifier (efficient Merkle aggregation).

## 3-week MVP scope
- Two Stylus-deployed rollups using Arbitrum Orbit + Espresso testnet.
- `BundleSequencer` contract that accepts `(tx_a, tx_b, signature)` tuples.
- Inclusion verifier on each leg checks Espresso commitment.
- Demo apps:
  1. **Atomic DEX arb** — buy USDC/USDT on Rollup A, sell on Rollup B, all in one signature.
  2. **Cross-rollup liquidation** — Aave-fork liquidation where collateral lives on A, debt on B.
  3. **Agent escrow** — two ERC-8004 agents settle a trade atomically.

## Risks
- **Espresso testnet stability** — fallback to a mock sequencer for demo.
- **Inclusion-proof cost** — Stylus optimization needed; could blow gas if naive.
- **Centralization optics** — shared sequencer = trusted operator. Mitigate via Espresso's restaking-based decentralization (currently 25+ operators).

## Sources
- [Espresso Systems docs](https://docs.espressosys.com/)
- [Astria shared sequencer](https://docs.astria.org/)
- [Madara appchain framework](https://docs.madara.build/)
- [Arbitrum Orbit](https://docs.arbitrum.io/launch-orbit-chain/orbit-gentle-introduction)
- [Flashbots SUAVE — cross-domain MEV](https://writings.flashbots.net/the-future-of-mev-is-suave)
