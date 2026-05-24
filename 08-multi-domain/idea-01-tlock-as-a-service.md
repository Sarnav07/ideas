# Idea 01: tlock-as-a-Service — Encrypt-to-a-Future-Block Primitive

## Pitch
*"One API. Encrypt anything to any future block. Every app inherits MEV resistance."*

## What it is
A drand-backed time-lock encryption service exposed as a single Solidity library + REST endpoint. Any contract calls `tlock.encrypt(payload, blockN)`; ciphertext is opaque until drand emits the BLS aggregate signature for block N, at which point anyone can decrypt. Sealed-bid auctions, sealed prediction-market positions, sealed governance votes, sealed agent prompts — all share the same primitive.

## How it works
- drand League-of-Entropy beacon emits a threshold BLS signature every 3 seconds on a publicly verifiable schedule.
- Burdges et al.'s tlock construction turns each future signature into a decryption key.
- Smart contract publishes ciphertext + target round; once drand reaches that round, anyone (frontend, indexer, MEV searcher) supplies the signature and the contract verifies + acts.
- No trusted committee, no per-app key ceremony, no liveness assumption beyond drand itself.

## Why it lands (Orbital filter)
"Encrypt your trade to next Tuesday at 3pm" sounds like sci-fi until the audience realizes drand already runs in production for Filecoin, Polkadot, and the League of Entropy. The primitive ships today; the missing piece is the *productized* developer surface.

## Cross-domain applications
- **DeFi (DEX/MEV)**: sealed-bid Uniswap V4 hook — every swap encrypted until the next block, killing sandwich attacks at the AMM layer.
- **Governance**: snapshot votes encrypted until quorum block; eliminates last-minute whale signaling and bribe-conditional voting.
- **AI agents**: agent prompts encrypted to the executor's commit block; prevents adversarial "look at my prompt, copy my trade" leakage.
- **NFT/auctions**: sealed-bid Sotheby's-style English auctions on-chain; bids encrypted until close.
- **Prediction markets**: late-resolving binary markets where bets stay hidden until the oracle deadline, defeating shill bidding.

## Future utility
1-yr: every Arbitrum Stylus DEX hook ships with an `if-tlock` flag. 3-yr: encrypted mempools become a default block-builder service, with tlock as the user-facing API. 5-yr: regulators accept tlock as the cryptographic standard for "fair access" sealed auctions (treasury, spectrum, carbon).

## Business model
Per-encryption micro-fee in $ARB or $USDC routed to drand operators (current operators are nonprofit; commercial relay would change economics). Network effect: more apps → more relayers → faster decryption SLA. Conservative TAM: 1% of $13B/month Polymarket-class volume + 0.1% of $50B/day DEX volume = $50M/yr at 1bp.

## Sponsor / track fit
Arbitrum Stylus (Solidity library + Rust BLS pairing verifier — Stylus 10x cheaper than EVM pairing precompile). Overall track: MEV defense is universally legible. Robinhood Chain track: fair-access auctions for tokenized stock IPOs.

## 3-week MVP scope
- Stylus contract: `Tlock.sol` with `encrypt(payload, round) → bytes` and `decrypt(ct, sig) → payload`, plus BLS12-381 pairing verifier in Rust/Stylus.
- 3 demo apps sharing the same library:
  1. Sealed-bid NFT auction (closes when drand round hit).
  2. Sealed snapshot vote (DAO proposal with hidden tallies).
  3. Sealed Uniswap V4 hook (single-block-delay swap).
- Live drand integration via [drand HTTP relay](https://drand.cloudflare.com).
- README: "Why your dApp needs tlock in 3 lines of Solidity."

## Risks
- **Adoption**: requires developer evangelism — primitives only matter when apps adopt them. Mitigate with 3 demo apps + open-source npm/crates package.
- **drand liveness**: if the League of Entropy fails, every dependent app halts. Mitigate by supporting fallback beacons (Filecoin's randomness, Chainlink VRF as escape hatch).
- **Gas cost**: BLS12-381 pairing on EVM is ~500K gas; Stylus brings this to ~50K. Acceptable.

## Sources
- [Burdges et al., *tlock: Practical Timelock Encryption from Threshold BLS* — IACR 2023/189](https://eprint.iacr.org/2023/189)
- [drand documentation](https://docs.drand.love/)
- [drand sealed-bid auction reference impl (2025)](https://docs.drand.love/blog/2025/03/04/onchain-sealed-bid-auction/)
- [Glaeser/Madathil/Scafuro, *T+1-eWEB* — IACR 2025/1064](https://eprint.iacr.org/2025/1064)
- [Shutter Network — production tlock for governance](https://blog.shutter.network/)
