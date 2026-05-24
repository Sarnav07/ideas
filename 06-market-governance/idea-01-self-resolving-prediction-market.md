# Idea 01: Self-Resolving Prediction Market

## Pitch
*"Polymarket settles itself. No oracle. Just math."*

## What it is
A prediction market that resolves unverifiable or subjective claims without ever calling an external oracle, UMA dispute, or human juror. Sequential reporters are scored against the *next* reporter's prediction, and a Bayesian Truth Serum payoff makes honest reporting the unique Bayesian Nash equilibrium. The market halts on an α-coin flip and pays cross-entropy distance.

## How it works
- Open a market on any proposition (verifiable or not).
- Traders report a probability `p_i`; their score is the log-loss against `p_{i+1}`, the next reporter's belief, plus a Prelec-style Bayesian Truth Serum surprise term that rewards answers more common in the population than predicted.
- After each report, an α-weighted coin flip decides whether the market continues or halts; on halt, accumulated cross-entropy scores settle the payouts.
- Honesty dominates because mis-reporting reduces your expected log-score against the next informed trader, and BTS surprise rewards beliefs the crowd under-predicts.

## Why it lands (Orbital filter)
"A market that settles itself without an oracle" sounds impossible to anyone who has read a Polymarket UMA-dispute story; the BTS-plus-α-stopping construction makes the impossible concrete.

## Future utility
- 1 yr: subjective markets (will this paper be cited 100×, is candidate X actually corrupt) that currently die at the oracle step.
- 3 yr: replaces UMA / Reality.eth for the long-tail of unfilable claims.
- 5 yr: every reputation, review, and forecasting product runs on self-resolving rails.

## Business model
- 0.30% per trade routed to protocol.
- 1.0% of payouts at resolution.
- At $200M monthly volume the protocol clears ~$8.4M/yr without ever paying an oracle fee.

## Sponsor / track fit
Overall (Paradigm-adjacent info-finance pitch). Robinhood track for "markets on anything." Lagrange ZK-coprocessor for verifiable score aggregation.

## 3-week MVP scope
- LMSR market maker in Stylus.
- Sequential reporter contract with BTS scoring and α-coin halt.
- Front-end demo on three live unverifiable claims (e.g., "Will Sam Altman still run OpenAI in 12 months").

## Risks
- Collusion across consecutive reporters; mitigate with rate limits and stake bonds.
- α-tuning: small α gives noisy halts, large α gives unrewarding length.
- BTS truthfulness assumes common-prior; partial-prior settings have weaker guarantees.

## Sources
- Srinivasan et al., *Self-Resolving Prediction Markets for Unverifiable Outcomes* — https://arxiv.org/abs/2306.04305
- Prelec, *A Bayesian Truth Serum for Subjective Data*, Science 2004 — https://www.science.org/doi/10.1126/science.1102081
- Buterin, *From Prediction Markets to Info Finance* — https://vitalik.eth.limo/general/2024/11/09/infofinance.html
