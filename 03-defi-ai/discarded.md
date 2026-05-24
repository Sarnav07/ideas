# DeFi × AI — Discarded ideas

Ideas that came up during brainstorm and didn't make the cut. Each line has the cut reason. Codes match `/DISCARDED.md` (CR-1 through CR-7).

---

### "An AI portfolio manager that rebalances your wallet" — Smart Wallet AI
**Cut: [CR-2, CR-3]** — 2021-era pitch. No verification mechanism. Every L1 has a project trying this. No paradox, no math.

### "A chatbot that explains DeFi to you and executes trades" — DeFi Copilot
**Cut: [CR-5]** — UX layer, not a primitive. Could be a feature of any wallet. Doesn't trigger lean-in.

### "AI predicts the next memecoin to pump" — MemeAlpha
**Cut: [CR-2, CR-6]** — Niche degen audience. Hallucination problem is fatal. No mechanism to verify "alpha."

### "Use an LLM to write smart contracts" — ContractGPT
**Cut: [CR-5]** — Tool, not protocol. Devtool play, not Orbital-shape.

### "Yield aggregator that uses ML to route funds" — AlphaAggregator
**Cut: [CR-3]** — Yearn/Idle/Beefy tried this since 2020. No new primitive without the verification layer (which becomes idea 01 zkVault).

### "Bot detects rug pulls before they happen" — RugRadar
**Cut: [CR-2, CR-7]** — Pure heuristics, no verification. Demo is "trust our model output." Without zkML, it's a Discord bot.

### "AI scores token launches on a 1-10 scale" — TokenScore
**Cut: [CR-2]** — TradFi has Morningstar; crypto has Token Terminal. Marginal value-add without bonded accountability. Folds into idea 09 (RiskNet) as a feature.

### "ChatGPT plugin that trades on Uniswap for you" — TradePlug
**Cut: [CR-5, CR-3]** — Pure UX layer. Multiple shipped (Wonderland, AINFT). Not a new primitive.

### "An AI bot that runs your lending positions to maximize APY" — APYBot
**Cut: [CR-3]** — DeFiSaver shipped 2020. Wraps existing protocols.

### "Decentralized GPT — pay to query a model, model lives on chain" — OpenLLM
**Cut: [CR-5, CR-7]** — Bittensor, Akash, Ritual all in this space. On-chain LLM weights = either infeasible (size) or thin wrapper around off-chain. The novel primitive is *attribution* (idea 07).

### "AI fine-tuner marketplace where users own slices of fine-tuned models" — FineMint
**Cut: [CR-3, CR-2]** — Sahara AI, 0G, and several others occupy this space. The novel part (royalties from inference) is covered by idea 07.

### "AI agent that automates your tax filing onchain" — CryptoTax-AI
**Cut: [CR-5, CR-6]** — Useful but no Orbital paradox. Productivity tool, not a financial primitive.

### "AI matches you with DAOs aligned to your values" — DAOMatch
**Cut: [CR-5, CR-2]** — Recommender system. Niche social use case. No skin in the game.

### "AI agent that runs your DAO treasury" — TreasuryAI
**Cut: [CR-3]** — Subset of idea 13 (GaugeBrain) without the bond/slashing. Without accountability, just "trust the AI" — fails Orbital.

### "AI generates personalized synthetic assets" — SynthGen
**Cut: [CR-4, CR-7]** — Pitch needs unpacking. Synthetic-asset platforms (Synthetix, UMA) struggle with adoption; adding AI doesn't fix the underlying liquidity problem.

### "AI predicts gas prices and submits txs when cheap" — GasOracle
**Cut: [CR-3, CR-5]** — Blocknative, Etherscan all do this. Plumbing.

### "AI agent acts as your custodian" — AI Custody
**Cut: [CR-3]** — Lit Protocol, Fireblocks, Turnkey all here. Without a novel verification, it's just "smart-account UX." FRONTIER #9 covers the witness-encrypted-key angle better.

### "DAO that votes via AI agents on behalf of token holders" — ProxyMind
**Cut: [CR-4, CR-3]** — FRONTIER cut "Phala Swarm DAO" for the same reason. Three concepts to unpack; not a new financial primitive.

### "AI-generated NFTs with onchain provenance of training data" — DataNFT
**Cut: [CR-6, CR-3]** — Niche artist audience. Story Protocol, Bittensor cover the data-provenance angle. Not DeFi.

### "Decentralized Kaggle — competitions where models train against on-chain bounty" — KaggleChain
**Cut: [CR-3, CR-6]** — Numerai and Ocean both occupy variations. Not DeFi-native enough.

### "AI-recommended liquidity provision strategy with shared profits" — LP-Coach
**Cut: [CR-2, CR-5]** — Coaching layer over Uniswap. No skin in the game without a vault primitive — and the vault primitive is idea 01.

### "Personal yield agent that auto-allocates your stablecoins" — DollarBrain
**Cut: [CR-3, CR-5]** — Ondo, Mountain, Yearn already optimize this. AI badge doesn't change the primitive.

### "AI agent that negotiates OTC trades for you" — OTCBot
**Cut: [CR-6, CR-7]** — Institutional OTC desks are slow to onboard new tech. Without a verification primitive, just "AI middleman." Folds into idea 04 (ShadowMatch) at the matching layer.

### "AI that scans social media to predict altcoin pumps" — SocialAlpha
**Cut: [CR-2, CR-7]** — Toy. Hallucination + adversarial-content problem fatal. No verification path.

---

## Why these all failed the Orbital filter

The common pattern: each "AI does the thing" without crypto doing anything load-bearing. Crypto becomes the *payment* or *ownership* layer, not the *verification/escrow/slashing* layer. That's a 2021 pitch shape — and it lost in 2021.

The 15 in this category that survived all have crypto doing structural work: zkML proves the model output; TEE attests the inference; bonds slash for misbehavior; nullifiers permanently lock out defaulters. That's the inversion.

If you want to argue back on any of these, the most defensible cases are:
- **AI Custody** — could re-frame as "verifiable custodian agent with bonded compromise insurance"
- **TreasuryAI** — could re-frame as "DAO controller with slashable bond + zkML rationale" (effectively idea 13 applied to treasury)
- **KaggleChain** — could re-frame as a sub-application of idea 07 (TrainYield)
