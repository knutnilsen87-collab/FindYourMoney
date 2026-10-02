# FM-PAY-001 — In-App Failed Payment Recovery Pilot

## Status

Pilot policy v0.2.

## Hypothesis

Showing an in-app payment recovery gate to an authenticated customer who returns after a failed subscription payment increases recovered revenue compared with Stripe-native recovery alone.

## Eligibility

Create an eligible opportunity when all are true:

1. failed subscription invoice/payment exists;
2. customer identity is resolved;
3. payment remains unresolved;
4. customer is in an active/recent merchant relationship;
5. merchant has enabled the pilot policy;
6. opportunity is not duplicate/test/fraud;
7. experiment assignment exists before exposure.

## Assignment

Randomize eligible opportunities:

- 50% CONTROL
- 50% TREATMENT

Assignment is immutable.

## Control

Merchant's existing Stripe-native recovery configuration continues unchanged.

No FoundMoney in-app recovery gate is shown.

## Treatment

When the authenticated customer returns to the product while payment remains unresolved:

1. verify current payment state;
2. show merchant-branded recovery gate;
3. direct customer to the supported payment-update/payment-completion surface;
4. log exposure and outcome.

The pilot does not introduce custom autonomous retry timing.

## State machine

```
PAYMENT_FAILED
  -> ELIGIBLE
  -> ASSIGNED_CONTROL | ASSIGNED_TREATMENT

ASSIGNED_CONTROL
  -> OBSERVE
  -> RECOVERED | UNRESOLVED

ASSIGNED_TREATMENT
  -> WAIT_FOR_AUTHENTICATED_RETURN
  -> EXPOSED_RECOVERY_GATE
  -> PAYMENT_UPDATE_STARTED
  -> RECOVERED | UNRESOLVED
```

## Exclusions before exposure

- payment already resolved,
- user already entered an active payment/auth flow,
- customer identity uncertain,
- merchant manually resolved state,
- account/product state makes the gate inappropriate,
- safety/legal policy fails.

## Outcome metrics

Primary:
- recovered economic value per eligible opportunity.

Secondary:
- recovery rate,
- time to recovery,
- payment-update initiation,
- support contacts,
- user complaints,
- treatment exposure rate,
- native collision rate.

## Causal analysis

Truth is treatment versus randomized control at cohort level.

A recovered treatment payment is not independently claimed as incremental.

## Pilot commercial rule

Fixed pilot fee.

No recovery success fee.

## Kill criterion

Stop or redesign FM-PAY-001 if:
- incremental value is not economically meaningful,
- treatment harms customer experience,
- implementation/support cost consumes the value,
- effect is not stable enough to justify continued development.
