# FoundMoney — Attribution Engine v0.3

## Purpose

Separate three concepts:

1. **Observed recovery** — money was recovered.
2. **Action attribution** — a FoundMoney action preceded or participated in recovery.
3. **Causal incrementality** — treatment created additional value versus a valid control.

Only the third supports an incrementality claim.

## Pilot billing

The initial pilot uses a **fixed fee**.

There is no success-fee calculation during the validation pilot.

## Experiment estimand

For a randomized cohort:

```
Treatment revenue per opportunity = R_t / N_t
Control revenue per opportunity   = R_c / N_c

Estimated incremental revenue per opportunity
= R_t / N_t - R_c / N_c

Estimated total incremental value
= N_t * (R_t / N_t - R_c / N_c)
```

Do **not** use `max(0, ...)` period by period.

Negative observations remain part of the cumulative estimate.

## Statistical uncertainty

No arbitrary "attribution confidence multiplier" is applied to each conversion.

Instead track:
- standard error,
- confidence interval,
- cumulative estimate,
- predefined experiment horizon,
- experiment validity checks.

If a later commercial model uses performance pricing, a conservative estimator such as a lower confidence bound may be used if agreed contractually.

## Evidence classes

### A — Randomized causal evidence
Valid treatment/control experiment.

### B — Deterministic action attribution
A specific FoundMoney action can be linked to an outcome.

Useful for:
- audit,
- debugging,
- user explanation,
- experiment analysis.

**B is not sufficient by itself to claim causal uplift or bill gross recovery.**

### C — Modeled opportunity/value estimate
Useful for prioritization and forecasting.

Not causal billing evidence.

### D — Correlated revenue
Observed after FoundMoney activity without sufficient causal linkage.

Not billable as incrementality.

## Pilot randomization

Default initial split: **50/50**.

Rationale: maximize statistical information while the treatment effect is unknown.

A later production experiment may use a more treatment-heavy split once uplift is established.

## Immutable experiment record

Each eligible opportunity records:
- tenant_id,
- opportunity_id,
- customer/payment/invoice identity,
- eligibility timestamp,
- policy version,
- experiment_id,
- assignment,
- assignment timestamp,
- baseline/native-state snapshot,
- exposure timestamp if treated,
- outcome,
- realized economic value.

## Competing causes

Record, do not silently erase:
- Stripe-native retry/recovery,
- merchant manual intervention,
- other dunning/CRM actions,
- user-initiated payment before exposure.

The randomized estimand remains the primary causal truth.

## Customer explanation

Example:

> This payment was recovered after exposure to the FoundMoney in-app recovery gate. It is counted as a treatment outcome in experiment FM-PAY-001. Incremental value is calculated at cohort level versus the randomized control group; this individual payment is not independently claimed as causal uplift.
