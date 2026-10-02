# FoundMoney — Pilot Model v0.1

## Objective

Answer one question:

> Does a FoundMoney in-app payment recovery gate create meaningful incremental recovered revenue above Stripe-native recovery alone?

## Treatment

Eligible customer:
- active/recent subscription relationship,
- failed subscription payment,
- authenticated user returns to product,
- payment remains unresolved,
- no exclusion or safety rule is triggered.

Treatment experience:
1. User logs in or returns.
2. FoundMoney verifies unresolved payment state.
3. Product shows a merchant-branded payment recovery gate.
4. User can update payment through the merchant/Stripe-supported payment-update flow.
5. Outcome is logged.

Control:
- merchant's existing Stripe-native recovery setup,
- no FoundMoney in-app gate.

## Randomization

**50% treatment / 50% control** for the initial pilot.

Assignment happens before treatment exposure and is immutable.

Stratify when material by:
- amount/value band,
- subscription tenure,
- decline category,
- customer segment.

## Pilot pricing

Fixed pilot fee. Exact amount is a commercial decision per design partner.

The pilot fee pays for measurement and integration, not claimed recovery.

**No success fee during the first validation pilot.**

## Measurement

Do not use:

```
max(0, treatment - control)
```

per month.

Negative periods must remain negative in the cumulative estimate.

Core measure:

```
Cumulative incremental value
= cumulative treatment revenue
- expected treatment revenue at control revenue/opportunity
```

Report:
- treatment recovery rate,
- control recovery rate,
- absolute uplift,
- incremental value,
- confidence interval,
- cumulative effect,
- cost per incremental recovered NOK.

A future billable model should use a conservative causal estimate, potentially a lower confidence bound, not a one-sided zero clamp.

## Pilot success criteria

Pilot is promising only if:
- uplift is positive and economically material,
- direction is stable over time/strata,
- merchant experience is acceptable,
- collision with native recovery is low,
- incremental value can support viable unit economics.

## Kill criterion

If no meaningful incremental effect emerges over the agreed experiment horizon, do not rationalize the result with attribution rules. Stop or redesign the action.
