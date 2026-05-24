# Idea 03: Cashu Cairo — Programmable Bearer Cash

## Pitch
*"Digital cash where every banknote runs a tiny zero-knowledge program before you can spend it."*

## What it is
Chaumian e-cash tokens (the mint can't see who holds them) where each token carries an arbitrary spending condition expressed as a Cairo program. The mint verifies a STARK proof of correct program execution at spend time without seeing the program's contents.

## How it works
A Cashu mint (deployed as an Arbitrum Stylus contract) issues blinded tokens per NUT-11 P2PK. Each token's spending condition is a Cairo program hash. To spend, the holder submits a STARK proof: "I executed program H correctly with these inputs and produced a valid spend transcript." The mint verifies the proof and burns the token. The mint learns *nothing* — not who held it, not what the program said, not what the inputs were.

## Why it lands (Orbital filter)
Money + Turing-complete + private + bearer is four contradictions in one. Chaumian blinding (mint can't see holder) + STARK proofs (mint can't see program) makes the banknote literally smarter than the bank.

## Future utility
1-year: privacy-first stablecoin remittance. 3-year: programmable cash for AI-agent commerce — agents trade banknotes with embedded "spend only on X" rules. 5-year: bearer-instrument replacement for sealed-envelope payments in legal/contractual contexts.

## Business model
- Mint operator fee: 0.1% per spend (current Cashu mints charge 0–1%).
- Premium program library: $10/mo SaaS for custom condition templates (multisig, time-lock, oracle-gated).
- B2B: $50k/yr license for fintechs running their own Cashu Cairo mints. Conservative $5B annual Chaumian-cash volume by 2028 → $5M mint fees.

## Sponsor / track fit
- **Arbitrum Stylus** — STARK verifier (Plonky3 / Risc0) in Rust beats EVM gas costs 50×.
- **Bitcoin/Lightning** — Cashu's natural settlement layer is BTC; mints can be backed by Lightning.
- **Privacy track** — combines two strongest privacy primitives (blind sigs + STARKs).

## 3-week MVP scope
- Stylus Cashu mint contract: blind-signature issuance + STARK verifier.
- Two demo Cairo programs: (a) time-lock "spend after block N", (b) ZK-attestation "spend only if I prove I'm over 18".
- Wallet CLI: mint, hold, spend, redeem.
- Demo: pay a coffee with a banknote that only unlocks after the barista proves the espresso machine pulled the shot.

## Risks
- **Technical:** STARK proving time on phones is 5-30s today; UX bottleneck.
- **Mint trust:** mint can still rug-pull reserves; this is a Cashu-inherent risk, not new.
- **Regulatory:** bearer instruments are politically contentious in some jurisdictions.

## Sources
- Cashu, *Bringing ZK Proofs to Cashu* — https://blog.cashu.space/bringing-zero-knowledge-proofs-to-cashu/
- Cashu NUT-11 P2PK — https://cashubtc.github.io/nuts/11/
- Cairo (StarkWare) — https://docs.starknet.io/architecture-and-concepts/cairo/
- Arbitrum Stylus — https://docs.arbitrum.io/stylus/gentle-introduction
- See also: [[idea-04-tlock-sealed-bid-mempool]], [[idea-12-snake-eye-mailbox]]
