# FUSED — Three Options for Arbitrum Open House 2026

**Status:** Final menu. Pick one. I write the Thesis-grade build plan for whichever you choose.
**Inputs:** 8 shortlisted ideas + 4 seed fusions + 3 parallel lens analyses + THESIS.md + PATTERN.md.
**Method:** A 4-teammate agent team analyzed every idea + seed through three lenses (market viability, judge wow, 2025-staleness), then a fusion architect synthesized 3 maximally-distinct options. Full working notes in `market-notes.md`, `pitch-notes.md`, `staleness-notes.md`, `fusion-worklog.md`.

---

## TL;DR

| | OMNIVERSE (A) | SIGMA (B) | INVISIBLE HAND (C) |
|---|---|---|---|
| **Spine** | Market / RWA / event-asset | DeFi math / cross-margin | AI-agent / cryptographic commerce |
| **Pitch** | *"Every event in the world is now a tradable asset."* | *"Hyperliquid's cross-margin for spot Apple and Tesla."* | *"An AI agent whose wallet doesn't exist until it does its job."* |
| **Wow (judge-wow)** | **9.5** — class leader | 6.5 → ~8.0 with reframe | 8.5–9.0 (est.) |
| **Market (market-2026)** | 6.0 | **8.0** — class leader | 6–7 (est.) |
| **Staleness (≥ = more 2026-native)** | 8 / 3 / mixed | mixed (math is older, distribution is 2026) | **9 + 8** — class leader |
| **Best sponsor track** | Overall ($70K) + Robinhood Chain ($30K) | Stylus + Robinhood Chain ($30K) + Overall | Best Agentic ($15K) + Overall ($70K) |
| **Max reserved-seat reach** | ~$50K | ~$50K | **~$85K — only one with both seats in play** |
| **One thing that kills it** | CFTC/SEC on permissionless derivatives | Robinhood-Chain option-AMM depth too thin in v1 | KZG witness-encryption Rust port doesn't ship in 3 weeks |
| **Team size needed** | 3 comfortable | 3 comfortable | 3 tight, 2 infeasible |
| **Demo theatre rating** | Best in portfolio | Strong (live Aave-vs-SIGMA diff + heat-map) | Strongest sci-fi (wallet appears from a cryptographic proof) |

---

## How to choose — a 2-axis read

```
Wow ↑
  10 ┤              ● OMNIVERSE (9.5, 6)
   9 ┤  ● INVISIBLE HAND (8.7, 6.5)
   8 ┤              ● SIGMA-reframed (8.0, 8)
   7 ┤
   6 ┤
       └──┬────┬────┬────┬────┬────→ Market →
          5    6    7    8    9    10
```

- **Top-right is the unicorn quadrant** — no single option is there. That's honest: each option dominates its axis and trades on the other.
- **OMNIVERSE** = bet on wow. The judging panel is humans deciding in 10 minutes; PATTERN.md says wow > revenue projection. Highest pitch ceiling, real regulatory floor.
- **SIGMA** = bet on market. Cleanest commercial story; the pitch reframe (drop the word "covariance," lead with "Hyperliquid for spot") recovers most of the wow gap.
- **INVISIBLE HAND** = bet on the 2026 moat. The only option whose primitives literally did not exist in 2024. Only option with two reserved seats in play. Highest tech risk.

---

# OPTION A — OMNIVERSE

> **Mint a new asset on stage in 60 seconds. Then trade it, borrow against it, and let the market resolve itself.**

**Pitch (10 words):** *"Every event in the world is now a tradable asset."*

**Backup explainer (14 words):** *"Mint a new asset, list its perp, borrow against it — all in one transaction."*

**Source ideas fused:**
- `02-defi/idea-08-permissionless-perp-factory.md` — Permissionless Perp Factory + EOTS oracle bond
- `02-defi/idea-01-multiverse-lending.md` — Multiverse Lending (conditional-token margin algebra)
- `06-market-governance/idea-01-self-resolving-prediction-market.md` — Self-Resolving PM *(as resolution cameo for subjective verses only — not the headline)*

**What's actually new (vs. each part alone):**
- **Single-tx capital-markets bootstrap.** User types a free-text event prompt → system creates the conditional token pair, lists its perp, opens its lending pool, wires it to a self-resolving oracle — one transaction.
- **Self-policing across all three legs.** EOTS bond on the perp's oracle, verse-scoped liquidation on the lending pool, BTS-α resolution on subjective verses. No external oracle, no governance vote, no whitelist anywhere.
- **The conditional-token-as-perp-underlying.** Existing perps trade real assets; existing prediction markets trade outcome shares. OMNIVERSE lets you **trade a perp whose underlying is a conditional token**, borrow USDC against it scoped to the matching verse. Nobody has shipped this.

**2026 market thesis:**
- **Who buys:** (1) Prediction-market degens who want leverage on conditional positions, (2) builders bootstrapping new tokenized assets on Robinhood Chain who need an instant credit + derivative market, (3) crypto-native hedge fund desks who want macro-event tail exposure with capital efficiency.
- **Who pays:** $1K listing-bond skim per launch, 2bp perp trading fees, 10% take on lending interest spread, 30bp on BTS-resolved settlements.
- **Why mid-2026 (not 2025, not 2027):** Paradigm's Multiverse Finance paper (May 2025) gave us the verse-scoped liquidation math. Hyperliquid HIP-3 (Dec 2025) normalized permissionless-perp design. Polymarket V2 (Apr 28, 2026) gives real conditional-token liquidity. Robinhood Chain testnet (Feb 10, 2026) needs a primitive that turns tokenized stocks into a market-creation platform. None of these were jointly production-ready before mid-2026.

**Judge appeal + best sponsor track:**
- **Primary: $70K Overall.** Category-defining novel primitive. The 60-second create-a-market-from-nothing demo IS the killer moment. Direct lineage to Orbital Pool (Dave White = Multiverse author = Orbital author — credibility transfers automatically).
- **Reserved seat: $30K Robinhood Chain.** Robinhood owns Kalshi (acquired 2025); event-asset distribution is dead center of their roadmap.
- **Stylus showcase:** EOTS secp256k1 verifier + push-down/pull-up verse algebra are Rust-heavy math (~10-30× gas savings).
- Best Agentic ($15K) is **not** a strong fit — skip.

**3-week build (concrete weekly milestones):**
- **Week 1 — Verse algebra + perp factory.** Fork Polymarket Gnosis Conditional Tokens. Stylus push-down/pull-up verse algebra. HIP-3-style permissionless perp factory + EOTS secp256k1 verifier in Stylus.
- **Week 2 — Lending pool + BTS resolution + orchestrator.** Verse-scoped lending pool (LTV per leaf of event tree). BTS+α-halt LMSR for subjective verses. One-tx "list+lend+resolve" orchestrator + minimal CLOB.
- **Week 3 — Live trial + demo.** Deploy 3 demo markets on Robinhood Chain testnet (real asset, conditional asset, subjective asset). Recruit 30-50 testers via Polymarket Discord. On-stage demo: deliberately sign two conflicting EOTS posts, prove key extraction, drain the bond live.

**The one risk that could kill this:**
**Regulatory exposure on permissionless derivative listing.** CFTC/SEC scrutiny on permissionless event-perps is the biggest commercial threat. Mitigation: KYC-gated frontend at launch; the factory primitive itself is base-layer infra (analogous to Uniswap V2 not being a securities exchange). Pre-record the live equivocation script as fallback if it flakes on stage.

**Lens verdicts:**
- **judge-wow (9.5/10 — class leader):** *"This is the fusion that genuinely hits the Orbital baseline. The pitch is generalist-graspable. The on-stage demo is the best in the entire portfolio — three independent primitives glued into a single 60-second user action, with a self-policing slashing punchline."*
- **market-2026 (6/10 — REJECT):** *"Thin Day-30 revenue, regulatory risk, builder-only TAM. The 'science project with no buyer.'"*
- **staleness-detector (mixed):** Multiverse Lending 8/10 (Paradigm May 2025 is the "why now"). Self-Resolving PM 3/10 — *use as cameo only, not headline.* Permissionless Perp inherits HIP-3 Dec 2025 freshness.

**How the conflict resolves:** market-2026 is correct that revenue is thin and regulation is real — but for a 10-minute hackathon judging window, wow dominates revenue projection. Address regulation in pitch deck (slide 9: compliance roadmap, Spearbit + legal opinion by day 60) and let the wow do the rest.

---

# OPTION B — SIGMA

> **Hyperliquid's cross-margin, for spot Apple and Tesla. Plus the trade Citadel runs against you.**

**Pitch (14 words):** *"Bring Hyperliquid's cross-margin to spot Apple and Tesla. Plus their hedge fund's favorite trade."*

**Generalist-only version (10 words):** *"Same basket. 25% more borrowing. Plus a built-in hedge."*

**Pitch reframe note:** The original "Covariance OS" pitch failed judge-wow's generalist test because the word "covariance" is a deal-breaker. This pitch **never says "covariance" or "Cholesky" or "Mahalanobis" in the headline.** Math judges still get the math (heat-map demo, Stylus benchmark). Generalist judges hear *"Hyperliquid for spot stocks"* — vocabulary everyone in 2026 already understands.

**Source ideas fused:**
- `02-defi/idea-04-ndim-portfolio-lending.md` — N-Dimensional Portfolio-Margin Lending (Mahalanobis LTV)
- `02-defi/idea-03-dispersion-pool.md` — Dispersion Pool (Cholesky-weighted variance basket)

*(Multiverse Lending was considered as a "conditional collateral" Option-B variant; decision: better as a Year-2 collateral-type addition, not a Week-3 deliverable. Drop.)*

**What's actually new (vs. each part alone):**
- **One covariance engine, two products.** The 20×20 Σ-matrix that prices borrow LTV is the *same* matrix that prices the dispersion vault's vega weighting. Same Stylus contract, two revenue streams. Aave can't add this without architectural replacement.
- **First on-chain CBOE DSPX equivalent for tokenized equities.** CBOE's Dispersion Index is TradFi-only; SIGMA is the **first permissionless retail-accessible version**, settled in USDC against Robinhood Chain tokenized stocks.
- **Honest cross-margin for spot.** Hyperliquid shipped portfolio margin for perps in Dec 2025; SIGMA is the **first clean implementation for spot lending** on Arbitrum. Live demo diff against Aave: same basket, 25% more borrowing power.

**2026 market thesis:**
- **Who buys:** (1) DeFi power traders capped by Aave's isolation limits (the public "I've been trying to lever a hedged basket and Aave won't let me" Twitter thread is real), (2) crypto-native quant desks (Wintermute, GSR, Cumberland) who want a dispersion-trading venue but won't touch the Volmex stack, (3) DAO treasurers hedging tokenized-equity positions on Robinhood Chain.
- **Who pays:** 10% take rate on borrow interest spread + 2/20 on the dispersion vault.
- **Day-30 realistic revenue:** $50K/month if 5-10 quant deposits land (market-2026's number).
- **Why mid-2026 (not 2025, not 2027):** Hyperliquid portfolio margin (Dec 2025) made the design mainstream-trader-accepted with zero spot-lending implementation. Robinhood Chain tokenized equity launch (Feb 2026) enables on-chain dispersion on AAPL/MSFT/GOOG/AMZN/NVDA — pre-2026 there were no real tokenized US equities with chain-native liquidity. Stylus maturity in 2026 makes 20×20 Cholesky at every health check cheap.

**Judge appeal + best sponsor track:**
- **Primary: Stylus showcase.** Single best Stylus case study in the entire fusion set. Concrete falsifiable pitch: "180k gas for a 5×5 Cholesky, 320k gas for a 20×20."
- **$30K Robinhood Chain (reserved seat).** Tokenized-equity dispersion + spot cross-margin are the canonical first strategies on a tokenized-stock chain.
- **$70K Overall.** Clean mathematical primitive with Paradigm-lineage research narrative.
- Best Agentic ($15K) — not a fit. Skip.

**3-week build (concrete weekly milestones):**
- **Week 1 — Math core.** Stylus Cholesky + Ledoit-Wolf shrinkage + Mahalanobis routine. Chainlink covariance pipeline (rolling 30-day Σ on 20 assets: BTC/ETH/SOL + tokenized AAPL/MSFT/GOOG/AMZN/NVDA + gold + …). Portfolio-margin lending pool with Σ-driven healthcheck.
- **Week 2 — Dispersion vault + UI.** Carr-Madan log-payoff replication + Cholesky-vega-weighted basket construction. Daily rebalance keeper. Live heat-map UI of 20×20 correlation matrix + side-by-side Aave-vs-SIGMA borrowing widget.
- **Week 3 — Trial + ship.** Recruit 20 quant testers. Benchmark: ≥20% more borrowing capacity vs. Aave on median tester basket; dispersion vault Sharpe ≥1 over 14-day backtest. Live demo: judge picks a basket on stage, two tabs show Aave's quote vs. SIGMA's quote, then "add a short ETH perp as collateral" → Aave's borrow drops, SIGMA's rises (the basket got market-neutral, the matrix knows it).

**The one risk that could kill this:**
**Robinhood Chain tokenized-equity option liquidity is too thin to make the dispersion leg work.** The lending leg ships regardless; the dispersion leg needs deep option books per constituent. Mitigation: v1 dispersion runs on a crypto basket fallback (BTC/ETH/SOL/AVAX vs. total-cap index). Acknowledge in pitch: *"v1 dispersion on crypto; tokenized-equity dispersion is v2 conditional on RH-Chain option-AMM depth."*

**Lens verdicts:**
- **market-2026 (8/10 — class leader):** *"Clear buyer with real capital, two compounding revenue streams, genuinely hard to copy. Day 30: $50K/month if 5-10 quant deposits land."*
- **judge-wow (6.5/10 original → ~8.0/10 with reframe):** *"Beautiful primitive, fails the generalist test."* — fixed by the reframe above.
- **staleness-detector (mixed):** Dispersion math is 2010; the 2026 hook is Robinhood Chain tokenized-equity dependency + Hyperliquid-portfolio-margin-as-spot framing.

**How the conflict resolves:** the pitch reframe is the resolution — hide "covariance," lead with "Hyperliquid for spot stocks + the hedge fund trade." Same product, half the generalist friction.

---

# OPTION C — INVISIBLE HAND

> **An AI agent whose model is sealed and whose wallet has no key — until it proves it did the job.**

**Pitch (15 words):** *"An AI agent whose wallet doesn't exist until it does its job — and whose model doesn't either."*

**Tighter (12 words):** *"The AI agent has no wallet and no model — until it earns them."*

**Source ideas fused:**
- `01-ai-agents/idea-01-sealed-model.md` — Sealed Model (KZG witness-encrypted AI weights, decrypted only by a Lagrange DeepProve zkML capability proof)
- `01-ai-agents/idea-04-witness-encrypted-agent-wallet.md` — Witness-Encrypted Agent Wallet (T+1-eWEB signature-based WE, keyed to a drand-attested task-completion oracle)

*(These were drawn from the broader 100-idea catalog rather than the original 8. Reasoning: the natural AI-agent triplet in the 8 — SwarmVault / ClaimGPT / LiquiBid — has individual kill conditions (THESIS-avoid / GuardChain collision / B2B drag). The staleness lens explicitly proposed this fusion as **the most 2026-native fusion available**. Both files verified in `ideas/01-ai-agents/`.)*

**What's actually new (vs. each part alone):**
- **One KZG-WE primitive, two unrelated agent properties.** The same Rust Stylus port of IACR 2024/264 underpins (a) the model's existence and (b) the wallet's signing key. The agent has *no key, no weights, no wallet* until and unless it proves the capability and delivers the task. This is the **first end-to-end zero-trusted-coordinator agent commerce protocol** anyone has shipped.
- **Outcome-bonded agent economy primitive.** Today's "agent wallet" is hot key in a TEE + policy guardrails + hope. INVISIBLE HAND replaces trust with cryptography: no completion → no key → no theft. ERC-8004 reputation rides on top.
- **The demo is genuinely impossible-looking.** Judge clicks "verify and decrypt" → zkML proof posts → model weights download AND agent wallet drains AND ERC-8004 reputation updates, all from the *same* witness-extracted secret.

**2026 market thesis:**
- **Who buys:** (1) Regulated AI procurement (defense, big-pharma R&D, fintech credit-model buyers) who today rely on SOC-2 reports because they have no way to verify *"is this the model you said it was?"* — sealed-model is the cryptographic alternative; (2) every builder of an autonomous AI agent paid for work (freelance contractors, DAO bounty workers, agent-to-agent commerce) who today accepts the hot-key-in-TEE risk; (3) protocol designers who want outcome-bonded payment rails without a trusted coordinator.
- **Who pays:** 0.5% take on sealed-model marketplace transactions + 25bp on every witness-encrypted withdrawal.
- **TAM (per source ideas):** regulated AI model market ~$25-35B by 2026; agent-managed AUM forecast $50B by 2027 (Citi GPS).
- **Why mid-2026 (not 2025, not 2027) — strongest of the three on this axis:** Lagrange DeepProve-1 (late 2025) made CNN-class capability proofs cheap. T+1-eWEB (IACR 2025/1064, Glaeser/Madathil 2025) made signature-based WE buildable. BLS12-381 Stylus precompiles matured at scale in 2025. ERC-8004 mainnet (Jan 2026). drand mature beacon. **None of these primitives were simultaneously production-ready before mid-2026** (staleness verdict: *"the most 2026-native idea in the vault"*).

**Judge appeal + best sponsor track:**
- **Primary: $15K Best Agentic.** Canonical Best Agentic build — ERC-8004 + ERC-4337 + WE cryptography is *exactly* what Best Agentic was carved out to reward.
- **$70K Overall.** First deployed witness-encryption + zkML composition on Arbitrum. Falsifiable benchmark: *"verifier gas < 5M, proof time < 60s on Gemma3-class model."*
- **Stylus showcase.** KZG verifier + BLS12-381 pairing ops are textbook Stylus territory.
- **$30K Robinhood Chain** — weak fit. Skip.
- **Asymmetric prize math:** the ONLY option of the three where **both reserved seats (Best Agentic + Overall) are realistically in play**. Single build, ~$85K max exposure.

**3-week build (concrete weekly milestones):**
- **Week 1 — WE Stylus library + sealed-model PoC.** Rust port of KZG witness encryption (IACR 2024/264) — high-risk infra, start Day 1. Lagrange DeepProve verifier in Stylus. Encrypt small CNN (CIFAR-10, ~100K params) under predicate "accuracy ≥ 0.85" on a public test set. End-to-end test: zkML proof → verifier releases witness → cleartext weights download.
- **Week 2 — WE Agent Wallet + drand.** Signature-based WE library (port from Glaeser/Madathil IACR 2025/1064) sharing KZG primitives with the model side. ERC-4337 smart wallet with drand-watcher Stylus contract; single-task predicate (zkTLS-attested HTTPS-200 to a target URL). ERC-8004 reputation hookup.
- **Week 3 — Unified demo + trial + ship.** 5-10 user trial: developer buys a sealed model, runs it, gets paid through the WE wallet. On-stage demo: judge buys a sealed model live, agent uses it to complete a task, agent's wallet drains paying both the model seller and the agent operator — all driven by one zkML proof + one drand signature.

**The one risk that could kill this:**
**WE library maturity.** KZG witness-encryption and signature-based WE constructions are research-grade with no production Rust ports. We are shipping the ports. If the Stylus implementation slips past Day 10, the unified demo collapses. **Mitigation:** Day-1 spike to evaluate library risk; fallback to a Phala-TEE-based "trusted enclave decryption" stand-in for the model side (clearly labeled as a v1 trust-assumption), keeping the wallet side cryptographic. This is the most technically aggressive option and the most likely to fail in a way invisible to judges.

**Lens verdicts:**
- **staleness-detector (9 + 8 — class leader):** *"The most 2026-native idea in the vault. Cannot be confused with any prior Bengaluru winner. This would be the first end-to-end cryptographic agent commerce protocol — no trusted coordinator at any step. Uniquely 2026-native."*
- **market-2026 (not directly scored — outside the 8; estimated 6–7/10):** Regulated AI procurement TAM is real but B2B-slow; agent-managed AUM forecast is real but speculative; revenue clean but Day-30 numbers depend on hand-building one model marketplace partner.
- **judge-wow (not directly scored; estimated 8.5–9.0):** *"An AI agent whose wallet doesn't exist until it does its job"* clears the Orbital bar — 12-word self-contained paradox. Demo is theatrical (judge watches a wallet appear from nothing) but costs 5-10 seconds of bandwidth to explain KZG WE.

**How the conflict resolves:** the lenses don't directly disagree — they weren't all asked about C. The honest read: 2026 hard-tech moat is strongest of the three, wow factor is high but not class-leading, commercial story is real but slowest to monetize. It is **the only option that can simultaneously win Best Agentic AND Overall reserved seats** — a property neither A nor B has.

---

# Kill list — original 8 ideas dropped entirely

| Idea | Why it fails the 2026 + market + wow filter |
|---|---|
| `03-defi-ai/idea-08-ai-swarm-vault.md` (SwarmVault) | **THESIS.md explicit avoid.** *"AI portfolio managers / yield farmer / trader → Saturated. ~20 teams per hackathon. Skip."* Cannot escape the Yearn-clone framing. |
| `03-defi-ai/idea-02-auto-adjudicated-insurance.md` (ClaimGPT) | **Prior winner collision.** Direct overlap with GuardChain AI; the staleness lens scores 4/10 and warns this is *"the most dangerous staleness risk of any tier-A idea."* High wow (9.0) does not save it — judges fire the *"isn't this GuardChain with TDX?"* objection in 30 seconds. |
| `03-defi-ai/idea-15-ai-liquidation-auctions.md` (LiquiBid) | **B2B distribution dependency.** Day-30 revenue is $0 without a signed Aave/Morpho partnership pre-arranged. Demo has to be simulated. Recommend revisiting as a standalone follow-on post-hackathon. |
| `06-market-governance/idea-01-self-resolving-prediction-market.md` (Self-Resolving PM) — **partial drop** | **BTS is 2023-era design**, scored 3/10 on staleness. Kept inside OMNIVERSE only as resolution cameo for subjective verses. As standalone hackathon submission: drop. |

**Net of the original 8:**
- 4 absorbed into options (Multiverse, Permissionless Perp → OMNIVERSE; N-Dim, Dispersion → SIGMA)
- 1 demoted to cameo (Self-Resolving PM → OMNIVERSE supporting role)
- 3 killed (SwarmVault, ClaimGPT, LiquiBid)

INVISIBLE HAND substitutes 2 ideas from the broader catalog (Sealed Model, WE Agent Wallet) for the AI-agent slot per the team-lead's "use if genuinely stronger" allowance.

---

# Honest recommendation if forced to one

**OMNIVERSE** — for three reasons:
1. judge-wow (the lens with most decision-weight in a 10-minute eval) calls it the clearest Orbital-bar fusion of the entire set, and the only pitch a non-crypto journalist would screenshot.
2. The on-stage demo is the best in the portfolio (type a free-text event → mint conditional pair → list perp → open lending → resolve via BTS → equivocate oracle and watch the bond drain).
3. Double-reserved-seat eligibility (Overall + Robinhood Chain) + Paradigm-research lineage (Dave White credibility) is the best prize math + free credibility combo available.

The market-2026 objection is *correct but resolvable in the pitch deck*.

**If you're risk-averse on regulation, build SIGMA.** Cleaner commercial story, no permissionless-derivative landmine. Give up class-leading wow + one reserved seat.

**If your team has unusually deep WE-crypto specialization, build INVISIBLE HAND.** Strongest 2026-native moat. Most asymmetric prize math. Only proceed if Day-1 spike confirms KZG-WE Stylus port feasibility.

---

# What's in this folder

- **`FUSED.md`** (this file) — final menu
- **`README.md`** — folder index
- **`fusion-worklog.md`** — fusion-architect's working draft (longer, all open questions surfaced)
- **`market-notes.md`** — market-2026 lens analysis of all 8 ideas + seeds
- **`pitch-notes.md`** — judge-wow lens analysis (Orbital filter + demo theatre)
- **`staleness-notes.md`** — staleness-detector lens analysis (what's stale, what's 2026-native, prior-winner collisions)

---

# Next step

Tell me which option you want and I'll write a Thesis-grade build plan for it: 3-week schedule with daily milestones, architecture diagram, demo script, sponsor framing, risk register, pre-submission outreach plan — same depth as the current `THESIS.md`.

If none of the three feels right, tell me which lens is closest to your gut and I'll respin from there.
