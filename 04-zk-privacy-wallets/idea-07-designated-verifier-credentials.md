# Idea 07: Designated-Verifier Credential Wallet

## Pitch
*"A credential you can prove to your bank — and useless to leak to anyone else."*

## What it is
A wallet that stores credentials (age, residency, accreditation, license) that can only be verified by a *specific* recipient you name at proof time. If the proof leaks, no third party can convince themselves it's real — only the original verifier can.

## How it works
Standard SNARKs are publicly verifiable: prove once, anyone can re-verify. Designated-Verifier SNARKs (DVS) bind a verifier's public key into the proof itself; the verifier *could have forged* the proof for themselves, so the proof is convincing only to them. Result: credentials become non-transferable. Showing your bank you're an accredited investor produces a proof that's literally useless to anyone else who steals it.

## Why it lands (Orbital filter)
"Prove it to one person, mathematically impossible to prove it to anyone else" inverts ZK's usual selling point (universal verifiability). The leak-resistance lands instantly with anyone who's heard of doxxing.

## Future utility
1-year: KYC-bypass airdrops where the credential can't be resold. 3-year: standard onboarding for institutional DeFi (RIA accreditation, KYC for permissioned pools). 5-year: full replacement for paper credentials in regulated finance.

## Business model
- Per-verification fee: $0.50 paid by the verifier (bank/exchange).
- Issuer subscription: $1k/mo per credential issuer (governments, universities, accredited-investor verifiers).
- Privacy-pool integration: 25bps on AML-compliant on-ramps. Conservative 5M verifications/yr × $0.50 = $2.5M direct + $30M SaaS.

## Sponsor / track fit
- **Arbitrum Stylus** — DVS verifier in Rust (curve pairings).
- **Privacy track** — credential layer for AML-compliant DeFi.
- **Identity track** — pairs with [[idea-08-self-biometric-zk-onboarding]].

## 3-week MVP scope
- Implement Li & Zhang DVS scheme (IACR 2024/1153) in Rust.
- Wallet UI: issuer signs credential → user picks verifier → wallet emits DVS proof bound to that verifier's pubkey.
- Demo: alice proves "I'm >18" to bar.eth's pubkey. bar.eth verifies in 50ms. alice tries to forward the proof to club.eth — fails (proof is verifier-bound).
- Bonus: implement a "leak detector" — if alice's proof appears unexpectedly, the binding alone shows it came from bar.eth's side.

## Risks
- **Technical:** DVS schemes have larger proofs than standard SNARKs (~5KB vs 200B).
- **UX:** users must know verifier's pubkey before proving — possible via .eth name resolution.
- **Adoption:** banks slow to integrate ZK; need a flagship issuer partner.

## Sources
- Li & Zhang, *Designated-Verifier SNARKs Revisited* (IACR 2024/1153) — https://eprint.iacr.org/2024/1153
- Jakobsson, Sako, Impagliazzo, *Designated Verifier Proofs* (EUROCRYPT 1996) — https://link.springer.com/chapter/10.1007/3-540-68339-9_13
- See also: [[idea-15-designated-verifier-loan-application]], [[idea-02-anti-sybil-personhood-bond]]
