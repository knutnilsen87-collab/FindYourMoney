# FoundMoney — Native Baseline & Product Wedge v0.2

## Problem

FoundMoney must create value **above** the merchant's existing Stripe-native recovery setup.

Failed-payment volume is not itself a FoundMoney opportunity.

## Native baseline

Before any action, FoundMoney records the merchant's active recovery configuration and relevant native recovery state.

The baseline may include:
- Stripe retry logic,
- native payment-update flows,
- failed-payment communication,
- card/account updater behavior,
- merchant-side dunning or CRM actions.

Anything recovered by baseline behavior is not automatically FoundMoney credit.

## Chosen pilot wedge

The first concrete intervention is:

> **Authenticated in-app payment recovery gate after a failed subscription payment.**

Why this action:
- it is distinct from merely waiting for Stripe-native retries;
- it uses a product-session moment Stripe does not control by itself;
- the treatment can be randomized cleanly;
- the outcome can be tied to a known customer/payment identity;
- it avoids broad marketing outreach in the first test.

## What is not being tested

- custom retry timing as the primary intervention,
- abandoned-cart email/SMS,
- generic churn messaging,
- discounts,
- autonomous sales outreach.

## Recovery Auditor

The read-only onboarding surface should report:

1. revenue at risk,
2. native recovery already observed,
3. unresolved failed payments,
4. customers eligible for the experiment,
5. experiment results once treatment is active.

Do not label unresolved historical value as "recoverable revenue" unless evidence supports that claim.

## Product boundary

If this single intervention cannot create measurable incremental value beyond native Stripe recovery, FoundMoney should not expand scope to hide the failed thesis.
