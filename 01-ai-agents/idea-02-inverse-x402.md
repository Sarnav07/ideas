# Idea 02: Inverse x402 — The API That Pays You to Call It

## Pitch
*"HTTP 402 in reverse — the API pays YOU to call it."*

## What it is
A reversed-direction x402 facilitator. Instead of an agent paying a server per call, the server (an LLM or content service) **pays the caller** per call, because the caller's prompt embeds an advertisement slot the LLM can auction. ChatGPT becomes a publisher; brands bid to be cited; the user pockets the spread.

## How it works
- An LLM endpoint exposes a Duetting/Mirrokni truthful auction (WWW'24 Best Paper) for ad placements inside its answer.
- Each prompt declares a topic vector; advertisers stake budget per topic.
- A second-price sealed-bid auction over advertisers fires per call; the LLM weaves the winning sponsor citation into the answer (with attribution).
- The Myerson-optimal revenue is split: 50% to the user (paid via **inverted x402** — `HTTP 402 → response includes USDC pull-request signature**), 30% to the LLM, 20% to the protocol.
- ERC-8004 reputation tracks click-through; advertisers slash their bids over time if CTR collapses.

## Why it lands (Orbital filter)
Single-sentence inversion of the protocol everyone now knows. *"Wait, instead of paying ChatGPT, ChatGPT pays me?"* — then the second beat ("every brand bids to be cited") inverts the entire $300B online ad market.

## Future utility
**1 year:** Indie LLM API earns its first dollar from this rail. **3 years:** Every LLM endpoint runs a bid layer; humans share inference revenue with their model provider. **5 years:** The Google-AdWords analog of the agentic web — and the dominant monetization rail for open-weight LLMs that can't sell training data.

## Business model
- 20% protocol take of ad-auction revenue. (Adwords historically captured ~30%; we leave headroom for the LLM.)
- TAM math: digital ad TAM 2026 = **$870B** (Statista). LLM-mediated search/answer is projected to be 5–15% by 2028 ≈ **$50–130B**. Capturing 0.1% = **$50M–130M annual fees**.
- Optional: protocol token gates the auction-runner role.

## Sponsor / track fit
- **Robinhood Chain ($30K reserved)** — payment-rail flavored; RH Chain is positioning as the agentic payments L2.
- **Best Agentic ($15K)** — canonical x402 composition.
- **Overall ($70K)** — single-sentence narrative.

## 3-week MVP scope
- Reverse-x402 facilitator contract on Arbitrum + RH Chain testnet.
- Duetting truthful-auction smart contract (sealed bids via tlock optional).
- Two demo agents: a buyer ("brand X") and a caller ("Claude wrapper"). User asks "what's the best running shoe?" → ad auction fires → answer embeds "On Cloud (sponsored)" → caller's wallet receives $0.0003 USDC.
- Frontend: live auction-log dashboard.

## Risks
- **Disclosure regulation** — sponsored LLM answers might fall under FTC native-ad rules. Mitigation: ship with bright "sponsored" tags and an OpenRTB-style disclosure manifest.
- **Adverse selection** — bots could spam queries to farm payouts. Mitigation: ERC-8004 caller reputation + Anti-Sybil Personhood Bond gate.
- **Bidder collusion** — covered by Duetting/Mirrokni truthfulness proofs in the paper.

## Sources
- x402 spec — https://www.x402.org/
- x402 whitepaper — https://www.x402.org/x402-whitepaper.pdf
- Duetting, Mirrokni et al., *Mechanism Design for LLMs* — https://arxiv.org/pdf/2310.10826
- Virtuals Agent Commerce Protocol — https://whitepaper.virtuals.io/
