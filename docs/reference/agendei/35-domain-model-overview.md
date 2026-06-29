# Domain Model Overview

## Scope
This document consolidates conceptual business entities from the existing Agendei public-reference docs, business rules, and user journeys only.
It is not a database schema.
It is not an architecture model.
It is not an Arena OS model.
It is a reference-product conceptual model.

## Source Documents

- `01-product-overview.md`
- `02-personas.md`
- `03-modules.md`
- `04-navigation.md`
- `05-booking-lifecycle.md`
- `06-scheduling-capabilities.md`
- `07-scheduling-entities.md`
- `09-payments-overview.md`
- `10-agendei-pay.md`
- `11-cancellation-penalties-and-refunds.md`
- `12-financial-capabilities.md`
- `14-customer-relationship-overview.md`
- `15-client-profile-and-history.md`
- `16-communication-and-chat.md`
- `17-engagement-coupons-and-match-organization.md`
- `19-manager-operations-overview.md`
- `20-facility-onboarding-and-configuration.md`
- `21-shared-management-and-permissions.md`
- `22-plans-tiers-and-feature-packaging.md`
- `24-business-rules-overview.md`
- `25-booking-business-rules.md`
- `26-payment-business-rules.md`
- `27-operations-business-rules.md`
- `28-business-rules-open-questions.md`
- `29-user-journeys-overview.md`
- `30-player-booking-journeys.md`
- `31-manager-operations-journeys.md`
- `32-payment-and-cancellation-journeys.md`
- `33-engagement-and-crm-journeys.md`
- `34-user-journeys-open-questions.md`

## Domain Areas

- Scheduling: courts, agendas, slots, bookings, day use, and cancellation behavior.
- Billing: payments, settlement, repasses, refunds, coupons, and announced financial features.
- CRM and engagement: customer relationship, chat, notifications, match organization, and social proof.
- Operations and permissions: registration, visibility, shared access, plan packaging, staff control, support, and announced AI assistance.

## Entity Inventory

This table references all conceptual entities defined in `36-scheduling-domain-model.md`, `37-billing-domain-model.md`, `38-crm-engagement-domain-model.md`, and `39-operations-permissions-domain-model.md`.

| Entity ID | Entity name | Domain area | Status | Confidence | Related rules | Related journeys | Notes |
|---|---|---|---|---|---|---|---|
| `E-SCHED-001` | Facility / Quadra Esportiva | Scheduling | Observed | High | `BR-BOOKING-011`, `BR-OPS-001`, `BR-OPS-003` | `J-MANAGER-001`, `J-MANAGER-002`, `J-MANAGER-003`, `J-PLAYER-001` | Multi-court operating unit. |
| `E-SCHED-002` | Court / Quadra | Scheduling | Observed | High | `BR-BOOKING-003`, `BR-BOOKING-004`, `BR-BOOKING-011` | `J-PLAYER-001`, `J-PLAYER-002`, `J-MANAGER-002`, `J-MANAGER-003`, `J-MANAGER-005` | Individual rentable surface. |
| `E-SCHED-003` | Agenda / Schedule | Scheduling | Observed | High | `BR-BOOKING-003`, `BR-BOOKING-004`, `BR-BOOKING-015` | `J-PLAYER-001`, `J-PLAYER-002`, `J-MANAGER-003` | Court-facing schedule. |
| `E-SCHED-004` | Available Time Slot / Horário Disponível | Scheduling | Observed | High | `BR-BOOKING-003`, `BR-BOOKING-004` | `J-PLAYER-001`, `J-PLAYER-002`, `J-PLAYER-004` | Bookable opening. |
| `E-SCHED-005` | Booking / Agendamento | Scheduling, Billing, Operations | Observed | High | `BR-BOOKING-004`, `BR-BOOKING-005`, `BR-BOOKING-006`, `BR-BOOKING-015` | `J-PLAYER-002`, `J-PLAYER-003`, `J-PLAYER-004`, `J-MANAGER-003`, `J-MANAGER-004`, `J-PAYMENT-003`, `J-PAYMENT-004` | Core reservation entity. |
| `E-SCHED-006` | One-off Booking / Agendamento Avulso | Scheduling | Observed | High | `BR-BOOKING-008`, `BR-OPS-003` | `J-MANAGER-003` | Single reservation. |
| `E-SCHED-007` | Fixed Booking / Agendamento Fixo | Scheduling | Observed | High | `BR-BOOKING-009`, `BR-BOOKING-010`, `BR-OPS-003` | `J-MANAGER-003`, `J-CRM-003` | Recurring slot. |
| `E-SCHED-008` | Monthly Player Relationship / Mensalista | Scheduling, CRM | Observed | High | `BR-BOOKING-010`, `BR-OPS-003` | `J-MANAGER-003`, `J-CRM-003` | Recurring customer relationship. |
| `E-SCHED-009` | Day Use Product / Diária | Scheduling, Operations, Billing | Observed | High | `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014` | `J-MANAGER-005`, `J-PLAYER-005` | Separate daily product. |
| `E-SCHED-010` | Day Use Purchase | Scheduling, Billing, Operations | Observed | High | `BR-BOOKING-012`, `BR-BOOKING-014`, `BR-PAYMENT-005` | `J-MANAGER-005`, `J-PLAYER-005` | Daily sale event. |
| `E-SCHED-011` | Cancellation | Scheduling, Billing | Observed | High | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011` | `J-PAYMENT-004` | Booking termination. |
| `E-SCHED-012` | Cancellation Rule | Scheduling, Billing | Observed | High | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-012` | `J-PAYMENT-004` | Timing/percentage rule. |
| `E-BILL-001` | Agendei Pay | Billing, Operations | Observed | High | `BR-PAYMENT-001`, `BR-PAYMENT-002`, `BR-PAYMENT-010`, `BR-OPS-004` | `J-MANAGER-006`, `J-PAYMENT-001`, `J-PAYMENT-005` | Financial layer. |
| `E-BILL-002` | Digital Account | Billing, Operations | Observed | High | `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-PAYMENT-010` | `J-MANAGER-006`, `J-PAYMENT-001`, `J-PAYMENT-005` | Settlement wallet. |
| `E-BILL-003` | Payment | Billing, Scheduling | Observed | High | `BR-BOOKING-005`, `BR-BOOKING-006`, `BR-PAYMENT-005`, `BR-PAYMENT-007` | `J-PLAYER-002`, `J-PLAYER-003`, `J-PLAYER-004`, `J-PAYMENT-001`, `J-PAYMENT-003` | Money movement. |
| `E-BILL-004` | PIX Payment | Billing | Observed | High | `BR-PAYMENT-005`, `BR-PAYMENT-008`, `BR-PAYMENT-014` | `J-PLAYER-002`, `J-PAYMENT-001` | PIX rail. |
| `E-BILL-005` | Card Payment | Billing | Observed | High | `BR-PAYMENT-006`, `BR-PAYMENT-009` | `J-PLAYER-003`, `J-PAYMENT-002` | Card rail. |
| `E-BILL-006` | Local Payment | Billing, Scheduling | Observed | High | `BR-PAYMENT-007`, `BR-BOOKING-006`, `BR-BOOKING-007` | `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003` | Pay at venue. |
| `E-BILL-007` | Repass / Transfer | Billing, Operations | Observed | High | `BR-PAYMENT-010`, `BR-OPS-004` | `J-PAYMENT-005`, `J-MANAGER-008` | Money out of account. |
| `E-BILL-008` | Settlement / Availability | Billing | Observed | High | `BR-PAYMENT-008`, `BR-PAYMENT-009`, `BR-PAYMENT-010` | `J-PAYMENT-001`, `J-PAYMENT-002`, `J-PAYMENT-005` | Funds availability timing. |
| `E-BILL-009` | Cancellation Penalty | Billing, Scheduling | Observed | High | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011` | `J-PAYMENT-004` | Retained value. |
| `E-BILL-010` | Refund | Billing, Scheduling | Observed | High | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-012` | `J-PAYMENT-004` | Non-penalized amount returned. |
| `E-BILL-011` | Coupon / Discount | Billing, CRM | Observed | High | `BR-PAYMENT-015`, `BR-OPS-011`, `BR-OPS-012` | `J-PLAYER-006`, `J-CRM-004` | Discount instrument. |
| `E-BILL-012` | Cash Flow / Financial Management | Billing, Operations | Observed | High | `BR-PAYMENT-016`, `BR-OPS-005` | `J-MANAGER-008`, `J-PAYMENT-006` | Finance view. |
| `E-BILL-013` | Charge / Cobrança | Billing, Operations | Observed | Medium | `BR-PAYMENT-017`, `BR-OPS-013` | `J-MANAGER-008` | Coming soon. |
| `E-BILL-014` | Material Rental Revenue | Billing, Operations | Observed | Medium | `BR-PAYMENT-018`, `BR-OPS-013` | `J-MANAGER-008` | Coming soon. |
| `E-CRM-001` | Player / Client / User | CRM, Engagement, Scheduling, Billing | Observed | High | `BR-BOOKING-001`, `BR-BOOKING-004`, `BR-PAYMENT-005`, `BR-OPS-017` | `J-PLAYER-001`, `J-PLAYER-007`, `J-PAYMENT-001`, `J-CRM-001` | Customer side. |
| `E-CRM-002` | Customer Profile | CRM, Operations | Inferred | Medium | `BR-BOOKING-001`, `BR-OPS-015`, `BR-PAYMENT-015` | `J-CRM-001`, `J-CRM-003`, `J-CRM-004` | Facility-facing identity. |
| `E-CRM-003` | Customer History | CRM, Operations, Billing | Inferred | Medium | `BR-OPS-016`, `BR-PAYMENT-016` | `J-CRM-001`, `J-CRM-002`, `J-CRM-003` | Interaction record. |
| `E-CRM-004` | Chat / Message Channel | CRM, Communication, Operations | Observed | High | `BR-OPS-015`, `BR-OPS-016` | `J-CRM-001`, `J-CRM-002` | In-app communication. |
| `E-CRM-005` | Operational Notification | CRM, Communication, Operations | Observed | High | `BR-BOOKING-007`, `BR-BOOKING-014`, `BR-OPS-016` | `J-CRM-002`, `J-MANAGER-004`, `J-MANAGER-005` | Alerts. |
| `E-CRM-006` | Invited Friend | CRM, Engagement | Observed | High | `BR-OPS-017` | `J-PLAYER-007`, `J-CRM-005` | Invited participant. |
| `E-CRM-007` | Match | CRM, Engagement, Scheduling | Observed | High | `BR-OPS-017`, `BR-OPS-018` | `J-PLAYER-007`, `J-CRM-005` | Organized play context. |
| `E-CRM-008` | Team Sorting | CRM, Engagement | Observed | High | `BR-OPS-018` | `J-PLAYER-007`, `J-CRM-005` | Team formation. |
| `E-CRM-009` | Lesson / Escolinha Participation | CRM, Operations, Engagement | Observed | Medium | `BR-OPS-010`, `BR-OPS-011` | `J-CRM-006` | Plan-visible feature. |
| `E-CRM-010` | Tournament Registration | CRM, Operations, Engagement | Observed | Medium | `BR-OPS-011`, `BR-OPS-014` | `J-CRM-006` | Plan-visible feature. |
| `E-CRM-011` | Testimonial / Social Proof | CRM, Marketing | Observed | High | None directly consolidated | None directly consolidated | Landing-page trust. |
| `E-OPS-001` | Manager / Facility Owner | Operations, Permissions, Scheduling, Billing | Observed | High | `BR-OPS-001`, `BR-OPS-003`, `BR-OPS-005` | `J-MANAGER-001`, `J-MANAGER-003`, `J-MANAGER-008` | Operator role. |
| `E-OPS-002` | Staff / Employee | Operations, Permissions, Scheduling | Observed | High | `BR-OPS-007`, `BR-OPS-010`, `BR-OPS-012` | `J-MANAGER-003`, `J-MANAGER-007` | Delegated employee. |
| `E-OPS-003` | Partner / Co-manager | Operations, Permissions | Observed | High | `BR-OPS-006`, `BR-OPS-008` | `J-MANAGER-007` | Shared responsibility. |
| `E-OPS-004` | Shared Access Profile | Operations, Permissions | Inferred | Medium | `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008` | `J-MANAGER-007` | Delegated access scope. |
| `E-OPS-005` | Staff Control | Operations, Permissions | Observed | High | `BR-OPS-010`, `BR-OPS-012` | `J-MANAGER-007` | Plan-visible staff access. |
| `E-OPS-006` | Facility Registration | Operations, Billing | Observed | High | `BR-OPS-001`, `BR-PAYMENT-002`, `BR-PAYMENT-004` | `J-MANAGER-001`, `J-MANAGER-006` | Public signup. |
| `E-OPS-007` | Facility Visibility / Publishing | Operations, Scheduling | Inferred | Medium | `BR-OPS-002`, `BR-BOOKING-001`, `BR-BOOKING-003` | `J-MANAGER-002`, `J-PLAYER-001` | Player discoverability. |
| `E-OPS-008` | Plan / Tier | Operations, Billing | Observed | High | `BR-OPS-009`, `BR-OPS-010`, `BR-OPS-014` | `J-MANAGER-008`, `J-CRM-006` | Public packaging. |
| `E-OPS-009` | Central de Atendimento | Operations, Support | Observed | Medium | `BR-OPS-009` | None directly consolidated | Support capability. |
| `E-OPS-010` | AI Management / Gestão Inteligente com IA | Operations, Automation | Observed | High | `BR-OPS-014` | None directly consolidated | Coming soon. |

## Cross-Domain Relationships

| Relationship | Source entity | Target entity | Status | Confidence | Related rules | Related journeys | Notes |
|---|---|---|---|---|---|---|---|
| A facility manages courts. | `E-SCHED-001` | `E-SCHED-002` | Observed | High | `BR-BOOKING-011`, `BR-OPS-003` | `J-MANAGER-003` | Multi-court operation is a core public feature. |
| A court exposes an agenda. | `E-SCHED-002` | `E-SCHED-003` | Observed | High | `BR-BOOKING-003`, `BR-BOOKING-004` | `J-PLAYER-001`, `J-PLAYER-002` | The agenda is the public schedule for the court. |
| An agenda contains available slots. | `E-SCHED-003` | `E-SCHED-004` | Observed | High | `BR-BOOKING-003`, `BR-BOOKING-004` | `J-PLAYER-001`, `J-PLAYER-002` | Slots are what the player selects. |
| A player creates a booking. | `E-CRM-001` | `E-SCHED-005` | Observed | High | `BR-BOOKING-004`, `BR-BOOKING-005`, `BR-BOOKING-006` | `J-PLAYER-002`, `J-PLAYER-003`, `J-PLAYER-004` | The booking begins in the player flow. |
| A booking uses a payment method. | `E-SCHED-005` | `E-BILL-003` | Observed | High | `BR-BOOKING-005`, `BR-BOOKING-006`, `BR-PAYMENT-005` | `J-PLAYER-002`, `J-PLAYER-003`, `J-PLAYER-004` | Payment choice drives confirmation behavior. |
| Online payment confirms the booking. | `E-BILL-004`, `E-BILL-005` | `E-SCHED-005` | Observed | High | `BR-PAYMENT-005`, `BR-PAYMENT-006` | `J-PLAYER-002`, `J-PLAYER-003` | PIX and card confirm immediately. |
| Local payment requires manager acceptance. | `E-BILL-006` | `E-SCHED-005` | Observed | High | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007` | `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003` | Pay-at-facility bookings stay pending. |
| A booking may be cancelled. | `E-SCHED-005` | `E-SCHED-011` | Observed | High | `BR-BOOKING-015`, `BR-BOOKING-016` | `J-PAYMENT-004` | Cancellation is part of the public lifecycle. |
| Cancellation may create penalty and refund behavior. | `E-SCHED-011` | `E-BILL-009`, `E-BILL-010` | Observed | High | `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013` | `J-PAYMENT-004` | The public example shows a split between retention and refund. |
| A manager creates a day use product. | `E-OPS-001` | `E-SCHED-009` | Observed | High | `BR-BOOKING-013`, `BR-BOOKING-014` | `J-MANAGER-005` | The manager defines the daily product first. |
| A player buys day use product. | `E-CRM-001` | `E-SCHED-010` | Observed | High | `BR-BOOKING-012`, `BR-BOOKING-014` | `J-PLAYER-005` | Day use is sold as a separate purchase flow. |
| A manager creates shared access for staff and partners. | `E-OPS-001` | `E-OPS-002`, `E-OPS-003`, `E-OPS-004` | Observed | High | `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008` | `J-MANAGER-007` | Shared management is a public operating pattern. |
| Staff may manage schedules. | `E-OPS-002` | `E-SCHED-003` | Observed | High | `BR-OPS-007`, `BR-OPS-003` | `J-MANAGER-003`, `J-MANAGER-007` | The public docs confirm schedule-management access. |
| A manager creates coupons. | `E-OPS-001` | `E-BILL-011` | Observed | High | `BR-PAYMENT-015`, `BR-OPS-011`, `BR-OPS-012` | `J-PLAYER-006`, `J-CRM-004` | Custom coupons are tied to plan visibility. |
| A player uses coupons. | `E-CRM-001` | `E-BILL-011` | Observed | High | `BR-PAYMENT-015` | `J-PLAYER-006`, `J-CRM-004` | Coupon use occurs in the booking context. |
| A player invites friends. | `E-CRM-001` | `E-CRM-006` | Observed | High | `BR-OPS-017` | `J-PLAYER-007`, `J-CRM-005` | Friend invitations are part of match organization. |
| A player sorts teams. | `E-CRM-001` | `E-CRM-008` | Observed | High | `BR-OPS-018` | `J-PLAYER-007`, `J-CRM-005` | Team sorting is publicly visible. |
| A manager activates Agendei Pay. | `E-OPS-001` | `E-BILL-001` | Observed | High | `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-OPS-004` | `J-MANAGER-006` | Activation follows credentialing and approval. |
| Payment settles into a digital account or bank account. | `E-BILL-003` | `E-BILL-008` | Observed | High | `BR-PAYMENT-008`, `BR-PAYMENT-009`, `BR-PAYMENT-010` | `J-PAYMENT-001`, `J-PAYMENT-002`, `J-PAYMENT-005` | Funds become available in the digital account first; bank-account movement follows through repass. |

## Conceptual Boundary Notes

- Internal screens are intentionally not modeled.
- Private APIs are intentionally not modeled.
- Exact statuses are intentionally not modeled beyond what the public docs show.
- Exact database fields are intentionally not modeled.
- Provider integrations are intentionally not modeled.
- Authentication internals are intentionally not modeled.
- Hidden permission matrices are intentionally not modeled.
- Release timing for announced features is intentionally not modeled.
- No claim in this document should be read as an Arena OS requirement.

## Not in Scope

This document does not define Arena OS behavior, database schema, APIs, architecture, or implementation.
