# Idea 09: Verifiable RLHF Market — "Get Paid for the Alignment You Add"

## Pitch
*"Rate AI answers. Your payout equals the IQ points your rating added to the next checkpoint."*

## What it is
A permissionless RLHF rating market. Anyone can rate `(prompt, response_A, response_B)` pairs; an off-chain trainer applies the new preferences and reports each rater's Shapley-style contribution to a held-out alignment benchmark. The chain pays the contributors strictly by their measured marginal lift. RLHF graduates from an OpenAI-internal $0.50/hr gig-worker pipeline to a public market.

## How it works
- Trainer commits weekly: `(round, model_commit, dataset_root, benchmark_score_pre)`.
- Raters submit `(pair_id, preference, rater_pubkey)` with an anti-Sybil personhood proof (World ID / Anon Aadhaar / zkPassport).
- Trainer DPO-fine-tunes the model on the new preferences, runs the held-out alignment benchmark, computes per-rater Shapley contribution via Crowd-SFT / FedToken style estimator.
- Trainer posts `(round, contributor → shapley_value, post_score, zk_proof_of_compute)`.
- Stylus contract pays USDC proportional to Shapley, slashes ratings that hurt the score.

## Why it lands (Orbital filter)
Every AI ethics complaint about "$1/hr Kenyan annotators" gets the pitch instantly. The inversion: alignment-labor becomes a measurable equity stake, not a wage. Math-decided alignment royalties at planetary scale.

## Future utility
**1 year:** Open-weight projects (Llama, Mistral, OLMo) use it for community fine-tuning. **3 years:** Default rail for any "model improvement" labor — bug bounties for LLMs. **5 years:** Frontier labs route their RLHF spend onto open markets; the unaligned wage gig disappears.

## Business model
- 7% protocol take on each round's reward budget.
- RLHF labor market 2026 estimate: **$1.5B annual** (Surge AI, Scale AI's RLHF arm + frontier-lab internal spend). 10% migration onto an open market = **$150M annual**, 7% take = **$10M annual fees**.
- Tokenized governance over alignment-benchmark choice (the most valuable lever).

## Sponsor / track fit
- **Best Agentic ($15K)** — open RLHF is a hot 2026 narrative (HuggingFace's TRL library, AI16Z trust market).
- **Overall ($70K)** — public-good framing for grants; ethical-AI tailwind.
- **Stylus showcase** — Shapley estimator + benchmark verifier in Stylus.

## 3-week MVP scope
- Stylus rater-reward contract: ERC-8004 reputation + Shapley payout + slash.
- Off-chain DPO trainer + Monte-Carlo Shapley estimator (HuggingFace TRL).
- 100-pair toy benchmark (TruthfulQA mini subset).
- Demo: judge submits 5 ratings; the chain shows their measured contribution to the new checkpoint's TruthfulQA score; USDC streams accordingly.

## Risks
- **Trainer trust** — trainer could lie about Shapley. Mitigation: v2 makes trainer compute zk-attested via DeepProve. V1 uses a bonded multisig.
- **Sybil rater spam** — gated by personhood proof at registration.
- **Benchmark gaming** — held-out benchmark must rotate; v1 hard-coded; v2 governance-rotated.

## Sources
- Crowd-SFT: Crowdsourcing for LLM Alignment — https://arxiv.org/pdf/2506.04063
- Survey of RLHF — https://arxiv.org/abs/2312.14925
- FedToken — https://arxiv.org/pdf/2209.09775
- World ID proof of personhood — https://world.org/blog/world/proof-of-personhood-what-it-is-why-its-needed
