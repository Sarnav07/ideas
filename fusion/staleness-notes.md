# Staleness Analysis — Arbitrum Open House 2026
**Lens:** "Is this 2025 hype dressed up, or genuinely 2026-native?"

**Baseline assumption for demo day:** ERC-8004 agents in market, x402 payments shipped (Coinbase), TEE-attested LLMs cheap (Marlin/Phala commodity), zkML production-ready (Lagrange DeepProve), shared sequencers (Espresso) live, intent markets (Anoma/UniswapX v2) shipped. Any idea that does NOT assume this as table stakes is already behind.

**Scoring rubric — "2026-native score" (1-10):**
- 1-3: Could have won a 2023-2024 hackathon unchanged
- 4-6: Uses 2025-era primitives but not uniquely reliant on 2026-native stack
- 7-8: Requires at least 2 of the 2026 baseline stack items to exist as working production infra
- 9-10: Literally impossible to build before mid-2026; the demo would have been science fiction at ETHDenver 2025

**Prior Arbitrum turf check:** Shinobi Cash (cross-chain privacy pools + AA paymaster), GuardChain AI (cooperative insurance, SHG distribution), Orbital Pool (N-dimensional AMM), No-Code Agent Builder (visual workflow builder), STARK Stylus Verifier (2.1x gas benchmark), Plexi Vault (perp+yield vault with mocked guts), TriggerX Keeper (Gelato clone), Kustodia (fiat escrow), Equalis (unified lending platform).

---

## Category 1 — AI Agents / Agentic AI

### idea-01: Sealed Model (Witness-Encrypted AI Weights)
**Stale signals:** Model marketplaces have been tried (Hugging Face, Replicate). "Escrow for model delivery" is conceptually 2023-level idea. Basic KZG witness encryption papers date to 2024.

**2026-specific requirements:** Requires Lagrange DeepProve being cheap enough to prove CNN accuracy in <60s, KZG witness encryption library production-ready (IACR 2024/264 port), and cheap enough on Arbitrum to not cost $500k in gas.

**Closest 2025 hackathon overlap:** No direct winner match, but general "verifiable AI model" submissions flooded ETH Bangkok 2024 and ETH India 2024. The specific KZG WE + zkML combo is genuinely fresh.

**Verdict:** The pitch is sticky, but the tech stack became feasible exactly in late 2025 / early 2026 when DeepProve-1 launched. Not buildable at ETHDenver 2024 — the proving infrastructure didn't exist. True 2026-native.

**2026-native score: 8/10**

---

### idea-02: Inverse x402 (API Pays You to Call It)
**Stale signals:** Ad-funded APIs are ancient (Google's entire business). Reverse-incentive ad models existed since 2022 in Web3 (attention tokens, Brave BAT). ERC-8004 is 2026 but the core ad-auction mechanism is textbook Myerson. The "LLM pays you for ads" angle is fresh but x402 itself only shipped in Q1 2026.

**2026-specific requirements:** Needs x402 (Coinbase, shipped 2026) as the payment rail. Without x402 being a real standard, this is a bespoke ad-payment system (boring). Duetting auction (WWW'24) is the pricing mechanism; ERC-8004 caller-reputation is the anti-Sybil layer.

**Closest 2025 hackathon overlap:** Virtuals Protocol agent commerce launched in late 2024 and covers the "agent monetization" angle. However, the specific "the server pays you" inversion + x402 reverse-rail + truthful Myerson auction is genuinely novel.

**Verdict:** The core primitive is uniquely tied to x402 being live. Without x402 as a shipped standard, this degenerates to a custom payment experiment. Solidly 2026-native.

**2026-native score: 8/10**

---

### idea-04: Witness-Encrypted Agent Wallet
**Stale signals:** Agent wallets with conditional release have been attempted (Lit Protocol task-based access conditions, Safe modules with guardian logic). Condition-gated wallets exist. drand is a 2020-era primitive.

**2026-specific requirements:** Requires T+1-eWEB (IACR 2025/1064, Glaeser/Madathil 2025) — signature-based witness encryption paper published mid-2025 — and BLS12-381 precompiles in Stylus (which only became usable at scale in 2025). Also needs ERC-4337 smart account infrastructure (deployed widely in 2024-2025) + zkTLS attestation being cheap enough for task predicates (2025-2026 window with Reclaim, Opacity).

**Closest 2025 hackathon overlap:** Lit Protocol's "programmatic access conditions" covers conceptual ground. ETH Singapore 2024 had several "agent escrow" builds. But none used the WE crypto construct — they all relied on trusted coordinators. This is the trustless version and requires 2025's crypto papers.

**Verdict:** The specific cryptographic construction (signature-based WE) became feasible exactly in 2025. This is genuinely 2026-native for the permissionless version.

**2026-native score: 9/10**

---

### idea-08: Proof-of-Inference Bond (EOTS slashing for AI output)
**Stale signals:** Modulus Labs shipped ZKML attestation in 2023. Giza had on-chain ML inference in 2023-2024. "Slashable AI agent" is a well-known design pattern in AVS space (EigenLayer operators get slashed). The pattern of "find inconsistency, drain bond" is directly borrowed from Babylon EOTS (2023 paper).

**2026-specific requirements:** Needs Lagrange DeepProve being production-ready and cheap enough (DeepProve-1 launched late 2025), ERC-8004 validation registry being a live standard (2026), and secp256k1 EOTS verification being deployable affordably in Stylus.

**Closest 2025 hackathon overlap:** "Verifiable inference + slashing" was the dominant theme of EigenLayer AVS hackathons throughout 2025. Infernet by Ritual Networks + EigenLayer AVS submissions cover nearly this exact territory. A reasonable judge looking at this would say "another Infernet clone."

**Verdict:** The EOTS-specific key-extraction slashing adds genuine novelty over plain AVS slashing. But the overall narrative of "AI agent posts bond, gets slashed for wrong inference" is well-explored 2025 territory. Not stale enough to kill, but not fresh either.

**2026-native score: 6/10** — EOTS key extraction is the only part that's genuinely novel vs existing 2025 submissions.

---

### idea-12: TEE-Attested AI Court
**Stale signals:** Kleros arbitration has existed since 2018. TEE-based dispute resolution was proposed in academic literature in 2023. "AI judge" pitches appeared at multiple 2024 hackathons. Marlin Oyster's CVM has existed since 2024.

**2026-specific requirements:** The idea benefits from TEE being cheap (commodity in 2026), but it doesn't strictly require anything that wasn't available in 2024-2025. A 2024 builder could have done this with Phala + Kleros + basic LLM.

**Closest 2025 hackathon overlap:** Multiple "AI + TEE + arbitration" submissions at ETHGlobal 2024-2025 hackathons. This is arguably the most well-trodden agentic infrastructure territory. A top-3 submission at the Phala 2025 Q4 bounty round covered similar ground.

**Verdict:** This is the most stale idea in Category 1. The TEE AI court design was fully feasible in 2024. ERC-8004 reputation is the only 2026-specific touch, and it's cosmetic. A 2024 hackathon submission could have won with this.

**2026-native score: 4/10**

---

## Category 2 — Pure DeFi

### idea-01: Multiverse Lending (Conditional-token collateral)
**Stale signals:** Conditional tokens (Gnosis CT framework) have existed since 2019. Polymarket-style prediction markets running since 2020. Lending against prediction-market positions is a conceptually obvious extension that teams discussed at ETHDenver 2023.

**2026-specific requirements:** Requires Polymarket (or equivalent) having enough liquidity depth that conditional tokens are worth borrowing against. The Paradigm "Multiverse Finance" paper dropped May 2025 — without that formal treatment, no one could safely implement the verse-scoped liquidation math. Also requires oracle infrastructure that can resolve conditional tokens cleanly (maturing in 2025-2026).

**Closest 2025 hackathon overlap:** No direct winner match in the Bengaluru batch. Polymarket-adjacent lending was discussed but not shipped in any major 2025 submission we've seen.

**Verdict:** The formal paper (May 2025, Paradigm) is the "why now" — before it, no one had the liquidation math. The implementation requires 2025+ Polymarket liquidity depth. Solidly 2026-ready.

**2026-native score: 8/10**

---

### idea-03: Dispersion Pool (On-chain correlation trading)
**Stale signals:** Variance swaps in DeFi were proposed in 2021-2022 (Volmex, Power Perpetuals by Paradigm). Correlation trading is a well-understood TradFi concept. Stylus Rust math is 2024-era. The Jacquier & Slaoui paper is from 2010.

**2026-specific requirements:** Needs Robinhood Chain tokenized equities to have enough liquidity for the index-vs-constituent option strips to actually work. Without real tokenized equity depth (maturing in 2026), this degrades to a pure-crypto correlation trade, which is lower-novelty. Stylus makes the Cholesky math affordable but not impossible before Stylus.

**Closest 2025 hackathon overlap:** Volatility trading AMMs appeared at multiple DeFi-focused hackathons. Volmex and similar projects built variance instruments in 2022. The CBOE DSPX Index (TradFi) has existed since 2023. This is the DeFi version of a known TradFi trade.

**Verdict:** The Robinhood Chain dependency is the 2026 hook, but the core math is entirely 2023-feasible. This is a "2026 distribution channel for a 2022 idea." Valuable but not novel.

**2026-native score: 5/10**

---

### idea-09: TEE-Attested Dark Pool
**Stale signals:** "Dark pool where the operator can't see orders" is exactly what encrypted mempools (Flashbots SUAVE, Shutter Network) have been pitching since 2022-2023. TEE-based order matching (Marlin CVM) was demonstrated in 2024. Multiple ETHGlobal 2024 projects used this exact pattern.

**2026-specific requirements:** Robinhood Chain tokenized equity block trading is the 2026-specific use case. TDX being a commodity (not a beta technology) makes it more practical. But the core TEE dark pool design is thoroughly 2024-explored.

**Closest 2025 hackathon overlap:** This is almost certainly covered by an Othentic or Marlin track submission in 2024-2025. SUAVE from Flashbots (publicly demonstrated 2024) covers the "even the sequencer can't see orders" narrative.

**Verdict:** The design is well-explored and the Robinhood Chain angle is thin cosmetic differentiation. A sharp judge will say "SUAVE did this."

**2026-native score: 4/10**

---

### idea-13: am-AMM (MEV recapture via auction-managed AMM)
**Stale signals:** Adams & Moallemi published the am-AMM paper in March 2024. Uniswap V4 hooks (2024 launch) already enable custom fee mechanisms. The am-AMM has been discussed extensively in research circles throughout 2024-2025. Several teams at ETHGlobal 2024-2025 hackathons built Uniswap V4 hooks that replicate parts of am-AMM.

**2026-specific requirements:** Stylus makes the auction state machine affordable, but the design works in Solidity too (just more expensive). There's no fundamental 2026-native dependency.

**Closest 2025 hackathon overlap:** am-AMM Uniswap V4 hook implementations appeared at multiple 2025 hackathons. This is well-trodden ground.

**Verdict:** The paper is 2024, the implementations are 2025, the "2026 version" adds nothing new except Stylus gas savings. This idea could have won ETHDenver 2024. Stale.

**2026-native score: 3/10**

---

## Category 3 — DeFi × Agentic AI

### idea-02: ClaimGPT (Auto-Adjudicated Insurance)
**Stale signals:** Lemonade AI insurance claims exist in TradFi. Parametric insurance on-chain is ancient (Etherisc founded 2017, multiple Chainlink hackathon winners 2021-2023). GuardChain AI (prior Arbitrum winner) literally did cooperative insurance with AI claims adjudication.

**2026-specific requirements:** TEE-attested adjudication is a 2025-2026 improvement over trust-based AI adjudication, but the basic "AI reads a claim and decides" pattern was already in GuardChain AI (prior winner) and multiple Lemonade-on-chain builds.

**Closest 2025 hackathon overlap:** GuardChain AI at Bengaluru is the direct predecessor. This is "GuardChain with a TEE." Any judge who saw GuardChain will immediately recognize the overlap.

**Verdict:** This is the most dangerous staleness risk of any "tier-A" idea — it overlaps directly with an actual prior winner. The TEE attestation differentiates, but not enough to avoid the "we've seen this" reaction.

**2026-native score: 4/10** — Prior winner overlap makes this actively risky.

---

### idea-06: InferenceFutures (Bet on what an LLM will say)
**Stale signals:** Prediction markets on AI capabilities (Metaculus forecasts on GPT-5, ARC evaluations) have existed as informal markets. The TEE-settled futures for specific model outputs is novel, but "bet on AI behavior" is conceptually 2023-era in informal markets.

**2026-specific requirements:** Needs deterministic TEE inference to be affordable and accessible (Marlin commodity pricing 2026), and requires specific model version pinning to be technically feasible (weight hashing for open-source models). Closed-model settlement via zkTLS API-relay is only feasible with 2025-era zkTLS.

**Closest 2025 hackathon overlap:** No direct match in known 2025 Arbitrum submissions. The specific "futures market on a deterministic model invocation" is novel. Most "AI + prediction market" builds forecast real-world outcomes using AI, not forecast the AI's behavior itself.

**Verdict:** The inversion of the AI's behavior as the underlying asset is genuinely novel and requires 2026-era infrastructure (cheap TEE inference, model versioning infrastructure). This is 2026-native.

**2026-native score: 7/10**

---

### idea-08: AI Swarm Vault
**Stale signals:** Ensemble ML trading strategies have existed in TradFi since the 1990s. Tokenized yield vaults with strategy competition appeared in DeFi in 2021-2022 (Yearn Finance, Ribbon). EigenLayer-based slashing of operators is 2023-2024. "Multi-agent voting on trades" was explored conceptually in Numerai (2017) and multiple 2023-2024 DeFi-AI submissions.

**2026-specific requirements:** Needs TDX-attested model inference to be commodity-cheap (2026), ERC-8004 agent reputation to be a real standard (2026), and a liquid agent operator market to have formed. Without the agent operator economy, this is a centralized multi-model vault with unnecessary complexity.

**Closest 2025 hackathon overlap:** Numerai's staked tournament model (2017-present) is the closest real precedent. "Slashable AI agents in a vault" appeared in multiple EigenLayer AVS hackathons 2024-2025. The TEE attestation adds novelty but doesn't fully differentiate.

**Verdict:** The slashing mechanics are genuinely improved by 2026 primitives, but the core concept is well-explored. The "adversarial minority slashing" is the novel angle — this is what makes it more than just Yearn with AI. Borderline 2026-native.

**2026-native score: 6/10**

---

## Category 4 — ZK / Privacy / Wallets

### idea-02: Anti-Sybil Personhood Bond (Anonymous credit with global default nullifier)
**Stale signals:** zkPassport has existed since 2022 (Starkware's work). World ID launched in 2023. Undercollateralized lending with identity gates (Goldfinch, TrueFi, Spectral) since 2021-2022. The specific "ZK nullifier + global blocklist" pattern has been discussed since 2023 (e.g., WorldcoinID-based lending).

**2026-specific requirements:** Needs Lagrange ZK coprocessor SQL to be production-ready (2025-2026), Self.xyz to be deployable (2025+), and actual proof-of-personhood penetration to be high enough to seed a meaningful blocklist. Without wide passport proof adoption (maturing 2025-2026), the blocklist has zero entries and the anti-Sybil guarantee is weak.

**Closest 2025 hackathon overlap:** Multiple ETHGlobal 2024 "proof-of-personhood lending" submissions. The World ID gated lending design specifically appeared at ETH India 2024. However, the Lagrange ZK coprocessor SQL query for the blocklist is new and is the 2026-specific component.

**Verdict:** The core identity-gated lending concept is 2023-era. The specific implementation using ZK SQL coprocessor queries for the nullifier blocklist is more 2026-specific. Worth building but not head-turning for knowledgeable judges.

**2026-native score: 6/10**

---

### idea-11: Privacy Pools for ERC-20
**Stale signals:** Privacy Pools paper (Buterin et al.) is from 2023. 0xbow deployed Privacy Pools on ETH mainnet in March 2025. Shinobi Cash (prior Arbitrum winner) built cross-chain privacy pools specifically on Arbitrum. This is literally the most well-covered ZK privacy primitive in the 2024-2025 hackathon ecosystem.

**2026-specific requirements:** Nothing. This requires only Solidity and basic zk-SNARK libraries that have existed since 2021.

**Closest 2025 hackathon overlap:** Shinobi Cash is the direct prior winner and covers Arbitrum privacy pools. Any judge who evaluated Bengaluru will immediately say "we already funded Shinobi Cash for this."

**Verdict:** This is the single most stale idea in the entire vault. It's directly adjacent to an actual Bengaluru winner. Building this is building Shinobi Cash.

**2026-native score: 1/10** — Avoid. Direct collision with prior winner.

---

## Category 5 — Crypto Primitives

### idea-06: Jolt zkVM (Prove Rust programs in seconds)
**Stale signals:** Jolt paper published at EUROCRYPT 2024. The a16z/jolt GitHub repository went public in 2023-2024. Other zkVMs (RISC Zero, SP1 by Succinct, Nexus) have existed since 2022-2024. "Write Rust, get a proof" has been the pitch of every zkVM team since 2022.

**2026-specific requirements:** Jolt prover performance improvements (2025-2026 GPU acceleration) make it production-feasible for non-trivial programs. But the core construct is thoroughly 2024-era. SP1 by Succinct already shipped production-grade "prove any Rust" in 2024.

**Closest 2025 hackathon overlap:** SP1, RISC Zero, and other zkVM demonstrations dominated the 2024-2025 ZK hackathon circuit. The Stylus-native Jolt verifier is new, but a judge will say "RISC Zero had this two years ago."

**Verdict:** The Stylus verifier is the only 2026-specific hook, but the core pitch of "prove any Rust" is extremely well-trodden. A 2023 hackathon builder working with RISC Zero was doing the same thing.

**2026-native score: 4/10**

---

## Category 6 — Markets & Governance

### idea-01: Self-Resolving Prediction Market (BTS + alpha-stopping)
**Stale signals:** Bayesian Truth Serum (Prelec 2004) is a decades-old academic construct. Self-resolving prediction markets using BTS were formally proposed in 2023 (arXiv 2306.04305). LMSR market makers on-chain since 2020 (Gnosis). "Oracle-free prediction markets" have been proposed at every crypto hackathon since 2022.

**2026-specific requirements:** Lagrange ZK coprocessor for verifiable score aggregation is the only 2026-specific touch. The core BTS + alpha-stopping is a Solidity deployment that works on 2022 infrastructure.

**Closest 2025 hackathon overlap:** Oracle-free prediction markets appeared at ETHGlobal 2023, ETHDenver 2024, ETHIndia 2024. The specific BTS formulation is uncommon, but "self-resolving market" is a well-known pitch. The Vitalik "info finance" framing (November 2024) created a wave of these submissions in 2024-2025.

**Verdict:** Conceptually compelling but requires nothing 2026-specific to build. A 2024 team could have shipped this. The BTS math is the differentiator, not the year.

**2026-native score: 3/10**

---

## Category 7 — Real-World

### idea-04: SLA Insurance / Slash Bezos
**Stale signals:** Parametric insurance on-chain (Etherisc, Nexus Mutual) since 2018-2020. Chainlink-triggered payouts for web2 events since 2021. EigenLayer AVS with slashable operators since 2023. "Auto-pay when AWS goes down" is a product Etherisc discussed in 2021.

**2026-specific requirements:** Witness Chain's Proof-of-Bandwidth AVS being live and stable on EigenLayer (matured 2025-2026). zkTLS-attested HTTP probes replacing trust in a single oracle reporter is the 2025+ innovation. Without zkTLS probes, this falls back to a trusted oracle network (same as Etherisc 2021).

**Closest 2025 hackathon overlap:** The parametric SLA + EigenLayer AVS + oracle verification pattern was explored in multiple AVS hackathons 2024-2025. The specific "zkTLS-attested HTTP probes as the oracle" is the 2026-native ingredient.

**Verdict:** The "Slash Bezos" pitch is brilliant and sticky. The underlying tech is improved by 2026 infra but not impossible before it. The zkTLS probe network is the genuinely new ingredient. Borderline.

**2026-native score: 6/10**

---

### idea-02: Parametric Cat Pool (Hurricane/earthquake cat bonds)
**Stale signals:** Parametric insurance on-chain has existed since Etherisc (2017), Nexus Mutual (2019), and cover protocols (2021-2022). Chainlink USGS earthquake feeds have existed since 2022. Multiple "hurricane insurance on-chain" projects appeared at ETHGlobal 2022-2023.

**2026-specific requirements:** Wang Copula-POT pricing model (arXiv 2302.00462, 2023) and Stylus for gas-affordable actuarial math are the technical differentiators. The paper is 2023, Stylus is 2024. Nothing here requires 2026 specifically.

**Closest 2025 hackathon overlap:** Parametric insurance is one of the most commonly submitted DeFi-real-world ideas in the history of crypto hackathons. Nexus Mutual covers protocol risk. Etherisc covers flight delays and crop insurance. The cat-bond tranche model adds sophistication but the space is crowded.

**Verdict:** Beautiful idea, commercially compelling, but thoroughly explored in hackathon context. The Stylus actuarial math is the differentiator from prior submissions, but a judge has seen many parametric insurance pitches.

**2026-native score: 4/10**

---

## Category 8 — Multi-Domain

### idea-09: Intent Solver Bus (Generalized intents for anything)
**Stale signals:** UniswapX launched in 2023. CowSwap intent-based trading since 2021. dappOS launched "intent-centric" UX in 2023. Anoma (intent machine for the chain) has been in development since 2021, with production milestones in 2024-2025. "Generalize UniswapX to arbitrary intents" is a well-known design direction discussed in every EVM roadmap since 2023.

**2026-specific requirements:** Anoma shipping intent markets as production infra (2026) would make the "solvers compete on arbitrary intents" market deep enough to be interesting. ERC-8004 agent-to-agent intent fulfillment (2026) is the novel layer. Without real agent economy, this is another DEX aggregator with extra steps.

**Closest 2025 hackathon overlap:** Multiple "generalized intent bus" submissions at ETHGlobal 2024 using CowSwap/1inch hooks + dappOS concepts. dappOS itself has an open hackathon bounty that generates these submissions regularly.

**Verdict:** The ERC-8004 agent-to-agent layer is the genuinely 2026-native application (agents as intent-fulfillment market participants), but the base infrastructure is well-covered. A 2023 team could build the DEX/NFT version; only the agent layer is new.

**2026-native score: 5/10** — Pass/fail depends on whether agent-to-agent fulfillment is the headline or an afterthought.

---

## Summary Table

| Idea | Score | Verdict | Key Stale Risk |
|---|---|---|---|
| 04-WE-agent-wallet | 9/10 | 2026-native | None — requires 2025 IACR paper + BLS Stylus precompiles |
| 01-sealed-model | 8/10 | 2026-native | DeepProve-1 makes it feasible; not possible at ETHDenver 2024 |
| 02-inverse-x402 | 8/10 | 2026-native | x402 standard (Coinbase 2026) is the hard dependency |
| 01-multiverse-lending | 8/10 | 2026-native | Paradigm May 2025 paper is the "why now"; requires prediction market liquidity depth |
| 06-inference-futures | 7/10 | 2026-native | TEE deterministic inference feasibility is 2026; zkTLS for closed models |
| 04-anti-sybil-personhood-bond | 6/10 | Borderline | Core design is 2023; ZK SQL coprocessor is new layer |
| 08-proof-of-inference-bond | 6/10 | Borderline | EOTS key-extraction is novel; rest mirrors 2025 AVS submissions |
| 08-ai-swarm-vault | 6/10 | Borderline | Slashing is new; concept explored in 2024-2025 |
| 04-SLA-slash-bezos | 6/10 | Borderline | zkTLS probes is 2026; rest is 2021-era Etherisc architecture |
| 09-intent-solver-bus | 5/10 | Borderline | Agent-to-agent layer is new; base infra is 2023 |
| 03-dispersion-pool | 5/10 | Weak 2026 | Math is 2010, Robinhood Chain is thin hook |
| 02-claimgpt-insurance | 4/10 | STALE | Direct overlap with GuardChain AI prior winner |
| 12-tee-ai-court | 4/10 | STALE | Feasible in 2024; ERC-8004 reputation is cosmetic |
| 09-tee-dark-pool | 4/10 | STALE | SUAVE/Shutter covered this; Robinhood angle is thin |
| 06-jolt-zkvm | 4/10 | STALE | SP1/RISC Zero covered this; Stylus verifier is minor extension |
| 02-parametric-cat-pool | 4/10 | STALE | Etherisc/Nexus covered this extensively; Stylus actuarial math is thin diff |
| 13-am-amm | 3/10 | STALE | Paper is 2024; Uniswap V4 hook implementations in 2025 |
| 01-self-resolving-pm | 3/10 | STALE | BTS design is 2023; requires nothing 2026-specific |
| 11-privacy-pools-erc20 | 1/10 | AVOID | Direct collision with Shinobi Cash (prior winner) |

---

## Top 3 Most 2026-Native Ideas (Build Candidates)

### 1. idea-04: Witness-Encrypted Agent Wallet (Score: 9/10)
**Why this is the most 2026-native idea in the vault:**
- The T+1-eWEB paper (IACR 2025/1064) is a mid-2025 publication; no production implementation exists
- BLS12-381 precompiles on Arbitrum Stylus only became practical at scale in 2025
- The "wallet with no key until it earns one" pattern is unique to the drand + WE crypto construction — no equivalent exists in Lit Protocol, Safe modules, or any 2024 architecture
- Requires ERC-4337 maturity (2024-2025), zkTLS task attestation (2025), and cheap BLS operations (2025-2026)
- **Cannot be confused with any prior Bengaluru winner** — Shinobi Cash was privacy, GuardChain was insurance, nothing touched WE-based agent wallets

**Critical risk:** WE library maturity. The Glaeser/Madathil impl is research-grade; shipping a Rust port in 3 weeks is aggressive.

---

### 2. idea-01: Sealed Model / Witness-Encrypted AI Weights (Score: 8/10)
**Why this is solidly 2026-native:**
- Lagrange DeepProve-1 launched late 2025 — literally the enabling infrastructure
- KZG witness encryption (IACR 2024/264) from 2024 with no production ports yet
- "Escrow the model itself" inverts every prior "verify model behavior" approach — prior work (Modulus Labs, Giza) verifies individual inferences, not the model's existence/quality
- The demo (model pays buyer if it's as advertised, refuses if it's not) is uniquely 2026-era

**Critical risk:** DeepProve proving time for CNN-class models needs to be <60s for the demo to land; this is achievable with DeepProve-1 hardware but requires dedicated GPU.

---

### 3. idea-02: Inverse x402 (Score: 8/10)
**Why this is 2026-native:**
- x402 (Coinbase) shipped in Q1 2026 — literally zero implementations before this year
- ERC-8004 reputation as the anti-Sybil layer (2026 standard)
- The "payment rail where servers pay callers" direction only becomes interesting when x402 is a real standard (vs a bespoke implementation)
- Duetting/Mirrokni truthful auction (WWW'24 Best Paper) for LLM ad placement is a 2024 academic result with zero production implementations

**Critical risk:** FTC disclosure rules on sponsored LLM answers; needs bright "sponsored" tags to be legally defensible. The ad-auction design must not resemble native advertising without disclosure.

---

## Fusion Implications

**Highest fusion potential:** idea-01 (Sealed Model) + idea-04 (WE Agent Wallet) share the same KZG witness encryption primitive. A single Stylus WE library could underpin both. The "model that pays itself" (Sealed Model) + "wallet that appears when the agent succeeds" (WE Agent Wallet) could be a unified product:

> *"An AI agent whose model is sealed until it proves capability, and whose wallet appears only when it delivers results."*

This would be the first end-to-end cryptographic agent commerce protocol — no trusted coordinator at any step. Uniquely 2026-native: requires DeepProve-1 (zkML), T+1-eWEB (WE for agent wallets), ERC-8004 (agent registry), and x402 (payment rail) all simultaneously. None of these primitives existed as production infrastructure before 2025-2026.

**Staleness red flags to avoid in fusion:**
- Do NOT anchor the pitch around insurance/claims (GuardChain collision)
- Do NOT anchor around privacy pools (Shinobi Cash collision)
- Do NOT use TEE-dark-pool as a core primitive (SUAVE covers it)
- Do NOT build an am-AMM as a headline feature (2024 territory)
- Anything with "TEE-attested AI" + "slashing" alone needs a differentiated angle from the 2025 AVS hackathon wave
