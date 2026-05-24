# Idea 08: Self.xyz Biometric ZK Onboarding

## Pitch
*"Tap your passport on your phone. The chain knows you're human. Nobody knows who."*

## What it is
A wallet onboarding flow that turns the NFC chip in every biometric passport into a Sybil-resistant ZK identity anchor. No iris scan, no orb, no centralized issuer. The user's own government already gave them the credential.

## How it works
Modern passports (170+ countries) contain a contactless NFC chip storing government-signed identity data. The Self.xyz SDK has the phone read the chip, verify the government signature locally, and generate a zk-SNARK proving "I hold a valid passport from country X, born before date Y, with unique nullifier N" — without revealing the document. On-chain contracts check the nullifier and the country/age claims.

## Why it lands (Orbital filter)
"Your passport is already a ZK credential, you just don't know it" lands in 12 words. Solves Sybil resistance with zero new infrastructure — the credential exists in every traveler's pocket.

## Future utility
1-year: Sybil-resistant airdrops, anonymous DAO voting, age-gated DeFi (no minors). 3-year: KYC alternative for cross-border crypto on-ramps. 5-year: foundation for proof-of-personhood at internet scale (7M+ Self.xyz users already in 2025; 174 countries supported).

## Business model
- Verification fee: $0.10 per onchain proof (paid by relying party, e.g. airdrop sponsor).
- Issuer integrations: $25k/yr per country-specific deployment (locality, attribute customization).
- Sybil-protection SaaS for airdrops: 1% of airdrop value as deduplication fee. $1B annual airdrop volume × 1% = $10M.

## Sponsor / track fit
- **Self Protocol** — direct partner; their SDK is the primitive.
- **Arbitrum Stylus** — SNARK verifier; passport-sig types vary (SHA1+RSA, ECDSA-P256) and Stylus handles the polymorphism cleanly.
- **Identity / Privacy track** — flagship onboarding pattern.

## 3-week MVP scope
- Self.xyz SDK integration in a React Native wallet (passport NFC read + proof generation).
- Stylus contract: `claim(proof, nullifier)` — emits Sybil-resistant ENS-style human handle.
- Demo: 3 phones, 3 passports, 3 distinct nullifiers, single-claim airdrop pool. Trying twice with same passport fails on-chain.
- Country-specific demo: India (Aadhaar QR), US (passport NFC), EU (eID).

## Risks
- **Technical:** older passports use SHA1+RSA which inflate SNARK constraints (~5M).
- **Privacy:** government-signed data leaks if proof is mis-constructed; rely on audited Self.xyz circuits.
- **Adoption:** ~70% of US adults have passports; lower in some regions. Mitigated by multi-issuer support (Aadhaar, EU eID).

## Sources
- Self Protocol docs — https://docs.self.xyz
- selfxyz/self GitHub — https://github.com/selfxyz/self
- ZKPassport circuits — https://github.com/zkpassport/circuits
- ICAO 9303 (passport chip standard) — https://www.icao.int/publications/pages/publication.aspx?docnum=9303
- See also: [[idea-02-anti-sybil-personhood-bond]], [[idea-07-designated-verifier-credentials]]
