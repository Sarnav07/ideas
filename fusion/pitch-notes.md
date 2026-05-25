# Pitch Notes — Judge-Wow / Orbital Filter Lens

**Lens:** Orbital baseline = *"Uniswap is 1D liquidity. Curve is 2D. Orbital is N-D liquidity across N stablecoins."* One sentence. Generalist parses it in 4 seconds. Triggers "wait, how is that possible?"

**Rejection rule:** any pitch needing >2 sentences to land is auto-failed. Smart-but-flat ≠ wow. "Wait, how?" or zero.

**Scoring rubric (1–10):**
- 1–3: smart-but-flat. Specialist nod, generalist blank stare.
- 4–6: clean inversion or generalization, but needs prior context (DeFi-native only).
- 7–8: paradox a non-trader feels. They can almost grasp it. Sponsor lean-in.
- 9–10: Orbital-grade. Generalist gasps. Twitter screenshots itself.

**Tracks:** Overall $70K · Robinhood Chain $30K (reserved seat) · Best Agentic $15K · Stylus (math/perf showcase)

---

## PART A — The 8 shortlisted ideas

---

### #1 Self-Resolving Prediction Market (`06-market-governance/idea-01`)

**Current pitch (their own):** *"Polymarket settles itself. No oracle. Just math."*

**Strongest ≤15-word rewrite:**
> **"A prediction market that resolves itself. No oracle. No human. The math is honest."** (14 words)

Tighter version (10 words, more violent):
> **"Polymarket without an oracle. The market grades itself."**

**Generalist test:** PASSES. Even my dad knows Polymarket needs Trump-or-Kamala to actually happen. "Settles itself" reads as an impossible loop. The "wait, how?" beat fires hard.

**30-second on-stage demo moment:**
> "We open a live market on stage: *'Is this judge wearing a black shirt?'* Five audience members report a probability into the dApp. The market halts on an α-flip mid-demo. Payouts settle in 8 seconds. No oracle was called. The contract address scrolls on screen. We then open a second market: *'Will Sam Altman still run OpenAI on Dec 31, 2026?'* — same mechanism, no resolution date needed. **The audible reaction:** judges lean forward when they realize the second market never needs an oracle either. Ever."

**Wow score: 8.5 / 10.** The pitch is short, the mechanism is genuinely paradoxical (BTS + α-stopping), and the live demo has a "no oracle was called" punchline that hits. Loses half a point because "Bayesian Truth Serum" is the actual mechanism and that phrase will appear somewhere — it shouldn't, but it will.

**Best sponsor track: Overall $70K** (primary — Paradigm-style info-finance is dead center of Overall). Secondary: **Robinhood Chain** (Robinhood owns Kalshi now; subjective markets are their next frontier).

---

### #2 Multiverse Lending (`02-defi/idea-01`)

**Current pitch:** *"Borrow against assets that only exist if Trump wins."*

**Strongest ≤15-word rewrite:** their own is already perfect.
> **"Borrow against assets that only exist if Trump wins."** (9 words)

**Generalist test:** PASSES VIOLENTLY. This is the rare pitch where a non-crypto reporter would screenshot it. "Assets that only exist if Trump wins" — every word is concrete; every word is wrong in a fascinating way; every word is right.

**30-second on-stage demo moment:**
> "I deposit a Polymarket *'Trump wins 2028'* YES token as collateral. The lending pool quotes me a USDC line — but only `notTrumpUSD`, an asset that **also only exists if Trump wins**. Both legs collapse together. I borrow against the future. On screen: a tree diagram with two leaves, USDC pooled in one, dust in the other. I then run the *'Trump wins'* resolution branch on testnet. The borrow collapses to real USDC. Then I rewind and run the *'Trump loses'* branch. The borrow simply ceases — no liquidation, no haircut, no margin call. **The reaction:** the judge from a TradFi background literally says *'wait, how does that not blow up?'* That's the whole demo."

**Wow score: 9.5 / 10.** The closest thing in the pool to the Orbital baseline. Dave White (same author as Orbital paper) gives free credibility. The mechanism — liquidations only fire inside the matching branch — is itself a "wait, how?" beat. Loses half a point only because "Trump" dates the pitch; pick a different event for the on-stage demo (Fed cut, FDA approval).

**Best sponsor track: Overall $70K** (primary — this is THE category-defining novel-primitive pitch in the pool). Secondary: **Robinhood Chain** (Kalshi distribution → conditional-margin credit layer is the natural extension).

---

### #3 Dispersion Pool (`02-defi/idea-03`)

**Current pitch:** *"One pool. Long the parts, short the whole. Profit if stocks decorrelate."*

**Strongest ≤15-word rewrite:**
> **"Bet on whether stocks move together. One vault. The Citadel trade, onchain."** (12 words)

**Generalist test:** PASSES, narrowly. "Bet on whether stocks move together" is genuinely generalist-graspable — a 14-year-old can picture S&P-all-up vs S&P-scattered. The "Citadel trade" frame triggers the right mix of envy and curiosity. The original pitch ("long the parts, short the whole") is sharp for DeFi natives but flat for generalists.

**30-second on-stage demo moment:**
> "Behind me: a live chart of the S&P. Five names — AAPL, MSFT, GOOG, AMZN, NVDA — plus the S&P-mini index, all tokenized on Robinhood Chain. I deposit $1,000. The vault auto-builds the Cholesky-weighted dispersion basket — long each constituent's variance, short the index's variance. The chart toggles between two synthetic days: **Monday** — all five stocks rally 2% together. P&L: flat. **Tuesday** — half rally 2%, half drop 2%. Index moves zero, individual variance pops. P&L: +$47. **The reaction:** the Robinhood judge nods slowly — this is the trade their HFT counterparties run daily that retail has zero access to. The Stylus chip on the side shows the 5×5 Cholesky ran in 180k gas."

**Wow score: 7.5 / 10.** Strong Orbital-shape inversion (variance is 1D, dispersion is 2D-correlation). "Profit if stocks decorrelate" is sharp but slightly inside-baseball. Hammered by the demo because retail-vs-Citadel-access is a sympathetic frame.

**Best sponsor track: Robinhood Chain $30K** (primary — tokenized equity dispersion is the canonical first-strategy on a tokenized-stock chain). Secondary: **Stylus** (50×50 Cholesky justifies Rust). Tertiary: **Overall $70K**.

---

### #4 N-Dimensional Portfolio-Margin Lending (`02-defi/idea-04`)

**Current pitch:** *"Aave isolates each asset. We margin your portfolio by its covariance matrix."*

**Strongest ≤15-word rewrite:**
> **"Aave gives leverage per asset. We give leverage on your whole portfolio's covariance."** (13 words)

Even tighter, more Orbital-shaped (11 words):
> **"Aave is 1D. Hyperliquid perps are N-D. We're N-D for spot."**

**Generalist test:** PARTIAL. "Aave is 1D" assumes the listener knows Aave silos collateral. For a DeFi-literate judge: 9/10. For a generalist Robinhood PM: 5/10. The covariance-matrix mention will lose half the room.

**30-second on-stage demo moment:**
> "I deposit $10K BTC + $10K ETH + $10K SOL — three correlated risk assets — on Aave-mainnet (live on screen). Aave's UI quotes my borrowing power: **$21K** (isolated LTV, ~70% each). I run the exact same deposit on our protocol. Borrowing power: **$25K** — because BTC/ETH/SOL covariance says these three are 70% redundant. I then **add a $10K short-ETH perp position** as collateral. Aave: borrowing power *drops* (it doesn't understand the hedge). Ours: borrowing power *rises* to $33K — the basket is now nearly market-neutral and the covariance matrix knows it. **The reaction:** the pro-trader judge realizes they could move their entire portfolio onchain at TradFi-grade margin. The Stylus chip shows 20×20 Cholesky in 320k gas."

**Wow score: 7 / 10.** Mechanism is elegant; the live diff against Aave is a hard demo moment. Loses points because the pitch needs "covariance" — a 4-syllable word that no Robinhood retail PM would print on a billboard. Wow factor is real but trader-coded.

**Best sponsor track: Stylus** (primary — Cholesky on a 20×20 matrix on every health check is the canonical Stylus case study, 30× cheaper than Solidity). Secondary: **Overall $70K** (clean mathematical primitive). Tertiary: **Robinhood Chain** (RH retail wants honest leverage).

---

### #5 Permissionless Perp Factory + EOTS Oracle Bond (`02-defi/idea-08`)

**Current pitch:** *"Anyone can launch a perp market. List a bad oracle and the market burns your bond."*

**Strongest ≤15-word rewrite:**
> **"Uniswap-V2 for perps. If you list a bad oracle, the market drains your bond."** (14 words)

Tighter (10 words):
> **"Anyone can launch a perp. Bad oracles auto-slash themselves."**

**Generalist test:** PASSES if "Uniswap-V2 for perps" is in their vocabulary; otherwise needs one swap. *"Anyone can launch a futures market on anything. The contract polices itself."* (13 words) is the generalist version.

**30-second on-stage demo moment:**
> "On stage I deploy three perp markets in three minutes — `AAPL/USDC`, `TSWIFT-CONCERT-ATTENDANCE/USDC`, and an adversarial `RIGGED-ORACLE/USDC` — each takes one signed transaction and a 100K USDC bond. Trading opens. I let the audience trade `AAPL/USDC` on a real Pyth feed. Then I **flip the rigged oracle**: I sign two EOTS price posts for the same slot with conflicting prices — equivocation. A bystander script extracts the private key from the two signatures (this is what EOTS does), drains the 100K bond, and routes 80% to traders harmed by the bad price. On screen: bond goes red, trader balances go green. **The reaction:** the judge from Hyperliquid leans forward — HIP-3 has a whitelist; we have math."

**Wow score: 8 / 10.** Two-beat pitch (Uniswap inversion + EOTS slashing) is sharp; the on-stage equivocation demo is genuinely theatrical because the slashing is **automatic and cryptographic** — no governance vote, no waiting. Loses points because "EOTS" is jargon and the explanation of *how* the key extracts itself is a 30-second sidebar that the pitch shouldn't need.

**Best sponsor track: Stylus** (primary — secp256k1 EOTS verifier is canonical Stylus territory). Secondary: **Overall $70K** (fresh narrative — HIP-3 + EOTS is genuinely unbuilt). Tertiary: **Robinhood Chain** (permissionless tokenized-equity perps is their natural extension).

---

### #6 ClaimGPT — Auto-Adjudicated Insurance (`03-defi-ai/idea-02`)

**Current pitch:** *"File a claim. An AI judge reads it. Money hits your wallet in 30 seconds."*

**Strongest ≤15-word rewrite:** the original is already strong. Sharper:
> **"File an insurance claim. AI judge reads it. You're paid in 30 seconds."** (13 words)

**Generalist test:** PASSES HARD. Everyone has waited 90 days for a claim. "30 seconds" is the violent contrast.

**30-second on-stage demo moment:**
> "Live demo: a judge in the audience submits a real expired-flight screenshot to the Aegis-Claim dApp ('my flight was 4hrs late, $200 policy'). The screenshot uploads. **A model running in an Intel TDX enclave** (a green TDX-attestation hash flashes on screen) reads the screenshot, cross-references Chainlink's flight oracle, signs an `{approve, $200}` decision. The Stylus verifier checks the attestation. $200 USDC hits the judge's wallet. **Stopwatch on screen: 23 seconds.** Then the kicker: I file a fraudulent claim ('my flight was 4hrs late' for a flight that wasn't). Same model. Denied in 4 seconds with cryptographic reasoning hash. **The reaction:** the regulatory-leaning judge — who came in skeptical of LLM adjudication — sees that *every decision is signed by attested hardware* and the denial is auditable."

**Wow score: 9 / 10.** Pitch is one sentence. Demo is theatre. The TDX attestation flash is the "wait, how is this trustworthy?" payoff. Sponsor convergence is unusually clean (Marlin TEE + agentic + DeFi). The only thing keeping it from 9.5 is that "AI insurance" is a phrase that exists in TradFi (Lemonade); the inversion is the *cryptographic* attestation, which the pitch should hint at.

**Best sponsor track: Best Agentic $15K** (primary — TDX-attested LLM signing onchain payouts is the canonical agentic-economy demo). Secondary: **Overall $70K**. Tertiary: **Robinhood Chain** (parametric travel/income protection is a retail-Robinhood-adjacent product).

---

### #7 SwarmVault — N Attested AI Agents Vote, Slashed if Wrong (`03-defi-ai/idea-08`)

**Current pitch:** *"A vault run by 7 AIs. They vote on every trade. The minority gets slashed."*

**Strongest ≤15-word rewrite:** original is sharp. Sharper still:
> **"Seven AIs run a vault. They vote on every trade. Losers lose their stake."** (14 words)

**Generalist test:** PASSES. "7 AIs vote, losers lose money" is grade-school graspable. Triggers "wait, why would an AI bet its own money?" which is exactly the right "wait, how?".

**30-second on-stage demo moment:**
> "On screen: seven AI agents (different base models — Llama, Mistral, Qwen, Claude, GPT, plus two classical RL bots), each in their own TDX enclave, each having staked 10 ETH. A live BTC/ETH rebalance signal triggers. All seven post their votes simultaneously, each with a TDX attestation hash. **The screen shows a real-time leaderboard** — five vote LONG, two vote SHORT. The vault executes LONG. Six hours fast-forward: BTC rips 4%. The two SHORT-voting agents lose 0.5 ETH of stake each, redistributed to the five winners. The reputation chart updates. **The reaction:** the judge realizes this is not 'AI trading' — this is **a market for AI alpha**, where the AIs themselves are the assets being priced. SwarmVault is to AI trading what Polymarket is to forecasting."

**Wow score: 8 / 10.** The pitch lands. The demo theatre (seven leaderboard rows, real attestation hashes, live slashing) is high. The framing — "market for AI alpha, AIs are the assets" — is the meta-beat that pushes it above #6. Loses points because there are now several "AI vault" projects out there; the *slashing-with-attestation* angle is what makes this one different, and the pitch doesn't quite convey that in ≤15 words.

**Best sponsor track: Best Agentic $15K** (primary — ERC-8004 + EigenLayer + TEE convergence is dead center of Best Agentic). Secondary: **Overall $70K**. Tertiary: **Robinhood Chain** (long-only tokenized-equity SwarmVault is a natural retail product).

---

### #8 LiquiBid — Sealed-Bid AI Liquidator Auctions (`03-defi-ai/idea-15`)

**Current pitch:** *"Liquidators are AI agents. They bid in sealed envelopes. The lowest-loss bid wins."*

**Strongest ≤15-word rewrite:**
> **"Today liquidators race to take the most from you. We make them race to leave the most."** (16 words — over.) →

Tightened (13 words):
> **"Liquidation MEV inverted. AI bots compete to leave more for the borrower."**

Even tighter (10 words):
> **"AI bots compete for *who liquidates you most gently*."**

**Generalist test:** PASSES for crypto-natives (everyone has been liquidated and seen MEV bots take 20% haircuts). For pure generalists: needs "borrower" → "the person being foreclosed on". The 10-word version is the magic one.

**30-second on-stage demo moment:**
> "Behind me: a borrower's underwater Aave position. Naive liquidation (running on Aave mainnet, live data): liquidator takes a 15% bonus, borrower walks away with $850 on a $1000 starting position. **Same position, routed through LiquiBid.** Four AI bots (in TDX enclaves) submit tlock-encrypted bids to next-block drand. The bids decrypt. Three bots want a 10% bonus. One bot — the smartest router, knowing it has Curve+Uni+1inch slack — bids only 4%. Lowest-loss bid wins. The borrower walks away with **$960**, not $850. **The reaction:** the lending-protocol judge realizes this is a 5-bps fee replacement for the *entire MEV liquidation industry*. The DeFi-Twitter judge realizes this is the first time a sealed-bid auction has been used to *protect a borrower from the searcher cartel*."

**Wow score: 8.5 / 10.** The inversion — "MEV that returns money to the user it took it from" — is the kind of paradox that sponsors retweet. tlock + drand + ERC-8004 sponsor convergence is dense. Loses half a point because the pitch demands the word "liquidation" which 60% of generalist audience doesn't carry; the *inversion* lands easier than the *primitive*.

**Best sponsor track: Best Agentic $15K** (primary — sealed-bid agent auctions are an ERC-8004 textbook product). Secondary: **Overall $70K**. Tertiary: **Robinhood Chain** (when RH-Chain tokenized-equity lending exists, this is its liquidator layer).

---

## PART B — The 4 seed fusions

Each seed combines 2–4 of the shortlisted ideas. For each, I score the fusion's pitch *as a fusion*, not as the strongest constituent — the bar is whether the fused pitch hits harder than the best component alone.

---

### Seed F1 — VERDICT LAYER

**Implied composition:** #1 Self-Resolving Prediction Market + #2 ClaimGPT (AI Judge Insurance) + #8 LiquiBid (sealed-bid AI liquidator) — a unified "machine adjudication" rail. Markets settle themselves. Claims pay themselves. Auctions decide themselves. All without human or oracle.

**Strongest ≤15-word pitch:**
> **"Every onchain decision — claims, liquidations, prediction markets — settled by code. No humans. No oracles."** (15 words, exactly at limit)

Tighter alternatives:
> **"Insurance, lending, and prediction markets share one verdict engine. No human judges. Ever."** (13 words)
> **"The verdict layer: claims, markets, liquidations all settle themselves."** (9 words)

**Generalist test:** PASSES, narrowly. "No humans. No oracles." is the right two-beat. But "verdict" + three domains in one sentence asks the listener to do too much classification. The 9-word version is the wow version; the 13/15-word versions are the explainer.

**30-second on-stage demo moment:**
> "Three windows open on stage, side by side. **Window A:** a prediction market resolves itself in 8 seconds with BTS-α scoring — no oracle. **Window B:** a flight-delay insurance claim is approved by a TDX-attested LLM in 23 seconds — no human adjuster. **Window C:** a sealed-bid AI auction picks the gentlest liquidator for a distressed borrower — no MEV cartel. **All three windows are running the same `Verdict.sol` interface in the bottom-right corner of each.** The pitch line on screen: 'one verdict engine, three universes.' **The reaction:** the judge realizes this is not three products — it is **the abolition of the trusted-third-party in DeFi**, packaged as a developer kit."

**Wow score: 8 / 10 as fusion.** Higher than any individual component because the *unifying claim* is bigger than the sum. Loses points because the demo is three windows, which is two windows too many — the wow factor halves with each extra context-switch. **Recommend: pick ONE flagship verdict surface (insurance) and put the other two as 5-second cameo demos.**

**Best sponsor track: Overall $70K** (primary — biggest narrative). **Best Agentic $15K** (secondary — TDX-attested agents are the connective tissue). Stylus tertiary (every verdict-engine is a math/verifier contract).

**Honest verdict on the fusion:** This is the most "Aegis-shaped" of the four seeds — a unifying-layer narrative with three demo beats. Strong. But the three demo beats fight each other for attention; trim hard.

---

### Seed F2 — COVARIANCE OS

**Implied composition:** #3 Dispersion Pool + #4 N-Dim Portfolio Lending — a unified covariance-matrix-as-protocol. The same 50×50 Σ-matrix prices your borrow LTV, your dispersion-trade variance, and (stretch) your delta-hedge requirements.

**Strongest ≤15-word pitch:**
> **"DeFi treats each asset alone. We treat your portfolio as a single number: its covariance."** (15 words, at limit)

Tighter and Orbital-shaped:
> **"Aave is 1D. Hyperliquid is partly N-D. Covariance OS is N-D across DeFi."** (13 words — but assumes DeFi vocabulary)

The wow version (10 words):
> **"One covariance matrix prices every borrow, hedge, and trade onchain."**

**Generalist test:** FAILS for pure generalists. "Covariance" is a 4-syllable Markowitz term that the median Robinhood retail user does not carry. The math judges will love it; the marketing judges will glaze.

**30-second on-stage demo moment:**
> "On screen: a 20×20 heat-map of correlations between BTC, ETH, AAPL, NVDA, gold, ... updating in real time from Chainlink. I deposit a mixed basket — half crypto, half tokenized equities. The protocol shows: borrowing power $X (vs Aave's $0.7X), dispersion-trade vault auto-suggests a hedge worth $Y, delta-neutral perp overlay $Z. **All three values come from the same 20×20 matrix.** I then break a correlation — short ETH against the basket — and watch the entire UI update in 200ms: borrowing power rises (basket got more market-neutral), dispersion suggestion shrinks (less correlation alpha). **The reaction:** the pro-trader judge realizes this is a *primitive* — the matrix is the OS, the lending/dispersion/hedging products are just apps on top."

**Wow score: 6.5 / 10 as fusion.** Mechanism is elegant. The "matrix as OS" frame is genuinely a wow for sophisticated audiences. But the pitch demands covariance literacy, and the audience for this hackathon is half-RH-retail-PMs, half-DeFi-natives. **Smart but flat for half the room.** The demo theatre rescues it slightly because the heat-map is visually striking.

**Best sponsor track: Stylus** (primary — Cholesky-on-20x20 is THE canonical Stylus showcase). **Robinhood Chain $30K** (secondary — tokenized-equity dispersion + portfolio margin on RH-Chain tokenized stocks). **Overall $70K** tertiary.

**Honest verdict on the fusion:** Strong fusion for *trader judges*. Weak fusion for *consumer judges*. Wins on technical depth and Stylus story. Loses on generalist gasp.

---

### Seed F3 — ASSET GENESIS STACK

**Implied composition:** #2 Multiverse Lending + #5 Permissionless Perp Factory + (optionally) #1 Self-Resolving Markets — a stack for **creating new assets from nothing** and **trading/lending against them**. Anyone can mint a conditional asset, list a perp on it, and borrow against it. The asset genesis is permissionless end-to-end.

**Strongest ≤15-word pitch:**
> **"Mint a new asset, list its perp, borrow against it — all in one transaction."** (14 words)

Tighter and more impossible-sounding:
> **"Create a new asset on stage in 60 seconds. Then trade, borrow, hedge it."** (13 words)

The wow version (10 words):
> **"Every event in the world is now a tradable asset."**

**Generalist test:** The 10-word version PASSES VIOLENTLY. It's the most science-fiction-sounding pitch in the entire pool. "Every event in the world is now a tradable asset" is the kind of line that makes a non-crypto journalist say *"is that real?"* and then ask for a phone number.

**30-second on-stage demo moment:**
> "**Live on stage, in 60 seconds:** I type a free-text event prompt: *'Will Robinhood Chain hit 100K daily users by July 1, 2026?'* The system: (1) mints a Polymarket-style YES/NO conditional pair via the multiverse contract, (2) deploys a permissionless perp market on the YES-token (EOTS-bonded oracle), (3) opens a lending pool that accepts the YES-token as collateral. **I borrow $500 USDC against my own freshly-minted asset.** The audience can scan a QR code on their phones and trade the brand-new market. **Then I equivocate the oracle on purpose** — the EOTS bond drains, the perp market gracefully closes, the lending pool seizes the collateral cleanly. **The reaction:** the entire room realizes they just watched **the first end-to-end permissionless capital-markets stack** spin up live. Robinhood's own product team takes a photo of the screen."

**Wow score: 9.5 / 10 as fusion.** This is the fusion that genuinely hits the Orbital baseline. The pitch ("every event is a tradable asset") is generalist-graspable. The on-stage demo is **the best demo in the entire portfolio** — three independent primitives glued into a single 60-second user action, with a self-policing slashing punchline at the end. The math credibility transfers from both Dave White (Multiverse author) and Hyperliquid (HIP-3 lineage).

**Best sponsor track: Overall $70K** (primary — clearly the strongest Overall pitch in the fusion set; this is the "category-defining novel primitive" that the Bengaluru winners pattern says wins). **Robinhood Chain $30K** (secondary — Robinhood owns Kalshi, owns event-asset distribution, *and* this is the natural credit layer). **Stylus** (tertiary — EOTS verifier + Cholesky pricing for the lending leg).

**Honest verdict on the fusion:** The strongest fusion in the seed set. Best pitch, best demo theatre, best sponsor alignment (RH + Overall stack). My pick if forced to choose one.

---

### Seed F4 — VERDICT × COVARIANCE

**Implied composition:** F1 (Verdict Layer) × F2 (Covariance OS) — machine adjudication applied to portfolio-level risk. A vault where: (a) trades are decided by attested AI swarm voting (Verdict), (b) margin/risk is priced by live covariance (Covariance), (c) liquidation auctions are sealed-bid AI (Verdict), (d) insurance against blow-up is auto-adjudicated (Verdict). Every decision is machine; every risk number is matrix.

**Strongest ≤15-word pitch:**
> **"A hedge fund where AIs trade, math prices risk, and the protocol adjudicates itself."** (14 words)

Tighter (11 words):
> **"An onchain hedge fund with no humans anywhere in the loop."**

The wow version (9 words, but loses some specificity):
> **"A hedge fund with no humans. Anywhere. Ever."**

**Generalist test:** The 9-word version PASSES — it lands like the Soylent-Green-for-finance pitch. "Hedge fund with no humans" is generalist crack. But it raises a real *trust* concern that the next sentence has to immediately answer ("then who's accountable?"). The 11- and 14-word versions are explainers, not hooks.

**30-second on-stage demo moment:**
> "On screen, a single dashboard: **The Verdict Fund.** A bar at top shows live AUM $1.2M (testnet). Seven AI agents (TDX-attested) vote LONG on a tokenized-equity basket — five say yes, two say no. The vote executes. The risk panel shows the covariance matrix updating: portfolio risk score drops because the new position is partially-hedged by existing holdings. Six hours later, a position goes underwater. **Sealed-bid AI liquidator auction triggers automatically**, four bots compete, the gentlest bid wins, borrower keeps 96% of residual. The two SHORT-voting agents on the original trade get slashed; the five LONG-voters get fee share. A separate insurance pool — adjudicated by a TDX-LLM — auto-pays a $50K claim for an oracle-feed-glitch event in under 30 seconds. **All four mechanisms (vote, margin, liquidation, insurance) are stamped onscreen with the same `Verdict.sol` audit trail.** The reaction: the judge realizes they just watched a fully-autonomous capital allocator run a full P&L cycle."

**Wow score: 7 / 10 as fusion.** The pitch is strong; the demo is genuinely impressive. But this is **the most ambitious fusion** and pays the price — the demo has **four** simultaneous mechanisms, each of which deserves its own 30 seconds. A judge experiencing the demo for the first time will catch *one* of the four beats, not all four. The pitch needs to land in 9 words and the demo needs to pick a single hero moment, not four. **Smart-but-overstuffed.** The Aegis-pattern playbook (lock MVP, one hero moment, everything else stretch) would chop this in half.

If trimmed aggressively (Verdict-only swarm vault, covariance as the risk-display surface, drop insurance, drop liquidation auction): score rises to 8.5. As proposed: 7.

**Best sponsor track: Best Agentic $15K** (primary — the AI-swarm + auto-adjudication is dead center of agentic). **Overall $70K** (secondary — if it can land, it's an Overall winner; if it can't, it's a Best Agentic winner). **Stylus** tertiary (covariance + verifier work).

**Honest verdict on the fusion:** Most ambitious. Most demo-fragile. **Will win the hackathon if trimmed to one hero beat. Will place 3rd if shipped as four beats.**

---

## PART C — Cross-cutting verdicts

### The seven pitches that hit the Orbital bar (≥8.0 wow)

| Rank | Idea / Fusion | Score | Pitch ≤15 words |
|---|---|---|---|
| 1 | **F3 — Asset Genesis Stack** | **9.5** | *"Every event in the world is now a tradable asset."* |
| 2 | #2 — Multiverse Lending | 9.5 | *"Borrow against assets that only exist if Trump wins."* |
| 3 | #6 — ClaimGPT | 9.0 | *"File an insurance claim. AI judge reads it. You're paid in 30 seconds."* |
| 4 | #1 — Self-Resolving Market | 8.5 | *"Polymarket without an oracle. The market grades itself."* |
| 5 | #8 — LiquiBid | 8.5 | *"AI bots compete for who liquidates you most gently."* |
| 6 | F1 — Verdict Layer | 8.0 | *"The verdict layer: claims, markets, liquidations all settle themselves."* |
| 7 | #5 — Perp Factory | 8.0 | *"Uniswap-V2 for perps. Bad oracles drain themselves."* |
| 8 | #7 — SwarmVault | 8.0 | *"Seven AIs run a vault. They vote. Losers lose their stake."* |

### Below the Orbital bar (smart-but-flat for generalists)

| Rank | Idea | Score | Reason |
|---|---|---|---|
| 9 | F4 — Verdict×Covariance | 7.0 | Pitch is fine; demo has 4 hero beats fighting each other |
| 10 | #3 — Dispersion Pool | 7.5 | Sharp for traders, "decorrelate" is a long word for generalists |
| 11 | #4 — N-D Portfolio Lending | 7.0 | "Covariance matrix" is the deal-breaker word |
| 12 | F2 — Covariance OS | 6.5 | Beautiful primitive, fails the generalist test |

### The one pitch I would force everyone to memorize

**Asset Genesis Stack (F3):** *"Every event in the world is now a tradable asset."* — 10 words, generalist-gasp, demo-theatre-ready, double-sponsor-track (Overall + Robinhood Chain), and the only fusion that beats every individual constituent on wow.

### Rejection list (>2 sentence pitch, auto-failed)

None of the 12 candidates require >2 sentences as I've rewritten them. **However**, the F4 Verdict×Covariance fusion fails a related test: it requires >1 hero demo moment. **Reject in its 4-beat form; accept in its 1-beat trimmed form.**

### Sponsor-track allocation summary

| Track | Strongest fits |
|---|---|
| **Overall $70K** | F3 (Asset Genesis), #2 (Multiverse), F1 (Verdict Layer), #1 (Self-Resolving) |
| **Robinhood Chain $30K** | F3 (Asset Genesis), #3 (Dispersion), #2 (Multiverse) |
| **Best Agentic $15K** | F4 (Verdict×Covariance, trimmed), #6 (ClaimGPT), #7 (SwarmVault), #8 (LiquiBid) |
| **Stylus** | F2 (Covariance OS), #4 (N-D Lending), #5 (Perp Factory), F3 (Asset Genesis pricing leg) |

**Pattern:** the *fusions* dominate Overall and Best Agentic. The *individual ideas* dominate Stylus and Robinhood Chain. This argues for a **fusion-led submission** with one individual idea as backup — exactly the Aegis-thesis shape.

### One sentence to the Fusion Architect (task #4)

**Pick F3 — Asset Genesis Stack. Trim F4. The Orbital filter says F3 is the only fusion that beats every component idea on wow factor, and the demo moment writes itself.**
