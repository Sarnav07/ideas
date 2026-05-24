# Idea 08: Proof-of-Inference Bond — "Drain the Bond If You Find a Wrong Answer"

## Pitch
*"Agents post a bond. Find an input where the agent's zkML proof is wrong — drain the bond, permissionlessly."*

## What it is
An agent registers with a bond and a published model commitment. For each user query, the agent must emit a Lagrange DeepProve zkML proof that the answer truly came from the committed model. *Anyone* who finds a query where the agent answered without a valid proof, or whose proof verifies but contradicts the committed model, can submit a counter-proof and drain the bond. No governance, no challenge period — algebraic key recovery in one block.

## How it works
- Agent registers `(model_commit, bond_address, tee_pubkey)` in ERC-8004 validation registry.
- Each call: agent returns `(answer, deepprove_proof)`. The proof asserts `answer = f(model_commit, query)`.
- A Stylus verifier contract validates the proof — if it fails, the call reverts and the agent's reputation slashes.
- Babylon-style EOTS scheme: the agent's signing key over each `(query, answer)` pair uses a deterministic nonce derived from the model commit. **Two contradictory answers for the same query = leaked private key = anyone drains the bond.**
- Slashing is permissionless and instant — exactly the Babylon BTC-staking pattern, applied to AI inference.

## Why it lands (Orbital filter)
"Lying to your AI doesn't punish your AI. Lying *as* your AI does." The pitch lands because the math removes the human arbiter — slashing fires *the second* an inconsistency surfaces, not weeks later through governance. Same primitive-inversion shape as FRONTIER #25 (EOTS validator), here applied to inference output.

## Future utility
**1 year:** Bounty hunters monitor every public agent for contradictions, like Etherscan watchers do today. **3 years:** Standard insurance underwriter requirement — agents must post a Proof-of-Inference bond to be insurable. **5 years:** Permissionless audit becomes free-market labour; bond markets price model reliability into yield curves.

## Business model
- 5% of slash proceeds go to the protocol (rest split: 80% finder, 15% bond burn).
- Inference Labs subnet projects ~$5B of inference-bond TVL by 2027 at 1% capture. 5% of slashed bonds (assume 2% annualized slash rate) = **~$5M/year**.
- Premium tier: agent-operator subscription for "monitored mode" alerting them to near-violations before a finder triggers slash.

## Sponsor / track fit
- **Best Agentic ($15K)** — direct ERC-8004 validation extension; canonical "verifiable agent" pitch.
- **Overall ($70K)** — pairs with Stylus showcase (EOTS verification + DeepProve verifier).
- **Stylus showcase** — permissionless slashing math is a Stylus killer demo (BLS12-381 + secp256k1 algebra).

## 3-week MVP scope
- Stylus contract: ERC-8004 validator + DeepProve verifier + EOTS key-extraction logic.
- Small CNN (MNIST classifier) as the committed model; agent answers digit classifications.
- Browser-based "finder" tool: feed an input, check inconsistency, submit counter-proof, drain bond.
- Demo: a malicious agent commits to model A but answers with model B → finder catches → bond drains in one Arbitrum block.

## Risks
- **DeepProve proof time** — seconds for CNN-class; minutes for LLM-class. MVP uses CNN; production needs DeepProve-1 GPU.
- **Front-running the finder** — solved by tlock-encrypting the counter-proof until inclusion.
- **False positives in EOTS recovery** — only fires on algebraically identical nonces; cryptographically tight.

## Sources
- Lagrange DeepProve-1 — https://lagrange.dev/blog/deepprove-1
- Inference Labs Subnet 2 — https://github.com/inference-labs-inc/subnet-2
- Babylon BTC Staking Litepaper (EOTS spec) — https://docs.babylonlabs.io/papers/btc_staking_litepaper(EN).pdf
- ERC-8004 validation registry — https://eips.ethereum.org/EIPS/eip-8004
