# Idea 11: Privacy Pools for ERC-20

## Pitch
*"Mix any ERC-20 — and prove your coins aren't from a hack at the same time."*

## What it is
A privacy mixer for arbitrary ERC-20 tokens (stablecoins, LSTs, governance tokens) with a built-in compliance layer: at withdrawal you ZK-prove your deposit belongs to an *approved* subset, excluding sanctioned origins. Privacy + AML in one operation.

## How it works
Buterin/Whitehat/Illum's Privacy Pools (2023) generalizes Tornado's withdrawal-side ZK. At deposit, you produce a commitment; the contract tracks (commitment, depositor-set membership). At withdrawal, you prove your commitment is in *either* the full anonymity set *or* a curated "good" subset that excludes blocklisted addresses (OFAC, Lazarus, etc.). The chain enforces the proof — depositors who can't prove non-association fail to withdraw. Extension to ERC-20s requires per-token pools + value-bucket granularity.

## Why it lands (Orbital filter)
"Privacy mixer that an OFAC compliance officer would approve of" sounds contradictory — until the association-set proof lands in one sentence. Vitalik's name as co-author transfers credibility.

## Future utility
1-year: USDC/USDT/DAI privacy pools as default privacy layer for stablecoin movement. 3-year: integration with Aave/Compound borrow/repay flows (private DeFi). 5-year: the only mixer regulators don't try to shut down — Privacy Pools is the off-ramp from Tornado-style political risk.

## Business model
- Withdrawal fee: 25bps per withdrawal, capped at $5.
- AML data subscription: $50k/yr per institution for the curated "approved set" feed.
- Compliance-audit reports: $5k each (sold to regulators and lenders). Conservative $10B/yr through-volume × 25bps = $25M.

## Sponsor / track fit
- **Privacy track** — flagship privacy primitive that survives political risk.
- **Arbitrum Stylus** — STARK/SNARK verifier + merkle tree mgmt.
- **DeFi / RWA track** — institutional bridge to private DeFi.

## 3-week MVP scope
- Deploy ERC-20 variant of 0xbow Privacy Pools on Arbitrum testnet (fork their open-source code).
- Add multi-token vault factory (USDC, USDT, ARB).
- Curated approved-set oracle: pulls Chainalysis/TRM blocklists into the proof.
- Demo: alice deposits 1000 USDC, alice's other wallet withdraws 1000 USDC; chain confirms no Lazarus-tainted commitments in proof's association set.

## Risks
- **Technical:** anonymity set fragmentation across token+value-bucket reduces privacy. Mitigated by minimum pool sizes (~$5M min commitment count).
- **Regulatory:** Tornado-cash precedent shows political risk. Privacy Pools' compliance-aware design is the explicit hedge.
- **Approved-set capture:** if OFAC's set drift inadvertently flags innocent users, the system breaks. Need community-multisig override.

## Sources
- Buterin/Illum/Nadler/Schar/Soleimani, *Blockchain Privacy and Regulatory Compliance: Towards a Practical Equilibrium* (SSRN 4563364, 2023) — https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4563364
- 0xbow Privacy Pools (mainnet launch March 2025) — https://0xbow.io/
- Buterin's $113k deposit press — https://decrypt.co/155278/vitalik-buterin-pushes-for-privacy-pools-to-balance-anonymity-with-regulatory-compliance
- See also: [[idea-10-stealth-address-salary-stream]], [[idea-12-snake-eye-mailbox]]
