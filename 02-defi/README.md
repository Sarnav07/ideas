# Category 02 — Pure DeFi (15 ideas)

15 Orbital-tier ideas in pure DeFi (no AI integration). Each idea has a ≤15-word pitch designed to trigger *"wait, how is that possible?"* in a smart generalist — the same shape as Orbital Pool's *"Uniswap is 1D, Curve is 2D, Orbital is N-D liquidity."*

Of the 15: **9 reused** from FRONTIER.md, **6 new** Orbital-tier finds.

---

## Index

### Reused from FRONTIER.md

| # | Pitch | Domain |
|---|---|---|
| [01](idea-01-multiverse-lending.md) | *"Borrow against assets that only exist if Trump wins."* | Conditional lending |
| [02](idea-02-rolling-dlc-streaming.md) | *"One Bitcoin transaction. Infinite derivative trades. None of them on-chain."* | BTC derivatives |
| [03](idea-03-dispersion-pool.md) | *"One pool. Long the parts, short the whole. Profit if stocks decorrelate."* | Correlation trading |
| [04](idea-04-ndim-portfolio-lending.md) | *"Aave isolates each asset. We margin your portfolio by its covariance matrix."* | Lending |
| [05](idea-05-autocallable-vault.md) | *"A vault paying 12% coupons monthly — until ETH drops 30% and you eat the loss."* | Structured products |
| [06](idea-06-self-slashing-eots-wallet.md) | *"Sign two conflicting messages and your wallet automatically pays your bond to the victim."* | DeFi safety primitive |
| [07](idea-07-infinity-pool-lrts.md) | *"A pool with millions of restaking tokens. Every swap quotes at zero slippage."* | LRT/AMM |
| [08](idea-08-permissionless-perp-factory.md) | *"Anyone can launch a perp market. List a bad oracle and the market burns your bond."* | Perps |
| [09](idea-09-tee-attested-dark-pool.md) | *"A dark pool where even the exchange itself can't see your orders."* | Dark pool |

### New Orbital-tier finds

| # | Pitch | Domain |
|---|---|---|
| [10](idea-10-cliquet-ratchet-vault.md) | *"An ETH vault that locks in your gains every month. It can only ratchet up."* | Cliquet options |
| [11](idea-11-quanto-perp.md) | *"A perp where you bet on BTC but get paid in ETH at a fixed exchange rate."* | Quanto perps |
| [12](idea-12-reverse-convertible-pool.md) | *"8% monthly coupons in USDC. If ETH drops 30%, your stack converts to ETH at strike."* | Reverse convertibles |
| [13](idea-13-am-amm-mev-recapture.md) | *"An AMM where arbitrageurs pay the LPs to play. MEV flows backwards."* | am-AMM |
| [14](idea-14-cds-pool.md) | *"Buy insurance against any DeFi protocol getting hacked. Premium is consensus risk."* | Credit derivatives |
| [15](idea-15-bermudan-vault.md) | *"You can sell on 12 specific days a year. The chain decides which day was optimal."* | Optimal-stopping vault |

---

## Top 3 picks

### #1 — Multiverse Lending (idea 01)
- **Pitch shock**: same author as Orbital (Dave White, Paradigm) — automatic credibility transfer to judges
- **Demo clarity**: borrow USDC against "Trump-wins" YES tokens, show liquidation only fires in the matching verse
- **Market size**: addressable conditional-collateral TAM = full $13B/mo Polymarket OI × emerging margin demand
- **Sponsor fit**: Robinhood Chain (Kalshi distribution) + Overall (novel primitive)

### #2 — Dispersion Pool (idea 03)
- **Pitch shock**: literal Orbital-mirror — "variance is 1D, dispersion is N-D correlation"
- **TradFi precedent**: $XB/yr prop strategy at Citadel/Susquehanna with zero retail access
- **Sponsor fit**: Robinhood Chain tokenized-equities is the *exact* substrate this needs
- **Stylus killer**: Cholesky decomposition over 50×50 covariance — Solidity can't do this

### #3 — Permissionless Perp Factory + EOTS Oracle Bond (idea 08)
- **Pitch shock**: two-beat killer — "anyone can launch a perp" + "list a bad oracle, lose your bond"
- **Narrative fit**: Hyperliquid HIP-3 + Arbitrum + Babylon EOTS = unbuilt cross-protocol play
- **Stylus killer**: secp256k1 EOTS verifier
- **Revenue path**: clearest fee model (listing bond + trading volume)

---

## Honorable mentions (just outside top 3)

- **#06 Self-Slashing EOTS Wallet** — same EOTS primitive as #08, but framed as the *underlying safety layer* across all of DeFi. Pairs well with #08 as a "primitive + product" combo.
- **#15 Bermudan Vault** — Longstaff-Schwartz onchain is the flagship Stylus math demo.
- **#10 Cliquet Vault** — most universally-comprehensible structured-product pitch.

---

## Cross-references

- See [`discarded.md`](discarded.md) for ideas we considered but cut, with reason codes.
- Reused ideas keep their FRONTIER.md provenance — see `/home/pratham/Sarnav/Open-House/FRONTIER.md`.
- Adjacent categories: 03 (DeFi × AI) for agent-integrated versions; 06 (Markets & Governance) for prediction-market primitives.
