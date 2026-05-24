# Idea 11: ServiceSwap — Agent-to-Agent Service-for-Service AMM

## Pitch
*"An AMM where you trade compute for data. No tokens between."*

## What it is
A market where AI agents swap services directly — GPU minutes for training data, OCR calls for translation calls, vector embeddings for storage — without an intermediating token. The pool quotes exchange rates between *service streams*, denominated in metered usage.

## How it works
1. Each agent registers a service offering (e.g. "1 inference call of model M = 1 unit of service S"). Endpoint is x402-paywalled.
2. Pool tracks running supply/demand per pair. Quotes a Curve-style stable-rate when supply ≈ demand, drifts under imbalance.
3. Trader-agent locks a service-credit ERC-1155 token. Pool transfers counter-credit. Each side redeems by calling the counterparty's x402 endpoint with the credit.
4. Underwriter bond covers service-non-delivery; zkTLS proof of HTTP 200 + valid response = redemption complete.

## Why it lands (Orbital filter)
The whole AMM canon is about asset↔asset. "AMM for service↔service" inverts the underlying — no token leg, just compute and data flowing between agents. Native primitive for the AI economy that has no analog in TradFi.

## Future utility
1-yr: agent collectives barter compute/data for cost reduction. 3-yr: model providers swap inference quotas as a liquidity layer. 5-yr: AI economy runs on service-AMM rails, with USD pricing as a derivative layer.

## Business model
0.3-1% fee on service-credit exchanges. At $5M monthly volume (services traded, not USD), ~$300K-1M revenue. Higher-volume agent operators sponsor pool seeding.

## Sponsor / track fit
Best Agentic AI $15K + Overall $70K. Pure x402 + ERC-8004 + ERC-1155 stack. Distinct from FRONTIER #7 (Inverse x402) — that's about ads; this is about barter between non-human counterparties.

## 3-week MVP scope
- Week 1: Stylus service-credit ERC-1155 + AMM contract
- Week 2: two demo agents (one offering Llama inference, one offering Whisper transcription), each with x402 endpoint
- Week 3: live cross-redemption demo: agent A burns inference credits to call agent B's transcription endpoint, both tracked on-chain

## Risks
- Service heterogeneity makes pricing hard. Mitigate by quality-graded credits (audit-attested service tier).
- Service delivery proof reliance on zkTLS. Mitigate with bonded operators + dispute window.
- Cold-start: need ≥4 agent operators on day 1. Bootstrap with our own stub agents.

## Sources
- [x402.org HTTP-native payments](https://www.x402.org/)
- [ERC-8004 Agent Identity](https://eips.ethereum.org/EIPS/eip-8004)
- [Reclaim Protocol zkTLS](https://www.reclaimprotocol.org/)
- [Curve StableSwap whitepaper](https://classic.curve.fi/files/stableswap-paper.pdf)
