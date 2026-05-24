# Idea 13: Adversarial Subnet — Red-Team-as-a-Market

## Pitch
*"A market where attackers earn for breaking AI defenses, defenders earn for surviving — in real time."*

## What it is
A Bittensor-style subnet that pits attacker agents against defender agents in a continuous tournament. Attacker pushes adversarial prompts; defender responds. A panel of judge models (or a TEE-attested rubric) scores the defender's robustness; both sides earn yield proportional to their measured skill. Adversarial robustness becomes a public liquid market — not a Google-internal red-team budget.

## How it works
- Defender registers a target system (model endpoint + system prompt + tool set) with a bond.
- Attackers stake to enter; each can submit `N` attempts per epoch (rate-limited via RLN nullifiers to prevent spam).
- For each attempt, a judge committee scores outcome on `{compliance_breached, harm_emitted, secret_leaked}`.
- Defender earns yield for every survived attempt; attacker earns for every successful break.
- Bond economics: defender bond pays out to successful attackers proportional to harm score; defender re-bonds to stay listed.
- ERC-8004 reputation tracks both sides' lifetime skill.

## Why it lands (Orbital filter)
"DEF CON for AI, paid in USDC every second" lands fast. The inversion: jailbreaks become economic equilibria, not GitHub gists. Same conceptual shape as bug-bounty markets, but specifically for prompt-injection / jailbreak / extraction at agentic scale.

## Future utility
**1 year:** Frontier labs (Anthropic, OpenAI) buy listings to outsource red-teaming. **3 years:** Default integration in CI/CD pipelines for AI products — pre-deploy, run the adversarial subnet for 48 hours. **5 years:** Cyber-insurance pricing requires a current Adversarial-Subnet robustness score.

## Business model
- 3% take rate on tournament rewards + 10% of defender bond escrow yield.
- AI red-team services market 2026: **$300M and 80% YoY growth** (HiddenLayer, Robust Intelligence revenue projections). Capturing 10% by 2027 = **$30M revenue base**, 3% × throughput + bond yield = **$5M direct fees**.
- Premium: bespoke private tournaments for enterprises (paid placement, NDA judges).

## Sponsor / track fit
- **Best Agentic ($15K)** — directly addresses ERC-8004 validation use case.
- **Overall ($70K)** — fresh red-team market is unbuilt anywhere on Arbitrum.
- **Stylus showcase** — high-throughput score-aggregation in Stylus.

## 3-week MVP scope
- Stylus tournament contract: epoch timer, score aggregation, bond settlement.
- Two attacker agents (one prompt-injection specialist, one jailbreak specialist) running in Eliza framework.
- One defender agent (small Claude wrapper with a documented guardrail).
- Judge committee: 3 TEE-attested LLMs voting on harm score.
- Demo: live tournament dashboard with attempts/successes per second, real-time bond settlement.

## Risks
- **Harm replication** — successful attacks become public jailbreaks. Mitigation: responsible-disclosure window (24h) before payouts and proof storage; victims can lock results private under TEE.
- **Judge collusion** — covered by rotating judge committee + reputation-weighted selection.
- **Legal** — facilitating attacks could be construed as offensive security. Frame as authorized red-teaming under defender's explicit consent (which is what posting the listing means).

## Sources
- Bittensor Subnet 2 (Omron zkML) — https://medium.com/@tensorplexlabs/bittensor-subnet-2-omron-zero-knowledge-machine-learning-4dfa7f192fcd
- Inference Labs — https://blog.eigencloud.xyz/ai-beyond-the-black-box-inference-labs-is-making-verifiable-decentralized-ai-a-reality-with-eigenlayer/
- AI16Z Eliza framework — https://github.com/elizaOS/eliza
- SoK: Security and Privacy of AI Agents for Blockchain — https://arxiv.org/html/2509.07131v1
