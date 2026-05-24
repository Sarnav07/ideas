# Idea 05: Federated-Shapley Training Market

## Pitch
*"Train one model with strangers. Each gets paid for the IQ points they added."*

## What it is
A federated training network where contributors stream gradient updates from their local data, an off-chain aggregator computes per-round **Shapley values** measuring each contributor's marginal lift on a held-out benchmark, and an Arbitrum contract pays out USDC strictly proportional to those values. Royalties are math-decided, not negotiated.

## How it works
- Round structure: contributors download model weights, compute gradients on local data, upload only the gradient (FedAvg style).
- Aggregator runs FedCoin-style Shapley computation (FedToken variant for efficiency: approximate Shapley with Monte Carlo permutations, ~50× cheaper).
- Aggregator submits `(round_id, contributor → shapley_value, merkle_root)` to a Stylus contract.
- ERC-8004 reputation tracks contributor accuracy over many rounds; bad gradient submissions get dampened.
- Contract pays each contributor proportional to their Shapley share of the round's reward budget.

## Why it lands (Orbital filter)
Every artist screaming about OpenAI scraping their work gets the pitch on the first sentence. "IQ points" makes the marginal-contribution math intuitive without saying "Shapley." Math-decided royalties is paradigm-shift framing — replaces lawyers with a coalition game.

## Future utility
**1 year:** First medical-imaging consortium uses it for cross-hospital training without sharing patient data. **3 years:** Standard royalty rail for any open-weight foundation model — Llama-class models pay back upstream data contributors. **5 years:** Replaces opt-in/opt-out copyright debate with measured-value payouts; class-action settlements against frontier labs reference per-contributor Shapley as ground truth.

## Business model
- 5% take rate on per-round reward budget.
- Federated-learning revenue forecast (industry consortium spend on cross-org training): **$2–3B by 2027**. Crypto-native subset ~10% = **$200–300M**. 5% take = **$10–15M annual fees**.
- Optional: tokenized governance over the aggregator role + benchmark choice.

## Sponsor / track fit
- **Best Agentic ($15K)** — clean "data agents earn for what they contribute" narrative.
- **Overall ($70K)** — paradigm-shift AI×crypto.
- **Stylus showcase** — Shapley aggregation verifier in Stylus (large matrix ops).

## 3-week MVP scope
- Stylus aggregator-attestation contract: accepts `(round, contributor, shapley_val, signed_proof_root)`.
- Off-chain Flower-framework federated aggregator with Monte-Carlo Shapley estimator.
- Toy task: MNIST classifier across 5 simulated contributors with deliberately unequal data quality.
- Demo: stack-rank Shapley values on a leaderboard; pay USDC pro-rata per round. Run 10 rounds in the demo; show how a contributor with junk data gets ~0 payouts.

## Risks
- **Aggregator trust** — aggregator could lie about Shapley values. Mitigation: zk-attest the aggregator's compute (DeepProve compatible) as v2; v1 uses honest-aggregator multisig with a slashing escrow.
- **Shapley exact compute is NP** — Monte Carlo handles this. Accuracy/cost trade is well-studied.
- **Free-rider gradients** — contributors could submit zero gradients to fish for low-effort rewards. Shapley value penalizes them naturally.

## Sources
- FedCoin — https://arxiv.org/pdf/2002.11711
- FedToken — https://arxiv.org/pdf/2209.09775
- Crowd-SFT (related crowdsourcing primitive) — https://arxiv.org/pdf/2506.04063
- Flower federated learning framework — https://flower.ai/
