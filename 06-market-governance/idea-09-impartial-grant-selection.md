# Idea 09: Impartial Grant Selection — Reviewers Can't Vote for Themselves

## Pitch
*"Researchers grade each other's grants. The math guarantees you can't help your own."*

## What it is
A grant-selection contract for DAOs where applicants are *also* the reviewers, and the mechanism is *impartial*: provably, no reviewer's own grading can change their own probability of being funded. Combines the Holzman-Moulin "impartial peer selection" mechanism with on-chain enforcement.

## How it works
- Each applicant submits a grant proposal and is assigned `k` other proposals to grade.
- Selection mechanism (Holzman-Moulin "Permutation"): randomly partition applicants into clusters of size `m`; each cluster's grades select winners *outside* the cluster. Mathematically, no applicant's grade affects whether *they* are selected.
- ZK enforcement: grades and partitioning are committed in a Merkle root; selection runs in a Stylus contract that verifies the partition is independent of the applicant's own grades.
- Impartiality guarantee (Theorem 1, Holzman-Moulin 2013): the mechanism is the unique anonymous, monotone, impartial rule for top-k selection.

## Why it lands (Orbital filter)
"The reviewer pool is the applicant pool — and the math makes self-promotion mechanically impossible" lands instantly to anyone who has been on a peer-review committee.

## Future utility
- 1 yr: DAO grant programs (Optimism RetroPGF reviewer rounds, Gitcoin community review).
- 3 yr: academic grant agencies (NSF, ERC) pilot impartial selection.
- 5 yr: replaces self-conflicted committees in foundation funding, prize selection, awards.

## Business model
- 3% protocol fee on grant amounts allocated via the mechanism.
- Whitelabel "Impartial Selection as a Service" for foundations at $20k/round.
- Optional governance token over kernel parameters.

## Sponsor / track fit
Overall. Direct fit for Optimism Collective, Gitcoin, any foundation track.

## 3-week MVP scope
- Partition + scoring contract in Stylus.
- Reviewer UI with hidden assignments.
- End-to-end test with 30 applicants, 5 winners, simulated self-promotion attempts → shows mechanism rejects them.

## Risks
- Coalitional gaming across clusters (mitigate with multiple rounds of repartitioning).
- Reviewer effort calibration — grades may be lazy if reviewers aren't selected from grades.
- Cold-start cluster size sensitivity.

## Sources
- Holzman & Moulin, *Impartial Nominations for a Prize* (Econometrica 2013) — https://onlinelibrary.wiley.com/doi/10.3982/ECTA10523
- Fischer & Klimm, *Optimal Impartial Selection* (SODA 2014) — https://arxiv.org/abs/1305.4972
- Aziz et al., *Strategyproof Peer Selection* (AAAI 2016) — https://arxiv.org/abs/1604.03632
