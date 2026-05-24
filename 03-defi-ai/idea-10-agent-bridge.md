# Idea 10: AgentBridge — AI-Routed Cross-Chain Messaging with TEE Attestation

## Pitch
*"A bridge run by an AI inside a sealed chip. It decides where your money goes."*

## What it is
A cross-chain message router where an LLM-based agent (in TDX) reads destination intent, evaluates current bridge liquidity/fee landscape (LayerZero, Wormhole, Across, native canonical), picks the optimal path, and signs the route with a TEE attestation. The agent's bond covers slippage vs a published optimum.

## How it works
1. User submits `(source_asset, source_chain, destination_chain, intent)`.
2. Agent (TDX-attested) reads current bridge fees + liquidity (via zkTLS + on-chain reads), produces `(route, expected_cost, attestation)`.
3. Settlement contract executes route. Post-execution, an off-chain prover compares against a Pareto-optimal benchmark; if actual cost > attested + tolerance, agent bond slashes to user.
4. Reputation accumulates per agent; users select by reputation curve.

## Why it lands (Orbital filter)
Bridges are the most-hacked layer in crypto ($2B+ in losses). "Replace the multi-sig committee with a slashable AI routing agent inside a sealed chip" inverts the trust assumption — accountable, fast, no governance attacks.

## Future utility
1-yr: smart bridge aggregator for retail. 3-yr: institutional cross-chain treasury management uses bonded agents. 5-yr: every multi-chain DeFi action routes through an agent layer.

## Business model
1-3bp of bridged volume. At $500M monthly volume across agents, $1.8M-5.4M/yr fees. Agent operators take 60%.

## Sponsor / track fit
Best Agentic AI $15K + Overall $70K. LayerZero/Wormhole/Across track fit if they expose their fee data. Marlin TDX + ERC-8004 stack.

## 3-week MVP scope
- Week 1: Stylus settlement + reputation contract
- Week 2: agent service in Marlin Oyster routing across testnet LayerZero + Across mocks
- Week 3: 50 simulated cross-chain transfers, dashboard showing route choices + cost-vs-optimal chart

## Risks
- TEE compromise = stolen funds. Mitigate by capping per-agent volume + dual-attestation (Intel + AMD).
- Agent could collude with one bridge for kickbacks. Mitigate by zk-TLS verification of public fee feeds + slashing on demonstrable preferential routing.
- Bridge protocols may not expose machine-readable fee data uniformly. Bootstrap with the 3-5 with best APIs.

## Sources
- [LayerZero docs](https://docs.layerzero.network/)
- [Across Protocol](https://docs.across.to/)
- [Marlin Oyster CVM](https://docs.marlin.org/oyster/protocol/cvm/)
- [ERC-8004 Agent Identity](https://eips.ethereum.org/EIPS/eip-8004)
