# Idea 02: Anti-Sybil Personhood Bond

## Pitch
*"Anonymous loans. No KYC. Default once — banned from every lender forever."*

## What it is
Undercollateralized lending where the collateral is your *personhood*, not your money. Borrow anonymously; if you default, your unique human-nullifier joins a global blocklist that every other lender checks before underwriting.

## How it works
On first borrow, the user generates a ZK proof of personhood (World ID iris hash / zkPassport / Anon Aadhaar / Self.xyz). The proof emits a unique nullifier tied to a registered human, with no on-chain link to identity. Default writes the nullifier to a merkle blocklist. Every lender queries this blocklist via a Lagrange ZK coprocessor SQL — borrower stays anonymous, but lender knows "this human hasn't defaulted."

## Why it lands (Orbital filter)
"Anonymous *and* rate-limited" is the contradiction. Anonymity says "no consequences." Rate-limiting requires consequences. The ZK nullifier dissolves the contradiction in one beat.

## Future utility
1-year: $10M-TVL pilot lending pool with 0.1% default rate vs 5%+ for anon DeFi credit. 3-year: anti-Sybil identity layer underlying airdrops, perp KYC-lite, and DAO voting. 5-year: replaces the FICO score with a binary "human in good standing" oracle.

## Business model
- Origination fee: 50bps on every loan.
- Lender SaaS: $5k/month per lending protocol for blocklist API.
- Identity-anchor fee: $1 paid once per human onboarding (covers World ID / zkPassport verification gas).
- TAM: $50B undercollateralized DeFi credit by 2028; 50bps origination = $250M/yr.

## Sponsor / track fit
- **Lagrange** — ZK coprocessor SQL query against the blocklist merkle root.
- **World ID / Self.xyz / zkPassport** — identity anchors.
- **Arbitrum** — lending pool deployment; Stylus for gas-efficient nullifier verification.
- **Privacy track** — anchor showcase for proof-of-personhood applications.

## 3-week MVP scope
- Solidity lending pool with `borrow(humanProof, amount)` and `repay()` / `default()` flows.
- Integrate Self.xyz SDK for passport-based personhood proof.
- Global nullifier blocklist as a merkle tree on Arbitrum.
- Lagrange query example: "Is nullifier X in the default set?"
- Demo: borrow $100, intentionally default, attempt to borrow from a second pool — denied without revealing identity.

## Risks
- **Technical:** nullifier collisions if multiple identity anchors are accepted naively (need namespaced nullifiers).
- **Adoption:** lenders won't trust anonymous credit until empirically defaults stay low — chicken-and-egg.
- **Regulatory:** anonymity vs. AML; mitigated by per-jurisdiction lender configurability.

## Sources
- Buterin et al., *Privacy Pools* — https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4563364
- World ID *Proof of Human* — https://world.org/blog/world/proof-of-human-essential-going-mainstream-2025
- ZKPassport circuits — https://github.com/zkpassport/circuits
- Anon Aadhaar — https://github.com/anon-aadhaar/anon-aadhaar
- Self Protocol — https://docs.self.xyz
- Lagrange ZK Coprocessor — https://www.lagrange.dev/
- See also: [[idea-08-self-biometric-zk-onboarding]], [[idea-14-rln-airdrop-faucet]]
