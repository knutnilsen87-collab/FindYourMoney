# FindYourMoney / FoundMoney AI

FoundMoney is in **pilot validation**.

## Current pilot thesis

- **Baseline:** Stripe-native failed-payment recovery.
- **Treatment:** Stripe-native recovery + a FoundMoney in-app payment recovery gate shown when an authenticated customer returns after a failed subscription payment.
- **Experiment:** 50/50 randomized treatment/control.
- **Pilot pricing:** fixed measurement/integration fee. No success fee during the validation pilot.
- **Primary metric:** incremental recovered revenue per eligible opportunity.
- **Billing later:** only after incremental uplift can be measured robustly; no billing on gross recovery.
- **Kill criterion:** if treatment does not produce economically meaningful uplift over Stripe-native recovery, stop or redesign the failed-payment wedge.

## Scope

Stripe first. Shopify abandoned-cart recovery is **not** part of the active V1 pilot until legal and incremental-value questions are resolved.

```text
docs/
  00_MASTER.md
  01_PRODUCT/
    pilot-model.md
    native-baseline-product-wedge.md
  02_ATTRIBUTION_LEGAL/
    attribution-engine-v0.3.md
    legal-design-norway-eu.md
  03_TECH_ARCHITECTURE/
    FM-PAY-001.md
    technical-architecture.md
  04_BUSINESS_GTM/
    icp-competitors-unit-economics.md
```

## Status

**Phase:** validation / pilot design.

Do not present performance pricing, abandoned-cart recovery, or a broad "financial incrementality layer" as validated product scope yet.
