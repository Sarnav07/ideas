# Idea 06: InferenceFutures — Bet on What an LLM Will Say

## Pitch
*"A futures market on tomorrow's GPT answer. Settles inside a sealed chip."*

## What it is
A market where you bet on whether a *specific* LLM, given a *specific* prompt, on a *specific* future date, will produce a specific structured answer. Settlement runs inside a TEE — the model is invoked once, deterministically, and the attested output decides the trade.

## How it works
1. Market creator pins (model_hash, prompt, schema, settlement_date). E.g. "GPT-5.4 on 2026-06-01, prompt='Will Fed cut rates?' answer ∈ {yes, no}".
2. Traders take YES/NO shares (LMSR or Distribution-Market-style continuous).
3. On settlement: TEE loads the model, runs greedy decode with temperature=0, signs `(output, attestation)`. Stylus verifier checks model_hash + attestation + parses output against schema.
4. Payout follows attested output.

## Why it lands (Orbital filter)
"Bet on what an AI will say next month" is brain-breaking on first hear — then unfolds into a deep new asset class: model behavior as a tradeable underlying. Hedge prompt-injection risk, bet on model drift, price AGI capability releases.

## Future utility
1-yr: hedge funds bet on model capability before public benchmarks. 3-yr: capability futures price corporate AI roadmaps. 5-yr: every major model has implied-capability curves like S&P implied vol.

## Business model
2% market-creation fee + 1% trading fee. At $5M monthly volume, ~$1.8M/yr. Premium feed for institutional bettors tracking model release schedules.

## Sponsor / track fit
Best Agentic AI $15K + Prediction Markets (Polymarket adjacent) + Overall $70K. TEE-attested settlement maps to Marlin/Phala bounties. Sister to FRONTIER #22 (Forecasting-Cohort) but inverts it — bet on the model, not via the model.

## 3-week MVP scope
- Week 1: Stylus market contract (LMSR) + TEE settlement verifier
- Week 2: Marlin Oyster CVM hosting open-weight model (Llama-3.3-70B) for deterministic settlement
- Week 3: live testnet with 3 demo markets (capability question, code-generation outcome, factual question), full settlement flow

## Risks
- Closed-weight models (GPT-5, Claude-4.7) can't be loaded into TEE — limits to open-weight or API-relay markets. Mitigated by zkTLS-attested API call for closed models.
- Determinism: even temperature=0 has GPU non-determinism. Mitigated by fixed-precision inference + canonical hardware spec.
- Manipulation: model providers could ship surprise patches before settlement. Hash-pin a specific weights checksum.

## Sources
- [Marlin Oyster CVM](https://docs.marlin.org/oyster/protocol/cvm/)
- [Phala AI Agent Contract](https://phala.com/posts/introducing-aiagent-contract-for-smart-agents)
- [Distribution Markets — Paradigm 2024](https://www.paradigm.xyz/2024/12/distribution-markets)
- [Optimistic TEE-Rollups for AI Inference — arXiv 2512.20176](https://arxiv.org/pdf/2512.20176)
