# Idea 02: Harberger-Tax NFTs

## Pitch
*"Anyone can buy your NFT — at the price you set."*

## What it is
An NFT standard in which every holder must continuously self-declare a sale price, pay a small recurring tax on that price, and accept that *anyone* may force-purchase the asset at the declared price. Underpricing is risky (someone snipes you); overpricing is costly (tax burns). Equilibrium = honest valuation.

## How it works
- Owner posts price `p` and locks a tax bond. Tax `τ × p` streams to a public goods pool block-by-block.
- Any caller may `forceBuy(tokenId)` by paying `p` into escrow; ownership transfers atomically.
- If owner stops topping up the bond, the contract auctions the NFT at the last declared price.
- Welfare-theoretic result (Posner-Weyl): for tax τ tuned to expected turnover, self-assessed price converges to the owner's true reservation value, eliminating the deadweight loss of monopolistic holdings.

## Why it lands (Orbital filter)
Zero crypto knowledge required; the paradox sells itself ("wait, anyone? at any time?") and the 5%-tax rebuttal sells the mechanism in one sentence.

## Future utility
- 1 yr: art, ENS-style names, in-game items, billboards.
- 3 yr: licensing rights (music samples, AI training corpora) where idle holders block use.
- 5 yr: domain names, spectrum allocation, public-utility easements.

## Business model
- Protocol skims 10% of the Harberger tax stream → directed to a public-goods quadratic-funding pool.
- At $50M TVL with τ = 5% annual, that's $250k/yr to the protocol from a single collection.

## Sponsor / track fit
Overall. Strong narrative for any track that talks about "public goods" or "mechanism design." Paradigm-adjacent.

## 3-week MVP scope
- ERC-721 Harberger extension with per-token bond stream.
- Stylus tax-accrual contract that supports `forceBuy()` in one call.
- Web UI with a "Buy at listed price" button on every token.

## Risks
- Tax-rate calibration: too high deters owners, too low deters honesty.
- Predatory force-buys against illiquid sellers; mitigate with grace periods.
- Tax obligations may attract regulatory scrutiny in some jurisdictions.

## Sources
- Posner & Weyl, *Radical Markets* — https://press.princeton.edu/books/hardcover/9780691177502/radical-markets
- Gwern, *Self-Funding Harberger Taxes* — https://gwern.net/harberger
- Weyl & Zhang, *Depreciating Licenses* — https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3082864
