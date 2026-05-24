# Idea 06: Traceable Ring Signatures

## Pitch
*"Sign anonymously. Double-sign and your identity reveals itself."*

## What it is
A signature scheme where any group member can sign one statement per topic anonymously, but signing twice on the same topic mathematically extracts their public key. Anonymity *and* accountability from the same primitive.

## How it works
Standard ring signatures hide the signer among N candidates. Traceable Ring Signatures (TRS) add a per-topic tag: signing on tag `t` once gives an anonymous sig; signing on tag `t` twice produces two signatures whose tag-difference algebraically reveals the signer's key. Latest scheme has O(log n) signature size for n ring members.

## Why it lands (Orbital filter)
"Anonymous but punishable" sounds like a contradiction — until the tag construction is explained in one breath. 11-word paradox; resolution is one math sentence.

## Future utility
1-year: whistleblower platforms, DAO governance with anti-bribe enforcement, anonymous bug bounties with deduplication. 3-year: Sybil-resistant voting + anonymous polling for journalism/media. 5-year: foundational layer for credible-anonymity systems (anonymous court testimony, etc.).

## Business model
- B2B SaaS: $500/mo per anonymous-platform deployment (whistleblower portals, DAO voting tools).
- Per-signature fee: $0.01 on high-volume use (anonymous reviews, anti-Sybil airdrop claims).
- Open-source core + paid managed-service for compliance audits. 1k enterprise clients × $500/mo = $6M ARR.

## Sponsor / track fit
- **Arbitrum Stylus** — log-n ring-sig verifier in Rust (curve ops are gas-prohibitive on EVM).
- **Privacy track** — drop-in replacement for naïve ring sigs in Monero-style mixers.
- **Governance track** — anti-collusion voting layer.

## 3-week MVP scope
- Implement IACR 2025/1807 O(log n) TRS in Rust (BN254 curve).
- Stylus verifier contract.
- Demo: 100-member ring; sign a vote anonymously; cast a *second* conflicting vote; verifier extracts the cheater's public key in <1s.
- Anti-bribe demo: bribing a voter requires them to sign your-way; if they ever sign the-other-way, their key leaks publicly and the bribe is repudiable.

## Risks
- **Technical:** verifier gas cost still ~500k gas at log n. Stylus brings it to ~80k.
- **Adoption:** "log n ring sigs" requires educating users on the threat model that benefits.
- **Topic-tag UX:** users must agree on canonical tags; mismatched tags break the trace.

## Sources
- Yamashita & Zhandry, *Traceable Ring Signatures Revisited: O(log n) Size* (IACR 2025/1807) — https://eprint.iacr.org/2025/1807
- Original TRS: Fujisaki & Suzuki — https://eprint.iacr.org/2006/389
- See also: [[idea-02-anti-sybil-personhood-bond]] (different anonymity-accountability trade), [[idea-14-rln-airdrop-faucet]]
