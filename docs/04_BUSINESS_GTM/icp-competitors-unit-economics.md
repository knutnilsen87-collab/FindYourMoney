# FoundMoney — ICP, Competition & Unit Economics v0.2

## Pilot ICP

The first design partner should not be chosen because it is "SMB."

Choose a merchant where the experiment can resolve quickly.

Preferred characteristics:
- Stripe Billing subscriptions,
- meaningful monthly failed-payment volume,
- authenticated product usage after billing failure,
- sufficient transaction value,
- product team able to add an in-app recovery gate,
- existing Stripe-native recovery left enabled,
- relatively low compliance complexity.

## Key constraint

The in-app gate requires product integration.

This is not a pure "connect once and forget" onboarding model.

The pilot intentionally accepts more integration friction to test whether the intervention creates incremental value.

If validated, productization should reduce integration effort through an SDK/component.

## Competition

Stripe native recovery is the baseline.

Adjacent failed-payment/dunning vendors already compete on retry, messaging, recovery analytics and related workflows.

Therefore these are **not** defensible differentiators by themselves:
- "AI-powered recovery",
- performance pricing,
- retry optimization,
- basic dunning emails.

The first differentiator being tested is narrower:

> product-session-aware payment recovery measured against a randomized native-only control.

Before external use, current competitor feature/pricing claims must be re-verified.

## Pilot economics

Pilot revenue is a fixed fee.

Do not depend on success-fee revenue before effect size is known.

After validation, model unit economics using:

```
Eligible opportunities
x average economic value
x measured incremental uplift
= incremental merchant value
```

Then evaluate a commercial fee model.

Example sensitivity only:

```
2,000 opportunities/month
x 1,000 NOK average value
x 3 percentage-point uplift
= 60,000 NOK incremental value/month
```

A 15% performance component would equal 9,000 NOK/month, but **15% is not a locked production price**.

At:
- 500 opportunities -> 15,000 NOK incremental value; 2,250 NOK at 15%.
- 100 opportunities -> 3,000 NOK incremental value; 450 NOK at 15%.

This demonstrates why very low-volume merchants may not support performance-only economics.

## Pilot commercial structure

Recommended validation structure:
- fixed integration/measurement fee,
- predefined experiment window,
- no recovery success fee,
- customer receives full treatment/control report.

After validation, choose among:
- fixed SaaS fee,
- fixed + performance,
- performance-only above a volume/evidence threshold.

## Go/no-go metrics

- incremental recovered value / opportunity,
- confidence interval and cumulative estimate,
- implementation cost,
- support burden,
- customer-experience impact,
- treatment exposure rate,
- native collision rate,
- time to statistically/economically useful evidence.

## Strategic boundary

Do not expand to upsell, ad optimization, price testing or generic experimentation until failed-payment recovery earns the right to expand.
