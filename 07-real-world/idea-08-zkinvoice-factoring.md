# Idea 08: zkInvoice — Anonymous Factoring with zkTLS

## Pitch
*"Sell your unpaid Stripe invoices to strangers — without revealing your customers."*

## What it is
An invoice-factoring pool where freelancers and SMEs upload zkTLS-attested invoices (Stripe, Shopify, QuickBooks, Razorpay) and receive instant USDC against them. The buyer (the customer paying the invoice) is never identified onchain; only the invoice's payment-track-record is proven. Solves the *"I'm a Lagos developer, US clients owe me $50K, I can't get a $40K bridge loan"* problem.

## How it works
Freelancer connects Stripe via zkTLS (Reclaim / TLSNotary). Proves to a ZK circuit: *"I have an unpaid invoice for $X, due in N days, from a customer whose Stripe-tier risk score is Y, and my last 12 months of receivables show Z% on-time payment rate."* Risk-tranching pool quotes a discount rate (e.g., 4% for 30-day invoice from gold-tier customer). USDC released instantly; on invoice payment, Stripe webhook (zkTLS-attested) settles the pool. On default → falls back to a personhood-bond blocklist (composes with Frontier #10 Anti-Sybil). Oracle dependency: **Reclaim Protocol zkTLS over Stripe/Shopify API + payment-webhook ZK proof**.

## Why it lands (Orbital filter)
"Anonymous invoice factoring with no KYC of your customer" sounds impossible because traditional factoring requires the buyer to *call* the customer and verify the receivable. **The customer is the credit risk; we prove the risk without naming them.** That inversion is Orbital-shaped — the math (ZK over private signed data) is real and shipping in 2025.

## Future utility
**1-yr:** Indian / Filipino / Nigerian freelancers and Etsy sellers get sub-24h liquidity against unpaid US receivables — the single largest unsolved problem for global freelance income. **3-yr:** anchored supply-chain finance (Walmart-tier buyer signs an on-chain commitment; suppliers factor against it instantly). **5-yr:** $5T+ trade-finance gap (Asian Development Bank 2024) starts being served onchain.

## Business model
TAM: $4.41T global factoring market 2025 → $5.92T by 2030 (Mordor Intelligence). $5T+ unmet trade-finance gap (ADB). Capture 0.05% → **$2.5B annual factoring volume**. Take rate: 0.5–1% of invoice face value → **$15M+ ARR**. Sticky moat: per-freelancer payment-history dataset (provably non-Sybil + reputation-bound) becomes the credit primitive.

## Sponsor / track fit
**Robinhood Chain ($30K reserved seat)** — strong RWA + emerging-markets-finance narrative. **Overall $70K** — community-serving angle hits the Bengaluru-winner pattern (GuardChain levered "Kudumbashree distribution"); freelancer-onboarding has similar real-world distribution potential. Composes with the **Aegis personhood-bond** primary thesis as the credit-side of the same wallet.

## 3-week MVP scope
- **Week 1:** Reclaim Protocol Stripe receivables circuit (prove "invoice X exists, amount Y, due Z"). Smart-contract pool with risk-tranche tiers.
- **Week 2:** ZK aggregator of 12-month receivables history → on-chain credit-tier (Stylus, since the dataset proof is heavy). Personhood-bond nullifier registration (zkPassport / Anon Aadhaar).
- **Week 3:** demo: a real freelancer (team member) factors a real $5K Stripe invoice live on stage; receive USDC in 30 seconds. Frontend with factor-now flow + tier dashboard.

## Risks
- **zkTLS legality** — Stripe ToS technically forbids automated scraping; zkTLS is a grey area legally. Mitigation: Stripe is actively engaging with zkTLS providers (Reclaim has shipped pilots).
- **Default risk concentration** — fraudster freelancers stack synthetic invoices. Mitigation: personhood-bond nullifier per Sybil-resistance; tier-2 vouching for high amounts.
- **Currency / FX risk** — invoices in USD but freelancer wants local-currency stablecoin. Mitigation: integrate Mento / Bridge.
- **Regulatory** — money-transmitter licensing in many jurisdictions. Mitigation: launch in pro-crypto jurisdictions (Singapore, UAE, Argentina) first.

## Sources
- [Reclaim Protocol zkTLS docs](https://docs.reclaimprotocol.org/)
- [Mordor Intelligence Factoring Market — $4.41T 2025](https://www.mordorintelligence.com/industry-reports/factoring-market)
- [Asian Development Bank Trade Finance Gaps Report](https://www.adb.org/publications/trade-finance-gaps-jobs-survey)
- [Anon Aadhaar / zkPassport for personhood](https://github.com/anon-aadhaar/anon-aadhaar)
