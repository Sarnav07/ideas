# Idea 05: TEE Compute Bus — Sealed CPUs for Any Smart Contract

## Pitch
*"A smart contract that runs code no one can see, including the operator."*

## What it is
A Marlin Oyster / Phala / Automata-backed compute marketplace exposed as a *single Solidity interface*: a contract submits a code blob + input commitment, receives a remote-attestation-signed output, and verifies the Intel TDX / AMD SEV-SNP quote on-chain via Stylus. Same TEE pool serves DEX matching, AI inference, dark pools, and private oracles — capability is decoupled from the application.

## How it works
- Operator network runs Confidential VMs (TDX / SEV-SNP) registered on-chain with their attestation roots.
- Contract calls `tee.execute(programHash, encryptedInput) → bytes32 jobId`.
- Operator picks up the job, runs inside the enclave, returns `(output, attestationQuote)`.
- Stylus verifier checks the quote against the trusted hardware root + the registered program hash; emits the output.
- Programs are content-addressed — verifying "this output came from *that* code" is as cheap as a hash comparison.

## Why it lands (Orbital filter)
The audience knows "trusted compute" from Apple's Secure Enclave / Signal contact discovery. Translating that to "any Arbitrum contract can outsource a computation that even the operator can't read" recasts smart contracts as orchestrators of *invisible* work.

## Cross-domain applications
- **AI**: private LLM inference — agent sends user query encrypted; TEE runs the model; returns attested output. No prompt leakage to operator.
- **DeFi (dark pools)**: CLOB matching inside TDX; even the exchange can't see the order book (extends FRONTIER #28).
- **Governance**: vote tallying inside TEE for MACI-style coercion resistance, with output proof posted on-chain.
- **Oracles**: private API pulls (e.g., bank balance via zkTLS+TEE) where the credential never touches the chain.
- **Gaming**: hidden-information games (poker, fog-of-war) where the state machine runs in TEE.
- **Compliance**: KYC providers attest to "this user passed our check" without revealing PII to the chain.

## Future utility
1-yr: 10+ protocols call the same TEE bus. 3-yr: TEE compute becomes a metered utility like RPC requests. 5-yr: enterprise auditors (Big Four) accept on-chain TDX attestations as evidence of off-chain compute correctness.

## Business model
- Metered per-CPU-second pricing in $USDC / $ARB.
- Operator side: revenue share to TDX hosts (~70%), protocol take ~30%.
- TAM: AI inference at hyperscale alone is a $100B+ market; even 0.01% on-chain capture = $10M/yr. Add private DeFi, oracle, and gaming use cases.

## Sponsor / track fit
- **Arbitrum Stylus** — Stylus is the natural home for TDX quote verification (BLS + RSA-PSS heavy).
- **Robinhood Chain** — private order matching for tokenized stock OTC blocks (legally important for institutional flow).
- **EigenLayer** — TEE operators backed by restaked ETH for slashable attestations.

## 3-week MVP scope
- `TeeBus.sol` (Stylus) with `submit(programHash, encInput)` / `claim(jobId, output, attestation)`.
- TDX quote verifier in Rust/Stylus (based on Marlin's open-source attestation library).
- Three demo apps sharing the bus:
  1. **Private dark pool**: 100-order CLOB match inside TDX, single attested output settles on-chain.
  2. **TEE-attested LLM oracle**: Claude-3.5 inference inside TDX, output signed and verifiable.
  3. **Sealed governance tally**: 1000 votes encrypted to TEE pubkey, output is `(yes_count, no_count, abstain)` only.

## Risks
- **TEE vulnerabilities** — Intel SGX/TDX has had side-channels (Spectre family). Mitigate by combining with restaked-ETH slashing (any disagreement between 2 attested replicas slashes both).
- **Quote freshness** — older quotes may be revoked. Verify against latest Intel PCS Cert Chain.
- **Adoption** — Marlin is live but ecosystem-niche. Demo apps are critical for legibility.

## Sources
- [Marlin Oyster CVM docs](https://docs.marlin.org/oyster/protocol/cvm/)
- [Phala Network confidential compute](https://docs.phala.network/)
- [Automata Network attestation](https://docs.ata.network/)
- [*Cross-Chain Sealed-Bid Auctions on Confidential Compute* — arXiv 2510.19491](https://arxiv.org/abs/2510.19491)
- [Intel TDX whitepaper](https://www.intel.com/content/www/us/en/developer/articles/technical/intel-trust-domain-extensions.html)
