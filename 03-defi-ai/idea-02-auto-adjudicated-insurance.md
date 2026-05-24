# Idea 02: ClaimGPT — Auto-Adjudicated Insurance

## Pitch
*"File a claim. An AI judge reads it. Money hits your wallet in 30 seconds."*

## What it is
A parametric+narrative insurance pool where claims are auto-adjudicated by an LLM running inside a TEE. The model reads the claim form, cross-references oracle data (flight status, weather, on-chain events), and signs an approve/deny with a TDX attestation. Approved claims auto-pay; denials can appeal to a human jury (slashing the model bond if reversed).

## How it works
1. Policy NFT specifies (peril, trigger payload schema, payout). Underwriters provide a capital pool.
2. Claimant submits structured + free-text evidence. A model running in Intel TDX (Marlin Oyster) outputs `{approve, amount, reasoning_hash}` signed by the TDX-attested key.
3. Stylus verifier checks attestation, releases payout from pool.
4. Appeals: human jury (Kleros-style) overturns ≥X% → model operator slashed proportionally.

## Why it lands (Orbital filter)
Insurance is the only industry where "the adjuster takes 3 months and denies 40%" is normalized. "LLM adjuster paying out in 30 seconds with cryptographic proof of fairness" inverts the entire claims process.

## Future utility
1-yr: travel delay, drone damage, gig-worker income protection. 3-yr: small-business interruption, freelance escrow. 5-yr: any claim a human reads can be adjudicated this way; reinsurance markets price models like underwriters.

## Business model
8% premium spread + 2% model-operator fee. At $10M annual GWP, ~$1M revenue. Model operator earns from approving accurately (low appeal-overturn rate = larger bond capacity).

## Sponsor / track fit
Best Agentic AI $15K + Overall $70K. Strong DePIN + agent-economy angle. Marlin Oyster + Phala TEE bounties direct fit. Distinct from FRONTIER #24 (Parametric Cat Pool) — that needs an oracle trigger; this handles unstructured narrative claims.

## 3-week MVP scope
- Week 1: Stylus pool contract + Marlin Oyster TDX verifier
- Week 2: GPT-4o-class model adjudicating travel-delay claims, with Chainlink flight oracle as ground-truth fallback
- Week 3: live demo — submit a synthetic delayed-flight claim with screenshots, get paid in 30s, jury appeal UI

## Risks
- LLM hallucination on edge cases. Mitigated by jury appeal + bond slashing + only approving claims within underwriter-set guardrails.
- Adversarial claim text (prompt injection). Mitigated by structured input parsing + FRONTIER #8 attention-mask techniques.
- Reinsurers may not back LLM judges initially. Start with pools where median claim < $500.

## Sources
- [Marlin Oyster CVM docs](https://docs.marlin.org/oyster/protocol/cvm/)
- [Kleros arbitration docs](https://docs.kleros.io/)
- [Phala AI Agent Contract](https://phala.com/posts/introducing-aiagent-contract-for-smart-agents)
- [Lemonade AI Jim claims engine (TradFi precedent)](https://www.lemonade.com/blog/lemonades-ai/)
