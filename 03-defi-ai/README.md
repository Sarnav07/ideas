# Category 3 — DeFi × Agentic AI (Integrated)

15 ideas where AI agents are first-class DeFi participants and crypto provides the verification, escrow, and slashing rails the AI alone cannot. Not chatbot wrappers. Not 2021-era "AI portfolio manager" pitches.

Every pitch here passes the **Orbital filter**: said cold to a smart non-crypto listener in ≤15 words, it triggers *"wait, how is that possible?"*

---

## Index

| # | Name | Pitch |
|---|---|---|
| [01](./idea-01-zkvault-encrypted-strategy.md) | **zkVault** | *"An AI runs your vault. You verify the Sharpe ratio. You never see the strategy."* |
| [02](./idea-02-auto-adjudicated-insurance.md) | **ClaimGPT** | *"File a claim. An AI judge reads it. Money hits your wallet in 30 seconds."* |
| [03](./idea-03-ml-priced-amm.md) | **NeuralAMM** | *"An AMM with no bonding curve. A neural net quotes every swap."* |
| [04](./idea-04-agent-darkpool.md) | **ShadowMatch** | *"A darkpool matched by an AI. Each fill is signed by its reputation."* |
| [05](./idea-05-agent-only-credit-market.md) | **AgentCredit** | *"A lending market where humans can't borrow. Only AI agents — and their reputation is the collateral."* |
| [06](./idea-06-inference-futures.md) | **InferenceFutures** | *"A futures market on tomorrow's GPT answer. Settles inside a sealed chip."* |
| [07](./idea-07-training-as-yield.md) | **TrainYield** | *"Stake your GPU. Earn yield from every query the model serves."* |
| [08](./idea-08-ai-swarm-vault.md) | **SwarmVault** | *"A vault run by 7 AIs. They vote on every trade. The minority gets slashed."* |
| [09](./idea-09-ai-risk-oracle.md) | **RiskNet** | *"Aave's LTVs are set by a committee. Ours are set by an AI — with a math proof."* |
| [10](./idea-10-agent-bridge.md) | **AgentBridge** | *"A bridge run by an AI inside a sealed chip. It decides where your money goes."* |
| [11](./idea-11-service-for-service-amm.md) | **ServiceSwap** | *"An AMM where you trade compute for data. No tokens between."* |
| [12](./idea-12-federated-priced-derivatives.md) | **FedDerivs** | *"An options pricer trained on private user data. Nobody sees the data. Nobody sees the model."* |
| [13](./idea-13-ai-fee-mechanism.md) | **GaugeBrain** | *"A protocol whose fees retune themselves every hour. Get it wrong and pay the LPs."* |
| [14](./idea-14-ai-escrow.md) | **ProofEscrow** | *"Escrow held by an AI. It looks at the proof, reads the contract, releases the money."* |
| [15](./idea-15-ai-liquidation-auctions.md) | **LiquiBid** | *"Liquidators are AI agents. They bid in sealed envelopes. The lowest-loss bid wins."* |

---

## Top 3 picks

**#1 — SwarmVault (Idea 08).** Best demo: a chart of 7 attested agents diverging on a single trade, with the minority's stake visibly slashing in real time. Captures the "wisdom of the silicon crowd" thesis with skin in the game. 3-week MVP is honest; sponsor convergence is unusual (ERC-8004 + EigenLayer + Marlin TDX all benefit). The pitch is Orbital-shape — N-D wisdom replaces single-model alpha.

**#2 — LiquiBid (Idea 15).** Inverts the entire MEV stack. "Borrowers retain 5-20% more on liquidation" is a quantifiable user-facing benefit no other AI×DeFi pitch matches. Sealed-bid tlock + AI bidders is exactly the kind of recombination the PATTERN.md "proven primitive + Arbitrum twist + one hook" formula rewards. Aave/Morpho integration is achievable in MVP.

**#3 — ClaimGPT (Idea 02).** The visceral pitch. Everyone has been screwed by an insurance claim. "AI judge, 30-second payout, math-backed appeal" is the kind of thing a generalist VC instantly forwards. Distinct from FRONTIER #24 (Parametric Cat) — narrative claims, not just parametric triggers. Strong distribution angle (insurance is a $7T global market with measurable user pain).

---

## Why DeFi × AI is the right 2026 bet

**1. The AI economy needs financial rails, and DeFi is the only stack that can attach to a non-human counterparty.** ERC-8004 just shipped (Nov 2025). x402 hit critical adoption (FRONTIER #7). Agents now have identity + payment primitives. What's missing: every other piece of finance — credit (idea 05), insurance (02, 09), market making (03, 04), settlement (10, 14, 15). Each is a multi-billion-dollar TradFi market that gets a native-AI version, *first* on crypto rails because regulation can't yet touch on-chain agent-to-agent contracts.

**2. zkML and TEEs are finally fast enough.** Lagrange DeepProve, EZKL, and Marlin Oyster CVM matured in 2025. For the first time, "verify an AI did what it claimed" is engineering, not a thought experiment. Every idea here picks one of these stacks and commits to its current latency budget honestly — daily cadence for zkML, per-message for TDX, hourly for big-model attestations.

**3. The combination unlocks what neither could alone.** Pure AI (a closed-source quant bot) cannot prove its track record to LPs without revealing alpha. Pure DeFi (a curve-based AMM, an oracle-fed risk pool) cannot adapt to non-parametric reality. The integration — encrypted-but-verifiable models attesting to a public chain — is the only architecture that gives LPs both *upside of closed-source intelligence* and *auditability of open-source software*. That's the asymmetric structural advantage no TradFi quant fund can replicate.

**4. Sponsor convergence is unusual in 2026.** Best Agentic AI ($15K) + Best DeFi + Overall ($70K) + EigenLayer + Marlin + Phala + Lagrange + ERC-8004 + x402 — multiple bounties stack on a single submission for nearly every idea in this list. The same project hits ≥3 sponsor tracks. That's prize math no pure category can match.

**5. The 2021 graveyard is the moat.** Every cut in `discarded.md` failed because it was a 2021-era pitch (yield aggregator with ML, Ethereum trading bot, AI-token-launchpad). Investors and judges are *immunized* against these. Anyone pitching "AI vault" without a verification mechanism gets discounted instantly. The 15 here all carry a structural integration (zkML, TDX, slashing) that lets them pass the "no, but how is the AI actually accountable" follow-up. The bar is high, but most competing teams won't clear it.

---

## How these 15 avoid duplicating FRONTIER.md

- **FRONTIER #6 (Sealed Model)** — encrypted weights, witness-encrypted decryption. Our idea 01 (zkVault) applies the *adjacent* mechanism (zkML attestation of model output) to *vault performance*, not model accuracy procurement.
- **FRONTIER #7 (Inverse x402)** — ad auction reversal. Our idea 11 (ServiceSwap) is the *non-ad* application of x402 — service-for-service barter, not ad-bidding.
- **FRONTIER #8 (Proof-of-Prompt-Injection-Free)** — attention-mask zk proof for individual agents. Our ideas 02, 04, 14 *consume* this as a building block, but the standalone primitive remains FRONTIER's.
- **FRONTIER #9 (Witness-Encrypted Agent Wallet)** — key materializes from task completion. Our ideas focus on agent *behavior in markets*, not key custody.
- **FRONTIER #20 (Federated-Shapley Training)** — single-round contribution. Our idea 07 (TrainYield) extends to *lifecycle royalties*; our idea 12 (FedDerivs) applies it to *productized inference*.
- **FRONTIER #21 (ERC-7715 Marketplace)** — wallet permissions as NFTs. Our idea 05 (AgentCredit) *uses* ERC-7715 streams but is the credit primitive, not the permission market.
- **FRONTIER #22 (Forecasting-Cohort Index)** — bet *via* the AI cohort. Our idea 06 (InferenceFutures) inverts: bet *on* the model itself.

---

## Coverage matrix (idea × DeFi primitive × AI stack)

| # | DeFi primitive | AI stack | Sponsor anchor |
|---|---|---|---|
| 01 | Vault | zkML | Lagrange |
| 02 | Insurance | TEE | Marlin/Phala |
| 03 | AMM | zkML | Lagrange + Stylus |
| 04 | DEX/Darkpool | TEE + zkTLS | Marlin + ERC-8004 |
| 05 | Lending | ERC-8004 reputation | x402 + ERC-7715 |
| 06 | Prediction Market | TEE inference | Marlin + Polymarket |
| 07 | Yield | zkML proof of training | EigenLayer + Lagrange |
| 08 | Vault (multi-agent) | TEE + ERC-8004 | Marlin + EigenLayer |
| 09 | Oracle | zkML | Lagrange + Aave |
| 10 | Bridge | TEE | LayerZero + Marlin |
| 11 | AMM (service) | x402 | x402 + ERC-8004 |
| 12 | Derivatives | Federated learning + zkML | Lagrange |
| 13 | Fee mechanism | TEE + bond | EigenLayer + Marlin |
| 14 | Escrow | TEE multimodal | Kleros + Marlin |
| 15 | Auction (liquidation) | tlock + TEE | drand + Aave |

Total domain coverage: vault (3), AMM/DEX (3), lending (1), insurance (1), oracle (1), bridge (1), yield (1), derivatives (1), prediction (1), fee mgmt (1), escrow (1), liquidation (1). No two ideas occupy the same primitive ×  AI-stack combo.

---

## Three-week build hot-take

If we ship ONE from this list, the right pick is **SwarmVault (08)** for the demo, **LiquiBid (15)** for the borrower-protection narrative, or **ClaimGPT (02)** for the visceral pitch. SwarmVault is the most likely to survive technical scrutiny from a Stylus-deep judge while still landing the Orbital pitch on a generalist. LiquiBid is the most likely to attract Aave/Morpho integration interest pre-submission. ClaimGPT is the one that gets retweeted.
