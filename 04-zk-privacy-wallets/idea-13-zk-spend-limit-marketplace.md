# Idea 13: ZK Spend-Limit Marketplace

## Pitch
*"Rent your wallet to an AI for an hour — math caps the worst-case loss."*

## What it is
A marketplace where wallet owners mint NFT-bound spending permissions (cap, expiry, ZK predicate) and AI agents bid to use them. Built on ERC-7715 advanced permissions plus ZK conditions that the agent must satisfy on every transaction.

## How it works
The wallet owner mints an ERC-721 permission token with parameters: max-spend $X, valid-until block N, allowed-targets list, and a ZK predicate (e.g. "only execute if the price oracle proves slippage < 1%"). Agents bid in a sealed auction; the highest bidder gets a session key bound to that permission. Every UserOp the agent submits must include a ZK proof satisfying the predicate, verified in `validateUserOp`. Cap exhaustion or expiry burns the permission.

## Why it lands (Orbital filter)
"Rent-your-wallet-to-an-AI with mathematically-bounded loss" is the visceral inversion — wallet permissions become a tradeable commodity, not a developer-side parameter. Lands in 13 words.

## Future utility
1-year: niche prosumer market for AI traders renting capital. 3-year: standard primitive for AI-agent commerce — agents pay for the spending power they need. 5-year: a "ZipCar for wallets" liquidity layer with billions in addressable spend.

## Business model
- Marketplace fee: 2.5% on every rental.
- Premium predicate-builder SaaS: $50/mo for non-technical owners to create custom ZK conditions.
- Insurance pool: 5bps premium on rentals → covers permission-misuse claims. $100M/yr rental GMV × 2.5% = $2.5M.

## Sponsor / track fit
- **Arbitrum Stylus** — ZK predicate verifier + ERC-7715 plugin.
- **AA / MetaMask Delegation Toolkit** — direct integration with the permissions standard.
- **AI agent track** — pair with [[idea-12-snake-eye-mailbox]] for the agent's inbox.

## 3-week MVP scope
- ERC-7715 grant + ERC-721 wrapper smart account on Arbitrum (extends MetaMask Delegation Toolkit).
- Sealed-bid marketplace contract (use [[idea-04-tlock-sealed-bid-mempool]] for bid encryption).
- Two pre-built predicates: (a) "Uniswap swap with <1% slippage proven via TWAP", (b) "Aave borrow only against ETH > $X price proof".
- Demo: alice rents her $1000 spending cap to an AI trader for 1 hour at 0.5% rental fee; AI executes 12 swaps under the cap; permission expires; alice keeps the rental fee.

## Risks
- **Technical:** ZK predicate composition with ERC-7715 plugins is new; need careful state-isolation.
- **Misuse:** AI agent could spam useless txs to drain cap on gas — mitigate with paymaster gas budget separate from spend cap.
- **Adoption:** depends on AA wallet ubiquity, which is finally hitting in 2026.

## Sources
- EIP-7715 (Request Execution Permissions) — https://eips.ethereum.org/EIPS/eip-7715
- MetaMask Delegation Toolkit — https://docs.metamask.io/smart-accounts-kit/concepts/advanced-permissions/
- ERC-4337 — https://eips.ethereum.org/EIPS/eip-4337
- See also: [[idea-04-tlock-sealed-bid-mempool]], [[idea-12-snake-eye-mailbox]]
