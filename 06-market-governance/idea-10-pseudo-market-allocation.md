# Idea 10: Hylland-Zeckhauser Pseudo-Market — Allocate Without Money

## Pitch
*"Give everyone fake budgets. The market matches resources to who values them most."*

## What it is
A DAO allocation contract that hands every member an equal endowment of "pseudo-tokens" (non-tradeable, non-transferable), then runs a Walrasian market over indivisible goods (grants, conference slots, fellowships, validator seats). Members buy probability shares; prices clear at unit supply. Result: Pareto-efficient and envy-free, *with no actual money involved*.

## How it works
- Each member receives 1.0 pseudo-budget.
- Goods = lottery shares over indivisible items (e.g., 100 grant slots, 50 validator seats).
- Tâtonnement procedure: pseudo-prices `p_g` adjust until aggregate demand = supply for every good.
- Hylland-Zeckhauser theorem (Econometrica 1979): there exists a competitive equilibrium that is Pareto-efficient over expected utility *and* envy-free.
- New 2024 AAMAS result (Peters et al.): the HZ equilibrium is approximable in polynomial time, making it on-chain-feasible.

## Why it lands (Orbital filter)
"A market with no money that's still Pareto-efficient" is the kind of paradox that breaks the brain — money was supposed to be what made markets work.

## Future utility
- 1 yr: DAO grant rounds, conference-slot allocation (Devcon ticket lottery), retreat selection.
- 3 yr: validator-seat lotteries, gas-priority allocation, public-resource scheduling.
- 5 yr: organ matching, school choice, fellowship boards — anywhere money allocation is morally unacceptable.

## Business model
- $5k/month flat fee per organization deployment.
- 1% of any *post*-allocation transaction (resale, secondary).
- Optional consulting on endowment design.

## Sponsor / track fit
Overall. Particularly Optimism Collective, ETHGlobal selection rounds, any foundation. Lagrange coprocessor for off-chain tâtonnement.

## 3-week MVP scope
- Tâtonnement solver in Stylus (or Lagrange coprocessor for heavy lift).
- Demo allocation: 100 simulated DAO members, 30 grant slots.
- Comparison dashboard: random vs. quadratic vote vs. HZ.

## Risks
- Tâtonnement convergence — pathological preference profiles may not converge cleanly.
- Endowment equality assumption can be politically contested.
- Computational cost on large item sets (use off-chain solver + ZK verification).

## Sources
- Hylland & Zeckhauser, *The Efficient Allocation of Individuals to Positions* (JPE 1979) — https://www.jstor.org/stable/1832194
- Peters et al., *Approximating the Hylland-Zeckhauser Mechanism*, AAMAS 2024 — https://arxiv.org/abs/2402.05236
- Echenique, Miralles, Zhang, *Constrained Pseudo-Market Equilibrium* (AER 2021) — https://www.aeaweb.org/articles?id=10.1257/aer.20191336
