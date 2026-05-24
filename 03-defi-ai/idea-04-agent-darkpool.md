# Idea 04: ShadowMatch — Agent-Run Darkpool with Reputation Bonds

## Pitch
*"A darkpool matched by an AI. Each fill is signed by its reputation."*

## What it is
A sealed-order venue where an LLM-based matching engine runs inside a TEE and signs each fill with a reputation NFT. Bad fills (excess slippage, leaked size) burn reputation and slash the matcher's bond. Traders submit encrypted orders; the agent finds liquidity across N attested venues and posts only the net trade on-chain.

## How it works
1. Matcher operator stakes ETH, mints a reputation NFT (ERC-8004 agent identity).
2. Trader submits tlock-encrypted order to next-block drand. Matcher (in TDX) decrypts, runs an LLM-driven matching policy (route across CoW, 1inch, internal book), produces fill + zkTLS proof of external venue prices.
3. On-chain settlement verifies attestation + zkTLS price proofs. Slippage > attested benchmark → bond slashes pro-rata to victim, reputation decays.
4. Traders pick matchers by reputation curve; high-rep matchers earn higher fees.

## Why it lands (Orbital filter)
FRONTIER #28 (TEE darkpool) hides orders from the exchange — this one goes further: the *agent matching* is the value. Reputation-bonded LLM matchers competing for order flow is a new market layer, not just darker shading of the old one.

## Future utility
1-yr: institutional crypto OTC moves on-chain. 3-yr: retail "smart routers" become reputation-scored agents. 5-yr: agent reputation becomes a tradeable credit primitive across markets.

## Business model
2-5bp per fill, 50/50 with matcher operator. At $1B daily volume across matchers, $200K/day fees. Reputation NFTs trade secondary; matchers stake LPs as undercollateralized capital backed by their on-chain rep score.

## Sponsor / track fit
Best Agentic AI $15K + DeFi + Overall $70K. ERC-8004 reference impl. Marlin Oyster + EigenLayer (rep slashing) bounty.

## 3-week MVP scope
- Week 1: Stylus settlement contract + ERC-8004 reputation registry
- Week 2: matcher service in TDX, integrating 1inch + Uniswap as backstop venues with zkTLS price snapshots
- Week 3: live testnet, 100 simulated orders, dashboard showing matcher rep changing in response to fill quality

## Risks
- TEE side-channel attacks could leak order flow. Dual-TEE attestation (Intel + AMD) mitigates.
- LLM matching may underperform deterministic algos initially. Position as augment + fallback.
- Reputation cold-start: matchers need initial trust. Bootstrap with high-bond requirement.

## Sources
- [ERC-8004 Agent Identity](https://eips.ethereum.org/EIPS/eip-8004)
- [Marlin Oyster CVM](https://docs.marlin.org/oyster/protocol/cvm/)
- [drand tlock](https://docs.drand.love/docs/timelock-encryption/)
- [Reclaim Protocol zkTLS](https://www.reclaimprotocol.org/)
