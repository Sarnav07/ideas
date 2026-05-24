# Idea 10: Stealth-Address Salary Stream

## Pitch
*"Get paid every block. No address on-chain ever sees two paychecks."*

## What it is
A continuous payroll/streaming-payments protocol where each second's worth of salary lands at a brand-new stealth address. Nobody — not your employer's bookkeeper, not chain analytics, not your nosy ex — can correlate paychecks into a single recipient.

## How it works
The recipient publishes a single ERC-5564 stealth meta-address (a viewing key + spending key pair). The payer computes a fresh stealth address per stream interval (every block, every minute, every hour — configurable). Each interval, the streamer contract emits an `ERC5564Announce` event and transfers the dust-sized payment to the freshly-derived address. The recipient scans events with their viewing key and consolidates.

## Why it lands (Orbital filter)
"A salary that's the same money but a new wallet every block" sounds impossible until ERC-5564 lands in one sentence. The visceral pitch — "your employer can't even prove what they paid you" — sells itself to any privacy-conscious worker.

## Future utility
1-year: privacy-first DAO payroll (Gitcoin grants, retroactive funding). 3-year: standard primitive for crypto-native gig work (Braintrust, Bountycaster). 5-year: payroll-rails replacement for shielded-pool stablecoin paychecks — every salary on-chain is privately routed by default.

## Business model
- Streamer SaaS: $5/mo per employee streamed (vs Sablier/Superfluid at similar pricing).
- B2B: $20k/yr per DAO/protocol for batched stream issuance.
- Premium privacy-audit: $500/yr per recipient for "no-leak guarantee" reports. 10k employees × $5 = $600k MRR / $7M ARR.

## Sponsor / track fit
- **Arbitrum Stylus** — stealth-address derivation (secp256k1 scalar mul) is gas-heavy on EVM; ~10× cheaper in Stylus.
- **Privacy / payments track** — flagship application of ERC-5564.
- **Account Abstraction** — recipient consolidation via session keys.

## 3-week MVP scope
- ERC-5564 stealth-address library + ERC5564Announcer integration.
- Streamer contract: configurable interval, drips USDC to derived address each interval.
- Recipient client: scans Announce events with viewing key, consolidates spendable balance.
- Demo: stream 100 USDC over 10 minutes to alice's meta-address. Block explorer shows 600 distinct stealth addresses, each holding ~0.16 USDC. Alice's client reconstructs the full balance.

## Risks
- **Technical:** scanning ERC-5564 events is bandwidth-heavy for the recipient; need view-tag optimization (in EIP).
- **Dust attack vector:** stealth addresses can be spammed; mitigated by stream-source whitelist + view-tag pre-filter.
- **Consolidation MEV:** sweeping many UTXOs reveals correlation; need batched private consolidation (use [[idea-11-privacy-pools-erc20]] as exit).

## Sources
- EIP-5564 (Stealth Addresses) — https://eips.ethereum.org/EIPS/eip-5564
- EIP-6538 (Stealth Address Registry) — https://eips.ethereum.org/EIPS/eip-6538
- Fluidkey (existing stealth address wallet) — https://fluidkey.com/
- See also: [[idea-11-privacy-pools-erc20]], [[idea-13-zk-spend-limit-marketplace]]
