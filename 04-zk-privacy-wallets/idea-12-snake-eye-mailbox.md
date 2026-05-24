# Idea 12: Snake-Eye Mailbox

## Pitch
*"A private inbox where spammers can't prove they ever sent you anything."*

## What it is
A wallet inbox for encrypted messages (chat, alerts, transactional notifications) whose privacy guarantee survives even adversaries trying to flood it. Built on snake-eye-resistant public-key encryption: the spammer cannot tell whether their flood reached the right recipient, so there is no DoS-able signal to amplify.

## How it works
Standard PKE leaks "ciphertext was for X" via the recipient's scanning effort: if alice can't keep up with scanning, the spammer wins. Snake-eye-resistant PKE adds an extra hiding step — even an adversary who *crafts* the ciphertexts can't distinguish whether they decrypt for alice vs. nobody. Combined with Oblivious Message Retrieval (OMR), alice's relay never reveals which messages are hers. Spammers can post millions of garbage ciphertexts; they cannot mount a confirmation-of-receipt attack.

## Why it lands (Orbital filter)
"A mailbox even the spammer can't tell they hit" is a paradox until the cryptographic-indistinguishability story lands. Universal pain point (everyone hates spam); cryptographic guarantee is fresh.

## Future utility
1-year: encrypted in-wallet messaging (alternatives to XMTP/Push for transactional alerts). 3-year: standard layer for AI-agent inboxes (agents receive proposals/job offers without revealing their address). 5-year: foundation for DoS-resistant private communication at internet scale.

## Business model
- Relay-as-a-service: $0.001 per delivered message, paid by sender.
- Premium wallet integration: $3/mo per privacy-mailbox user.
- Enterprise: $10k/yr per protocol that uses the mailbox for system notifications. 100k users × $3/mo = $300k MRR.

## Sponsor / track fit
- **Privacy track** — anchor messaging primitive.
- **Arbitrum Stylus** — OMR scanning + PKE verification.
- **AI agent track** — see [[idea-13-zk-spend-limit-marketplace]]; agents need private inboxes for receiving jobs.

## 3-week MVP scope
- Implement snake-eye-resistant PKE + OMR scheme (Liu et al. IACR 2024/204 for OMR baseline).
- Relay service in Rust.
- Wallet UI: receive encrypted notifications without leaking which were "real."
- Demo: spammer floods 1M ciphertexts; alice's actual message latency stays under 100ms; spammer cannot prove any single ciphertext was delivered.

## Risks
- **Technical:** OMR is bandwidth-heavy at scale (~1KB scan per msg); group OMR (IEEE S&P 2024) helps.
- **UX:** end-users won't care unless framed as anti-spam value-add.
- **Adoption:** needs critical mass of sender/receiver wallets; bootstrap via XMTP/Push partnership.

## Sources
- Liu/Tromer, *Oblivious Message Retrieval* (IACR 2024/204) — https://eprint.iacr.org/2024/204
- *Group Oblivious Message Retrieval* (IEEE S&P 2024) — https://www.computer.org/csdl/proceedings-article/sp/2024/313000a106/1Ub234OOzeo
- Snake-Eye Resistance for DKEM (USENIX Security 2024) — https://www.usenix.org/conference/usenixsecurity24/presentation/
- See also: [[idea-10-stealth-address-salary-stream]], [[idea-11-privacy-pools-erc20]]
