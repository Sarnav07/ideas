# Idea 07: TrainYield — Distributed Training as a Yield Primitive

## Pitch
*"Stake your GPU. Earn yield from every query the model serves."*

## What it is
A protocol that lets GPU owners contribute gradient updates to a shared open-weight model and earn perpetual royalties from downstream inference fees. Each contribution is hashed onto the model lineage; payout streams via on-chain Shapley-style attribution.

## How it works
1. Base model checkpoint published with a "training pool" address.
2. Contributors submit gradient batches with zkML proofs that gradients came from the announced data + were applied to the announced checkpoint (Kaizen-style zk proof of training).
3. Aggregator publishes new checkpoint; Shapley attribution updates each contributor's share (sister to FRONTIER #20 Federated-Shapley, but applied to live model evolution, not single training round).
4. Inference fees (x402 streams from API consumers) split per attribution.

## Why it lands (Orbital filter)
DeFi yield comes from rent (lending) or rebate (LP). This invents a third source: *cognitive labor*. Stake compute, earn perpetual royalties on the model's lifetime revenue — a yield curve indexed to AI demand, not interest rates.

## Future utility
1-yr: GPU farms diversify from PoW/inference-only into training pools. 3-yr: open-weight models with permissionless contributors outperform closed labs on long-tail tasks. 5-yr: GPU staking becomes a treasury allocation comparable to ETH staking.

## Business model
Protocol takes 5-10% of inference fee stream. At a model serving $10M/yr in inference, $500K-1M protocol revenue. Contributor APY scales with model quality + adoption (long-tail bet).

## Sponsor / track fit
Best Agentic AI $15K + Overall $70K. EigenLayer (restaking infrastructure for slashable training compute) + Lagrange (zk proof of training) bounty fit. Distinct from FRONTIER #20 (single-round Shapley) — this is continuous lifecycle yield.

## 3-week MVP scope
- Week 1: Stylus attribution contract + Shapley accounting
- Week 2: small-model training pool (DistilBERT-class) with EZKL zkML proof-of-training (Kaizen-paper-style) for one fine-tuning step
- Week 3: live inference endpoint streaming x402 micropayments + on-chain split demo

## Risks
- zkML proof-of-training is at the bleeding edge (Kaizen CCS 2024). Compute cost may make small contributions uneconomic. Mitigate via batch proofs.
- Shapley computation expensive; use sampling-based approximations.
- Model coordination problem: how to prevent fork wars. Solution: bond-gated checkpoint proposals + governance veto.

## Sources
- [Kaizen zk proof of training — IACR 2024/162](https://eprint.iacr.org/2024/162)
- [FedCoin — arXiv 2002.11711](https://arxiv.org/pdf/2002.11711)
- [Bittensor subnet model](https://docs.bittensor.com/)
- [Gensyn ML compute network](https://docs.gensyn.ai/)
