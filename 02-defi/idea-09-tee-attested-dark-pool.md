# Idea 09: TEE-Attested Dark Pool

## Pitch
*"A dark pool where even the exchange itself can't see your orders."*

## What it is
A CLOB-style order-matching dark pool whose matching engine runs inside Intel TDX (Confidential Virtual Machine via Marlin Oyster). Orders enter encrypted to the TEE, get matched inside the sealed environment, and emerge as signed fills attested by the hardware enclave. Settlement happens on Arbitrum via a Stylus attestation verifier. The exchange operator, the sequencer, and even the chain-state observer cannot see unfilled orders.

## How it works
Marlin Oyster CVM hosts the CLOB matching code; user encrypts each order to the TEE's published attestation key. TEE matches, signs the resulting fills with its hardware key, releases only the matched-fill events to the chain. Stylus contract verifies the TDX attestation chain (Intel root → enclave → fill signature) and settles atomic swaps via Arbitrum precompiles. Orders that never matched are not revealed — they expire silently. Reference: *Cross-Chain Sealed-Bid Auctions on Confidential Compute* (arXiv 2510.19491).

## Why it lands (Orbital filter)
"Dark pool" lands instantly for any non-crypto VC who has read Flash Boys or watched The Big Short. The second-order paradox ("the *exchange itself* can't see it") flips the user's mental model: in TradFi dark pools, the operator sees everything — they're the trusted party. Here, hardware attestation removes even the operator. Cleanly distinct from encrypted-mempool (which is sequencer infra, not a consumer venue).

## Future utility
1-year: institutional block trading (>$1M ticket sizes) moves from RFQ desks to TEE dark pools because the operator-trust assumption disappears. 3-year: tokenized-equity block trading runs natively onchain. 5-year: every major asset class has its TEE pool; lit CLOBs (Uniswap V4 with hooks) handle small flow, TEE pools handle large flow.

## Business model
Fee: 5-10 bps of matched volume (TradFi dark pools charge 1-3 bps; we get more because of crypto-native settlement convenience). At $10B annual block-trade volume (1% of US dark-pool TAM, conservative), $5-10M annual revenue. Plus TEE-host fee capture (Marlin Oyster shares its CVM revenue). TAM: $X trillion annual dark-pool flow in US equities, single-digit-percent achievable as tokenized-equity volumes ramp via Robinhood Chain.

## Sponsor / track fit
**Robinhood Chain $30K** primary — institutional block trading of tokenized equities is the killer feature Robinhood Chain needs. **Overall $70K** secondary. **Stylus** — TDX attestation chain verification (a complex parsed proof) is a Stylus-only-feasible Solidity bypass.

## 3-week MVP scope
- Week 1: Marlin Oyster CVM with CLOB matching engine inside; TEE-key attestation publishing.
- Week 2: Stylus TDX attestation verifier; order submission UI with client-side encryption.
- Week 3: live demo — 10 large orders from 3 users, matched inside TEE, only matched fills appear on Arbitrum explorer; demonstrate `eth_getBlock` doesn't reveal unfilled orders.

## Risks
- **TEE vulnerabilities** — Intel TDX has had side-channel bugs. Mitigation: multi-TEE quorum (TDX + AMD SEV-SNP) for high-stakes orders.
- **Attestation gas cost** — verifying full TDX attestation onchain is expensive. Mitigation: Stylus implementation drops ~50× vs Solidity.
- **Operator front-running** — even with TEE, operator can MEV at the L1-settlement boundary. Mitigation: time-locked commit-reveal for fills.

## Sources
- *Cross-Chain Sealed-Bid Auctions on Confidential Compute* — [arXiv 2510.19491](https://arxiv.org/abs/2510.19491)
- Marlin Oyster CVM docs — [docs.marlin.org/oyster/protocol/cvm](https://docs.marlin.org/oyster/protocol/cvm/)
- Intel TDX whitepaper — [intel.com/content/www/us/en/developer/articles/technical/intel-trust-domain-extensions](https://www.intel.com/content/www/us/en/developer/articles/technical/intel-trust-domain-extensions.html)
