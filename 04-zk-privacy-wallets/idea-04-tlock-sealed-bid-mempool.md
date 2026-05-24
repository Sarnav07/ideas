# Idea 04: tlock Sealed-Bid Mempool

## Pitch
*"Encrypt your trade to a future block. Front-running becomes mathematically impossible."*

## What it is
A transaction-submission layer where every order is encrypted to a future drand BLS signature. The ciphertext only opens at a specific block height — no committee, no trusted dealer, no MEV searcher can read your trade until inclusion.

## How it works
The user picks a future drand round R. They encrypt their tx with signature-based witness encryption — the witness is the (not-yet-existing) BLS signature at round R. They post the ciphertext to the sequencer immediately. When drand emits the round-R sig (a public, predictable event), anyone can decrypt the ciphertext. By that time, the tx is already ordered and executed; front-running is impossible.

## Why it lands (Orbital filter)
"Encrypt to a moment in time" is sci-fi until you realize drand emits one block-witness BLS sig per epoch like clockwork. The committee-free part is the second-beat killer: every other "encrypted mempool" needs a threshold ceremony.

## Future utility
1-year: MEV-protected DEX swaps as default UX on a single L2. 3-year: standard sequencer feature for every L2 that cares about retail. 5-year: end of toxic-MEV revenue (~$1B/yr currently extracted from users).

## Business model
- Sequencer fee surcharge: 5bps per encrypted tx routed through the protected mempool.
- Builder SaaS: $20k/mo per validator running the decryption helper.
- Enterprise institutional dark-flow desk: 10bps + minimum $50k/mo. At $20B/mo protected volume → $12M/yr.

## Sponsor / track fit
- **Arbitrum Nitro / Stylus** — sequencer integration + ciphertext verification.
- **drand / League of Entropy** — beacon provider.
- **MEV defense track** — anchor product.

## 3-week MVP scope
- drand-witness-encryption library (Go/Rust, reuse `tlock-js`).
- Stylus contract that accepts ciphertext, holds it in a mempool buffer, and reveals + executes on round-N signature publication.
- Demo DEX: user encrypts a $10k swap; bot tries to front-run; bot sees only ciphertext and fails.
- Latency measurement: 6-12s extra confirmation cost vs zero-MEV protection.

## Risks
- **Technical:** drand round latency adds 6-30s to UX. Mitigated by routing only price-sensitive trades.
- **Liveness:** if drand stalls, the entire encrypted backlog stalls; need fallback decryption committee for graceful degradation.
- **Sequencer collusion:** sequencer can still time-stop. Cryptographic protection is against searchers, not sequencer itself.

## Sources
- Burdges et al., *tlock: Practical Time-lock Encryption from threshold BLS* (IACR 2023/189) — https://eprint.iacr.org/2023/189
- Glaeser/Madathil/Scafuro, *T+1-eWEB* (IACR 2025/1064) — https://eprint.iacr.org/2025/1064
- drand sealed-bid auction reference — https://docs.drand.love/blog/2025/03/04/onchain-sealed-bid-auction/
- See also: [[idea-13-zk-spend-limit-marketplace]], [[idea-06-dead-man-switch-inheritance]]
