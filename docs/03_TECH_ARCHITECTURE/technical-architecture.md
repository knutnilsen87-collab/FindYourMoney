# FoundMoney — Technical Architecture v0.2

## Architecture principle

Deterministic systems own:
- identity,
- eligibility,
- experiment assignment,
- permissions,
- safety/legal gates,
- attribution calculations,
- billing records.

LLMs may assist with analysis or explanations but do not control money movement or causal/billing truth.

## Pilot components

### 1. Stripe Connector

Consumes required Stripe events/API state for:
- invoices,
- payment status,
- subscriptions,
- customers,
- supported payment-update flows.

### 2. Identity Resolver

Maps merchant user identity to Stripe customer/payment entities.

### 3. Opportunity Engine

Creates idempotent FM-PAY-001 opportunities from failed-payment events.

### 4. Experiment Service

Responsibilities:
- deterministic random assignment,
- 50/50 pilot allocation,
- immutable experiment assignment,
- optional stratification,
- exposure tracking.

### 5. Native State Snapshot

Stores what the merchant/native recovery configuration/state looked like at eligibility time.

### 6. Policy Engine

Checks:
- merchant enablement,
- eligibility,
- legal/safety gates,
- suppressions,
- exposure rules.

### 7. In-App Recovery API

Merchant product asks:

```
Should this authenticated user see the recovery gate?
```

Response is deterministic and includes an opportunity/action token.

### 8. Recovery Surface

Merchant-controlled UI or SDK component that:
- explains payment problem,
- sends customer into supported update/payment flow,
- never handles raw card data itself.

### 9. Outcome Processor

Links payment resolution back to opportunity and experiment assignment.

### 10. Attribution Service

Computes cumulative treatment/control metrics and statistical uncertainty.

No monthly zero-clamping.

### 11. Audit Log

Append-only records for:
- input event,
- policy version,
- assignment,
- eligibility,
- exposure,
- outcome,
- analysis version.

## Core entities

- Tenant
- CustomerIdentity
- PaymentFailure
- Opportunity
- NativeStateSnapshot
- PolicyVersion
- Experiment
- ExperimentAssignment
- Exposure
- Outcome
- AnalysisSnapshot
- AuditEvent

## Reliability

Non-negotiable:
- webhook idempotency,
- replay-safe processing,
- immutable assignment,
- durable queue,
- dead-letter handling,
- trace IDs,
- no duplicate treatment exposure.

## Security

- least-privilege Stripe scopes,
- secrets vault,
- encryption in transit/at rest,
- tenant isolation,
- retention/deletion policy,
- no storage of raw payment-card data.

## Deployment

Start as a modular monolith:
- API,
- worker,
- relational database,
- queue,
- append-only audit storage.

Do not introduce microservices until operational evidence requires them.
