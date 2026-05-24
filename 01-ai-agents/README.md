# Category 01 — AI Agents / Agentic AI (15 ideas)

15 Orbital-tier ideas for the Arbitrum Open House 2026 hackathon, in the AI / agentic-AI category.

**Filter applied:** every pitch ≤15 words must trigger *"wait, how is that possible?"* in a smart non-crypto listener — same shape as Orbital Pool's *"Uniswap is 1D, Curve is 2D, Orbital is N-D liquidity across N stablecoins."*

**Sponsor lanes targeted:** Overall ($70K) · Best Agentic ($15K) · Robinhood Chain ($30K reserved) · Stylus showcase.

---

## Idea index

| # | Name | Pitch (≤15 words) |
|---|---|---|
| 01 | [Sealed Model](idea-01-sealed-model.md) | The model decrypts itself only when its own output passes a public test. |
| 02 | [Inverse x402](idea-02-inverse-x402.md) | HTTP 402 in reverse — the API pays YOU to call it. |
| 03 | [Proof-of-Prompt-Injection-Free Agent](idea-03-proof-of-prompt-injection-free.md) | Prove your AI agent followed orders — even after it sees a malicious email. |
| 04 | [Witness-Encrypted Agent Wallet](idea-04-witness-encrypted-agent-wallet.md) | An AI agent wallet whose private key only exists if it does its job. |
| 05 | [Federated-Shapley Training Market](idea-05-federated-shapley-training-market.md) | Train one model with strangers. Each gets paid for the IQ points they added. |
| 06 | [ERC-7715 Wallet Marketplace](idea-06-erc7715-wallet-marketplace.md) | Rent your wallet to an AI for an hour, with math-bounded loss. |
| 07 | [Forecasting-Cohort Index](idea-07-forecasting-cohort-index.md) | The Vanguard fund of AI agents — buy the median LLM's market view in one click. |
| 08 | [Proof-of-Inference Bond](idea-08-proof-of-inference-bond.md) | Find an input the AI agent lied about — drain its bond, permissionlessly. |
| 09 | [Verifiable RLHF Market](idea-09-verifiable-rlhf-market.md) | Rate AI answers. Get paid the IQ points your rating added to the next checkpoint. |
| 10 | [MCP Server Yield Vault](idea-10-mcp-server-yield-vault.md) | MCP servers stake reputation. Each call pays them. Each wrong answer drains the bond. |
| 11 | [Agent Personhood Liability Pool](idea-11-agent-personhood-liability-pool.md) | Every AI has one anonymous human soul. Default — and that soul gets banned forever. |
| 12 | [TEE-Attested AI Court](idea-12-tee-attested-ai-court.md) | A robot judge whose ruling is binding because the silicon proves the code didn't change. |
| 13 | [Adversarial Subnet](idea-13-adversarial-subnet.md) | A market where attackers earn for breaking AI defenses, defenders earn for surviving. |
| 14 | [Watermark Royalty Rail](idea-14-watermark-royalty-rail.md) | Detect a watermark, claim a royalty. The chain decides who wrote the internet. |
| 15 | [Agent-to-Agent Trust Coprocessor](idea-15-agent-trust-coprocessor.md) | Two AI agents meet. In one query, one proves 10,000 deals with zero disputes. |

---

## Top-3 picks for this category

### #1 — Sealed Model (Idea 01)
**Why:** unmatched pitch shock value ("the model is its own escrow"). Composes two fresh primitives — KZG witness encryption (IACR 2024/264) and Lagrange DeepProve-1 zkML (2025). Stylus-killer demo (pairing verifier on BLS12-381). Speaks to a *real* Pentagon/Boeing/pharma problem with no current cryptographic solution. Single best Sealed-Model-class candidate to win Best Agentic outright.

### #2 — Witness-Encrypted Agent Wallet (Idea 04)
**Why:** "an AI agent wallet whose private key only exists if it does its job" is brain-breaking in 14 words. ERC-4337 + drand + signature-based witness encryption — three primitives, one canonical demo. Pairs naturally with RH Chain ($30K) since the demo flow is "agent earns by delivering, wallet drains automatically." Buildable in 3 weeks; clean stylus integration.

### #3 — Proof-of-Inference Bond (Idea 08)
**Why:** permissionless slashing (Babylon EOTS shape) applied to AI inference is unbuilt anywhere. Insurance/audit market crater right now: every enterprise AI deployment is paused on "how do we trust the model didn't drift?" This is the answer in one block. Combines all four Arbitrum levers: Stylus (algebraic key recovery), ERC-8004 (validation registry), x402 (per-inference billing), and Best Agentic narrative.

---

## Sponsor-track coverage

| Track | Strongest fit in this folder |
|---|---|
| **Best Agentic ($15K)** | #01 Sealed Model · #03 Prompt-Injection-Free · #04 WE Wallet · #08 Inference Bond · #10 MCP Yield Vault · #15 Trust Coprocessor |
| **Overall ($70K)** | #01 · #02 · #04 · #07 · #08 · #11 |
| **Robinhood Chain ($30K)** | #02 Inverse x402 · #06 ERC-7715 Marketplace · #07 Cohort Index · #11 Personhood Pool |
| **Stylus showcase** | #01 (KZG WE) · #03 (zk-attention verifier) · #08 (EOTS key recovery) · #15 (coprocessor SQL verifier) |

---

## Build-difficulty rank

| Tier | Ideas |
|---|---|
| ✅ Easy (one strong dev, 3 weeks) | 02, 04, 06, 10, 11, 13 |
| ⚠️ Medium (needs zkML or TEE specialist) | 01, 03, 07, 08, 09, 12, 15 |
| 🔴 Hard (research-grade dependencies) | 14 (watermark robustness still maturing); 05 (federated infra heavy) |

---

## Where these came from

- Ideas 01-07: ports of FRONTIER.md #6, #7, #8, #9, #20, #21, #22 — the AI-category survivors of the 30-pitch shortlist.
- Ideas 08-15: hunted fresh against 2025–2026 primitives (Bittensor zkML, MCP, ERC-8004, watermarking, TEE-AI courts, adversarial subnets, trust coprocessors).
- Discarded candidates with cut reasons in `discarded.md`.
