# Idea 01: Drosera — Smart Contract Immune System

## Pitch
*"Your contract has antibodies. They detect exploits in one block and freeze the protocol — automatically."*

## What it is
A live restaked-operator mesh that runs Solidity-defined "Traps" — tiny invariant checks (e.g., *"no single transaction may move >30% of TVL"*) every block against a target DeFi protocol. When a Trap fires, the operator quorum auto-invokes a circuit-breaker on the protected contract, all in the same block as the exploit.

## How it works
Protocol authors write a `Trap` contract exposing `collect()` (snapshot state) and `isValid(snapshot)` (invariant). Restaked ETH operators on EigenLayer continuously execute both; if `isValid` returns false, BLS-aggregated signatures over the trap fire a registered response (pause, drain to vault, rate-limit). Slashing collateral underwrites both honest reporting and missed-detection penalties. Oracle dependency: **EigenLayer AVS quorum + on-chain protocol state** (no external feed — the chain is the oracle, which is why detection is one-block).

## Why it lands (Orbital filter)
Biological metaphor sells the pitch — "antibodies for code" lands on a non-crypto VC without any DeFi jargon. Every listener has read a $100M-hack headline; *"what if the contract defended itself"* is visceral, paradox-shaped, and currently impossible without restaking.

## Future utility
**1-yr:** every top-50 DeFi protocol wraps a Drosera trap around its lending pool / DEX / bridge. **3-yr:** insurance underwriters (Nexus Mutual, Sherlock) require a deployed Trap before binding cover — premiums drop 40% when one exists. **5-yr:** chain-level mandate — Optimism / Arbitrum require all canonical bridges to ship with default Traps; "uninsured" protocols become uninvestable.

## Business model
TAM: $80B DeFi TVL × 0.5% annual insurance-equivalent spend = **$400M/yr**. Take rate: 15% of premium routed to operators + 5% protocol fee = **$20M ARR** at 10% market penetration. Token captures operator-staking yield and trap-deploy fees; long-tail SaaS-style ARR per protected protocol ($500/mo flat + 0.01% TVL fee).

## Sponsor / track fit
**Overall $70K + Arbitrum reserved seat** — Stylus is the canonical environment for Trap execution (gas-cheap invariant math, BLS signature verification). Drosera is already an EigenLayer AVS, so the restaking-narrative slot is checked. Secondary: **Grants ($30K)** — milestone-based fits Drosera's roadmap of new Trap templates.

## 3-week MVP scope
- **Week 1:** fork Drosera Trap interface; write 3 reference Traps (TVL-velocity, oracle-deviation, sudden-mint). Deploy mock vulnerable Aave fork to Arbitrum Sepolia.
- **Week 2:** operator mesh of 5 restaked nodes running Trap-collector. Stylus BLS-aggregator contract verifying quorum signatures. End-to-end: simulated exploit → Trap fires → pause executes inside one block.
- **Week 3:** dashboard ("immune system view") + replay theatre showing 3 historical hacks (Euler, Cream, Beanstalk) that Traps would have caught. Public testnet faucet.

## Risks
- **False positives** — over-aggressive invariants pause healthy protocols. Mitigation: dual-quorum (Trap + governance veto for non-emergency triggers).
- **Restaking slashing risk** — operators face cascading slashing from multiple AVSs. Mitigation: Symbiotic-style isolated subnetworks.
- **Oracle quality** — relies on on-chain state being canonical. Mitigation: only protect contracts whose state is fully on-chain (no oracle-derived invariants in v1).
- **Regulatory** — auto-pausing user funds without user consent may trip CFTC / SEC custody rules in some jurisdictions.

## Sources
- [Drosera Network blog](https://drosera-network.github.io/blog/)
- [Luganodes Drosera case study](https://www.luganodes.com/blog/luganodes-drosera/)
- [EigenLayer Economic System](https://p2p.org/economy/2025-the-year-eigenlayer-became-an-economic-system/)
