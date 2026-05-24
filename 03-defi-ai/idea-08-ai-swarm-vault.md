# Idea 08: SwarmVault — N Attested AI Agents Vote, Slashed if Wrong

## Pitch
*"A vault run by 7 AIs. They vote on every trade. The minority gets slashed."*

## What it is
A vault whose trading decisions are made by a swarm of N independent attested LLM agents. Each agent posts a vote + reasoning hash; majority decision executes; agents on the losing side of poorly-performing trades lose stake. Over time, accuracy-weighted voting evolves.

## How it works
1. N agent operators each stake ETH and register a TDX-attested model.
2. Per rebalance: all N independently emit `(action, confidence, attestation)`. Stylus contract weights votes by per-agent reputation score.
3. After T epochs, P&L attributed per vote. Agents on the consistent wrong side lose stake; right-side agents gain reputation × fee share.
4. New agents can join by staking; failing agents auto-eject.

## Why it lands (Orbital filter)
"Wisdom of the crowd" is a known phrase. "Wisdom of an *adversarial* AI crowd, with cash at stake" inverts the cooperation assumption — each agent is financially motivated to be uniquely right, not to herd. Markets-not-models for AI alpha.

## Future utility
1-yr: small-cap crypto trading vaults outperform single-model bots. 3-yr: pension funds allocate via swarm-vetted strategies. 5-yr: every consequential AI decision (medical, legal) runs through a swarm with skin in the game.

## Business model
1.5% mgmt + 15% perf, of which 30% goes to consistently-best agents as bonus. At $30M TVL, $1.2M/yr gross. Agent operators run multi-vault as "AI quant employees."

## Sponsor / track fit
Best Agentic AI $15K + DeFi + Overall $70K. ERC-8004 reputation + EigenLayer slashing + Marlin TDX attestation. Strong sponsor convergence.

## 3-week MVP scope
- Week 1: Stylus vault + voting/slashing engine
- Week 2: 5 distinct agents (different LLMs/RL strategies) in TEE producing daily vote on synthetic ETH/BTC long-short
- Week 3: 14-day backtest replay with on-chain attribution + slashing demo + reputation chart UI

## Risks
- Correlated failure modes: all LLMs hallucinate similar mistakes. Mitigate by diversifying base models (Llama, Mistral, Qwen, classical RL).
- Sybil: one operator runs N "different" agents. Mitigate by capping per-operator stake + requiring distinct attestation hardware.
- Slow consensus: 7 attestations per trade is heavy. Mitigate by hierarchical voting (3-of-5 fast, 7 only for high-conviction).

## Sources
- [Wisdom of the Silicon Crowd — arXiv 2402.19379](https://arxiv.org/pdf/2402.19379)
- [Marlin Oyster CVM](https://docs.marlin.org/oyster/protocol/cvm/)
- [ERC-8004 Agent Identity](https://eips.ethereum.org/EIPS/eip-8004)
- [EigenLayer slashing](https://docs.eigenlayer.xyz/)
