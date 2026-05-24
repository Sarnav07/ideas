# Category 04 — ZK / Privacy / Wallets

15 ideas at the intersection of zero-knowledge cryptography, privacy primitives, and next-generation wallet architecture. Each one passes the **Orbital filter**: the one-sentence pitch, said cold to a smart non-crypto listener, must trigger the same "wait, how is that possible?" reaction as Orbital Pool's "Uniswap is 1D, Curve is 2D, Orbital is N-D liquidity."

## Index

| # | Idea | Pitch (≤15 words) | Primitive |
|---|------|-------------------|-----------|
| 01 | [PACTs Quantum Escape Hatch](idea-01-pacts-quantum-escape-hatch.md) | *"Prove you owned this wallet before quantum existed."* | OpenTimestamps + STARK |
| 02 | [Anti-Sybil Personhood Bond](idea-02-anti-sybil-personhood-bond.md) | *"Anonymous loans. No KYC. Default once — banned forever."* | ZK proof-of-personhood nullifier |
| 03 | [Cashu Cairo](idea-03-cashu-cairo-programmable-bearer-cash.md) | *"Digital cash where every banknote runs a ZK program before you spend it."* | Chaumian blind sigs + STARK |
| 04 | [tlock Sealed-Bid Mempool](idea-04-tlock-sealed-bid-mempool.md) | *"Encrypt your trade to a future block. Front-running becomes impossible."* | drand signature-based WE |
| 05 | [Dead-Man-Switch Inheritance](idea-05-dead-man-switch-inheritance.md) | *"A wallet that decrypts itself if you stop checking in."* | Witness encryption + heartbeat |
| 06 | [Traceable Ring Signatures](idea-06-traceable-ring-signatures.md) | *"Sign anonymously. Double-sign and your identity reveals itself."* | O(log n) TRS |
| 07 | [Designated-Verifier Credentials](idea-07-designated-verifier-credentials.md) | *"A credential you can prove to your bank — useless to leak."* | DVS SNARK |
| 08 | [Self.xyz Biometric ZK Onboarding](idea-08-self-biometric-zk-onboarding.md) | *"Tap your passport. Chain knows you're human. Nobody knows who."* | Passport NFC + ZK |
| 09 | [Lattice Account Abstraction](idea-09-lattice-account-abstraction.md) | *"A wallet that survives quantum. Ships today as ERC-4337."* | Dilithium AA |
| 10 | [Stealth-Address Salary Stream](idea-10-stealth-address-salary-stream.md) | *"Get paid every block. No address sees two paychecks."* | ERC-5564 stealth |
| 11 | [Privacy Pools for ERC-20](idea-11-privacy-pools-erc20.md) | *"Mix any token — and prove your coins aren't from a hack."* | Association-set ZK |
| 12 | [Snake-Eye Mailbox](idea-12-snake-eye-mailbox.md) | *"A private inbox where spammers can't prove they hit it."* | Snake-eye PKE + OMR |
| 13 | [ZK Spend-Limit Marketplace](idea-13-zk-spend-limit-marketplace.md) | *"Rent your wallet to an AI for an hour, math-capped loss."* | ERC-7715 + ZK predicates |
| 14 | [RLN Airdrop Faucet](idea-14-rln-airdrop-faucet.md) | *"Claim airdrops anonymously. Greed past the rate limit and self-dox."* | RLN polynomial |
| 15 | [DV Loan Application](idea-15-designated-verifier-loan-application.md) | *"Show your credit score to one lender. The proof is useless to others."* | DVS over credit history |

## Top 3 — best of category

1. **#02 Anti-Sybil Personhood Bond** — solves the holy-grail of crypto credit (undercollateralized lending) with a single Orbital-shaped paradox: anonymous yet rate-limited. Ships with verified identity primitives (Self.xyz, World ID, zkPassport) already serving 7M+ users in 2025. Universally pitchable.

2. **#04 tlock Sealed-Bid Mempool** — cryptographic MEV defense that needs no committee, no trusted dealer, no governance. "Encrypt to a future moment in time" is sci-fi until drand's beacon explains itself. $1B/yr in MEV extracted from users is the addressable damage.

3. **#01 PACTs Quantum Escape Hatch** — Paradigm published the paper three weeks before Open House 2026. First-mover narrative writes itself. $190B+ of dormant Satoshi-era BTC waiting for a recovery path. Pre-positioned dormancy is the inversion no other PQ scheme offers.

## Honorable mentions

- **#08 Self.xyz Biometric ZK Onboarding** — the most ship-ready primitive in the set; passport NFC is universal, Self.xyz SDK is production. Demo-ready in <1 week.
- **#13 ZK Spend-Limit Marketplace** — the most original AA-flavored pitch; "ZipCar for wallets" lands fast and the AI-agent secular tailwind is real.
- **#06 Traceable Ring Signatures** — perfect 11-word paradox; new O(log n) construction (IACR 2025/1807) makes Stylus deployment feasible.

## Domain spread

| Sub-domain | Ideas |
|---|---|
| Post-quantum wallet security | 01, 09 |
| Anonymous-but-accountable identity | 02, 06, 08, 14 |
| Bearer cash + programmable privacy | 03, 11 |
| Time-locked / witness encryption | 04, 05, 12 |
| Designated-verifier credentials | 07, 15 |
| Stealth + streaming privacy | 10 |
| AA-native delegation | 13 |

## Reused from FRONTIER.md

Six ideas in this category derive from the curated 30-idea FRONTIER.md shortlist (#5 PACTs, #10 Anti-Sybil Bond, #11 Cashu Cairo, #15 tlock, #17 Dead-Man-Switch, #19 Traceable Ring Sigs). The other 9 are NEW additions hunted from designated-verifier credentials, snake-eye-resistant PKE, RLN extensions, stealth-address payroll, ERC-7715 marketplaces, biometric ZK, lattice AA, ERC-20 privacy pools, and DVS lending. See `discarded.md` for ideas that didn't pass the Orbital filter.

## Sponsor track alignment

- **Arbitrum Stylus**: 01 (STARK verifier), 03 (Cashu), 06 (log-n TRS), 09 (Dilithium), 10 (secp256k1), 11 (SNARK verifier), 12 (OMR), 13 (ZK predicates), 14 (interp), 15 (DVS) — 10/15 ideas have a direct Stylus performance advantage.
- **Lagrange**: 02, 15 (ZK coprocessor for on-chain credit/identity).
- **Self.xyz / World ID / zkPassport**: 02, 08, 15.
- **drand / League of Entropy**: 04, 05, 13.
- **MetaMask Delegation Toolkit**: 13.
- **0xbow / Privacy Pools**: 11.
