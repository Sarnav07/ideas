# Idea 06: ERC-7715 Wallet Marketplace — "Zipcar for Wallets"

## Pitch
*"Rent your wallet to an AI for an hour, with math-bounded loss."*

## What it is
A marketplace where wallet owners mint ERC-7715 "advanced-permission" tokens — capped session keys for their own smart account — and agents bid to rent them. The owner caps spend, expiry, allowed selectors, and counterparties; the agent gets temporary signing power within the cage. Wallet capacity becomes a tradeable commodity.

## How it works
- Owner deploys an ERC-4337 smart account (MetaMask Delegation Toolkit, ZeroDev, Biconomy).
- Owner mints an **ERC-7715 permission grant** as an ERC-721 with calldata: `{cap_usd, expiry, allowed_selectors, allowed_addresses, predicate}`.
- The grant is listed on a Stylus orderbook with English auction or sealed-bid via tlock.
- Winning agent pays rent (per-hour USDC stream via x402) and receives a session key bound to the grant.
- ERC-8004 reputation accrues both ways: agents that respect the cage build trust; owners that mint clean cages get higher rent.

## Why it lands (Orbital filter)
"I can rent my wallet's spending power to an AI, math-capped" lands instantly for anyone who has refused to give an AI their credit card. Inverts the wallet-agent relationship — wallet capacity becomes a market, not a permission grant.

## Future utility
**1 year:** Niche utility for "I want my agent to do groceries on Tuesday only." **3 years:** Default monetization for retail users — your idle wallet earns yield as agent compute capacity. **5 years:** Power-law concentration: institutional wallet-rental desks emerge (like prime brokerage for agent compute).

## Business model
- 2% take rate per rental settlement.
- Forecast 2027 agent-economy turnover routed through delegated wallets: **$80B** (Citi GPS, ChainUp x402). 2% take of 5% turnover via marketplace = **~$80M annual fees**.
- Tiered listings: featured slots, premium-cap underwriting (deeper-pocket owners get pre-negotiated agent allocations).

## Sponsor / track fit
- **Best Agentic ($15K)** — direct ERC-7715 + ERC-4337 composition.
- **Robinhood Chain ($30K)** — RH Chain is positioned for payment rails; consumer wallet rental is the dream demo.
- **Overall ($70K)** — "Zipcar for wallets" is meme-tier; sticks in judges' heads.

## 3-week MVP scope
- ERC-7715 permission-grant minter contract on Arbitrum + RH Chain testnet.
- Stylus orderbook (listing, bid, settle).
- Demo agent (Eliza framework) that bids on a wallet and uses the session key to buy $50 of tokenized AAPL on RH Chain.
- Frontend: rental dashboard with cap remaining, time remaining, kill-switch.

## Risks
- **ERC-7715 immaturity** — MetaMask Delegation Toolkit + Biconomy modular accounts are early; we ship our own minimal grant verifier as fallback.
- **Adverse agent behavior** — covered by selector/address allow-lists in the predicate; kill-switch always live.
- **Regulatory** — delegated trading on tokenized securities is regulated. Demo against a non-securities asset (USDC or test-token) for the MVP.

## Sources
- EIP-7715 — https://eips.ethereum.org/EIPS/eip-7715
- MetaMask Delegation Toolkit — https://docs.metamask.io/smart-accounts-kit/concepts/advanced-permissions/
- *Giving AI Agents Access to Cryptocurrency* — https://arxiv.org/abs/2507.08249
- ERC-4337 — https://eips.ethereum.org/EIPS/eip-4337
