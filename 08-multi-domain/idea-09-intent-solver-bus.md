# Idea 09: Intent Solver Bus — UniswapX Semantics for Anything

## Pitch
*"Write what you want. Solvers race to make it happen. Pay only on success."*

## What it is
A generalized intent settlement layer where users sign declarative goals (`"I want X by deadline T at price ≤ P"`) and a permissionless solver market competes to execute. Same auction mechanism powers swaps, NFT acquisitions, AI agent task fulfillment, governance proposal sponsorship, and cross-chain transfers. Solvers bond restaked ETH against execution; winning solver gets paid, losers slashed on no-show.

## How it works
- Intent format = `(want, constraint, deadline, maxPrice, signedBy)`.
- Solvers monitor the mempool of unfulfilled intents; submit fulfillment bids with attached execution txs.
- Auctioneer (Stylus contract) accepts cheapest valid fulfillment within deadline.
- Solvers post slashable bonds (composes with Idea #02 — Slashable Bond Market).
- Optional Dutch decay: reservation price decays over time to clear inventory.

## Why it lands (Orbital filter)
UniswapX and CowSwap proved this for spot swaps. Generalizing to *any* declarative intent — "buy me an NFT under $5K", "find an AI agent that completes task T under $50", "execute this DAO proposal across 3 rollups" — reframes Web3 UX as "intent, not transaction". The audience already knows the UniswapX side; the inversion is "this works for arbitrary user wants".

## Cross-domain applications
- **DeFi swaps**: standard UniswapX/1inch use case — best price across CEX, DEX, market makers.
- **NFT acquisition**: floor sweepers; user says "buy me 5 BAYC under 25 ETH each", solver routes across Blur, OS, Magic Eden.
- **AI agents**: ERC-8004 agent advertises task ("translate this doc, $5"); solver agents bid; cheapest wins, executes via x402.
- **Cross-chain transfers**: "send 100 USDC to Solana, deadline 5 min" — solver bridges via fastest route (Across, deBridge, native bridge).
- **Governance sponsorship**: "execute Aave proposal #234 if it passes" — solver fronts gas; gets reimbursed by proposal treasury.
- **Subscription bundling**: "renew my 5 SaaS subs monthly under $X total" — solver aggregates x402 calls.

## Future utility
1-yr: 5+ verticals migrate from imperative txs to intents. 3-yr: typical user signs intents, not txs; wallets become intent editors. 5-yr: intents are the user-facing primitive; raw EVM calls feel like writing assembly.

## Business model
- Take rate on solver winnings (1-3 bps of intent notional).
- Solver subscription for high-volume integrators (priority intent feed).
- TAM: UniswapX did $15B+ in 2025; cross-domain intents could 10x this. Even 1 bp on $100B = $10M/yr.

## Sponsor / track fit
- **Arbitrum Stylus** — efficient solver auction + bond manager in Rust.
- **Robinhood Chain** — solver routing for tokenized-stock spot orders across RH Chain + Arb One + CEX surfaces.
- **ERC-8004 ecosystem** — agent-to-agent intent fulfillment is the canonical agentic-web demo.

## 3-week MVP scope
- `IntentBus.sol` (Stylus) — auction logic, bond escrow, Dutch decay.
- Solver SDK in Rust + Python.
- Three demo apps:
  1. **Generic DEX router intent** — UniswapX-style swap across Arbitrum DEXs.
  2. **Agent task intent** — ERC-8004 agent broadcasts "summarize this URL for $0.50"; solver agents bid.
  3. **Cross-chain transfer intent** — composes with Atomic Cross-Rollup Bundles (Idea #03) for atomic fulfillment.

## Risks
- **Solver concentration** — early markets get captured by a few sophisticated solvers (UniswapX has this problem). Mitigate via mandatory solver rotation + bond tiers.
- **Adverse selection on solver bonds** — solvers may bond minimum to grief. Mitigate with bond-size-weighted priority.
- **Crowded space** — UniswapX, CowSwap, Across, dappOS all claim this. Differentiate via *generality* (not just swaps).

## Sources
- [UniswapX whitepaper](https://uniswap.org/whitepaper-uniswapx.pdf)
- [CowSwap protocol docs](https://docs.cow.fi/)
- [Across Protocol — intent-based bridging](https://docs.across.to/)
- [Anoma intent architecture](https://anoma.net/papers)
- [Chitra/Kulkarni/Pai, *Mechanism Design for Intents* — arXiv 2403.02525](https://arxiv.org/pdf/2403.02525)
- [Khalani Protocol](https://www.khalani.network/)
