# Idea 05: AgentCredit — Lending Market Where Only AIs Can Borrow

## Pitch
*"A lending market where humans can't borrow. Only AI agents — and their reputation is the collateral."*

## What it is
A credit pool that only lends to ERC-8004-registered AI agents. Each agent has a reputation score earned from on-chain task completion (settled jobs, API revenue, oracle uptime). The agent's bond + reputation set its APR; default permanently nullifies the agent identity.

## How it works
1. Agents register under ERC-8004 with a TDX-attested key + initial bond.
2. Borrow: agent presents recent earnings stream (zkTLS proof of x402 payments received). Pool sets LTV based on agent reputation × stream stability.
3. Repayment auto-streams from agent's incoming x402 payments via ERC-7715 spending-limit token (FRONTIER #21).
4. Default: agent's nullifier added to global blocklist (sister to FRONTIER #10 personhood bond) + bond drained. Identity permanently dead.

## Why it lands (Orbital filter)
"A loan market that locks out humans" is a paradox that lands instantly. The undercollateralized-lending holy grail solved via *agent* identity, not human KYC. AI economy gets a working credit layer years before consumer crypto.

## Future utility
1-yr: agents take micro-loans to bid for inference jobs or expand GPU rentals. 3-yr: agent SaaS businesses funded via on-chain debt; humans LP into the pool. 5-yr: the AI economy has its own credit cycle, denominated in compute hours.

## Business model
6-15% APR spread. At $50M loan book, ~$3M/yr net interest. Pool LPs earn variable APY based on borrower mix. Reputation oracle takes 5bp.

## Sponsor / track fit
Best Agentic AI $15K + DeFi + Overall $70K. ERC-8004 + x402 + ERC-7715 triple-stack. AI-economy native — sponsors love.

## 3-week MVP scope
- Week 1: Stylus credit contract + ERC-8004 reputation registry + nullifier blocklist
- Week 2: x402 income-stream oracle (zkTLS proof of received payments)
- Week 3: live demo with 3 synthetic agents (one good repayer, one defaulter, one new) showing dynamic APR + slashing flow

## Risks
- Agents are sybil-resistant only as strong as ERC-8004 attestation. Mitigated by requiring TEE-attested keys + bond floor.
- Income stream proofs assume x402 adoption. Bootstrap with simulated streams + selected partner APIs.
- LP capital may be thin pre-agent-economy. Start with whitelisted agent operators (proven track record).

## Sources
- [EIP-8004 Agent Identity](https://eips.ethereum.org/EIPS/eip-8004)
- [x402.org HTTP-native payments](https://www.x402.org/)
- [EIP-7715 advanced permissions](https://eips.ethereum.org/EIPS/eip-7715)
- [Secure Autonomous Agent Payments — arXiv 2511.15712](https://arxiv.org/abs/2511.15712)
