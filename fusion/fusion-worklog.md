# Fusion Worklog — 3 Deep Options for Arbitrum Open House 2026

**Synthesizer:** fusion-architect
**Date:** 2026-05-25
**Inputs:** 8 shortlisted ideas + 4 seed fusions + 3 parallel lens analyses (market-2026, judge-wow, staleness-detector) + THESIS.md + PATTERN.md.

---

## The conflict the lenses surfaced (and why it's load-bearing)

The two strongest lenses point in **opposite directions**:

| Lens | Top pick | Score | Kill |
|---|---|---|---|
| market-2026 | Covariance OS | 8/10 | Asset Genesis Stack (6/10 — "thin Day 30, regulatory risk, B2B TAM") |
| judge-wow | Asset Genesis Stack | 9.5/10 | Covariance OS (6.5/10 — the word "covariance" fails the generalist test) |
| staleness-detector | (broader scan) Sealed Model + WE Agent Wallet fusion | 8-9/10 each | ClaimGPT (4/10 — GuardChain collision), Privacy Pools (1/10 — Shinobi collision), Self-Resolving PM (3/10 — BTS is 2023-era) |

**What's going on:** Hackathon judges score on a hybrid of "would I fund this" (market) and "did I gasp" (wow). PATTERN.md says Bengaluru winners hit 18+/20 by being *both* commercially legible *and* viscerally pitchable. Neither lens alone is sufficient — but for a **demo-day product**, wow > market by roughly 60/40 (judges decide in ~10 minutes; revenue projections are post-hoc). The frame I'm using to break the tie: **the pitch reframe that recovers Covariance OS's generalist gasp without losing its math credibility is the real fix.** And the staleness lens supplies a third axis (one of the original 8 — Self-Resolving PM — is 2023-era despite a strong wow score, which forces me to either reframe its role or replace it).

I am NOT averaging the lenses. I am picking three options where each is the *unambiguous winner of its own axis*, and I show every lens verdict for every option — including disagreements.

---

## The three maximally-distinct options

```
   ┌────────────────────────────────────────────────────────────────┐
   │                                                                │
   │   OPTION A — OMNIVERSE                  (Market / RWA spine)   │
   │   "Every event in the world is now a tradable asset."          │
   │                                                                │
   │   OPTION B — SIGMA                      (DeFi-math spine)      │
   │   "Hyperliquid's cross-margin, for spot Apple and Tesla."      │
   │                                                                │
   │   OPTION C — INVISIBLE HAND             (AI-agent spine)       │
   │   "An AI agent whose model is sealed and whose wallet has      │
   │    no key — until it proves it did the job."                   │
   │                                                                │
   └────────────────────────────────────────────────────────────────┘
```

Each option is internally coherent, ships in 3 weeks, and is *maximally different* from the other two on technical primitive, sponsor track, buyer, and demo aesthetic. Option C draws on `01-ai-agents/idea-01` (Sealed Model) and `01-ai-agents/idea-04` (WE Agent Wallet) — both verified in the catalog. Staleness-detector flagged these as the 9/10 and 8/10 most 2026-native ideas in the entire vault, and as a natural fusion. I am using them because the original AI-agent triplet from the 8 (SwarmVault, ClaimGPT, LiquiBid) is structurally weaker (saturation, prior-winner collision, B2B dependency); replacing rather than averaging preserves the "maximally distinct" constraint.

---

# OPTION A — OMNIVERSE

> **Mint a new asset on stage in 60 seconds. Then trade it, borrow against it, and let the market resolve itself.**

## 1. Name
**OMNIVERSE** — every event becomes a verse, every verse a market. Short, brandable, googleable.

## 2. One-line pitch (≤15 words)
> **"Every event in the world is now a tradable asset."** *(10 words.)*

Backup explainer (14 words):
> *"Mint a new asset, list its perp, borrow against it — all in one transaction."*

## 3. Source ideas fused
- `02-defi/idea-08-permissionless-perp-factory.md` — Permissionless Perp Factory + EOTS oracle bond
- `02-defi/idea-01-multiverse-lending.md` — Multiverse Lending (conditional-token margin algebra)
- `06-market-governance/idea-01-self-resolving-prediction-market.md` — Self-Resolving PM (BTS + α-halt) *as the resolution layer for non-price markets*

## 4. What's actually new (vs each part alone)
- **Single-tx capital-markets bootstrap.** Perp Factory alone gives you a market on an existing asset; Multiverse Lending alone gives you collateral on an *existing* conditional token; Self-Resolving PM alone resolves *one* market. Fused, the user types a free-text event prompt and the system *creates* the conditional token pair AND lists its perp AND opens its lending pool AND wires it to a self-resolving oracle — in one transaction.
- **Self-policing across all three legs.** EOTS bond on the perp's oracle, verse-scoped liquidation on the lending pool, BTS-α resolution on subjective verses. No external oracle, no governance vote, no whitelist anywhere in the stack.
- **The conditional-token-as-perp-underlying.** Existing perps trade real assets; existing prediction markets trade outcome shares. OMNIVERSE lets you **trade a perp whose underlying is a conditional token** ("YES Trump wins" futures), and **borrow USDC against that perp's collateral, scoped to the matching verse**. Nobody has shipped this.

## 5. 2026 market thesis
- **Who buys:** (1) Prediction-market degens who want leverage on conditional positions, (2) builders bootstrapping new tokenized assets on Robinhood Chain who need an instant credit + derivative market, (3) crypto-native hedge fund desks who want macro-event tail exposure with capital efficiency.
- **Who pays:** Listing bond skim ($1K/launch), 2bp perp trading fees, 10% take on lending interest spread, 30bp on BTS-resolved settlements.
- **Why 2026 (not 2025, not 2027):**
  - Paradigm's *Multiverse Finance* paper dropped May 2025 — before that, no one had the verse-scoped liquidation math (staleness verdict on Multiverse Lending: 8/10 — "Paradigm May 2025 paper is the 'why now'").
  - Hyperliquid HIP-3 (Dec 2025) made permissionless-perp the new design space; OMNIVERSE is the **first HIP-3-grade primitive on Arbitrum** with an EOTS auto-slashing layer Hyperliquid's whitelist doesn't have.
  - Polymarket V2 launches April 28, 2026 — conditional-token depth becomes real exactly during our hackathon window.
  - Robinhood Chain testnet (Feb 10, 2026) needs a primitive that turns tokenized stocks into a market-creation platform, not just a tradable list.
  - **The 2026-specific primitive it requires:** Hyperliquid HIP-3 (Dec 2025) as the reference design + Babylon EOTS production-grade secp256k1 verifier in Stylus + Polymarket V2 conditional-token liquidity. None of these were simultaneously production-ready before mid-2026.

## 6. Judge appeal + best sponsor track
- **Primary track: $70K Overall.** This is the "category-defining novel primitive" that PATTERN.md says wins. The 60-second on-stage create-a-market-from-nothing demo IS the killer moment. Direct lineage to Orbital Pool (Dave White, Multiverse author = Orbital author — credibility transfers automatically).
- **Reserved seat: $30K Robinhood Chain.** Robinhood owns Kalshi (acquired 2025); event-asset distribution is dead center of their roadmap. OMNIVERSE is the credit + derivative layer for that distribution. Robinhood's product team is the literal target audience.
- **Stylus showcase:** Both EOTS secp256k1 verifier and the push-down/pull-up verse algebra are Rust-heavy math that justifies Stylus over Solidity (~10-30x gas savings).
- Best Agentic ($15K) is **not** a strong fit and we should not chase it for this option.

## 7. 3-week build feasibility
- **Week 1 — Verse algebra + perp factory contracts.**
  - Days 1-2: Fork Polymarket's Gnosis Conditional Tokens (ERC-1155 outcome shares).
  - Days 3-4: Stylus contract for push-down/pull-up verse algebra (the Dave White math) + Foundry fuzz tests.
  - Days 5-7: HIP-3-style permissionless perp factory in Stylus, EOTS secp256k1 verifier (shared lib with idea 06 in catalog).
- **Week 2 — Lending pool + BTS resolution + self-resolving cameo.**
  - Days 8-10: Verse-scoped lending pool contract (LTV per-leaf-of-event-tree) + circuit breaker on disputed verses.
  - Days 11-12: BTS+α-halt LMSR market maker (Stylus) for the "subjective" verses where there's no oracle; one demo market: *"Will Robinhood Chain hit 100K daily users by July 1, 2026?"*
  - Days 13-14: One-tx "list+lend+resolve" orchestrator + minimal CLOB matching engine on the perp leg.
- **Week 3 — Live trial + demo.**
  - Days 15-17: Deploy 3 demo markets on Robinhood Chain testnet (real asset, conditional asset, subjective asset), recruit 30-50 testers via Polymarket Discord + crypto Twitter. Measure: time-to-first-market-creation, BTS resolution accuracy on seeded ground-truth markets, EOTS equivocation drains under adversarial test.
  - Days 18-19: On-stage equivocation script: deliberately sign two conflicting EOTS posts, prove key extraction, drain the bond live.
  - Days 20-21: 3-min demo video, pitch deck, README citing Paradigm May 2025 + Babylon EOTS lite paper + Polymarket V2 release notes + Vitalik info-finance essay, submit to Overall + Robinhood Chain tracks.

## 8. The one risk that could kill this
**Regulatory exposure on permissionless derivative listing.** market-2026 lens called this "existential" — CFTC/SEC scrutiny on permissionless event-perps is the biggest commercial threat. Mitigation: KYC-gated frontend at launch; the factory primitive itself is base-layer infra (analogous to Uniswap V2 not being a securities exchange). Reserve a backup demo path: if the live equivocation script flakes on stage, pre-record it as fallback.

## 9. Lens verdicts (in their own words)
- **judge-wow (9.5/10, *the* winner of the wow axis):** *"This is the fusion that genuinely hits the Orbital baseline. The pitch (every event is a tradable asset) is generalist-graspable. The on-stage demo is the best demo in the entire portfolio — three independent primitives glued into a single 60-second user action, with a self-policing slashing punchline at the end."*
- **market-2026 (6/10, REJECT):** *"Thin Day-30 revenue, regulatory risk, builder-only TAM. The EOTS perp factory is an excellent infra primitive worth a standalone idea post-hackathon. The multiverse lending layer adds complexity without adding demo-day impact. This one is the 'science project with no buyer' the task description warned about for demo day context."*
- **staleness-detector:** Mixed. Multiverse Lending 8/10 (genuinely 2026-native, Paradigm May 2025 paper), Self-Resolving PM 3/10 (BTS is 2023-era — *use it as a cameo BTS resolution layer, not as the headline mechanism*). Permissionless Perp Factory not in the staleness scan but inherits Hyperliquid HIP-3 (Dec 2025) freshness.

**Disagreement framing for OMNIVERSE:** market-2026 is correct that Day-30 revenue is thin and regulatory exposure is real. But judge-wow is correct that this is the only fusion that hits the Orbital bar with a generalist-gasp pitch and a six-beat demo. **For a hackathon judged on 10-minute impression, wow dominates revenue projection. The fix is not to drop OMNIVERSE — it is to acknowledge the regulatory risk in the pitch deck (slide 9: "Compliance roadmap — KYC-gated frontend at launch; Spearbit + legal opinion by day 60") and let the wow do the rest.**

---

# OPTION B — SIGMA

> **Hyperliquid's cross-margin, for spot Apple and Tesla. Plus the trade Citadel runs against you.**

## 1. Name
**SIGMA** — refracts a basket of correlated assets into its components and back. Short, no math jargon, visualizable as a logo.

## 2. One-line pitch (≤15 words)
> **"Bring Hyperliquid's cross-margin to spot Apple and Tesla. Plus their hedge fund's favorite trade."** *(14 words.)*

Generalist-only version (10 words):
> *"Same basket. 25% more borrowing. Plus a built-in hedge."*

**Note on the pitch reframe:** judge-wow's killer objection was the word "covariance." This pitch deliberately *never* says "covariance" or "Cholesky" or "Mahalanobis" in the headline. The math judges still get the math (it's all in the comparison table and the demo); the generalist judges hear *"Hyperliquid for spot stocks"* — a primitive everyone in 2026 already understands.

## 3. Source ideas fused
- `02-defi/idea-04-ndim-portfolio-lending.md` — N-Dimensional Portfolio-Margin Lending (Mahalanobis LTV)
- `02-defi/idea-03-dispersion-pool.md` — Dispersion Pool (Cholesky-weighted variance basket)

(`02-defi/idea-01-multiverse-lending.md` — Multiverse Lending — was considered for a "conditional collateral" Option-B variant, but the Verdict×Covariance market verdict was that this is better as a *Year-2 collateral-type addition*, not a Week-3 deliverable. Drop.)

## 4. What's actually new (vs each part alone)
- **One covariance engine, two products.** The 20×20 Σ-matrix that prices borrow LTV is the *same* matrix that prices the dispersion vault's vega weighting. Same Stylus contract, two revenue streams. Aave can't add this without architectural replacement; Volmex-style variance products can't add lending without becoming a bank.
- **First on-chain CBOE DSPX equivalent for tokenized equities.** CBOE's Dispersion Index is TradFi-only; SIGMA is the **first permissionless retail-accessible version**, settled in USDC against Robinhood Chain tokenized stocks.
- **Honest cross-margin for spot.** Hyperliquid shipped portfolio margin for perps in Dec 2025; SIGMA is the **first clean implementation for spot lending** on Arbitrum. Live diff against Aave: same basket, 25% more borrowing power, visible in the demo.

## 5. 2026 market thesis
- **Who buys:** (1) DeFi power traders capped by Aave's isolation limits (the public "I've been trying to lever a hedged basket and Aave won't let me" Twitter thread is real), (2) crypto-native quant desks (Wintermute, GSR, Cumberland) who want a dispersion-trading venue but won't touch the Volmex stack, (3) DAO treasurers hedging tokenized-equity positions on Robinhood Chain.
- **Who pays:** 10% take rate on borrow interest spread + 2/20 on the dispersion vault. Day-30 realistic: $50K/month if 5-10 quant deposits land (market-2026's number, not mine).
- **Why 2026 (not 2025, not 2027):**
  - **Hyperliquid portfolio margin shipped Dec 2025** — the design is now mainstream-trader-accepted but has *zero* spot-lending implementation. SIGMA is the spot version of the perp primitive everyone now wants.
  - **Robinhood Chain tokenized equity launch (Feb 2026)** — the first time you can actually do an on-chain dispersion trade with AAPL, MSFT, GOOG, AMZN, NVDA. Pre-2026 there were no real tokenized US equities with chain-native liquidity.
  - **Stylus maturity in 2026** — Cholesky on a 20×20 matrix at every health check is the canonical Stylus benchmark case (~30x cheaper than Solidity per N-Dim idea author).
  - **The 2026-specific primitive it requires:** Robinhood Chain tokenized-equity liquidity + Stylus production-grade BLAS-ish math + Hyperliquid HIP-3 having normalized portfolio-margin as the trader UX. None of these were jointly true in 2025.

## 6. Judge appeal + best sponsor track
- **Primary track: Stylus showcase.** SIGMA is the **single best Stylus case study in the entire fusion set** — Cholesky on a real-time covariance matrix is exactly the kind of math that loses to Solidity gas costs. The numerical pitch ("180k gas for a 5×5 Cholesky, 320k gas for a 20×20") is concrete and falsifiable.
- **$30K Robinhood Chain (reserved seat).** Tokenized-equity dispersion trading + spot cross-margin are the canonical first strategies on a tokenized-stock chain. Robinhood retail wants Hyperliquid-grade cross-margin honesty; SIGMA ships exactly that for spot.
- **$70K Overall.** Clean mathematical primitive, Paradigm-lineage research narrative. judge-wow gives it 6.5 *for the generalist test only* — with the pitch reframe ("Hyperliquid's cross-margin for spot"), the generalist axis recovers because Hyperliquid is now generalist vocabulary.
- Best Agentic ($15K) — not a fit. Skip.

## 7. 3-week build feasibility
- **Week 1 — Math core.**
  - Days 1-2: Stylus Cholesky factorization + Ledoit-Wolf shrinkage estimator + Mahalanobis distance routine. Foundry fuzz on numerical stability.
  - Days 3-4: Chainlink price-stream covariance pipeline (rolling 30-day Σ for 20 assets: BTC/ETH/SOL + tokenized AAPL/MSFT/GOOG/AMZN/NVDA + gold + others).
  - Days 5-7: Portfolio-margin lending pool contract with Σ-driven healthcheck, dutch-auction liquidation over the marginal-risk component.
- **Week 2 — Dispersion vault + UI.**
  - Days 8-10: Carr-Madan log-payoff replication math + Cholesky-vega-weighted basket construction. Option-strip integration (Lyra-style on the deep names, discrete-strike approximation on the long-tail).
  - Days 11-12: Daily rebalance keeper, P&L attribution.
  - Days 13-14: Live heat-map UI of the 20×20 correlation matrix + side-by-side Aave-vs-SIGMA borrowing-power widget + dispersion P&L chart.
- **Week 3 — Trial + ship.**
  - Days 15-17: Recruit 20 quant testers (DeFi Twitter, Bankless community, ex-TradFi desks). Tasks: (1) deposit mixed crypto-equity basket and beat Aave's borrowing quote, (2) deposit into dispersion vault during a low-correlation week, measure realized P&L. Benchmark: ≥20% more borrowing capacity vs Aave on the median tester basket; dispersion vault Sharpe ≥1 over 14-day backtest.
  - Days 18-19: Live demo: judge picks a basket on stage, two browser tabs show Aave's quote vs SIGMA's quote, then "add a short ETH perp as collateral" → Aave's borrow drops, SIGMA's borrow rises (the basket got more market-neutral, the matrix knows it).
  - Days 20-21: Pitch deck (Hyperliquid comparison front and center, dispersion as "the Citadel trade you can't normally do"), 3-min video, submit Overall + Robinhood Chain + Stylus.

## 8. The one risk that could kill this
**Robinhood Chain tokenized-equity option liquidity is too thin to make the dispersion leg work.** The lending leg ships regardless; the dispersion leg needs deep option books per constituent. Mitigation: launch dispersion with a crypto-basket fallback (BTC/ETH/SOL/AVAX vs total-cap index) so the demo isn't dependent on option-AMM depth that doesn't exist yet. Acknowledge in pitch: *"v1 dispersion runs on crypto; tokenized-equity dispersion is v2 conditional on RH-Chain option market depth."*

## 9. Lens verdicts (in their own words)
- **market-2026 (8/10, *the* winner of the market axis):** *"Clear buyer with real capital, two compounding revenue streams, genuinely hard to copy. Risk: niche market (quants only) caps total addressable TVL unless retail wrapper is added."* And: *"Day 30 runway: $50K/month if 5-10 quant deposits land."*
- **judge-wow (6.5/10, the lens's lowest fusion score):** *"Beautiful primitive, fails the generalist test. The pitch demands covariance literacy, and the audience for this hackathon is half-RH-retail-PMs, half-DeFi-natives. Smart but flat for half the room. The demo theatre rescues it slightly because the heat-map is visually striking."* **My response:** the pitch reframe above ("Hyperliquid's cross-margin for spot Apple and Tesla") fixes precisely the generalist failure mode the lens flagged. We never say "covariance" in the headline. The 6.5 was for the *original* covariance-OS pitch; with the reframe I estimate this rises to ~8.0 on the wow axis.
- **staleness-detector:** N-Dim Lending not directly scanned but inherits Hyperliquid HIP-3 freshness (Dec 2025). Dispersion Pool 5/10 — *"core math is 2010, Robinhood Chain dependency is the 2026 hook."* True. This is the option where staleness is *the* legitimate concern — we mitigate by leaning on Hyperliquid-portfolio-margin-as-spot (the genuinely 2026 framing) and the Robinhood Chain tokenized-equity dependency (the genuinely 2026 distribution).

**Disagreement framing for SIGMA:** judge-wow and market-2026 are *both right about the original framing* — the math is commercially superior and pitch-fragile. The reframe is the resolution: hide the word "covariance," lead with "Hyperliquid for spot stocks + the hedge fund trade." Same product, half the generalist friction. The math judges still get the heat-map demo and the Stylus benchmark.

---

# OPTION C — INVISIBLE HAND

> **An AI agent whose model is sealed and whose wallet has no key — until it proves it did the job.**

## 1. Name
**INVISIBLE HAND** — Adam Smith's term for self-organizing markets; here, the agent organizes itself out of cryptographic obligation. Memorable, slightly literary, distinct from the typical "Agentic Vault" naming pattern.

## 2. One-line pitch (≤15 words)
> **"An AI agent whose wallet doesn't exist until it does its job — and whose model doesn't either."** *(15 words.)*

Tighter (12 words):
> *"The AI agent has no wallet and no model — until it earns them."*

## 3. Source ideas fused
- `01-ai-agents/idea-01-sealed-model.md` — Sealed Model (KZG witness-encrypted AI weights, decrypted by a Lagrange DeepProve zkML capability proof)
- `01-ai-agents/idea-04-witness-encrypted-agent-wallet.md` — Witness-Encrypted Agent Wallet (T+1-eWEB signature-based WE keyed to a drand-attested task-completion oracle)

(**Why these and not the AI-agent triplet from the 8.** The staleness lens flagged that the natural AI-agent fusion candidate inside the catalog is Sealed Model + WE Agent Wallet — *"a single Stylus WE library could underpin both. The 'model that pays itself' + 'wallet that appears when the agent succeeds' could be a unified product: the first end-to-end cryptographic agent commerce protocol — no trusted coordinator at any step."* The original triplet candidates from the 8 each have a kill condition (see Kill List below). I verified both files exist in `ideas/01-ai-agents/` before using them.)

## 4. What's actually new (vs each part alone)
- **One KZG-WE primitive, two unrelated agent properties.** The same Rust Stylus port of IACR 2024/264 (KZG witness encryption) underpins (a) the model's existence and (b) the wallet's signing key. The fusion isn't "two products glued together" — it's *one cryptographic substrate, used to seal both halves of the agent*. The agent has no key, no weights, no wallet until and unless it proves the capability and delivers the task. This is the **first end-to-end zero-trusted-coordinator agent commerce protocol** anyone has shipped.
- **Outcome-bonded agent economy primitive.** Today's "agent wallet" pattern is: hot key in a TEE + policy guardrails + hope. INVISIBLE HAND replaces the trust assumption with cryptography: no completion → no key → no theft. Combined with the sealed-model layer, the *entire* agent (capability + custody) is contingent on observable outcome. ERC-8004 reputation just rides on top.
- **The demo is genuinely impossible-looking.** Judge clicks "verify and decrypt" → zkML proof posts → model weights download AND agent wallet drains AND ERC-8004 reputation updates, all from the *same* witness-extracted secret. The audience watches a wallet's USDC move *after* a cryptographic proof of work that was previously unprovable.

## 5. 2026 market thesis
- **Who buys:** (1) Regulated AI procurement (defense contractors, big-pharma R&D, fintech credit-model buyers) who today rely on SOC-2 reports because they have no way to verify "is this the model you said it was?" — sealed-model is the cryptographic alternative; (2) every builder of an autonomous AI agent paid for work (freelance contractors, DAO bounty workers, agent-to-agent commerce) who today accepts the hot-key-in-TEE risk; (3) protocol designers who want outcome-bonded payment rails that don't need a trusted coordinator.
- **Who pays:** 0.5% take rate on sealed-model marketplace transactions + 25bp on every witness-encrypted withdrawal. Combined TAM (per the idea-01 + idea-04 sources): regulated AI model market ~$25-35B by 2026; agent-managed AUM forecast $50B by 2027 (Citi GPS). At 1% of the regulated subset and 5% turnover on $50B → low-to-mid eight figures annual.
- **Why 2026 (not 2025, not 2027) — and this is the strongest of the three options on this axis:**
  - **Lagrange DeepProve-1 launched late 2025** — literally the enabling infrastructure for proving CNN-class model capability cheaply enough to do this in a demo.
  - **T+1-eWEB paper (IACR 2025/1064) Glaeser/Madathil 2025** — signature-based witness encryption only became a buildable thing in 2025; no production implementations exist.
  - **BLS12-381 Stylus precompiles** matured at scale in 2025 — without them the WE wallet costs $500K/op.
  - **ERC-8004 mainnet (Jan 2026)** — the agent identity standard that ties the reputation update to a registered ERC-8004 entity.
  - **The 2026-specific primitive it requires:** DeepProve-1 + T+1-eWEB + BLS12-381 Stylus + ERC-8004 + drand mature beacon — all four were not simultaneously production-ready before mid-2026. staleness lens: *"None of these primitives existed as production infrastructure before 2025-2026."*

## 6. Judge appeal + best sponsor track
- **Primary track: $15K Best Agentic.** This is the canonical Best Agentic build — ERC-8004 + ERC-4337 + WE-cryptography is *exactly* what Best Agentic was carved out to reward. Marlin / Phala TEE bounties also adjacent.
- **$70K Overall.** First deployed witness-encryption + zkML composition on Arbitrum. Falsifiable benchmark: *"verifier gas < 5M, proof time < 60s on Gemma3-class model."* Plus the sci-fi pitch makes Overall a real shot.
- **Stylus showcase.** Pairing-friendly curve operations (KZG verifier + BLS12-381 ops) are textbook Stylus territory.
- **$30K Robinhood Chain** — weak fit; not a flagship use case for Robinhood. Skip.
- **Asymmetric prize math:** This is the only option of the three where **both reserved seats (Best Agentic + Overall) are realistically in play** if executed well. Single build, ~$85K max exposure (per THESIS.md prize-math note).

## 7. 3-week build feasibility
- **Week 1 — WE Stylus library + sealed-model proof of concept.**
  - Days 1-2: Rust port of KZG witness encryption (IACR 2024/264) — this is the high-risk infrastructure work; start day 1. Foundry + cargo-stylus integration.
  - Days 3-4: Lagrange DeepProve verifier contract in Stylus. Encrypt a small CNN (CIFAR-10, ~100K params) under predicate "accuracy ≥ 0.85" on a public test set.
  - Days 5-7: End-to-end test: post zkML proof → verifier releases witness → witness decrypts blob → cleartext weights download. The "fake model" denial case also wired (no proof → no decryption forever).
- **Week 2 — WE Agent Wallet + drand integration.**
  - Days 8-10: Signature-based WE library (port from Glaeser/Madathil IACR 2025/1064) sharing the KZG primitives with the model side.
  - Days 11-12: ERC-4337 smart wallet with drand-watcher Stylus contract; single-task predicate (zkTLS-attested HTTPS-200 to a target URL). Wallet's signing key is encrypted to "drand signature for the first block after `done(T)` is emitted."
  - Days 13-14: ERC-8004 reputation hookup — successful completions ratchet up the agent's registry score; the same witness extraction that unlocks the wallet also signs the reputation update.
- **Week 3 — Unified demo + trial + ship.**
  - Days 15-17: 5-10 user trial: developer builds a toy agent that buys a sealed model, runs it, and gets paid through the WE wallet. Measure: end-to-end zero-trusted-coordinator flow completion rate; mean witness-extraction-to-payment latency.
  - Days 18-19: Build the on-stage demo: judge buys a sealed model live, an agent uses it to complete a task (post a verifiable HTTPS-200 to a tester URL), the agent's wallet drains paying both the model seller and the agent operator — all driven by one zkML proof + one drand signature.
  - Days 20-21: Pitch deck citing IACR 2024/264 + IACR 2025/1064 + DeepProve-1 + Citi GPS agentic AUM forecast. 3-min video. Submit Overall + Best Agentic + Stylus.

## 8. The one risk that could kill this
**WE library maturity.** Both idea-01 and idea-04 note this explicitly — the KZG witness encryption and signature-based WE constructions are research-grade, with no production Rust ports. We are shipping the ports. If the Stylus implementation slips past Day 10, the unified demo collapses. **Mitigation:** Day 1 spike to evaluate library risk; fallback to a Phala-TEE-based "trusted enclave decryption" stand-in for the model side (clearly labeled as a v1 trust-assumption), keeping the wallet side cryptographic. This is the most technically-aggressive option of the three and the most likely to fail in a way that's invisible to judges (because "the WE library isn't working" doesn't make a good demo).

## 9. Lens verdicts (in their own words)
- **staleness-detector (9/10 + 8/10 → *the* winner of the staleness axis):** *"The most 2026-native idea in the vault. Cannot be confused with any prior Bengaluru winner. Requires Lagrange DeepProve-1 (late 2025), T+1-eWEB (IACR 2025/1064), BLS12-381 Stylus, ERC-8004 (Jan 2026), drand maturity — none of these were simultaneously production-ready before mid-2026."* And on the fusion specifically: *"This would be the first end-to-end cryptographic agent commerce protocol — no trusted coordinator at any step. Uniquely 2026-native."*
- **market-2026 (not directly scored — these ideas were outside the 8):** would likely score 6-7/10. Regulated AI procurement TAM is real but B2B-slow; agent-managed AUM forecast is real but speculative; revenue model is clean but Day-30 numbers depend on hand-building one model marketplace partner.
- **judge-wow (not directly scored — outside the 8):** The pitch *"An AI agent whose wallet doesn't exist until it does its job"* almost certainly clears the Orbital bar — it's a 12-word self-contained paradox. My estimate: 8.5-9.0 wow. Equal to Multiverse Lending's wow, below OMNIVERSE's 9.5. The demo is theatrical (judge watches a wallet appear out of nothing) but requires explaining KZG WE in the pitch, which costs 5-10 seconds of bandwidth.

**Disagreement framing for INVISIBLE HAND:** the three lenses *don't* directly disagree on this option — they weren't all asked. The staleness lens (which surveyed the whole catalog) treats this as the strongest 2026-native fusion available. The market and wow lenses didn't evaluate it because it falls outside the original 8, but inherited estimates suggest 6-7 (market, B2B drag) and 8.5-9.0 (wow, sci-fi pitch). The honest read: **this is the option where the 2026 hard-tech moat is strongest, the wow factor is high but not class-leading, and the commercial story is real but slowest to monetize. It is the only option of the three that can simultaneously win Best Agentic AND Overall reserved seats** — a property neither A nor B has.

---

# Comparison snapshot — when each option wins

| Dimension | OMNIVERSE (A) | SIGMA (B) | INVISIBLE HAND (C) |
|---|---|---|---|
| Headline pitch | "Every event is a tradable asset" | "Hyperliquid for spot Apple and Tesla" | "An AI agent whose wallet doesn't exist until it does its job" |
| Pitch spine | Market / RWA / event-asset | DeFi math / cross-margin | AI agent / cryptographic commerce |
| 2026-primitive load-bearing | Hyperliquid HIP-3 + Polymarket V2 + RH Chain | Hyperliquid PM + RH Chain tokenized stocks + Stylus | DeepProve-1 + T+1-eWEB + BLS12-381 + ERC-8004 |
| Best track | Overall ($70K) + Robinhood Chain ($30K) | Stylus + Robinhood Chain ($30K) + Overall | Best Agentic ($15K) + Overall ($70K) |
| Max reserved-seat exposure | RH-only (~$50K) | RH-only (~$50K) | Both seats in play (~$85K) |
| Wow score (judge-wow) | 9.5 — class leader | 6.5 (8.0 after reframe) | 8.5-9.0 (est) |
| Market score (market-2026) | 6/10 | 8/10 — class leader | 6-7/10 (est) |
| Staleness score | mixed (8 / 3 / —) | mixed (— / 5 / —) | 9/10 + 8/10 — class leader |
| Single failure mode | CFTC/SEC on permissionless derivatives | RH-Chain option-AMM depth too thin | WE library doesn't ship in 3 weeks |
| Generalist test (PATTERN.md) | passes violently | passes (after reframe only) | passes (cryptographic-paradox style) |
| Demo theatre | 60-second create-a-market + live equivocation drain | live Aave-vs-SIGMA diff + 20×20 heat-map | wallet appears from cryptographic proof |
| Team-size sensitivity | 3-person comfortable | 3-person comfortable | 3-person tight; 2-person infeasible |

---

# The honest recommendation if forced to one

**OMNIVERSE.** Three reasons, in order:
1. Judge-wow (the lens with the most decision-weight in a 10-minute hackathon evaluation) calls it the clearest Orbital-bar fusion of the entire set, and the only one whose pitch a non-crypto journalist would screenshot.
2. The on-stage demo (type a free-text event → mint conditional pair → list perp → open lending → resolve via BTS → equivocate oracle and watch the bond drain) is the **best demo in the entire portfolio**. PATTERN.md is explicit that prior winners landed the value in the first 30 seconds; OMNIVERSE lands it in *the first 60 with continuous escalation*.
3. Double-reserved-seat eligibility (Overall + Robinhood Chain) maximizes prize math, and the Paradigm-research lineage (Dave White = Multiverse author = Orbital author) gives free credibility.

The market-2026 objection (thin Day-30 revenue, regulatory risk) is *correct* but resolvable in the pitch deck — slide 9 covers compliance roadmap and the asymmetric upside (every event tradable) covers the revenue projection lens.

**If you're risk-averse on regulatory exposure, build SIGMA** — cleaner commercial story, no permissionless-derivative landmine, but you give up the class-leading wow factor and one reserved seat.

**If you have an unusually crypto-deep team and want the strongest 2026-native moat with the most asymmetric prize math, build INVISIBLE HAND** — but only if Day-1 spike confirms the KZG-WE Stylus port is feasible. This is the only option where the moat is *the cryptography itself*, not the market design.

---

# KILL LIST — original 8 ideas to drop entirely (not merged into A/B/C)

| Idea | Why it fails the 2026 + market + wow filter |
|---|---|
| `03-defi-ai/idea-08-ai-swarm-vault.md` (SwarmVault) | **THESIS.md explicit avoid:** *"AI portfolio managers / AI yield farmer / AI trader → Saturated. ~20 teams per hackathon. Skip."* market-2026 verdict: *"Direct violation of THESIS.md's explicit 'avoid' list. Recommend against."* staleness 6/10 — slashing-with-attestation angle is genuinely novel but cannot prevent the "we added AI agents" framing from blending into the Yearn-clone background. **Drop entirely.** |
| `03-defi-ai/idea-02-auto-adjudicated-insurance.md` (ClaimGPT) | **Prior winner collision.** staleness 4/10: *"Direct overlap with GuardChain AI prior winner. The TEE attestation differentiates, but not enough to avoid the 'we've seen this' reaction. This is the most dangerous staleness risk of any 'tier-A' idea."* market-2026 also rejects as standalone: *"Without a signed insurance partner, this is a science project."* High wow score (9.0) does NOT save it — the staleness collision is a kill signal a hackathon judge can fire in 30 seconds (*"isn't this GuardChain with TDX?"*). **Drop entirely.** Notably this is the *single most-flagged-as-stale tier-A idea*; ignoring the staleness collision and folding it into a fusion would be costly. |
| `03-defi-ai/idea-15-ai-liquidation-auctions.md` (LiquiBid) | **B2B distribution dependency.** market-2026: *"Best agentic idea commercially. Real buyer, real revenue, B2B. Risk is integration dependency — zero revenue without a signed protocol partner."* In a 3-week window with no Aave/Morpho governance partnership pre-arranged, the Day-30 revenue is $0 and the demo has to be simulated. wow score 8.5 is real but tlock+drand+sealed-bid is **inferior wow per-unit-complexity** to OMNIVERSE's create-a-market demo. **Drop.** (Note: tlock and sealed-bid auctions are genuinely valuable primitives — recommend revisiting LiquiBid as a *standalone follow-on* post-hackathon, not as a fusion ingredient.) |
| `06-market-governance/idea-01-self-resolving-prediction-market.md` (Self-Resolving PM) — **partial drop** | staleness 3/10: *"BTS design is 2023; requires nothing 2026-specific to build. A 2024 team could have shipped this."* I use it inside OMNIVERSE *only as the resolution cameo for subjective verses*, not as the headline. As a standalone hackathon submission: **drop**. The BTS math is the differentiator, not the year, and judges who know Vitalik's Nov 2024 info-finance essay have seen this submission pattern repeatedly through 2025. |

**Ideas from the 8 that survive (because they're inside an option):**
- `02-defi/idea-01-multiverse-lending.md` → inside OMNIVERSE
- `02-defi/idea-08-permissionless-perp-factory.md` → inside OMNIVERSE
- `02-defi/idea-04-ndim-portfolio-lending.md` → inside SIGMA
- `02-defi/idea-03-dispersion-pool.md` → inside SIGMA
- `06-market-governance/idea-01-self-resolving-prediction-market.md` → cameo in OMNIVERSE only

**Net of the 8: 4 absorbed, 1 demoted to cameo, 3 killed.** The two non-original ideas in INVISIBLE HAND (Sealed Model, WE Agent Wallet) were brought in from the broader catalog under the team-lead's "use as Option 3 if genuinely stronger" allowance and per staleness-detector's explicit fusion suggestion.

---

# Open questions for the team lead

1. **Lens-conflict tiebreaker confirmation:** I am weighting wow > market 60/40 for a 10-minute hackathon judging window. If the team has a signal that the panel is heavily VC/grant-allocator (revenue-focused), the weighting flips and SIGMA becomes the recommendation, not OMNIVERSE.
2. **Team size:** All three options are 3-person feasible. INVISIBLE HAND is the only one that's 2-person *infeasible* — the KZG-WE port + Lagrange DeepProve verifier + ERC-4337 wallet is too much WE-crypto specialization for two people.
3. **Permission to use Sealed Model + WE Agent Wallet as Option C:** I exercised the team-lead's stated allowance to substitute these for the Verdict Layer seed because (a) Verdict Layer as composed is partly stale (ClaimGPT GuardChain collision, Self-Resolving PM 3/10), (b) the staleness lens explicitly proposed this fusion, (c) both files exist in `ideas/01-ai-agents/` and the fusion is internally coherent under a single KZG-WE Stylus library. If the team-lead disallows this substitution and requires Option C to be drawn purely from the original 8, the best fallback is a **trimmed Verdict×Covariance** (per judge-wow's note that trimming to a single hero beat rescues it from 7/10 to 8.5/10) — but it would not be maximally distinct from SIGMA and would inherit ClaimGPT's GuardChain collision unless ClaimGPT is also dropped from it.
