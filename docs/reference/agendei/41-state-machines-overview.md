# State Machines Overview

## Scope
This document consolidates conceptual lifecycle states from existing Agendei public-reference docs, business rules, journeys, and the domain model only.
It is not a database schema.
It is not an architecture model.
It is not an Arena OS model.
It is not a technical event model.
It is a reference-product conceptual lifecycle model.

## Source Documents
- `24-business-rules-overview.md`
- `25-booking-business-rules.md`
- `26-payment-business-rules.md`
- `27-operations-business-rules.md`
- `29-user-journeys-overview.md`
- `30-player-booking-journeys.md`
- `31-manager-operations-journeys.md`
- `32-payment-and-cancellation-journeys.md`
- `33-engagement-and-crm-journeys.md`
- `35-domain-model-overview.md`
- `36-scheduling-domain-model.md`
- `37-billing-domain-model.md`
- `38-crm-engagement-domain-model.md`
- `39-operations-permissions-domain-model.md`
- Earlier source docs used directly in the reference set: `01-product-overview.md`, `02-personas.md`, `03-modules.md`, `04-navigation.md`, `05-booking-lifecycle.md`, `09-payments-overview.md`, `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`, `12-financial-capabilities.md`, `16-communication-and-chat.md`, `17-engagement-coupons-and-match-organization.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `21-shared-management-and-permissions.md`, `22-plans-tiers-and-feature-packaging.md`

## State Machine Inventory

| State machine ID | Name | Lifecycle subject | Domain areas | Status | Confidence | Related entities | Related rules | Related journeys | Notes |
|---|---|---|---|---|---|---|---|---|---|
| `SM-BOOKING-001` | Standard Booking Lifecycle | Hourly court booking from discovery through confirmation and cancellation | Scheduling, Billing, Operations | Observed | High | `E-SCHED-004`, `E-SCHED-005`, `E-BILL-003`, `E-BILL-006`, `E-BILL-009`, `E-BILL-010` | `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003`, `BR-BOOKING-004`, `BR-BOOKING-005`, `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-005`, `BR-PAYMENT-006`, `BR-PAYMENT-007` | `J-PLAYER-001`, `J-PLAYER-002`, `J-PLAYER-003`, `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003`, `J-PAYMENT-004` | Public docs show discovery, slot selection, payment branching, confirmation, and cancellation; exact internal labels and reschedule/no-show handling are not public. |
| `SM-PAYMENT-001` | Online Payment and Settlement Lifecycle | PIX and card booking payment from confirmation through settlement and repass | Billing, Scheduling, Finance | Observed | High | `E-BILL-001`, `E-BILL-002`, `E-BILL-003`, `E-BILL-004`, `E-BILL-005`, `E-BILL-007`, `E-BILL-008` | `BR-PAYMENT-005`, `BR-PAYMENT-006`, `BR-PAYMENT-008`, `BR-PAYMENT-009`, `BR-PAYMENT-010`, `BR-PAYMENT-013`, `BR-PAYMENT-014`, `BR-PAYMENT-016` | `J-PAYMENT-001`, `J-PAYMENT-002`, `J-PAYMENT-005`, `J-PAYMENT-006` | Public docs separate immediate booking confirmation from later availability and repass timing. |
| `SM-PAYMENT-002` | Local Payment Lifecycle | Pay-at-facility booking request through manager acceptance and local collection | Billing, Scheduling, Operations | Inferred | Medium | `E-BILL-006`, `E-SCHED-005`, `E-OPS-001` | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007` | `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003` | The public flow is visible, but the exact ordering of acceptance, local collection, and final confirmation is not fully exposed. |
| `SM-CANCEL-001` | Cancellation Penalty and Refund Lifecycle | Booking cancellation, penalty evaluation, refund split, and retained-value handling | Scheduling, Billing | Observed | High | `E-SCHED-005`, `E-SCHED-011`, `E-SCHED-012`, `E-BILL-009`, `E-BILL-010` | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013` | `J-PAYMENT-004` | Public example shows an 8h tolerance window and 20% penalty, but the retained-amount destination is not fully public. |
| `SM-DAYUSE-001` | Day Use Product and Purchase Lifecycle | Manager-defined daily reservation product through player purchase and downstream usage handling | Scheduling, Operations, Billing | Inferred | Medium | `E-SCHED-009`, `E-SCHED-010`, `E-BILL-003`, `E-CRM-005` | `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014` | `J-MANAGER-005`, `J-PLAYER-005` | Public docs clearly show the product and purchase branch; the consumption and refund branches are not publicly detailed. |
| `SM-OPS-001` | Facility Onboarding and Visibility Lifecycle | Public facility registration through player-visible court publishing | Operations, Scheduling, Billing | Inferred | Medium | `E-OPS-006`, `E-OPS-007`, `E-SCHED-001`, `E-SCHED-002` | `BR-OPS-001`, `BR-OPS-002`, `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003` | `J-MANAGER-001`, `J-MANAGER-002`, `J-PLAYER-001` | Registration and setup are public; the exact publish/review workflow is not. |
| `SM-ACCESS-001` | Shared Access Lifecycle | Shared operational access for staff and partners, including schedule management | Operations, Permissions, Scheduling | Inferred | Medium | `E-OPS-001`, `E-OPS-002`, `E-OPS-003`, `E-OPS-004`, `E-OPS-005` | `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008`, `BR-OPS-010` | `J-MANAGER-007` | Public docs confirm profile-based shared access, but exact permission boundaries and revocation behavior are not public. |

## Cross-State-Machine Dependencies

| Dependency | Source state machine | Target state machine | Related entities | Related rules | Related journeys | Confidence | Notes |
|---|---|---|---|---|---|---|---|
| Booking confirmation depends on payment method state | `SM-PAYMENT-001` | `SM-BOOKING-001` | `E-SCHED-005`, `E-BILL-003`, `E-BILL-004`, `E-BILL-005`, `E-BILL-006` | `BR-BOOKING-005`, `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-005`, `BR-PAYMENT-006`, `BR-PAYMENT-007` | `J-PLAYER-002`, `J-PLAYER-003`, `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003` | High | Online PIX/card confirm immediately; local payment stays pending until manager acceptance. |
| Local-payment booking depends on manager acceptance | `SM-ACCESS-001` | `SM-BOOKING-001` | `E-OPS-001`, `E-OPS-002`, `E-SCHED-005`, `E-BILL-006` | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008` | `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003`, `J-MANAGER-007` | High | The manager side must be able to receive and accept the pay-at-facility request. |
| Cancellation/refund depends on booking and payment state | `SM-BOOKING-001` | `SM-CANCEL-001` | `E-SCHED-005`, `E-SCHED-011`, `E-SCHED-012`, `E-BILL-009`, `E-BILL-010`, `E-BILL-003` | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013` | `J-PAYMENT-004` | High | The public example is booking-based and uses the payment layer to split retained and refunded value. |
| Day use purchase depends on manager-created day use product | `SM-OPS-001` | `SM-DAYUSE-001` | `E-SCHED-009`, `E-SCHED-010`, `E-OPS-001`, `E-CRM-005` | `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014` | `J-MANAGER-005`, `J-PLAYER-005` | High | The daily product must exist before the player can buy it. |
| Repass depends on settlement state | `SM-PAYMENT-001` | `SM-PAYMENT-001` | `E-BILL-002`, `E-BILL-007`, `E-BILL-008` | `BR-PAYMENT-008`, `BR-PAYMENT-009`, `BR-PAYMENT-010` | `J-PAYMENT-001`, `J-PAYMENT-002`, `J-PAYMENT-005`, `J-PAYMENT-006` | High | Internal payment lifecycle dependency: funds must become available before repass or transfer. |
| Facility visibility depends on facility onboarding/configuration | `SM-OPS-001` | `SM-OPS-001` | `E-OPS-006`, `E-OPS-007`, `E-SCHED-001`, `E-SCHED-002` | `BR-OPS-001`, `BR-OPS-002`, `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003` | `J-MANAGER-001`, `J-MANAGER-002`, `J-PLAYER-001` | High | Internal onboarding dependency: registration and setup precede player discovery. |
| Staff schedule access depends on shared access state | `SM-ACCESS-001` | `SM-OPS-001` | `E-OPS-002`, `E-OPS-004`, `E-SCHED-003` | `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008`, `BR-OPS-010` | `J-MANAGER-003`, `J-MANAGER-007` | High | Staff can manage schedules only after shared access and profile scope exist. |

## Conceptual State Labels Disclaimer
Exact internal status labels are not publicly visible unless they are explicitly documented.
The state labels in files `42` to `46` are conceptual business labels derived from public-reference flows, not confirmed internal enums or API values.

## Not in Scope
This document does not define Arena OS behavior, database schema, APIs, architecture, implementation, or technical events.
