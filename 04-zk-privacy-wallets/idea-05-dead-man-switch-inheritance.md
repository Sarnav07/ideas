# Idea 05: Dead-Man-Switch Inheritance Wallet

## Pitch
*"An inheritance wallet that decrypts itself if you stop checking in. No executor, no lawyer."*

## What it is
A self-custodial wallet whose seed phrase is encrypted to a future signature that *only exists* if the owner stops heartbeating. The chain itself becomes the executor — no human notary, no legal trust, no multisig of friends.

## How it works
The owner posts an encrypted seed phrase, ciphertext bound to a future drand round R and a heartbeat condition. The owner publishes a heartbeat tx every N days; doing so re-anchors the encryption to round R+M. If the heartbeat stops, the drand signature at the deadline round eventually appears in public, and the beneficiary's wallet client uses it to decrypt the seed. Witness-encryption guarantees nobody — including drand operators — can decrypt early.

## Why it lands (Orbital filter)
Universal use case (every crypto holder has thought "what if I die?"). Inversion is total: every existing solution needs trusted humans; this needs *nothing* — the math is the executor.

## Future utility
1-year: paid product for $1B+ HNWI crypto wealth. 3-year: default wallet feature in MetaMask/Ledger. 5-year: replaces estate-planning lawyers for digital assets ($XB market).

## Business model
- Subscription: $20/mo per heartbeat-monitored wallet.
- Premium: $200/yr for multi-beneficiary with conditional logic ("split 70/30 between spouse and child").
- Enterprise: family offices pay $5k/yr for batched monitoring of 100+ wallets. 100k user base at $20/mo = $24M ARR.

## Sponsor / track fit
- **Arbitrum Stylus** — witness-encryption verifier; gas-cheap heartbeat tx.
- **drand** — the deadline-attesting beacon.
- **Wallet track** — flagship Account Abstraction integration.
- **Privacy track** — extension of [[idea-04-tlock-sealed-bid-mempool]] mechanism family.

## 3-week MVP scope
- Witness-encryption library (using BqETH / Avitabile et al. compact-ciphertext scheme).
- Heartbeat tx contract: stores latest heartbeat block + drand round binding.
- Beneficiary CLI: `inherit reveal <address>` (only works post-deadline).
- Demo: alice sets a 5-minute heartbeat. Stop heartbeating. Bob runs `inherit reveal` 6 minutes later and the seed decrypts to his terminal.

## Risks
- **Technical:** witness encryption ciphertext sizes for long deadlines (years) can balloon; need compact-ciphertext schemes.
- **Adoption:** users hate thinking about death — UX needs to feel like "automated 2FA backup."
- **Beneficiary key loss:** if beneficiary loses their key, recovery is impossible. Mitigated by multi-beneficiary thresholds.

## Sources
- Avitabile et al., *SWE with Compact Ciphertext* (IACR 2024/1477) — https://eprint.iacr.org/2024/1477
- Glaeser et al., *T+1-eWEB* (IACR 2025/1064) — https://eprint.iacr.org/2025/1064
- drand — https://drand.love/
- BqETH (witness-encrypted ETH inheritance) whitepaper — https://bqeth.com/
- See also: [[idea-04-tlock-sealed-bid-mempool]], [[idea-09-lattice-account-abstraction]]
