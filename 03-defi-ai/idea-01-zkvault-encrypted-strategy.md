# Idea 01: zkVault — Agent-Run Vault with Encrypted Strategy

## Pitch
*"An AI runs your vault. You verify the Sharpe ratio. You never see the strategy."*

## What it is
An ERC-4626 vault whose rebalance logic is an LLM/RL agent running off-chain inside a TEE. The agent's policy weights stay encrypted; LPs verify performance claims (Sharpe, max drawdown, factor exposure) via zkML proofs, not by inspecting the model.

## How it works
1. Operator stakes a bond, registers an encrypted model commitment on-chain (KZG-style).
2. Each epoch the agent emits trades + a zkML proof that the trades came from a model whose hash matches the commitment.
3. Performance attestation: a separate zkML circuit proves `Sharpe ≥ X` over the last N epochs from on-chain trade logs.
4. Liquidity entries/exits price off the attested NAV. If proof fails to land for K epochs, vault freezes and bond covers slippage to LPs.

## Why it lands (Orbital filter)
"Trust the model without seeing it" is the AI procurement holy grail. Vault depositors get the upside of a closed-source quant fund with the auditability of a public smart contract — without copy-trading.

## Future utility
1-yr: niche quant LPs deploy proprietary strategies on-chain without leaking alpha. 3-yr: model-as-IP marketplace where strategies trade like patents. 5-yr: every alpha-bearing fund is a verifiable on-chain shell.

## Business model
2/20 fee split with vault. At $50M TVL, 2% mgmt + 20% perf on 15% APY ≈ $2.5M/yr gross. Operator runs multiple vaults under one bond — bond ROI ~30%/yr.

## Sponsor / track fit
Best Agentic AI $15K + Overall $70K. Lagrange (DeepProve zkML) bounty fit. Sister to FRONTIER #6 (Sealed Model) but applied to vault performance, not model accuracy.

## 3-week MVP scope
- Week 1: ERC-4626 vault + Stylus zkML verifier (single Lagrange DeepProve circuit for a small policy net)
- Week 2: simple RL agent (PPO on Curve TVL/fee data) running in Marlin Oyster TEE
- Week 3: live testnet with $10k mock TVL, one rebalance/day, on-chain Sharpe attestation chart

## Risks
- zkML proof time for non-trivial nets is minutes-to-hours (2026 Lagrange numbers). Acceptable at daily cadence, fatal at intraday.
- TEE compromise leaks strategy. Mitigated by Intel TDX + dual-attestation across Marlin + Phala.
- LPs may want strategy transparency anyway. Sell to family offices, not retail.

## Sources
- [Lagrange DeepProve roadmap](https://www.lagrange.dev/blog/lagrange-roadmap-2025)
- [Marlin Oyster CVM docs](https://docs.marlin.org/oyster/protocol/cvm/)
- [Survey of ZK-verifiable ML — arXiv 2502.18535](https://arxiv.org/pdf/2502.18535)
- [EZKL framework](https://ezkl.xyz/)
