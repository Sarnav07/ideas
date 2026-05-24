# Idea 04: Wesolowski VDF — The Uncheatable Lottery

## Pitch
*"Randomness that costs an hour to produce and a millisecond to verify."*

## What it is
A Verifiable Delay Function (VDF) — `y = x^(2^T) mod N` — that *anyone* can verify in milliseconds but *no one* can compute in less than T sequential squarings. Even with infinite parallel hardware, the math forces wall-clock delay. Onchain, this means a randomness beacon nobody — not the proposer, not the validator set, not a quantum adversary — can predict or grind.

## How it works
Wesolowski's VDF (EUROCRYPT 2019) takes a public input `x` and outputs `y = x^(2^T) mod N` plus a constant-size proof `π` that verifies in two RSA exponentiations. The squaring chain cannot be shortcut or parallelized — the only way to get `y` faster than T squarings is to break the group's order assumption.

Onchain demo: a permissionless onchain lottery. Anyone deposits to slot N. After slot N closes, a public VDF runs on `x = hash(slot N entropy)`. Winner = `y mod num_entries`. The proposer of slot N had no way to know `y` when they sequenced the block — they would have needed T squarings (configured as ~10 minutes), longer than the block time. No oracle, no DRAND, no committee.

## Why it lands (Orbital filter)
"Even the proposer can't grind it." The standard onchain randomness story is "trust the proposer, trust drand, trust an oracle." VDF inverts: there is *literally no shortcut* — the universe's physics force the delay. Sounds like cheating until the squaring chain lands.

## Future utility
- **1 yr:** unbiased onchain lotteries, NFT mint orderings, raffle settlements.
- **2-3 yr:** L1/L2 leader election (Ethereum already discusses VDF for RANDAO post-Merge); validator-rotation oracles.
- **3-5 yr:** post-quantum lattice VDFs (active research) replace RSA — every chain has a native, quantum-secure randomness beacon at the consensus layer.

## Business model
Per-randomness fee (Chainlink VRF model, ~$0.50/request). VDF-as-a-service: dedicated ASIC operators sell beacon access to chains that don't run their own. Sponsor-funded public beacon for the ecosystem.

## Sponsor / track fit
- **Arbitrum Stylus** — RSA arithmetic in Rust is faster than Solidity; Stylus is the natural verifier home. Class-group VDF (no trusted setup) is a Stylus showcase.
- **Cryptography track** — first production VDF on a public L2 outside Chia.
- **Gaming / NFT tracks** — unbiased mint randomness sells itself to any team that has been burned by VRF manipulation.

## 3-week MVP scope
- **W1:** Implement Wesolowski VDF verifier in Stylus. Use class-group variant (Wesolowski class group of imaginary quadratic order) to avoid RSA trusted setup. Reference: Stanford VDF survey + Chia VDF impl.
- **W2:** Build the lottery contract — deposit window, VDF input = `hash(post-deadline block hashes)`, T tuned for ~10 min.
- **W3:** Demo: run a live lottery on testnet with 100 entries, show the VDF compute taking exactly the configured time, verification in <50ms.

## Risks
- **Technical:** Wesolowski uses RSA groups (needs trusted setup) OR class groups (no setup but slower verification). Class group is the right choice for permissionless deployment.
- **Hardware:** specialized ASICs can speed up squaring by 10× over general CPUs — the *delay* parameter T needs to be set against the fastest known ASIC.
- **Post-quantum:** RSA/class-group VDFs are not PQ-secure. Lattice VDFs exist (early research) but aren't production-ready. Disclose the assumption.

## Sources
- Wesolowski — *Efficient Verifiable Delay Functions* (EUROCRYPT 2019)
- Boneh, Bünz, Fisch — *A Survey of Two Verifiable Delay Functions* — [Stanford PDF](https://crypto.stanford.edu/~dabo/pubs/papers/VDFsurvey.pdf)
- Chia VDF implementation reference — [chia-network/chiavdf](https://github.com/Chia-Network/chiavdf)
- Neodyme tutorial — [Secure Randomness: VDFs Part 2](https://neodyme.io/en/blog/secure-randomness-part-2/)
