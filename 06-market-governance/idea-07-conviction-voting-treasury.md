# Idea 07: Conviction Voting Treasury — No Deadlines, Just Pressure

## Pitch
*"Hold your vote longer, it counts more. The treasury drips to whatever's leading."*

## What it is
A continuous-time DAO treasury where every proposal accrues "conviction" proportional to how long token holders have staked their vote on it. When conviction crosses a dynamic threshold, the proposal auto-funds. No voting deadlines, no quorum theatre — just a continuous tug-of-war.

## How it works
- Each token holder allocates their stake across active proposals (or none).
- Conviction `C_p(t)` evolves as `dC/dt = α(s_p(t) − C_p(t))`, where `s_p(t)` is current stake on proposal `p`.
- Funding threshold `θ_p` scales with requested amount and treasury balance: `θ_p ∝ requested / (1 − requested/treasury)²`.
- When `C_p(t) ≥ θ_p`, the proposal auto-executes and treasury sends the funds.
- Withdrawing your stake makes conviction decay; the protocol favors *persistent* preferences over flash mobs.

## Why it lands (Orbital filter)
"There are no voting deadlines, only how long you hold your vote" inverts the entire DAO governance loop in one sentence.

## Future utility
- 1 yr: Commons Stack and 1Hive variants get a clean Stylus implementation.
- 3 yr: open-source maintainer compensation (every PR is a proposal).
- 5 yr: protocol fee distribution in real time.

## Business model
- 2% treasury skim on every funded proposal → protocol DAO.
- Licensing to mid-sized DAOs at $5k/month.
- At $100M treasury with 20% annual distribution, that's $400k/yr.

## Sponsor / track fit
Overall. Strong fit for any DAO-track sponsor. Arbitrum Stylus for continuous-time integral on-chain.

## 3-week MVP scope
- Conviction integral approximated as block-wise exponential moving average.
- Stylus implementation with auto-execute hook.
- Demo with three live proposals competing for a $10k test treasury.

## Risks
- Whale-dominated conviction (mitigate with √-token weighting → quadratic conviction).
- Threshold tuning: too low → spammy funding; too high → nothing passes.
- Front-running auto-execute calls (use commit-reveal).

## Sources
- Emmett, *Conviction Voting: A Novel Continuous Decision Making Alternative* — https://medium.com/commonsstack/conviction-voting-a-novel-continuous-decision-making-alternative-to-governance-aa746cfb9475
- 1Hive Gardens implementation — https://1hive.gitbook.io/gardens/
- Commons Stack token engineering — https://commonsstack.org/research
