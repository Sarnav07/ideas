# Idea 09: RiskNet — zkML Risk Oracle for Lending Parameters

## Pitch
*"Aave's LTVs are set by a committee. Ours are set by an AI — with a math proof."*

## What it is
A risk oracle that publishes per-asset LTV, liquidation thresholds, and reserve factors derived from a neural net trained on on-chain liquidity, volatility, and correlation data. The network outputs come with a zkML proof binding them to a published model commitment. Lending protocols subscribe; parameters update hourly.

## How it works
1. Risk model committed on-chain (KZG). Operator stakes a bond.
2. Hourly: model reads oracle feeds (TWAP depth, realized vol, cross-asset correlation), outputs `{LTV_i, liq_thresh_i, RF_i}` + zkML proof.
3. Lending protocols call `getParams(asset)` — receives parameters only if proof verifies vs current commitment.
4. Bond covers protocol losses if a bad-debt event traces to overstated LTV; payout determined by post-mortem inquiry committee.

## Why it lands (Orbital filter)
Every major lending protocol pays Gauntlet/Chaos Labs $millions/yr for human-curated risk parameters. "Replace the consultancy with a verifiable AI" is a $50M+/yr addressable market with a clean before/after pitch.

## Future utility
1-yr: small protocols outsource risk to RiskNet. 3-yr: Aave/Morpho subscribe. 5-yr: every DeFi protocol uses verifiable AI risk oracles the way they currently use Chainlink for prices.

## Business model
$5K-50K/month subscription per protocol, scaled to TVL. At 20 protocols, $5M/yr ARR. Plus 0.5bp on liquidations triggered.

## Sponsor / track fit
Best Agentic AI $15K + DeFi + Overall $70K. Aave/Morpho/Compound integration potential. Lagrange zkML bounty direct fit. Gauntlet/Chaos as TradFi inversion target.

## 3-week MVP scope
- Week 1: Stylus parameter publisher + zkML verifier
- Week 2: gradient-boosted risk model (simple enough for EZKL) trained on 12 months Aave liquidation data
- Week 3: live testnet integration with mock-Aave fork; compare RiskNet params vs current Aave for 30 historical days

## Risks
- Model error → bad debt. Mitigated by conservative bounds + bond + human override committee for catastrophic events.
- zkML proof time. Hourly cadence is acceptable; if not, optimistic + fraud proofs.
- Protocols may not trust AI parameters initially. Sell first to permissionless long-tail markets (Morpho, Euler).

## Sources
- [Gauntlet Aave risk dashboard](https://gauntlet.network/products)
- [Chaos Labs methodology](https://chaoslabs.xyz/)
- [Lagrange DeepProve](https://www.lagrange.dev/blog/lagrange-roadmap-2025)
- [Aave V3 risk parameters](https://docs.aave.com/risk/asset-risk/risk-parameters)
