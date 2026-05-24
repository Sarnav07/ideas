# Category 04 — Discarded ZK/Privacy/Wallets ideas

Ideas that surfaced during hunting but didn't pass the Orbital filter, or were already covered elsewhere. Reuses the cut-reason codes from `/home/pratham/Sarnav/Open-House/DISCARDED.md`.

## Cut Reason Codes

- **[CR-1]** Pitch needs DeFi/crypto context — falls flat with a generalist
- **[CR-2]** Pitch is incremental — "X but better," not "wait, how?"
- **[CR-3]** Already shipped or in the air
- **[CR-4]** Pitch needs unpacking (>1 beat)
- **[CR-5]** Infra plumbing — no user-facing magic
- **[CR-6]** Niche audience
- **[CR-7]** Beautiful math, demo doesn't sing

---

## Discarded

### "Receive private messages without scanning a single byte." — Oblivious Message Retrieval (standalone)
**Cut: [CR-5]** — Pure infra plumbing. Folded into [[idea-12-snake-eye-mailbox]] as a building block.
- Liu et al. — https://eprint.iacr.org/2024/204

### "A whole group retrieves messages without revealing the group." — Group OMR (standalone)
**Cut: [CR-5]** — Same plumbing issue; useful sub-component of #12 rather than a standalone pitch.

### "A bridge where the destination is hidden from everyone but the receiver." — Stealth-Address Bridge
**Cut: [CR-2]** — Fluidkey already ships single-chain stealth UX; bridges are incremental. The salary-stream framing [[idea-10-stealth-address-salary-stream]] has more visceral pitch.
- EIP-5564 — https://eips.ethereum.org/EIPS/eip-5564

### "MPC wallet recovery via your social graph." — Lit Protocol social recovery
**Cut: [CR-2, CR-3]** — Lit Protocol + Web3Auth + every other AA wallet has shipped social recovery variants. "Recover via friends" doesn't trigger lean-in.
- Lit Protocol docs — https://developer.litprotocol.com/

### "Encrypted ERC-4626 vaults with FHE strategies." — FHE Vaults
**Cut: [CR-7]** — Same FHE-latency problem flagged in master DISCARDED.md. ~5 swaps/min vs Uniswap V3 at hundreds/sec.

### "Privacy-preserving on-chain analytics with differentially private SQL." — DP Analytics
**Cut: [CR-5, CR-6]** — Plumbing for compliance teams. No retail-facing magic.

### "ZK proof of solvency for CEXs (Xiezhi)." — Proof of Solvency v2
**Cut: [CR-3]** — Post-FTX proof-of-reserves has shipped many times. Incremental.
- IACR 2024/2001

### "ZK proof of liabilities (Notus)." — Proof of Liabilities
**Cut: [CR-3]** — Same family as solvency proofs; CEX-only audience.

### "Functional encryption for oracles (inner products)." — FE Oracle
**Cut: [CR-4, CR-7]** — Master DISCARDED.md already cut this. Beautiful but needs unpacking.
- Zhu et al. — https://eprint.iacr.org/2024/327

### "Statement-Oblivious Witness Encryption" — committee decrypts without learning condition
**Cut: [CR-4, CR-7]** — Already cut in master DISCARDED.md; folded conceptually into [[idea-05-dead-man-switch-inheritance]] mechanism family.

### "Threshold encryption with silent setup." — Garg/Kolonelos/Policharla/Wang
**Cut: [CR-5]** — Pure infrastructure improvement. No user-facing pitch.
- IACR 2024/263

### "Programmable Inheritance via Lit Actions." — Lit-based dead-man-switch
**Cut: [CR-3]** — Same user-facing pitch as [[idea-05-dead-man-switch-inheritance]] with different mechanism. Witness-encryption variant has cleaner trust assumptions.

### "Stylus-native Plonky3 / Risc0 verifier as a standalone product." — Stylus ZK verifier
**Cut: [CR-5]** — Infra primitive. Distributed across multiple ideas (01, 03, 06, 11, 13) as the verification layer rather than a standalone pitch.

### "ZK-of-trade-history credentials for institutional credit." — Onchain trade-history reputation
**Cut: [CR-2]** — Subset of [[idea-15-designated-verifier-loan-application]]. Trade-history is one input; the DVS framing is the actual primitive.

### "Anonymous credentials with extendable threshold rings (Tetris ETRS)." — Group-signature petition
**Cut: [CR-4, CR-6]** — Already cut in master DISCARDED.md. Niche application.
- Aranha et al. — https://eprint.iacr.org/2025/730

### "Wallet that splits keys with N TEE chips and recovers via attestation." — TEE-MPC wallet
**Cut: [CR-3]** — Fireblocks, Coinbase MPC, and Web3Auth all ship variants. No fresh inversion.

### "ZK proof you ran the latest wallet-firmware patch." — Verifiable patch attestation
**Cut: [CR-5, CR-6]** — Wallet vendor infra. Not user-facing.

### "Anonymous-yet-revocable credentials via accumulator." — Revocable AnonCreds
**Cut: [CR-3]** — Hyperledger Indy / W3C VC has shipped this for years. Not novel.

### "Witness encryption to future blocks (extensions)." — Generic future-block WE
**Cut: [CR-3]** — Same family as [[idea-04-tlock-sealed-bid-mempool]] and [[idea-05-dead-man-switch-inheritance]]. Folded in.

### "Snake-eye-resistant DKEM as a standalone primitive." — Snake-eye DKEM
**Cut: [CR-5]** — Used as a component of [[idea-12-snake-eye-mailbox]] rather than a standalone product.

---

## If you want to argue back

Most plausibly underrated cuts:
- **MPC wallet recovery via social graph** — the "your friends are your seed phrase" pitch is more universal than I credited. If this category needs a more retail-friendly pitch, this could pull back as Tier A.
- **Stealth-Address Bridge** — bridging is a hotter pain point in 2026 than stand-alone stealth UX; if "stealth bridge" is positioned as a $XB cross-chain privacy product, it could re-enter.
- **TEE-MPC wallet** — Fireblocks-style products are commercial, but a Stylus-native open-source variant with attestation verification could be Tier A.

Otherwise the category is full at 15.
