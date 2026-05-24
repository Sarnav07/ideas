# Idea 12: FedDerivs — Federated-Learning-Priced Options

## Pitch
*"An options pricer trained on private user data. Nobody sees the data. Nobody sees the model."*

## What it is
An exotic-options pricing engine whose model is trained via federated learning across N data holders (e.g. exchange flow, OTC dealer books, options market makers). Each price quote comes with a zkML attestation that the model was the federated-averaged outcome. The model holders earn from every quote consumed.

## How it works
1. N data holders run local training on private trade data. Aggregator combines weights via secure aggregation (SecAgg/MPC) — no individual data ever leaves.
2. Aggregator publishes new global model commitment after each round.
3. Pricing engine serves quotes with zkML proof binding to current commitment.
4. Each round, Shapley attribution (FRONTIER #20 mechanism) splits quote-fee revenue among data holders proportional to marginal contribution.

## Why it lands (Orbital filter)
TradFi options pricing requires either public data (mispriced exotics) or proprietary data (siloed at one desk). "Federated model trained on everyone's data, owned by no one, paid to everyone" is the inversion. Distinct from FRONTIER #20 — that's training compensation; this is *productized inference* with continuous federated updates.

## Future utility
1-yr: better volatility surface for autocallables, lookbacks, Asian options on crypto. 3-yr: TradFi desks contribute via federated bridges. 5-yr: the global vol surface is a federated, on-chain attested public good.

## Business model
10-25bp on option premiums priced through engine. At $100M monthly options volume, ~$1.2-3M/yr quote fees. Split: 60% data holders, 30% protocol, 10% aggregator.

## Sponsor / track fit
Best Agentic AI $15K + DeFi + Overall $70K. Strong fit with FRONTIER #23 (Autocallable Vault) — this could price its barriers. Lagrange zkML + EigenLayer (aggregator slashing) bounty.

## 3-week MVP scope
- Week 1: Stylus pricing contract + commitment registry + attribution
- Week 2: 3-party federated training of a small vol-surface MLP, using SecAgg toy + EZKL inference proof
- Week 3: demo: ETH/USDC vanilla call quoted with attested federated model, compared to Deribit IV

## Risks
- Federated learning over private data needs honest aggregator. Mitigate via MPC aggregation in TEE + slashing bond.
- zkML on full vol-surface net may be too slow. Use lightweight surface-fitting net (~5k params).
- Data holders may not contribute without proven revenue. Bootstrap with synthetic + a single anchor exchange partner.

## Sources
- [FedToken — arXiv 2209.09775](https://arxiv.org/pdf/2209.09775)
- [Secure Aggregation — Bonawitz et al.](https://eprint.iacr.org/2017/281)
- [Lagrange DeepProve](https://www.lagrange.dev/blog/lagrange-roadmap-2025)
- [Deribit option chain API](https://docs.deribit.com/)
