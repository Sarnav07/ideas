# Category 01 — Discarded AI Agent Candidates

Ideas we considered but cut. Cut-reason codes:

- **CR-1** — Niche audience (lands only for one subculture)
- **CR-2** — Incremental ("X but better" framing)
- **CR-3** — Already shipped or in the air
- **CR-4** — Needs unpacking (>1 beat before lean-in)
- **CR-5** — Too infra-y / not productable
- **CR-6** — Niche audience (already used; kept for compat with parent DISCARDED.md)
- **CR-7** — No clean demo path

---

### "An agent that automates DeFi yield farming for you." — AI Yield Farmer
**Cut: CR-2, CR-3** — Saturated. Every hackathon ships one. THESIS.md explicitly tells us to avoid this archetype.

### "ChatGPT but on Arbitrum — answer with on-chain provenance." — On-chain LLM
**Cut: CR-2** — Wrapper, not a primitive. No paradox.

### "Your AI agent has its own NFT identity." — Agent Identity NFT
**Cut: CR-3** — ERC-8004 already shipped Jan 2026. Wrapping it as an NFT is incremental.

### "Decentralized GPU rental for training LLMs." — Akash-for-LLMs
**Cut: CR-3** — Akash, io.net, Render Network etc. all live. Crowded.

### "An agent that summarizes a DAO's chat history for new joiners." — DAO Summarizer Bot
**Cut: CR-2, CR-1** — Util tool, not a primitive. Lands only for DAO operators.

### "AI judge for Kleros disputes." — AI Juror
**Cut: CR-2** — Weaker pitch than Idea 12 (TEE-Attested AI Court). The TEE-attestation angle is what makes #12 lean-in; without it this is just "an LLM votes."

### "Multi-agent autonomous hedge fund." — DAO Hedge Agent
**Cut: CR-2, CR-3** — AI16Z, Numerai, Olas Autonomous all variants. Crowded.

### "Agents earn carbon credits for efficient inference." — Green-AI Agent
**Cut: CR-4** — Three beats: "agent" + "inference" + "carbon market." Doesn't land in 15 words.

### "An agent that pays you in tokens for sharing your screen-time data." — Data-for-Tokens Agent
**Cut: CR-3** — Vana, Ocean Protocol shipped this. Brave Browser BAT shipped this. Crowded.

### "AI-curated NFT marketplace where the AI signs off on authenticity." — AI Authenticator
**Cut: CR-2, CR-7** — Authenticity is opinion not provable; pitch is "trust the AI" which is the opposite of crypto-native framing.

### "Reasoning chain market — agents earn for each thought-step." — Chain-of-Thought Market
**Cut: CR-4, CR-7** — Pretty primitive but the 60-second demo doesn't show anything legible to a judge.

### "Bittensor for vector embeddings." — Embedding Subnet
**Cut: CR-1** — Lands for ML infra crowd; outside that, "embedding" is meaningless.

### "AI agent that mirrors your wallet behavior anonymously to confuse trackers." — Shadow Agent
**Cut: CR-3** — Tornado-adjacent privacy primitive; not novel post-Privacy Pools.

### "Multi-modal AI marketplace — pay for inference in vision/text/audio combined." — Multimodal x402
**Cut: CR-2** — Just x402 with one extra parameter. Incremental.

### "An agent governance DAO whose voters are AI agents." — Agent DAO
**Cut: CR-4** — Was in DISCARDED.md round 2 (Phala Swarm DAO) at CR-4. Stand by the cut.

### "Provable agent state migration across chains." — Cross-chain Agent Sync
**Cut: CR-5** — Infra plumbing. Not user-facing.

### "AI agent that automatically claims your airdrops." — Airdrop Hunter
**Cut: CR-3** — Earnifi, Layer3, dozens shipped. Saturated.

### "AI-driven IBC routing for cosmos packets." — IBC Router Agent
**Cut: CR-1, CR-6** — Cosmos audience only.

### "Anti-deepfake AI court for content provenance." — DeepFake Court
**Cut: CR-3** — Truepic, C2PA already shipped industry standard; cryptographic-on-chain version is incremental from Idea 14 (Watermark Royalty Rail).

### "Federated forecasting for hyperlocal weather." — FedWeather Agent
**Cut: CR-1, CR-6** — Domain-specific; niche audience.

### "An LLM that runs inside a zkVM and outputs only provable answers." — zkLLM
**Cut: CR-3** — That's literally Lagrange DeepProve-1, already shipped. Idea 08 wraps it in a bond mechanism, which is the actual novelty.

### "AI-only social network with on-chain reputation." — AI Twitter
**Cut: CR-2, CR-3** — Truth Terminal etc. already pioneered; not a new primitive.

### "TEE-attested AI oracle for DeFi prices." — TEE Price Oracle
**Cut: CR-3** — In FRONTIER round-2 cuts as "Verifiable TEE AI Oracle (CR-3)". Stand by the cut.

### "Agent stake-slashing pool against hallucination." — Hallucination Bond
**Cut: CR-3** — In DISCARDED.md round-2 (CR-2 there). Idea 08 (Proof-of-Inference Bond) is the more visceral version because slashing is permissionless not bonded-arbitration.

### "Cross-agent reputation oracle that bridges Bittensor to Ethereum." — Bittensor Bridge
**Cut: CR-5** — Plumbing. No user-facing demo magic.

### "Programmable bounty platform for AI bug reports." — Bug Bounty AI
**Cut: CR-2** — Existing Immunefi-style products dominant; "for AI" is a label not a primitive.

### "AI insurance broker that quotes a policy per inference call." — InferenceInsurer
**Cut: CR-2, CR-4** — Idea 03 (Proof-of-Prompt-Injection-Free Agent) is the canonical mechanism — this would be its broker layer, not a separate idea.

### "Privacy-preserving auditing of AI fine-tuning datasets." — DataAudit
**Cut: CR-5** — Infra primitive, no user-facing pitch.

### "Predictive market on which LLM model is best at each task." — LLM ranking market
**Cut: CR-4** — Hard to demo in 60s; benchmark-rotation game; CR-7 also applies.

---

## If you want to argue back

The closest cuts (would have been ideas 16-18 if we'd extended):
- **InferenceInsurer (CR-2/4)** — could be a Layer 4 distribution play on top of Idea 03.
- **Hallucination Bond (CR-3)** — argued back: differs from #08 in being bonded-arbitration (slow path) vs permissionless extraction (fast path). Could co-exist in a real product.
- **zkLLM (CR-3)** — argued back: if pitched as "an LLM whose every word is provable on-chain," the demo is striking. But it's Lagrange's own product, so first-mover slot is taken.
