# Idea 12: TEE-Attested AI Court — "An AI Judge Whose Verdict Is Binding Because the Code Cannot Lie"

## Pitch
*"A robot judge whose ruling is binding because the silicon proves the code didn't change."*

## What it is
A binary dispute resolver running inside an Intel TDX enclave. The judge's code (a fine-tuned LLM with a fixed prompt and tool set) is committed to a measurement hash; the enclave signs each ruling with a key bound to that measurement. Smart contracts that opt into the court accept a ruling iff the attestation verifies. The judge's behavior is provable in a way Kleros human jurors never can be.

## How it works
- Judge code (LLM + scoring prompt + evidence-fetching tool set) is published; Marlin Oyster builds a reproducible enclave image with a deterministic measurement hash `M`.
- An attestation chain (Marlin / Phala) publishes the enclave's signing pubkey bound to `M`.
- Parties to a dispute post evidence + funds into an arbitration contract. Contract waits for the judge enclave to emit `Verdict(disputeId, winner, signature)`.
- Stylus verifier checks: enclave attestation valid, signature over verdict valid, measurement matches the pre-agreed code commit. Funds release.
- ERC-8004 reputation tracks reversal rate (if humans audit and overturn a verdict, the enclave's measurement is downgraded).

## Why it lands (Orbital filter)
"AI judge" sounds horrifying. "AI judge whose code is cryptographically frozen and whose ruling is binding by attestation" inverts that — the listener realizes this is *more* accountable than a human judge: the code is public, the inputs are public, the ruling is signed. Kleros took 6 years to dispute one case; this takes 30 seconds.

## Future utility
**1 year:** Small-stakes consumer disputes (refund disputes on tokenized stocks, "was this NFT delivered?"). **3 years:** B2B agent-to-agent SLA disputes; default into x402 commerce. **5 years:** Specialized judges per domain (a contract-law-trained variant for DeFi, a creative-arbitration variant for content marketplaces).

## Business model
- $5–50 per case (volume-based) + 1% of disputed amount.
- ODR (online dispute resolution) market 2026: **$1.5B globally** (eBay alone runs 60M disputes/year). Crypto-native disputes are 0.1% of that today, growing. Capture 10% of crypto disputes at $5 average = **$3M starter**.
- Premium tier: enterprises can self-host the enclave (open-source judge code) under a license.

## Sponsor / track fit
- **Best Agentic ($15K)** — direct agent-economy infrastructure.
- **Overall ($70K)** — TEE + AI + dispute resolution is fresh; sticky pitch.
- **Stylus showcase** — attestation verification (DCAP-attestation) is Stylus-canonical.

## 3-week MVP scope
- Marlin Oyster CVM with a small Claude-class judge model + fixed system prompt + Tenderly-fork evidence-fetcher.
- Stylus DCAP attestation verifier (port existing reference).
- Demo: an agent claims another agent failed to deliver a service; judge enclave reviews the on-chain evidence; rules; verdict executes on Arbitrum.
- Frontend: dispute filing form → live verdict.

## Risks
- **Enclave-side-channel attacks** — Intel SGX/TDX have a long bug history. Mitigation: dual-attestation (TDX + SEV-SNP).
- **Judge bias** — LLM verdicts can be inconsistent. Mitigation: judge runs 5 inference passes per dispute; majority wins; the 5 hashes anchored on-chain for audit.
- **Legal recognition** — verdicts are not court-of-law binding. Frame as private-contract arbitration only; out of scope for regulated finance v1.

## Sources
- Marlin Oyster CVM — https://docs.marlin.org/oyster/protocol/cvm/
- Phala TEE AI Agents — https://phala.com/solutions/ai-agents
- *Optimistic TEE-Rollups for AI Inference* — https://arxiv.org/pdf/2512.20176
- DAO-AI: Agentic AI in Decentralized Governance — https://arxiv.org/abs/2510.21117
