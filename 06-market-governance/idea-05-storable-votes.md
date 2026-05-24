# Idea 05: Storable Votes — Save Your Vote for Issues You Care About

## Pitch
*"Skip this DAO vote, bank it, spend two on the one that matters."*

## What it is
A DAO voting system where token holders receive one vote per issue *plus* a personal vote-bank. Pass on issues you don't care about, accumulate votes, and dump them on the proposals that matter to you. Casella's storable-votes result: this Pareto-dominates one-vote-per-issue when preference intensities differ.

## How it works
- Each voter has a budget `b_i` accumulating at one vote per issue.
- On issue `t`, voter spends `s_t ∈ [0, b_i]` votes; remaining `b_i - s_t` rolls forward.
- Outcome = majority of total votes spent on that issue.
- Welfare theorem (Casella, NBER w9982): in any two-issue model with heterogeneous intensities, storable votes strictly improve expected utilitarian welfare vs. one-vote-per-issue, and the equilibrium banking strategy is computable in closed form.
- All vote-bank balances live in a public Merkle accumulator; spending requires a zero-knowledge proof of "I had ≥ s_t votes."

## Why it lands (Orbital filter)
Every DAO voter has felt "I don't care about this but I do care about the next one" — banking your vote for the issue you actually care about is universally intuitive and the welfare theorem is rigorous.

## Future utility
- 1 yr: DAO governance for treasuries with many small proposals (Optimism, Arbitrum grants).
- 3 yr: cooperative housing, condo boards, union locals.
- 5 yr: shareholder voting where institutional holders genuinely engage on issues that matter.

## Business model
- License the contract suite to DAOs at $2k/month flat per deployment.
- Optional 0.10% take rate on any treasury action approved via storable votes.
- Or pure public-goods deployment funded by quadratic funding.

## Sponsor / track fit
Overall. Pattern-match for Optimism Collective, Arbitrum DAO. Robinhood for shareholder-vote experiments on tokenized equities.

## 3-week MVP scope
- Vote-bank accumulator (Merkle) + ZK spend proof in Stylus.
- Demo DAO with 10 sample proposals over 8 weeks.
- Front-end "skip / spend N" slider.

## Risks
- Whales hoard and dominate a single critical issue (mitigate with per-issue caps).
- ZK-proof gas cost if banking proofs are submitted on-chain (use Lagrange coprocessor).
- Complexity of strategic banking confuses casual voters.

## Sources
- Casella, *Storable Votes*, NBER w9982 — https://www.nber.org/papers/w9982
- Casella, *Storable Votes* (book) — https://global.oup.com/academic/product/storable-votes-9780195309089
- Casella & Macé, *Does Vote Trading Improve Welfare?* — https://www.annualreviews.org/doi/10.1146/annurev-economics-080620-091514
