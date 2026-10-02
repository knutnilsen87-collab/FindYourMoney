# FoundMoney — Legal Design Norway/EU v0.2

> Product design note, not legal advice. Obtain external legal review before production launch.

## V1 legal simplification

The first pilot avoids abandoned-cart marketing outreach.

The chosen treatment is an **in-product payment recovery experience** presented to an authenticated customer in an existing subscription/payment relationship.

This reduces, but does not eliminate, legal and privacy obligations.

## Required legal/privacy controls

For every customer-facing action record:
- jurisdiction,
- purpose,
- channel/surface,
- controller/processor role,
- lawful-basis metadata where required,
- suppression/opt-out state where applicable,
- policy version.

## Data protection

FoundMoney must define:
- controller vs processor responsibilities,
- data processing agreement requirements,
- purpose limitation,
- data minimization,
- retention/deletion rules,
- subprocessors,
- access controls,
- tenant isolation.

Avoid storing card data that can remain within Stripe-supported payment surfaces.

## Marketing channels

Abandoned-cart email/SMS remains deferred.

Before FM-CART-001 is activated in Norway/EU, verify:
- marketing consent,
- existing-customer exception requirements,
- opt-out handling,
- channel-specific restrictions,
- merchant responsibility and documentation.

## Product rule

A payment-recovery label does not automatically make a communication "transactional." Classification depends on actual purpose and content.

## Launch gate

No production rollout without:
1. documented data flow,
2. DPA/subprocessor review,
3. security review,
4. external legal review of customer-facing recovery surfaces and any messaging flows.
