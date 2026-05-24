# Idea 04: Historical State SQL — Query Any Chain's Past With a ZK Proof

## Pitch
*"Run SQL across five years of Ethereum history. Get one proof. Trust nothing."*

## What it is
A ZK coprocessor service (Lagrange / Brevis / Axiom pattern) exposed as a familiar SQL interface. Any contract submits a SQL-like query over historical state (e.g., "sum of token X transfers from address Y in last 100K blocks") and receives a succinct STARK/SNARK proof verifiable on Arbitrum in <500K gas. No trust assumption on the coprocessor.

## How it works
- Coprocessor maintains an indexed Merkle-Patricia trie of every block's state root (verified against the canonical L1 root via beacon chain hashes).
- Query DSL compiles to a zkVM (RISC0 / Jolt / SP1) circuit that walks the trie.
- Proof submitted with the result; on-chain verifier checks the proof's commitment to the trusted state root.
- Result: contracts can react to *any* historical fact, not just current state.

## Why it lands (Orbital filter)
Smart contracts are amnesic — they only see the current block. Saying "your contract can now condition on five years of cross-chain history with one cheap proof" reframes what's possible. It's the cryptographic analog of giving a contract a database.

## Cross-domain applications
- **DeFi credit**: undercollateralized lending priced on a borrower's 3-year DEX repayment + LP history across all chains, zero KYC.
- **Governance**: vote-weight as a function of *historical* token holding (e.g., "you held for ≥1 year"); kills flash-loan governance attacks.
- **AI agents**: reputation queries — "this ERC-8004 agent has completed N successful jobs in the past M blocks" verified cryptographically.
- **Insurance**: parametric payouts conditioned on historical oracle prints (e.g., "USDC depegged below $0.95 for ≥10 blocks").
- **Airdrops**: provably fair distributions based on past activity; eliminates "Sybil farming" detected only post-hoc.
- **Analytics**: Dune-style dashboards become trust-minimized; one proof, anyone can verify the chart.

## Future utility
1-yr: 5-10 protocols launch with coprocessor-priced features. 3-yr: ZK coprocessors are commodity infrastructure (like RPCs today). 5-yr: "stateless smart contracts" disappear — every contract can query history.

## Business model
- Per-query fee paid in $ARB / $USDC, split between prover marketplace operators and protocol.
- Subscription model for high-volume integrators (Aave, MakerDAO, Lido).
- TAM: every smart-contract analytics use case currently routed through Dune ($XB ARR) is a candidate. Conservative capture: 1% of Dune-class revenue + 10% of new "history-aware" DeFi primitives = $10-50M/yr.

## Sponsor / track fit
Arbitrum Stylus — efficient verifier in Rust beats Solidity by 5-10x on circuit verifier cost. Lagrange ecosystem alignment. Overall track: "history-aware contracts" is a thesis-shaped narrative.

## 3-week MVP scope
- Build on top of Lagrange ZK Coprocessor SDK (already production on Arbitrum).
- `HistoricalQuery.sol` (Stylus) with a verifier for a constrained query DSL (sum, count, exists).
- Three demo apps:
  1. **Loyalty lending**: Aave-fork pool gives borrowers a 200bp rate cut if they've LP'd >$5K for >6 months historically.
  2. **Time-locked governance**: DAO vote weight = balance × min(holding_age, 1 year).
  3. **Agent reputation oracle**: ERC-8004 agent's job-completion count over last 90 days, proven on-chain.

## Risks
- **Prover cost** — historical queries with large windows are expensive to prove. Mitigate by precomputing common indexes off-chain.
- **DSL expressiveness** — too narrow = niche, too wide = blowup. Lock MVP to SUM/COUNT/EXISTS.
- **Trust assumption on coprocessor liveness** — fallback to multiple competing provers (Lagrange + Brevis + Axiom).

## Sources
- [Lagrange ZK Coprocessor docs](https://www.lagrange.dev/coprocessor)
- [Brevis ZK Coprocessor](https://docs.brevis.network/)
- [Axiom v2 — ZK queries on Ethereum history](https://docs.axiom.xyz/)
- [Vitalik, *Low-Risk DeFi* — history-aware undercollateralized lending](https://vitalik.eth.limo/general/2025/09/21/low_risk_defi.html)
- [Lagrange DeepProve roadmap](https://www.lagrange.dev/blog/lagrange-roadmap-2025)
