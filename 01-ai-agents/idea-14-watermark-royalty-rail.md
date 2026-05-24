# Idea 14: Watermark Royalty Rail — "Prove This Text Came From My Model. Get Paid."

## Pitch
*"Detect a watermark, claim a royalty. The chain decides who wrote the internet."*

## What it is
A royalty rail for LLM-generated content. Model providers embed cryptographic watermarks in outputs (e.g., Bileve bi-level signatures, VOW). Any third-party scraper, search engine, or AI detector can submit text + a verifiable watermark-detection proof to a contract; if it verifies against a registered model, the *publisher* of the text pays a micropayment royalty to the model provider, via x402. Content provenance with bidirectional payment flow.

## How it works
- Model provider registers `(model_id, watermark_pubkey, royalty_rate, x402_payable)`.
- Each generation embeds the Bileve / VOW watermark via deterministic logit shifts keyed by the provider's secret.
- A third party scraping web content runs the detector; constructs a **VOW oblivious-detection proof** (privacy-preserving — proves match without revealing the secret key).
- The third-party publishes the proof + the offending text URL on-chain. Stylus verifier validates.
- The text-publisher's pre-funded x402 royalty escrow pays the model provider; finder takes a 5% bounty.
- ERC-8004 reputation registry tracks each model's "leakage rate" — how much of the internet ends up watermarked to them.

## Why it lands (Orbital filter)
"You sue OpenAI for training on your articles; OpenAI's model retroactively gets *paid* for the articles its watermark survives in." That's the paradox flip — provenance becomes a *receivable* asset. Same shape as ASCAP royalties for music, applied to language tokens.

## Future utility
**1 year:** First royalty payments from AI-detection startups (GPTZero, Copyleaks) to providers. **3 years:** Default rail for "is this AI-generated?" disclosure regulations (EU AI Act enforcement). **5 years:** Watermark royalties form a six-figure-per-month revenue line for open-weight model trainers — funding alternative to centralized API monetization.

## Business model
- 5% royalty take on every paid detection.
- AI-content detection market 2026 projection: **$1.6B**, growing 50% YoY (MarketsandMarkets). Pair with EU AI Act enforcement market = another **$0.5B**. 5% of 10% capture = **$10M annual fees**.
- Token-gated detector accreditation (model providers list trusted detectors).

## Sponsor / track fit
- **Best Agentic ($15K)** — agent-economy + content-provenance composition.
- **Overall ($70K)** — EU AI Act timing (Aug 2026 high-risk AI obligations) gives why-now.
- **Robinhood Chain ($30K)** — x402-flavored micropayment composition.

## 3-week MVP scope
- Model wrapper that injects Bileve watermarks (open-source Hugging Face artifact exists).
- Stylus verifier for VOW oblivious-detection proofs.
- Demo: a "publisher" page (HTML with LLM-generated copy) → finder runs the detector → proof posts → escrow pays the registered model provider.
- Frontend: provider dashboard showing per-text detected leakage with watermark strength.

## Risks
- **Watermark removal attacks** — paraphrasing erodes watermark signal by ~20-30% (per IACR 2604.27666). Mitigation: VOW + bi-level signature for robustness; royalty rate auto-scales with detection confidence.
- **Adversarial false watermarks** — anyone could re-key text. Mitigation: VOW's verifiability prevents this cryptographically.
- **Privacy of publishers** — publisher addresses can be obfuscated through stealth addresses on Arbitrum (EIP-5564).

## Sources
- VOW: Verifiable and Oblivious Watermark Detection — https://arxiv.org/html/2604.27666.pdf
- Bileve bi-level signature watermarking — https://arxiv.org/pdf/2406.01946
- Watermarking Language Models — https://arxiv.org/html/2411.05091v2
- x402 — https://www.x402.org/x402-whitepaper.pdf
