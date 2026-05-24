# Idea 01: PACTs — Pre-Quantum Wallet Escape Hatch

## Pitch
*"Prove you owned this wallet before quantum existed."*

## What it is
A pre-positioned cryptographic claim that lets any Bitcoin or Ethereum holder rescue their funds the day a quantum computer breaks ECDSA. No on-chain footprint until the rescue happens — the claim is dormant, salted, and timestamped years in advance.

## How it works
The user commits `H(addr || salt)` to OpenTimestamps today. Once a post-quantum hard-fork rescue rule activates (because a quantum adversary is draining ECDSA wallets), the user posts a ZK-STARK opening proof: "I knew this preimage before block N, and I am the only person who could." The chain accepts a fresh PQ-signature key from the prover and freezes the legacy address.

## Why it lands (Orbital filter)
"Prove you owned it before quantum existed" sounds like time travel. The dormancy is the inversion — every other PQ-migration scheme demands on-chain action *now*; this one demands nothing visible until the apocalypse.

## Future utility
1-year: rescue product for Satoshi-era P2PK addresses (1.9M BTC at risk). 3-year: standard wallet feature shipped by every PQ-aware wallet. 5-year: the only legitimate way to claim a "lost" address survives a quantum break — anything else looks like theft.

## Business model
- Free claim registration (anchor fee paid in OTS tx, ~$0.10).
- Premium rescue service: 0.5% of rescued value at trigger time. With 1.9M BTC dormant (~$190B at $100k/BTC), even 5% adoption yields $475M lifetime revenue per BTC's quantum break.
- Enterprise SaaS for custodians: $50k/yr per institution to pre-position claims on 100k+ addresses.

## Sponsor / track fit
- **Arbitrum Stylus** — STARK verifier in Rust, gas-efficient PQ-sig verification.
- **Bitcoin/L2 track** — first protocol to make Satoshi-era coins recoverable.
- **Privacy track** — the salt+commit pattern is general-purpose ZK identity.

## 3-week MVP scope
- Ethereum testnet contract that accepts STARK opening proofs against OpenTimestamps roots.
- Dilithium-2 signer (CRYSTALS reference impl) for the post-rescue key.
- CLI: `pacts commit <addr>` (today) and `pacts rescue <addr> <salt> <new-pq-key>` (trigger day).
- Demo: simulate a "quantum break" on Ropsten by exposing a private key, then rescue via PACTs.

## Risks
- **Technical:** STARK verifier on EVM is gas-heavy (~5M gas). Stylus brings it under 1M.
- **Adoption:** users won't pre-register if quantum feels >10yr away. Counter: package as default in wallet SDKs.
- **Governance:** activation requires hard-fork rescue rule — political risk.

## Sources
- Robinson, *PACTs: Protecting Your Bitcoin from a Quantum Sunset* (Paradigm, May 2026) — https://www.paradigm.xyz/2026/05/pacts-protecting-your-bitcoin-from-a-quantum-sunset
- OpenTimestamps — https://opentimestamps.org/
- CRYSTALS-Dilithium NIST FIPS 204 — https://csrc.nist.gov/pubs/fips/204/final
- See also: [[idea-09-lattice-account-abstraction]]
