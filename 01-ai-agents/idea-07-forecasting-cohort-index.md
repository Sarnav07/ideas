# Idea 07: Forecasting-Cohort Index — "S&P 500 of AI Predictions"

## Pitch
*"The Vanguard fund of AI agents — buy the median LLM's market view in one click."*

## What it is
An ERC-4626 vault whose strategy is *the median view of N TEE-attested LLM agents over open prediction markets*. Each LLM agent produces a confidence-weighted position on Polymarket/Drift; the vault deposits route across positions weighted by the cohort's median confidence. Index token issues against vault NAV.

## How it works
- N (start with 10) frontier LLMs run inside Marlin Oyster TDX enclaves. Each enclave emits an attested daily JSON: `{market_id, side, confidence}` for every active prediction market.
- Aggregator computes the per-market median position weighted by cohort confidence and historical Brier-score reputation.
- Vault contract rebalances daily to match.
- LP token (`fcIDX`) issued against vault NAV; redeemable like any ERC-4626 share.
- 2024 paper *Wisdom of the Silicon Crowd* shows ensembled LLMs match human superforecaster accuracy. We turn that into an index product.

## Why it lands (Orbital filter)
Recognizable analogy (Vanguard ETFs are universal), counterintuitive payoff (LLMs collectively outpredict humans), and lands on three fresh primitives — TEE attestation, prediction markets, and ERC-4626. The "one click and you're long the AI hive-mind" framing is sticky.

## Future utility
**1 year:** First retail-accessible AI-driven prediction index. **3 years:** Multiple cohort indices — by topic (geopolitics, sports, crypto-native events), by tier (frontier-only, cheap-models-only). **5 years:** Default benchmark for "what does AI think?" — quoted on Bloomberg ticker.

## Business model
- 0.5% annual management fee + 10% performance fee.
- Polymarket monthly volume Q2 2026: **$13B**. Prediction-market index TAM at 1% capture = **$1.5B AUM**. 0.5% + perf = **$7.5M base + perf upside**.
- Tokenized governance over cohort selection (which LLMs are in the index).

## Sponsor / track fit
- **Best Agentic ($15K)** — clean multi-agent demo with TEE attestation.
- **Overall ($70K)** — sticky Vanguard analogy + Polymarket V2 timing (Apr 2026 launch).
- **Robinhood Chain ($30K)** — RH Chain wants RWA-flavored indices on its L2.

## 3-week MVP scope
- Marlin Oyster CVM with 5 LLM agents (Claude, GPT-4o, Gemini, Llama, Mistral) reading Polymarket-fork markets.
- Stylus aggregator: takes attested JSON, computes median, emits rebalance instruction.
- ERC-4626 vault on Arbitrum that mirrors positions on a Polymarket testnet fork.
- Frontend: cohort dashboard showing each LLM's per-market view + cohort median + NAV chart.

## Risks
- **TEE supply-chain attacks** — Intel TDX has had attestation bugs. Mitigation: dual-TEE (Intel + AMD SEV-SNP) attestation v2.
- **Polymarket regulatory shifts** — US OFAC etc. Mitigation: launch via Polymarket-fork testnet for the hackathon; production targets non-US markets first.
- **LLM herding** — all LLMs trained on similar data may correlate. Mitigation: cohort includes one adversarial-trained variant; reputation reweights via Brier score over time.

## Sources
- *Wisdom of the Silicon Crowd* — https://arxiv.org/pdf/2402.19379
- Polymarket V2 launch — https://www.kucoin.com/blog/polymarket-v2-launch-pusd-prediction-market-infrastructure-2026
- Marlin Oyster CVM — https://docs.marlin.org/oyster/protocol/cvm/
- ERC-4626 — https://eips.ethereum.org/EIPS/eip-4626
