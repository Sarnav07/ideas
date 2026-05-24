# Idea 08: Programmable Shielded Pool — Aztec Notes for Any Application

## Pitch
*"A private bank account whose every transaction runs a custom program."*

## What it is
A generalized shielded pool (Aztec / Aleo / Penumbra mental model) deployed on Arbitrum via Stylus + STARK verifier. Users deposit any ERC-20 → receive a shielded note → spend the note by submitting a ZK proof that the note's *predicate program* allows the spend. The predicate is Turing-complete (Cairo / Noir / Risc0). Same pool, different programs, every application gets privacy + programmability simultaneously.

## How it works
- Pool tracks a Merkle tree of note commitments `H(value, asset, owner, predicateHash, salt)`.
- Spending a note requires a ZK proof: nullifier derivation + predicate satisfaction.
- Predicates are arbitrary Noir/Cairo programs (e.g., "spendable only after block N", "spendable only by owner of NFT X", "spendable only to receivers in allow-list").
- Pool is single, multi-asset; assets enter via deposit, exit via withdraw with selective unshielding (Goldberg et al. 2026 pattern for compliance).

## Why it lands (Orbital filter)
Tornado Cash was private-but-dumb. Aztec is private-and-smart, but Aztec is a separate chain — adoption is its own gravity well. Saying "Aztec semantics, but it's just a Solidity contract on Arbitrum that any app can use" collapses the deployment friction. Programmable bearer cash, but generalized.

## Cross-domain applications
- **DeFi**: private DEX trades, private LP positions, private lending — all using one pool, no per-app re-deployment.
- **Voting**: shielded ballots where the spending predicate is "this note can only be spent in the official tally tx" — coercion-resistant MACI replacement.
- **Inheritance**: predicate = "spendable only if drand emits signature for round N AND no heartbeat detected" (composable with tlock).
- **Payroll**: shielded salary streams where the spending predicate enforces vesting schedules.
- **Cashu-style bearer cash**: programmable e-cash notes that run zero-knowledge spending logic (extends FRONTIER #11 to Arbitrum).
- **Subscriptions**: notes spendable in N equal chunks across N months; recipient enforces no early withdrawal.
- **Compliance**: selective-unshielding committee (Goldberg pattern) can unmask specific notes on lawful request; full privacy preserved otherwise.

## Future utility
1-yr: 5-10 apps share one shielded pool. 3-yr: shielded notes are the default for any value transfer where amount/recipient confidentiality matters (corporate treasury, payroll, OTC). 5-yr: regulated banks settle commercial paper on this pool via the selective-unshielding compliance pattern.

## Business model
- Per-shielded-tx fee in $ARB (1-5 bps of notional).
- Premium: predicate compiler-as-a-service for non-cryptographers.
- TAM: private-payments market is enormous if regulators tolerate compliance-aware privacy. Conservative: $1B/yr in shielded volume × 5bps = $50M/yr.

## Sponsor / track fit
- **Arbitrum Stylus** — Cairo/Noir verifier in Stylus = native composability + 10x cost reduction.
- **Robinhood Chain** — selective-unshielding compliance pattern (per Goldberg et al. 2026) is exactly what regulated brokers need for private block trades.
- **Privacy ecosystem grants** — Aztec, Aleo, Penumbra all want their semantics expanded.

## 3-week MVP scope
- `ShieldedPool.sol` (Stylus) with Noir verifier + nullifier set + Merkle insertion.
- Three demo apps sharing the pool:
  1. **Private DEX swap**: deposit USDC shielded → swap inside the pool → withdraw to recipient. Trade amount + counterparty hidden.
  2. **Coercion-resistant DAO vote**: shielded ballots; tally tx is the only one that can spend them.
  3. **Tlock-gated will**: shielded inheritance note spendable only when drand emits round N AND no heartbeat (composes with Idea #01 and #06).
- Selective-unshielding admin contract — minimal MVP with 3-of-5 arbitration multisig.

## Risks
- **Proving cost** — Noir/Stylus proofs at ~5-10s on consumer hardware. Acceptable for governance/payroll; not for HFT.
- **Compliance optics** — depending on jurisdiction, regulators may still object. Selective unshielding (per Goldberg et al.) is the answer; v1 ships single-arbiter for demo, v2 progressive decentralization.
- **Composability**: predicates that interact with non-shielded state need bridges; scope MVP to pure shielded primitives.

## Sources
- [Aztec Network docs](https://docs.aztec.network/)
- [Aleo language reference](https://developer.aleo.org/)
- [Penumbra protocol](https://penumbra.zone/)
- [Goldberg et al., *Scalable Compliant Privacy on Starknet* — IACR 2026/474](https://eprint.iacr.org/2026/474)
- [Noir ZK DSL](https://noir-lang.org/)
- [Cashu NUT-11 P2PK spec](https://cashubtc.github.io/nuts/11/)
