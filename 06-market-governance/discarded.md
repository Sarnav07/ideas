# Discarded — Markets & Governance

Ideas considered and cut from the final 10. Each lists *why* — usually pitch failure, redundancy with another idea, or insufficient mechanism rigor.

---

## Cut: MACI-only Anonymous Voting
**Cut reason:** Pitch ("anonymous voting on-chain") is solid but already shipping (clr.fund, Privacy & Scaling Explorations). Mechanism is well-known crypto, not novel social choice. Would belong in Category 04 (ZK/Privacy) anyway.

## Cut: Burn-Your-Vote Receipt-Free Voting (IACR 2025/1022)
**Cut reason:** Fresh paper but pitch overlaps MACI's domain — voters can't prove how they voted. Pure crypto primitive, not a market/governance design. Goes to Category 04 or 05.

## Cut: Liquid Democracy with Anonymous + Copy-Robust Delegation (arXiv 2307.01174)
**Cut reason:** Strong paper but the pitch ("delegate your vote, but anonymously, and the system handles delegation cycles") needs a three-beat explanation. Fails Orbital filter for cold-pitch impact. Storable Votes (#5) covers the same "delegate intensity" intuition with a sharper pitch.

## Cut: Top-Trading-Cycles for Token Allocation
**Cut reason:** Roth-Sönmez TTC is beautiful for indivisible-good exchange but the use case in DAO context ("swap your DAO seat for another's") is too niche to motivate a 15-word pitch. Pseudo-market (#10) subsumes most TTC use cases.

## Cut: All-Pay Auctions for Blockspace (Tullock contest)
**Cut reason:** Already adjacent to existing fee markets (EIP-1559 variants). Pitch "every bidder pays even if they lose" lands but is too close to existing MEV-burn discussions. Better at Crypto Primitives if at all.

## Cut: Crémer-McLean Full Surplus Extraction
**Cut reason:** Mechanism is elegant (extract 100% of surplus under correlated valuations) but the assumption of common-prior correlated types is fragile in practice. Hard to ship a believable MVP that handles uncorrelated edge case.

## Cut: Bulow-Klemperer Auction Recruitment
**Cut reason:** Classical result is "one more bidder beats any reserve price" — beautiful theorem, but the pitch is hard to make Orbital-shaped without an existing auction context. Belongs as a feature of #3 or #10 if anywhere.

## Cut: Decision Markets (standalone)
**Cut reason:** Subsumed by Futarchy (#4), which is decision markets *with* welfare aggregation. Standalone decision markets pitch is weaker.

## Cut: Continuous Double Auction (Smith 1962) on-chain
**Cut reason:** CDAs are the *default* exchange mechanism. Pitch fails because there's no inversion — readers go "that's just how exchanges work." Frequent batch auctions (below) tried to fix this but also got cut.

## Cut: Frequent Batch Auctions (Budish-Cramton-Shim)
**Cut reason:** Strong mechanism for MEV mitigation but the pitch ("auctions every 250ms, no latency racing") fits better as a sequencer/MEV defense (Category 04 or Crypto Primitives) than as info-finance.

## Cut: Combinatorial / VCG on-chain
**Cut reason:** VCG is computationally infeasible for >5–10 items; the on-chain implementation story collapses. Pseudo-market (#10) is the on-chain-feasible version of the same intuition.

## Cut: Posted-Price Prophet Mechanisms
**Cut reason:** Elegant CS theory (1/2 vs. optimal) but pitch is too academic. Failed Orbital filter at the cold-read stage.

## Cut: Robust Mechanism Design (Bergemann-Morris)
**Cut reason:** Meta-result, not a concrete product. Influences how *every* mechanism in the set should be evaluated; not itself a buildable demo.

## Cut: Mussa-Rosen Screening Menus
**Cut reason:** Classical price-discrimination; doesn't fit the "Orbital paradox" pitch shape. Could augment a lending or subscription product but not standalone.

## Cut: Multiverse Finance extension to Governance
**Cut reason:** Multiverse Lending is in FRONTIER #2 (DeFi). Extending it to conditional governance ("vote conditional on Trump winning") is interesting but feels like a feature of Futarchy rather than its own idea.

## Cut: Continuous-outcome CLMSR variants beyond Distribution Markets
**Cut reason:** Distribution Markets (#3) already ships the cleanest CLMSR variant; further variants don't add Orbital-shaped pitch differentiation.

## Cut: pm-AMM extensions
**Cut reason:** Niche prediction-market AMM tweaks; no Orbital-shaped pitch surfaced after a hard look. Live infrastructure (Polymarket) already covers this.

## Cut: Opportunity Markets (Paradigm 2025)
**Cut reason:** Strong paper but pitch is "markets for opportunities" which needs too much context to land. Adjacent to Futarchy; folded into #4.

## Cut: Deferred-Acceptance Clock Auctions (Milgrom-Segal FCC)
**Cut reason:** Beautiful mechanism for radio-spectrum allocation but the on-chain pitch doesn't have a sticky inversion. Real-World category would be a better fit if the spectrum-allocation angle were pursued.

## Cut: Bayesian Truth Serum Standalone Oracles
**Cut reason:** BTS is the math under Self-Resolving Prediction Market (#1). Standalone "BTS as oracle" is weaker as a separate idea.
