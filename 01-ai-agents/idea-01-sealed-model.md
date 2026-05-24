# Idea 01: Sealed Model — Witness-Encrypted AI Weights

## Pitch
*"The model decrypts itself only when its own output passes a public test."*

## What it is
Encrypted ML weights that sit on a public blob store and refuse to decrypt until the model proves — to a smart contract — that it scores above a threshold on a public test vector. The model is its own escrow. The buyer pays once, the seller delivers a ciphertext, and the chain decides whether the ciphertext was honest.

## How it works
- Seller commits to weights `W` and a benchmark predicate `P(output) = score ≥ τ`.
- Seller encrypts `W` under a **KZG witness-encryption** scheme to the predicate "Lagrange DeepProve zkML proof of `P` over a public test set verifies on-chain."
- Buyer pays into an Arbitrum escrow.
- Anyone can run an inference, produce the zkML proof, and post it. The verifier contract releases the witness, which is also the decryption key.
- If the model is fake, no proof exists and the funds never move; the encrypted blob is useless forever.

## Why it lands (Orbital filter)
Inverts every AI procurement story. The Pentagon, Boeing, and every Big Pharma R&D buyer asks the same question — "is this the model you said it was?" Witness encryption makes the *model itself* answer. The pitch breaks the listener's mental model of "escrow needs a third party."

## Future utility
**1–2 years:** Cryptographic model marketplace — sell fine-tuned LLMs without a single Hugging Face download leaking weights. **3–5 years:** Default delivery channel for any regulated ML procurement (defense, drug-discovery, fintech credit models). Replaces SOC-2-style "trust us" reports with mathematical settlement.

## Business model
- 0.5% take rate on each sealed model transaction (industry comp: marketplace SaaS ~3–10%, but ours is one-shot).
- ML model marketplace TAM in 2026: **$25–35B** (Hugging Face revenue run-rate, OpenAI fine-tune marketplace, Replicate). Capturing 1% of regulated subset (~$5B) = **$25M/year fee**.
- Tokenized governance over the verifier upgrade path (separate from take rate).

## Sponsor / track fit
- **Overall ($70K)** — first deployed witness-encryption + zkML composition; falsifiable benchmark ("verifier gas < 5M, proof time < 60s on Gemma3-class model").
- **Best Agentic ($15K)** — sealed model is the canonical primitive for agent capability delivery.
- **Stylus showcase** — pairing verifier (KZG witness opening) is a textbook Stylus accel case.

## 3-week MVP scope
- Stylus contract: KZG witness-encryption verifier + Lagrange DeepProve plonky3 verifier.
- Off-chain: encrypt a small CNN (CIFAR-10, ~100K params) under predicate "accuracy ≥ 0.85."
- Frontend: judge clicks "verify and decrypt," sees the cleartext weights download once the proof posts.
- Demo: a fake model with a fake claim — the buyer's funds stay locked; the weights remain unreadable.

## Risks
- **zkML proof cost** — Gemma3-scale proofs take minutes. MVP de-risks with a small CNN; production needs DeepProve-1 GPU pipeline.
- **Witness encryption recency** — production KZG WE libraries are still researchy; we ship our own Rust port of IACR 2024/264.
- **Adoption** — regulated AI buyers move slowly. Pitched as the "Spotify-for-models" cryptographic layer to soften.

## Sources
- Fleischhacker, Hall-Andersen, Simkin, *Extractable Witness Encryption for KZG Commitments* — https://eprint.iacr.org/2024/264
- Lagrange DeepProve roadmap — https://www.lagrange.dev/blog/lagranges-year-in-review-2025
- Lagrange DeepProve-1 announcement — https://lagrange.dev/blog/deepprove-1
- Survey of ZK-verifiable ML — https://arxiv.org/pdf/2502.18535
