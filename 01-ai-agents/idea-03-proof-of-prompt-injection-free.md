# Idea 03: Proof-of-Prompt-Injection-Free Agent

## Pitch
*"Prove your AI agent followed orders — even after it sees a malicious email."*

## What it is
A zk-attention circuit that produces, alongside an agent's output, a cryptographic proof that the model's attention from **system-prompt tokens** to the output dominated the attention from **untrusted user-input tokens**. Insurers and enterprises pay out only when the proof verifies. This is the cryptographic primitive that makes AI agents insurable.

## How it works
- Wrap the agent's transformer call with EZKL/DeepProve zkML.
- The circuit computes, per output token, the attention-weight ratio `A(sys → out_t) / A(untrusted → out_t)`.
- The proof asserts `min_t (ratio) ≥ θ` where `θ` is publicly chosen by the insurance contract.
- On verify, the bonded coverage pool pays out for any post-incident damage if the proof fails to verify (or doesn't exist) on the offending call.
- ERC-8004 reputation registry tags agents with their lifetime injection-proof success rate.

## Why it lands (Orbital filter)
Cyber-insurers in 2026 *explicitly exclude prompt injection from policies* (search: "AI exclusion endorsement Lloyd's"). Every Fortune 500 enterprise has frozen agent rollouts because of this. The pitch is the missing primitive — visceral and urgent.

## Future utility
**1 year:** First enterprise pilots — Salesforce, ServiceNow agents covered by a bonded "proof or pay" insurer. **3 years:** Standard rider on E&O policies; auditors require it. **5 years:** Default circuit fused into every production agent runtime.

## Business model
- Insurance premium take: 10% (industry comp: Nexus Mutual, Lloyd's).
- Cyber-insurance TAM 2026: **$22B**. AI-agent exclusion is currently the #1 carved-out risk; if 5% migrates onto cryptographic enforcement: **$1.1B premium pool, $110M annual fees**.
- Secondary: zk-proving as a service — $0.05 per inference proof, billed to enterprise agent operators.

## Sponsor / track fit
- **Best Agentic ($15K)** — directly answers ERC-8004 validation registry's open question.
- **Overall ($70K)** — enterprise narrative; "we make AI agents insurable" is a board-room pitch.
- **Stylus showcase** — Stylus verifier for zk-attention proof.

## 3-week MVP scope
- A small transformer (DistilBERT, 6 layers) with EZKL-compiled attention circuit.
- Insurance Vault contract on Arbitrum: stake USDC, claim against agent address on injection.
- Test set: 50 known prompt-injection payloads (Greshake et al. corpus). Agent runs each; ones that pass proof get covered. Demo: an agent reads a poisoned email, refuses, posts a passing proof; another agent yields and the claim fires.
- Frontend dashboard: lifetime proof-pass rate per agent.

## Risks
- **Proving cost** — full-LLM attention proofs are seconds today via DeepProve-1; we use a smaller model for MVP.
- **Threshold gaming** — adversaries could craft inputs that barely satisfy ratio. Mitigation: threshold publicly auctioned per coverage policy.
- **False sense of safety** — math proves attention dominance, not semantic correctness. Limit claims accordingly in disclaimers.

## Sources
- Survey of ZK-verifiable ML — https://arxiv.org/pdf/2502.18535
- Lagrange DeepProve-1 — https://lagrange.dev/blog/deepprove-1
- EZKL toolkit — https://github.com/zkonduit/ezkl
- ERC-8004 — https://eips.ethereum.org/EIPS/eip-8004
