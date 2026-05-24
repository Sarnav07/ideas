# Idea 09: Lattice Account Abstraction

## Pitch
*"A wallet that survives the day quantum computers wake up. Native ERC-4337."*

## What it is
An ERC-4337 smart account whose signature scheme is post-quantum lattice cryptography (Dilithium or Falcon). Looks like a normal AA wallet — bundlers, paymasters, session keys all work — but the underlying signature is quantum-resistant from day one.

## How it works
The smart account's `validateUserOp` runs a Dilithium-2 verifier (NIST FIPS 204) instead of ECDSA `ecrecover`. Signatures are ~2.4KB instead of 65 bytes; the AA paymaster covers the gas premium. Falcon variant for size-sensitive flows (~700-byte sigs). User onboarding hides the complexity — the wallet derives a lattice keypair from a passkey or biometric, just like any modern AA wallet.

## Why it lands (Orbital filter)
"Quantum-safe Ethereum wallet that ships today" is the inversion. Every other PQ wallet pitch is "we'll migrate after quantum arrives." This one is operational *now* — and the migration cost is just gas.

## Future utility
1-year: niche but tangible — institutions with 10+ year custody horizons start mandating PQ wallets. 3-year: regulators (US NSA NSM-10, EU NIS2) require PQ for financial institutions; this becomes table-stakes. 5-year: default wallet type for any new AA deployment.

## Business model
- Bundler/paymaster fee: 50bps premium for PQ-validated UserOps.
- Enterprise license: $100k/yr per custodian (Coinbase, Anchorage, BitGo).
- SDK as open-source loss-leader; revenue from bundler infra. Mid-case 100k PQ wallets × $50/yr fees = $5M ARR.

## Sponsor / track fit
- **Arbitrum Stylus** — Dilithium verifier in Rust (verification cost ~200k gas on Stylus vs 5M+ on EVM).
- **ERC-4337 / AA track** — flagship example of "alternative signature schemes" Vitalik has been requesting since 2022.
- **Privacy / security track** — pairs with [[idea-01-pacts-quantum-escape-hatch]].

## 3-week MVP scope
- Dilithium-2 verifier as Stylus contract (reuse NIST reference impl).
- ERC-4337 smart account that delegates `validateUserOp` to the verifier.
- Onboarding flow: passkey-derived seed → Dilithium keypair → smart-account deployment via bundler.
- Demo: send 100 USDC from a quantum-safe wallet on Arbitrum testnet; benchmark gas overhead (~250k vs ~50k baseline).

## Risks
- **Technical:** signature size inflates calldata costs; mitigated by blob/EIP-4844 + Stylus efficient encoding.
- **Adoption:** PQ urgency is still theoretical for most users. Counter: pitch as "institutional default" before retail.
- **Scheme choice:** Dilithium vs Falcon vs SLH-DSA — need clear story; recommend Dilithium-2 as default + Falcon-512 for low-bandwidth.

## Sources
- NIST FIPS 204 (ML-DSA / Dilithium) — https://csrc.nist.gov/pubs/fips/204/final
- NIST FIPS 206 draft (Falcon / FN-DSA) — https://csrc.nist.gov/Projects/post-quantum-cryptography/post-quantum-cryptography-standardization
- ERC-4337 — https://eips.ethereum.org/EIPS/eip-4337
- Stylus Dilithium experiments — https://github.com/Plonky3/awesome-plonky3
- See also: [[idea-01-pacts-quantum-escape-hatch]], [[idea-05-dead-man-switch-inheritance]]
