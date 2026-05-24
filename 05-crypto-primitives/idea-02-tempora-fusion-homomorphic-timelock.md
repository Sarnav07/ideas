# Idea 02: Tempora-Fusion — Compute on Sealed Bids Before They Open

## Pitch
*"Sum encrypted bids while they're still locked. The total is public; no bid is."*

## What it is
A time-lock puzzle (TLP) primitive that supports *verifiable homomorphic linear combinations* — anyone can add, scale, or average TLP-encrypted values before any of them open, and prove the result is correct. The math means the chain can clear an auction *before the puzzles unlock*: only the winning bidder ever needs to decrypt.

## How it works
Aydin Abadi's *Tempora-Fusion* (arXiv 2406.15070, June 2024) extends classical RSA repeated-squaring TLPs with verifiable homomorphism over linear combinations. The verifier checks correctness *without* asymmetric-key crypto, so the on-chain check is cheap (hash-based + a Pedersen commitment). The puzzle still releases its plaintext after T squarings — but anyone can compute `Σ wᵢ·xᵢ` over locked puzzles in the meantime.

Onchain demo: a sealed-bid blockspace auction. Each searcher commits a TLP-encrypted bid for slot N. A keeper aggregates `Σ bidᵢ` (and `argmax bidᵢ` via standard combinatorial encoding) before slot N opens. The chain publishes "winner: bidder #23 at $X" before any bid is decryptable. Bidder #23 unlocks just their own puzzle to pay; everyone else's bids stay sealed forever.

## Why it lands (Orbital filter)
"Compute on a number you can't see, prove the answer, and only the winner ever opens their bid." Inverts the entire auction-revealing flow. Existing sealed-bid auctions either need a trusted operator (eBay) or require everyone to decrypt at the end (drand tlock); Tempora-Fusion is the first that lets the *chain* aggregate without seeing any individual input.

## Future utility
- **1 yr:** blockspace auctions, MEV searcher bids, NFT mints with sealed reserves.
- **2-3 yr:** federated learning royalty pools — clients post TLP-encrypted gradients; aggregator computes the global update; only clients whose updates were used decrypt their pay.
- **3-5 yr:** any "average across N private inputs" use case — salary benchmarking, sealed-bid M&A, private polling. The verifiable homomorphism is the secret sauce.

## Business model
Per-auction settlement fee (10-50 bps on cleared volume). Premium API: pre-built TLP-bid SDKs for MEV searchers and treasury-management bots. Licensing the Tempora-Fusion verifier as a Stylus library to L2 sequencers that want native sealed mempool support.

## Sponsor / track fit
- **Arbitrum Stylus** — RSA group ops in Rust, repeated-squaring verifier is a Stylus-native workload.
- **Flashbots / Searcher community** — sealed-bid blockspace is their unsolved problem.
- **Cryptography track** — first onchain deployment of verifiable homomorphic TLPs.

## 3-week MVP scope
- **W1:** Implement Tempora-Fusion in Stylus — RSA squaring puzzle, Pedersen-committed linear combination, hash-based correctness check.
- **W2:** Build the sealed-bid blockspace auction contract on Arbitrum testnet. Off-chain solver computes the aggregate; chain verifies.
- **W3:** Live demo with 50 simulated searchers — show that the aggregate clears at slot N, individual losing bids never decrypt, winner pays.

## Risks
- **Technical:** RSA TLP needs a trusted setup (RSA modulus) — use a class-group variant (no setup) for production. Tempora-Fusion's paper supports both.
- **Performance:** verifier cost is `O(participants)`. At 1000 bidders, gas is non-trivial; batched verification needed.
- **Adoption:** searchers are conservative; need a no-loss migration path from current mempool flow.

## Sources
- Abadi — *Tempora-Fusion: Time-Lock Puzzle with Efficient Verifiable Homomorphic Linear Combination* — [arXiv 2406.15070](https://arxiv.org/abs/2406.15070) / [IACR 2024/1013](https://eprint.iacr.org/2024/1013)
- Follow-up — *Verifiable Homomorphic Linear Combinations in Multi-Instance Time-Lock Puzzles* — [arXiv 2408.12444](https://arxiv.org/html/2408.12444v1)
