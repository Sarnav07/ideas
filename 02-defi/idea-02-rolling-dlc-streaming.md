# Idea 02: Rolling DLC Streaming Channel

## Pitch
*"One Bitcoin transaction. Infinite derivative trades. None of them on-chain."*

## What it is
A Lightning-style payment channel for Bitcoin derivatives. Two parties fund a single multisig output, then roll daily CFDs (or any payoff curve) against drand-attested oracle prices using adaptor signatures. The oracle never learns the contract exists. Settle on demand with one close-out transaction.

## How it works
Discreet Log Contracts (Dryja 2017) + adaptor signatures + scriptless scripts. The payoff function is encoded as an adaptor secret keyed to drand's BLS signature on the daily price quote. When drand publishes the signature, only the winning party can complete the spend. Channel state rolls forward via consecutive adaptor sigs (Aumayr et al., IACR 2024/241) without touching L1. Stylus verifier on Arbitrum exposes the rolled position to other DeFi (use it as collateral, sell the channel, restake the IOU).

## Why it lands (Orbital filter)
Lightning's "one funding tx → infinite payments" was the killer abstraction of 2017. This is *"one funding tx → infinite derivatives"* — same primitive-inversion shape. Adaptor-sig magic means the oracle is blind to the contract. Same Orbital flavor: a generalist hears "the oracle doesn't know the bet exists" and leans in.

## Future utility
1-year: BTC/USD CFD desks running 24/7 with zero gas. 3-year: every BTC option desk uses DLC factories — institutional venue replacement for Deribit. 5-year: cross-asset DLC channels (BTC oracle attesting ETH/SPX) supersede ISDA bilateral derivatives.

## Business model
Routing fees on every adaptor-sig settlement (0.5–2 bps of notional, same as Lightning channel fees). At $1B daily notional through 3 weeks (matching Lightning's mature throughput), $20–80M annual fee pool. Stylus verifier earns a separate L2 collateralization fee — channels using the verifier as a liquidity bridge pay 10 bps. Comparable: Deribit BTC options revenue ~$300M/yr; capturing 10% of that is base case.

## Sponsor / track fit
**Overall $70K** — BTC-native, Stylus-canonical. The BLS pairing verifier for adaptor signatures is the kind of math that justifies a Stylus contract (Solidity would cost 50× the gas). **Robinhood Chain $30K** — Robinhood holds the largest US retail BTC book; channel-based derivatives are the natural retail derivatives product. Strong Arbitrum positioning ("BTC L2 of L2s").

## 3-week MVP scope
- Week 1: Stylus BLS-12-381 pairing verifier; drand-feed integration; adaptor-signature primitive in Rust.
- Week 2: two-party DLC channel state machine (Aumayr consecutive adaptor sigs); daily-roll CFD payoff.
- Week 3: settle-anytime close-out tx; demo: 30 rolled CFD positions, single L1 settlement, sub-cent gas.

## Risks
- **Adaptor-sig wallet UX** — no mainstream wallet exposes adaptor signing. Mitigation: ship our own minimal browser wallet for demo.
- **Drand availability** — single-source oracle. Mitigation: multi-network drand quorum.
- **Bitcoin reorgs** — channel close requires deep confirmations. Mitigation: 144-block finality for settlement.

## Sources
- Dryja, *Discreet Log Contracts* — [adiabat.github.io/dlc.pdf](https://adiabat.github.io/dlc.pdf)
- Aumayr et al., *Consecutive Adaptor Signatures* — [IACR 2024/241](https://eprint.iacr.org/2024/241)
- DLC Factories writeup — [conduition.io/scriptless/dlc-factory](https://conduition.io/scriptless/dlc-factory/)
- drand docs — [docs.drand.love](https://docs.drand.love/)
