# Idea 08: Sortition Jury — Random-Ballot DAO Decisions

## Pitch
*"Forget the vote. The chain rolls dice and picks the winning policy."*

## What it is
A DAO governance contract that doesn't tally votes — instead, it samples a *random* token holder (weighted by stake) and lets their single preference be the outcome. This is the centuries-old practice of sortition, with a verifiable-random-function as the lottery wheel. Result: strategy-proof in the strongest sense, no whale dominance unless they hold near-100%.

## How it works
- Voters submit signed preference ballots over candidate policies.
- At resolution, a drand BLS signature seeds a stake-weighted VRF.
- VRF selects one ballot; that ballot's first choice executes.
- Gibbard's theorem corollary: under random-ballot, telling the truth is a (weakly) dominant strategy — there's no point inflating preferences you don't hold.
- Stoyanovich-Procaccia "impartial culture" guarantee: ex-ante, every voter's expected outcome utility ≥ that of any pure-majority rule under uniform priors.

## Why it lands (Orbital filter)
"The chain just rolls dice" sounds insane until you realize majority rule is *also* manipulable, expensive, and slow — and sortition is the only known strategy-proof, dictator-free rule.

## Future utility
- 1 yr: small treasury allocations, grant-committee selection, dispute-jury picks.
- 3 yr: Kleros/Aragon Court replacement; randomly seated juries that can't be bribed in advance.
- 5 yr: citizen assemblies, participatory budgeting, even legislative branches.

## Business model
- 0.5% of any treasury allocation routed through sortition.
- Bundled service for tokenized HOAs / co-ops at $1k/month.
- Sortition-as-a-service VRF API.

## Sponsor / track fit
Overall. Specifically fits any "anti-whale" governance sponsor. Drand integration shows live verifiable randomness.

## 3-week MVP scope
- Stake-weighted VRF using drand + on-chain commitment.
- Demo DAO that picks one of three policies via sortition each month.
- Comparison dashboard vs. simulated majority vote outcomes.

## Risks
- High variance in single-shot outcomes (smooth with K-of-N sampling).
- Buying off the selected ballot post-reveal (use commit-reveal ballots, force selection-before-reveal).
- Cultural resistance — "but my vote didn't count" is the entire point.

## Sources
- Stone, *Why Lotteries Are Just* (2011) — https://global.oup.com/academic/product/the-luck-of-the-draw-9780199756100
- Procaccia, *Cake Cutting: Not Just Child's Play* (CACM) — https://cacm.acm.org/research/cake-cutting-algorithms/
- Cortés-Cediel et al., *Sortition Algorithms* (2024 survey) — https://arxiv.org/abs/2406.14025
