# Idea 14: ProofEscrow — AI Agent Releases Funds on Verified Milestones

## Pitch
*"Escrow held by an AI. It looks at the proof, reads the contract, releases the money."*

## What it is
An escrow contract where release conditions are written in natural language and resolved by an LLM agent (in TDX) reading multimodal milestone proofs — vision (delivery photos, completed UI screenshots), zkTLS (API endpoints showing milestone state), GitHub commits, signed third-party attestations. Disputes appeal to a Kleros jury.

## How it works
1. Buyer + seller agree on escrow with natural-language milestones, lock funds.
2. Seller submits milestone proof bundle (images, URLs, hashes, on-chain pointers).
3. Agent (TDX-attested) reads contract + evidence, outputs `{release_amount, justification_hash, attestation}`.
4. Stylus verifier checks attestation, releases funds. Disputes within X days route to Kleros; if jury reverses, agent operator slashed proportional to error.

## Why it lands (Orbital filter)
Escrow today needs either oracle-feed-shaped milestones (parametric) or a human arbiter (Kleros, Centaur). "AI reads the actual delivery photos and the actual contract" is the productivity unlock — Upwork+Fiverr+freelance escrow gets a layer that resolves in seconds, not weeks.

## Future utility
1-yr: freelance crypto payments, NFT-art commission escrow. 3-yr: international B2B service contracts. 5-yr: $1T+ global trade-finance escrow runs on agent rails.

## Business model
1-2% escrow fee + 0.5% AI adjudication fee. At $50M annual escrow volume, ~$1.25M revenue. Reputation-graded agent operators take 40%.

## Sponsor / track fit
Best Agentic AI $15K + Real-World + Overall $70K. Kustodia (prior Open House winner) is the human-arbiter precedent; this inverts to AI-arbiter. Phala/Marlin TEE + Kleros + ERC-8004 stack.

## 3-week MVP scope
- Week 1: Stylus escrow contract + Kleros appeal hook
- Week 2: GPT-4o-class agent in Marlin Oyster reading milestone bundles (image + zkTLS endpoint snapshot)
- Week 3: 3 demo escrows (UI design delivery, code-PR-merged milestone, physical product shipping proof), full settle + appeal demo

## Risks
- AI misreads ambiguous milestones. Mitigated by jury appeal + bond + low cap on auto-release per epoch.
- Prompt injection via milestone payload. Use FRONTIER #8 attention-mask techniques + strict schema for evidence.
- Cold-start trust. Bootstrap with whitelist agents (notable model providers) + low-stakes pilots.

## Sources
- [Kleros docs](https://docs.kleros.io/)
- [Kustodia escrow primer](https://kustodia.app/)
- [Marlin Oyster CVM](https://docs.marlin.org/oyster/protocol/cvm/)
- [Reclaim Protocol zkTLS](https://www.reclaimprotocol.org/)
