# Idea 1: OMNIVERSE

## Pitch
*"Every event in the world is now a tradable asset."* *(10 words)*

**Backup explainer (14 words):** *"Mint a new asset, list its perp, borrow against it — all in one transaction."*

## Spine
Market / RWA / event-asset.

## What it is
A single-transaction capital-markets bootstrap. A user types a free-text event prompt (*"Will Robinhood Chain hit 100K daily users by July 1, 2026?"* or *"Apple acquires Anthropic before Dec 31"*) and the system:

1. **Creates** a conditional-token pair for the event (YES/NO outcome shares).
2. **Lists** a permissionless perp on that token, secured by an EOTS-bonded oracle.
3. **Opens** a verse-scoped lending pool — borrow USDC against the conditional token, with liquidation that only fires *inside the matching verse*.
4. **Wires** the market to a self-resolving oracle (Bayesian Truth Serum + α-halt) for subjective events that no Chainlink feed can settle.

All in one tx. No external oracle for the legs that don't need one. No governance vote. No whitelist.

## How it works
Three primitives stacked under one orchestrator contract:

- **Permissionless Perp Factory + EOTS oracle bond.** Anyone bonds 100k USDC and deploys a perp with any oracle. Each price post is an EOTS-signed claim over `(market_id, slot, price)`. Equivocate on two prices = key extraction = bond drained, 80% paid to harmed traders. Inherits HIP-3 (Hyperliquid Dec 2025) margining; EOTS is the novel slashing primitive (Babylon 2024).
- **Multiverse Lending (Paradigm, Dave White, May 2025).** Borrows against conditional tokens scoped to outcomes. Probability-lattice algebra (push-down / pull-up maps) ensures collateral in `notFiredETH` only collateralizes `notFiredUSD`, so liquidations only fire inside the matching "verse." When the event resolves, verses merge back to base collateral.
- **Self-Resolving PM (BTS + α-halt) — cameo only.** Used as the resolution layer for *subjective* verses where no external oracle exists. Sequential reporters bet on unverifiable propositions; each reporter's payoff is scored against the *next* reporter's belief using cross-entropy plus a Bayesian Truth Serum bonus. An α-weighted coin flip halts the market; accumulated log-scores settle.

The conditional token, perp on conditional token, and verse-scoped lending pool all reference the same `market_id` — so the slashing, margining, and lending invariants compose cleanly.

## Why it lands (Orbital filter)
*"Every event in the world is now a tradable asset"* passes the generalist test: a non-crypto journalist understands the sentence. The 60-second demo is the best in the entire portfolio — type a free-text event → mint conditional pair → list perp → open lending → resolve via BTS → equivocate the oracle and watch the bond drain live on stage. Six demo beats in one minute. Direct lineage to Orbital Pool (Dave White = Multiverse author = Orbital author) so the Paradigm-research credibility transfers automatically.

## Future utility (2026 market thesis)
**Who buys:**
- Prediction-market degens who want leverage on conditional positions.
- Builders bootstrapping new tokenized assets on Robinhood Chain who need an instant credit + derivative market.
- Crypto-native hedge fund desks who want macro-event tail exposure with capital efficiency.

**Why mid-2026 (not 2025, not 2027):**
- Paradigm's *Multiverse Finance* paper dropped May 2025 — before that no one had verse-scoped liquidation math.
- Hyperliquid HIP-3 (Dec 2025) made permissionless-perp the new design space. OMNIVERSE is the first HIP-3-grade primitive on Arbitrum with an EOTS auto-slashing layer Hyperliquid's whitelist doesn't have.
- Polymarket V2 (Apr 28, 2026) makes conditional-token depth real exactly during the hackathon window.
- Robinhood Chain testnet (Feb 10, 2026) needs a primitive that turns tokenized stocks into a market-creation platform.
- None of these were jointly production-ready before mid-2026.

## Business model
- $1K listing-bond skim per launch
- 2bp perp trading fees
- 10% take on lending interest spread
- 30bp on BTS-resolved settlements

Long-tail prediction-market venues already do $1B+ monthly volume globally (Polymarket + Kalshi). Capture even 1% of that volume at 2bp = $20K/mo from just the perp fee leg.

## Sponsor / track fit
- **Primary: $70K Overall.** Category-defining novel primitive. PATTERN.md says category-defining wins. The 60-second on-stage demo IS the killer moment.
- **Reserved seat: $30K Robinhood Chain.** Robinhood owns Kalshi (acquired 2025); event-asset distribution is dead-center of their roadmap. OMNIVERSE is the credit + derivative layer for that distribution.
- **Stylus showcase.** EOTS secp256k1 verifier + push-down/pull-up verse algebra are Rust-heavy math (~10-30× gas savings).
- **Best Agentic ($15K)** — NOT a strong fit. Skip.

**Max reserved-seat reach:** ~$50K (Overall + RH Chain).

## 3-week MVP scope
**Week 1 — Verse algebra + perp factory contracts.**
- Days 1-2: Fork Polymarket's Gnosis Conditional Tokens (ERC-1155 outcome shares).
- Days 3-4: Stylus contract for push-down / pull-up verse algebra (the Dave White math) + Foundry fuzz tests.
- Days 5-7: HIP-3-style permissionless perp factory in Stylus, EOTS secp256k1 verifier.

**Week 2 — Lending pool + BTS resolution + cameo.**
- Days 8-10: Verse-scoped lending pool (LTV per leaf of event tree) + circuit breaker on disputed verses.
- Days 11-12: BTS + α-halt LMSR market maker (Stylus) for subjective verses. One demo market: *"Will Robinhood Chain hit 100K daily users by July 1, 2026?"*
- Days 13-14: One-tx "list + lend + resolve" orchestrator + minimal CLOB.

**Week 3 — Live trial + demo.**
- Days 15-17: Deploy 3 demo markets on Robinhood Chain testnet (real asset, conditional asset, subjective asset). Recruit 30-50 testers via Polymarket Discord + crypto Twitter.
- Days 18-19: On-stage equivocation script. Deliberately sign two conflicting EOTS posts, prove key extraction, drain the bond live.
- Days 20-21: 3-min demo video, pitch deck (citing Paradigm May 2025 + Babylon EOTS lite paper + Polymarket V2 + Vitalik info-finance essay), submit Overall + Robinhood Chain.

## Risks
**The one that could kill this:** Regulatory exposure on permissionless derivative listing. CFTC/SEC scrutiny on permissionless event-perps is the biggest commercial threat (market-2026 lens called this *"existential"*).

**Mitigation:**
- KYC-gated frontend at launch; the factory primitive itself is base-layer infra (analogous to Uniswap V2 not being a securities exchange).
- Slide 9 of pitch deck: compliance roadmap (Spearbit audit + legal opinion by day 60).
- Pre-record the live equivocation script as fallback if it flakes on stage.

**Secondary risks:**
- Cold-start liquidity on demo-day testnet markets (mitigate with seeded LP + tester recruitment).
- Polymarket V2 launch slips past Apr 28 — falls back to Polymarket V1 conditional-token contracts.

## Lens verdicts
- **judge-wow (9.5/10 — class leader):** *"This is the fusion that genuinely hits the Orbital baseline. The pitch is generalist-graspable. The on-stage demo is the best in the entire portfolio — three independent primitives glued into a single 60-second user action, with a self-policing slashing punchline."*
- **market-2026 (6/10 — REJECT):** *"Thin Day-30 revenue, regulatory risk, builder-only TAM. The 'science project with no buyer.'"*
- **staleness-detector (mixed):** Multiverse Lending 8/10 (Paradigm May 2025 is the "why now"). Self-Resolving PM 3/10 — *use as cameo only, not headline.* Permissionless Perp inherits HIP-3 Dec 2025 freshness.

**Honest framing:** market-2026 is correct that revenue is thin and regulation is real — but for a 10-minute hackathon judging window, wow dominates revenue projection. Address regulation in pitch deck (slide 9) and let the wow do the rest.

## Sources
- `ideas/02-defi/idea-08-permissionless-perp-factory.md` — Permissionless Perp Factory + EOTS
- `ideas/02-defi/idea-01-multiverse-lending.md` — Multiverse Lending
- `ideas/06-market-governance/idea-01-self-resolving-prediction-market.md` — Self-Resolving PM (cameo)
- Paradigm — *Multiverse Finance* (Dave White, May 2025)
- Babylon — EOTS lite paper (2024)
- Hyperliquid — HIP-3 (Dec 2025)
- Polymarket V2 release notes (Apr 28, 2026)
- Vitalik — info-finance essay (Nov 2024)
