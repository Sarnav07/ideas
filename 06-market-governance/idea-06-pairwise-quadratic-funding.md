# Idea 06: Pairwise Quadratic Funding — Collusion-Proof Public Goods

## Pitch
*"Quadratic funding, but a sybil's matched grant goes to zero if it colludes."*

## What it is
A funding mechanism that takes the original Buterin-Hitzig-Weyl quadratic funding formula and replaces the sum-of-square-roots with a *pairwise* discount kernel — each pair of donors' contributions is discounted by their correlation. Result: a perfect sybil or coalition is mathematically demoted to a single donor.

## How it works
- Standard QF subsidy = `(Σ √c_i)² − Σ c_i`.
- Pairwise QF subsidy = `Σ_{i<j} K(d_ij) · √(c_i · c_j)`, where `K(d_ij)` is a kernel decreasing in donor correlation `d_ij`.
- Correlation is computed across the entire grant round: two addresses funding identical projects with identical timing get `K → 0`.
- Math result (Miller, Weyl, Erichsen): pairwise QF retains the welfare-maximizing property of QF while bounding the gain from collusion to a constant independent of coalition size.

## Why it lands (Orbital filter)
Anyone who has watched a Gitcoin round get sybil-attacked feels the pain immediately; "the kernel zeroes out colluders" is the Orbital-style mechanical fix.

## Future utility
- 1 yr: Gitcoin, Optimism RetroPGF, Octant.
- 3 yr: national-scale participatory budgeting (Taiwan, Boulder CO experiments).
- 5 yr: replaces grant committees for foundation funding.

## Business model
- 5% protocol fee on matching pool.
- $50k–$500k per round at Gitcoin-scale ($10M matching pools).
- Optional governance token captures kernel-parameter decisions.

## Sponsor / track fit
Overall. Direct fit for Gitcoin, Optimism, any public-goods sponsor. Lagrange coprocessor for cross-round correlation queries.

## 3-week MVP scope
- Pairwise-QF scoring contract in Stylus.
- Lagrange ZK SQL coprocessor that computes pairwise correlation across donor history.
- Demo round with 200 simulated donors (50 honest, 150 colluding clusters) → show match converges.

## Risks
- Correlation kernel calibration; too aggressive penalizes genuine community alignment.
- Privacy: pairwise correlation requires donation graphs (mitigate with anonymous credentials).
- Game-theoretic: sophisticated attackers may anti-correlate to game the kernel.

## Sources
- Buterin, Hitzig, Weyl, *Liberal Radicalism* — https://arxiv.org/abs/1809.06421
- Miller, Weyl, *Pairwise Quadratic Funding* (2022) — https://www.radicalxchange.org/media/papers/Pairwise-Quadratic-Funding.pdf
- Optimism RetroPGF analyses — https://community.optimism.io/citizens-house/retro-funding-overview
