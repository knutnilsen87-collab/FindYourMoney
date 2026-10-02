# FoundMoney AI — MASTER

## Product thesis

FoundMoney tests whether a narrowly defined intervention can create **incremental recovered revenue above an already-strong native payment-recovery baseline**.

The first product is not a generic AI agent, not a CRM, and not an experimentation platform.

## Pilot scope

**Data source:** Stripe Billing.

**Control:** existing merchant setup with Stripe-native recovery.

**Treatment:** the same native setup plus one FoundMoney intervention:

> When an authenticated customer with a failed subscription payment returns to the merchant's product, FoundMoney presents a merchant-controlled in-app payment-recovery gate that asks the customer to update/fix payment before normal product use continues.

No autonomous custom retry logic is introduced in the first pilot.

## Commercial model

### Pilot
Fixed pilot fee covering:
- integration,
- measurement,
- experiment operation,
- reporting.

No success fee during initial validation.

### Post-validation
A performance component may be considered only after a robust causal measurement model is demonstrated. No fee is based automatically on gross recovered revenue.

## Experiment

Default pilot split: **50/50 treatment/control**.

Reason: the intervention is unproven, so information value is more important than maximizing treatment exposure.

Primary estimand:

```
Incremental revenue per eligible opportunity
= treatment revenue / treatment opportunities
- control revenue / control opportunities
```

Do not clamp negative periods to zero.

Evaluation is cumulative across the agreed experiment horizon.

## Current product principles

1. Stripe native recovery is the baseline, not FoundMoney credit.
2. Touchpoint attribution is not causal incrementality.
3. LLM output never determines billing.
4. Policies and experiment assignment are immutable for historical events.
5. No marketing communication without a legal gate.
6. No broad expansion until the first recovery wedge is validated.

## Kill criterion

Stop or redesign this wedge if the treatment fails to create an economically meaningful incremental effect over Stripe-native recovery.

## Deferred scope

- Shopify abandoned checkout
- generic churn prevention
- upsell
- advertising optimization
- pricing experimentation
- cost optimization
- broad "financial incrementality layer"

These may be future hypotheses, but they are not validated V1 scope.
