# Idea 01: KZG Witness Encryption — Conditional Payments

## Pitch
*"Encrypt money that unlocks itself the instant a public proof exists."*

## What it is
A primitive that lets you encrypt a payload (USDC, an NFT, a private key, a contract clause) directly to a *statement* — "f(α) = β where f is the KZG-committed history" — and the only way to decrypt is to produce a valid KZG opening proving the statement is true. No oracle, no committee, no trusted server has the key. The chain itself becomes the decryption witness.

## How it works
Fleischhacker–Hall-Andersen–Simkin (ASIACRYPT 2024) built an *extractable* witness encryption scheme where ciphertexts are a single BN254 group element, encryption/decryption use one pairing each. Encrypt under `(com, α, β)`. Anyone holding an opening that `f(α)=β` recovers the message; everyone else gets nothing — *extractable* means there is no way to decrypt without literally producing the opening.

Onchain demo: KZG-commit the rollup's state history every epoch. A bounty contract escrows USDC encrypted to `(state_root_epoch_N, slot_X, value)`. The first relayer to produce a KZG opening proving the bug was patched at slot X decrypts the bounty — no governance vote, no claims process, no human in the loop.

## Why it lands (Orbital filter)
The pitch sounds physically impossible — "money that unlocks itself when a proof exists" — and then a single sentence about the KZG opening makes it real. The math is one pairing; the experience is "money with logic baked into the ciphertext."

## Future utility
- **1 yr:** bug-bounty escrows, sealed contract clauses, "release this NFT when block N proves X."
- **2-3 yr:** conditional secondary markets — sell a Polymarket YES position before resolution as a WE-ciphertext that auto-settles.
- **3-5 yr:** entire derivative payoffs encoded as WE ciphertexts. The "contract" is the ciphertext; settlement is decryption.

## Business model
Toll-bridge: a fee on every encryption call (paid in USDC, sized by ciphertext value). Stylus precompile licensing to L2s that want native WE-KZG opcodes. Premium tier: SDK for structured product issuers who want WE payoff curves.

## Sponsor / track fit
- **Arbitrum Stylus** — KZG pairing in Rust/Stylus is a canonical Stylus showcase (BN254 precompiles already exist; the WE wrapper is short).
- **Lagrange / EigenLayer** — KZG commitments are exactly what their ZK coprocessor produces; this becomes the natural payoff primitive on top.
- **EthGlobal Cryptography track** — first end-to-end WE demo on a live chain.

## 3-week MVP scope
- **W1:** Port the Fleischhacker–Hall-Andersen–Simkin scheme to Stylus (single pairing, BN254). Reference impl: `rot256/research-we-kzg`.
- **W2:** Build the bug-bounty contract — KZG-commit state history, escrow USDC encrypted to `(state_root, slot, expected_value)`, claim endpoint takes the opening.
- **W3:** Demo — live testnet: post a buggy contract, anyone who fixes it produces an opening and instantly drains the bounty. No multisig, no foundation, no claim form.

## Risks
- **Technical:** extractability proofs assume generic-group adversaries — fine for a hackathon, audit-grade requires the AGM caveat in disclosures.
- **Adoption:** devs need a clean SDK. Encrypt-to-a-statement is a new mental model; the SDK has to feel like `encrypt(value, where: 'price > 1000 at block 500k')`.
- **Performance:** one pairing per decrypt is cheap; scaling to 10k concurrent ciphertexts needs batched pairings (Miller loop sharing) — doable in Stylus.

## Sources
- Fleischhacker, Hall-Andersen, Simkin — *Extractable Witness Encryption for KZG Commitments and Efficient Laconic OT* — [IACR 2024/264](https://eprint.iacr.org/2024/264)
- zkSecurity blog explainer — [blog.zksecurity.xyz/posts/kzg-we](https://blog.zksecurity.xyz/posts/kzg-we/)
- Reference impl — [github.com/rot256/research-we-kzg](https://github.com/rot256/research-we-kzg)
