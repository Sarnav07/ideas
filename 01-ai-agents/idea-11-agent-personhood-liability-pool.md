# Idea 11: Agent Personhood Liability Pool — "AI With a Human Co-Signer"

## Pitch
*"Every AI agent has one anonymous human soul behind it. Default — and the soul gets banned forever."*

## What it is
Every AI agent on the network must bond itself against exactly one proof-of-personhood nullifier (World ID, zkPassport, Anon Aadhaar). The human is anonymous, but the *uniqueness* is enforced cryptographically. Bad agent behavior triggers a slash that *also* burns the human's personhood-bond — they can never re-register an agent under any pseudonym. Sybil-proof liability for the agent economy.

## How it works
- Operator registers an agent: posts a ZK proof of unique personhood (nullifier `N`) + USDC bond.
- ERC-8004 agent registry stores `(agent_id, nullifier, bond, reputation)`. Each nullifier can back at most one *active* agent.
- Victims of agent misbehavior file claims with evidence (zkTLS receipts, on-chain logs).
- Coverage pool insures the claim; if the dispute resolves against the agent, both the agent's bond and the human's personhood nullifier are added to a global blocklist.
- Anyone — every other agent operator on the network — can ZK-check incoming counterparty agents against the blocklist via a Lagrange ZK coprocessor query.

## Why it lands (Orbital filter)
"Anonymous agent operators with permanent reputation" sounds like a contradiction. It isn't, once the nullifier mechanic lands. Same shape as FRONTIER #10 (Anti-Sybil Personhood Bond), applied specifically to the agent economy. Pitch tested: "the human goes anonymous, the soul stays accountable."

## Future utility
**1 year:** First lending products that loan to agents without 200% collateral, because their human is bonded. **3 years:** Default personhood layer for ERC-8004 agent registries. **5 years:** Spec-extension into ERC-8004 itself (or successor) — every conforming agent registry checks the personhood bond.

## Business model
- 1.5% fee on bond posting + 10% of claim-resolved insurance pool payouts.
- Agent-economy 2027 forecast: **$8B → $3.5T by 2031** (CertiK, ChainUp). At 1% bonded penetration of even $50B = $500M bonded pool, 1.5% take = **$7.5M/year**.
- Personhood-blocklist queries as a paid coprocessor API ($0.001/query) — Lagrange revenue share.

## Sponsor / track fit
- **Best Agentic ($15K)** — clean ERC-8004 extension; new validator/reputation primitive.
- **Robinhood Chain ($30K)** — RH Chain needs sybil-resistant identity for tokenized stocks; this is the consumer-facing primitive.
- **Overall ($70K)** — "AI with a human co-signer" lands in 8 words.

## 3-week MVP scope
- ERC-8004 extension contract on Arbitrum: registry + nullifier-binding + blocklist.
- World ID / Anon Aadhaar verifier (use existing circom artifacts).
- Demo: two agents register; one misbehaves (drains a counterparty); claim fires; nullifier banned; the operator can't re-register a new agent under a different pseudonym.
- Frontend: agent profile page showing the bonded nullifier status (active / banned).

## Risks
- **Personhood-oracle dependence** — single-source nullifiers (World ID) have geographic gaps. Mitigation: support 3 PoP rails at register-time, require >=1 valid.
- **Bricking honest agents on false-positive disputes** — mitigation: dispute resolution layer with optimistic challenge window before nullifier-burn (7 days).
- **Privacy concerns about personhood orbs** — anonymity is preserved; the chain only sees nullifiers, never identity.

## Sources
- ERC-8004 — https://eips.ethereum.org/EIPS/eip-8004
- World ID proof of personhood — https://world.org/blog/world/proof-of-personhood-what-it-is-why-its-needed
- zkPassport — https://github.com/zkpassport/circuits
- Anon Aadhaar — https://github.com/anon-aadhaar/anon-aadhaar
- Decentralized Governance of AI Agents — https://arxiv.org/pdf/2412.17114
