# Idea 03: NeuralAMM — ML-Priced Automated Market Maker

## Pitch
*"An AMM with no bonding curve. A neural net quotes every swap."*

## What it is
A market maker that replaces `x*y=k` (or any closed-form curve) with a tiny attested neural net trained on order-flow history. The model outputs a per-swap quote; an on-chain zkML proof guarantees the quote came from the committed model. LPs deposit; the model rebalances inventory across regimes (calm, volatile, news-driven).

## How it works
1. Operator trains a small inventory-aware market-making net (Avellaneda–Stoikov + ML residual). Commits weights via KZG.
2. Per swap, off-chain quoter runs the net, returns `(quote, proof)`. Stylus verifier checks proof against commitment + inventory state.
3. Bond covers slippage if net quotes a price worse than a fallback Curve curve by more than tolerance.
4. Periodic retraining: weights update via on-chain governance vote + new commitment.

## Why it lands (Orbital filter)
Every AMM since Uniswap has been a math curve. "Replace the curve with a learned function" is the Orbital-shape inversion for AMM design — the same N-D leap, but for pricing, not topology.

## Future utility
1-yr: stablecoin DEXs where the net handles depeg regimes Curve can't. 3-yr: long-tail asset AMMs adapt to order flow without LP intervention. 5-yr: every major pool runs a learned quote layer with formal bounds.

## Business model
Fee tier 5–30bp, model operator earns 20% of fees as ROI on bond. At $100M TVL, $5M/day volume, ~$150K/yr fees to operator. Model marketplace: license trained nets to other pools.

## Sponsor / track fit
Best Agentic AI $15K + Best DeFi + Overall $70K. Stylus-canonical (matrix multiply for inference). Triple-track fit.

## 3-week MVP scope
- Week 1: Stylus AMM shell + KZG commitment of small MLP (~10k params)
- Week 2: zkML inference proof for the MLP (EZKL); off-chain quoter service
- Week 3: testnet WETH/USDC pool, demonstrate quote-vs-Uniswap spread chart in volatile vs calm regimes

## Risks
- zkML proof latency: 30s-2min per swap is too slow. Fix: batched proofs (one proof per K swaps), or optimistic + fraud proofs.
- Net could be gamed by adversarial order flow. Mitigated by inventory penalties + bond.
- Cold-start: net needs training data. Bootstrap with synthetic + Curve-replicated outputs.

## Sources
- [Avellaneda-Stoikov High-frequency market making](http://web.math.ku.dk/~rolf/Svend/AvellanedaStoikov.pdf)
- [EZKL zkML toolkit](https://ezkl.xyz/)
- [Lagrange DeepProve](https://www.lagrange.dev/blog/lagrange-roadmap-2025)
- [Stylus docs](https://docs.arbitrum.io/stylus/stylus-gentle-introduction)
