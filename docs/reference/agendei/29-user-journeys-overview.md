# User Journeys Overview

## Scope
This document consolidates user journeys from the existing Agendei public-reference docs and the consolidated business rules only.
It stays within the public reference set, separates observed facts from inferred journeys, and does not define Arena OS behavior.

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

## Journey Categories
- Player booking journeys
- Manager operations journeys
- Payment and cancellation journeys
- Engagement and CRM journeys

## Journey Inventory

| Journey ID | Journey name | Primary persona | Domain areas | Confidence | Related rules | Notes |
|---|---|---|---|---|---|---|
| `J-PLAYER-001` | Browse and discover courts before account creation | Player | Discovery, Scheduling | High | `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003` | Public browsing is visible before booking starts. |
| `J-PLAYER-002` | Book a court with online PIX payment | Player | Scheduling, Payments | High | `BR-BOOKING-003`, `BR-BOOKING-004`, `BR-BOOKING-005`, `BR-PAYMENT-005`, `BR-PAYMENT-008` | Confirmation is immediate; settlement is handled later. |
| `J-PLAYER-003` | Book a court with online card payment | Player | Scheduling, Payments | High | `BR-BOOKING-003`, `BR-BOOKING-004`, `BR-BOOKING-005`, `BR-PAYMENT-006`, `BR-PAYMENT-009`, `BR-PAYMENT-010` | Confirmation is immediate; settlement and repass sit in the payment layer. |
| `J-PLAYER-004` | Request booking with local payment | Player | Scheduling, Payments | High | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007` | Booking waits for manager acceptance. |
| `J-PLAYER-005` | Buy day use product | Player | Scheduling, Operations, Payments | High | `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014` | Day use is a separate product from hourly booking. |
| `J-PLAYER-006` | Use coupon during booking | Player | Payments, Promotions | Medium | `BR-PAYMENT-015`, `BR-OPS-011`, `BR-OPS-012` | Redemption timing is not publicly shown. |
| `J-PLAYER-007` | Invite friends and sort teams after booking | Player | Engagement, CRM | High | `BR-OPS-017`, `BR-OPS-018` | Match organization is tied to booking context. |
| `J-MANAGER-001` | Register facility and receive App Gestor access | Manager | Operations, Onboarding | High | `BR-OPS-001`, `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-PAYMENT-004` | Public signup and access are visible; full form fields are not. |
| `J-MANAGER-002` | Configure facility visibility in App Agendei | Manager | Operations, Scheduling | Medium | `BR-OPS-002`, `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003` | Visibility is inferred from onboarding and discovery docs. |
| `J-MANAGER-003` | Manage schedule and availability | Manager | Scheduling, Operations | High | `BR-BOOKING-008`, `BR-BOOKING-009`, `BR-BOOKING-010`, `BR-BOOKING-011`, `BR-OPS-003` | Covers avulso, fixed bookings, mensalistas, and multiple courts. |
| `J-MANAGER-004` | Accept local-payment booking request | Manager | Scheduling, Payments, Communication | High | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007` | Exact approval screen and statuses are not public. |
| `J-MANAGER-005` | Create day use product | Manager | Scheduling, Operations, Payments | High | `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014` | The manager defines the daily product before sale. |
| `J-MANAGER-006` | Activate Agendei Pay | Manager | Payments, Operations | High | `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-PAYMENT-004`, `BR-OPS-004` | Credentialing and approval precede PIX/card activation. |
| `J-MANAGER-007` | Share access with staff or partners | Manager | Operations, Permissions | High | `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008` | Profile boundaries are not fully public. |
| `J-MANAGER-008` | Use financial/cash-flow management | Manager | Finance, Operations | High | `BR-OPS-005`, `BR-PAYMENT-010`, `BR-PAYMENT-016` | Financial visibility centers on revenue, expense, profit, and cash flow. |
| `J-PAYMENT-001` | PIX booking payment and settlement | Player | Payments, Finance | High | `BR-PAYMENT-005`, `BR-PAYMENT-008`, `BR-PAYMENT-009` | Immediate confirmation is separate from settlement timing. |
| `J-PAYMENT-002` | Card booking payment and settlement | Player | Payments, Finance | High | `BR-PAYMENT-006`, `BR-PAYMENT-009`, `BR-PAYMENT-010` | Public card settlement timing is separate from confirmation. |
| `J-PAYMENT-003` | Local payment booking | Player | Payments, Scheduling | High | `BR-PAYMENT-007`, `BR-BOOKING-006`, `BR-BOOKING-007` | Confirmation waits for manager acceptance. |
| `J-PAYMENT-004` | Cancellation penalty and partial refund | Player | Payments, Cancellation | High | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013`, `BR-PAYMENT-014` | Public example uses an 8h / 20% split. |
| `J-PAYMENT-005` | Transfer/repass to facility | Manager | Payments, Finance | High | `BR-PAYMENT-001`, `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-PAYMENT-010` | Repasses follow settlement into the digital account. |
| `J-PAYMENT-006` | Financial management and cash flow | Manager | Finance, Operations | High | `BR-PAYMENT-016`, `BR-OPS-005`, `BR-PAYMENT-001` | The public surface shows finance concepts, not reconciliation detail. |
| `J-CRM-001` | Facility communicates with client through chat/messages | Manager | CRM, Communication | High | `BR-OPS-015` | The public chat scope and retention model are not public. |
| `J-CRM-002` | Manager receives operational notifications | Manager | CRM, Communication, Operations | Medium | `BR-OPS-016`, `BR-BOOKING-007`, `BR-BOOKING-014` | Booking confirmation notifications are inferred. |
| `J-CRM-003` | Customer becomes recurring/monthly player | Manager | CRM, Scheduling | Medium | `BR-BOOKING-009`, `BR-BOOKING-010`, `BR-OPS-003` | Public docs expose the recurring concept, not the commercial meaning. |
| `J-CRM-004` | Manager creates and player uses coupons | Manager | CRM, Promotions, Payments | Medium | `BR-PAYMENT-015`, `BR-OPS-011`, `BR-OPS-012` | Exact redemption, limits, and stacking are unknown. |
| `J-CRM-005` | Player organizes match after booking | Player | CRM, Engagement, Scheduling | High | `BR-OPS-017`, `BR-OPS-018` | Friend invites and team sorting are publicly visible. |
| `J-CRM-006` | Player participates in lessons or tournaments | Player | CRM, Operations, Engagement | Low | `BR-OPS-010`, `BR-OPS-011`, `BR-OPS-014` | The plan page names the features, but not the workflow. |

## Cross-Journey Dependencies

| Dependency | Related journey IDs | Related rule IDs | Confidence | Notes |
|---|---|---|---|---|
| Player booking with online payment depends on payment method | `J-PLAYER-002`, `J-PLAYER-003`, `J-PAYMENT-001`, `J-PAYMENT-002` | `BR-BOOKING-003`, `BR-BOOKING-004`, `BR-BOOKING-005`, `BR-PAYMENT-005`, `BR-PAYMENT-006`, `BR-PAYMENT-008`, `BR-PAYMENT-009`, `BR-PAYMENT-010` | High | PIX and card confirm immediately; settlement is handled in the payment layer. |
| Player booking with local payment depends on manager acceptance | `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003` | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007` | High | The request is not confirmed until the manager accepts it. |
| Day use purchase depends on manager-created day use product | `J-PLAYER-005`, `J-MANAGER-005` | `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014` | High | The product must exist before the player can buy it. |
| Cancellation and refund behavior depends on cancellation rule configuration | `J-PAYMENT-004` | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013`, `BR-PAYMENT-014` | High | The public example shows the split, but not every configuration detail. |
| Match organization depends on booking context | `J-PLAYER-007`, `J-CRM-005` | `BR-OPS-017`, `BR-OPS-018` | Medium | Friend invitations and team sorting appear after a booking exists. |
| Staff schedule management depends on shared access and profile rules | `J-MANAGER-003`, `J-MANAGER-007` | `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008` | High | Staff access is public, but the permission matrix is not. |
| Facility visibility depends on manager onboarding and configuration | `J-MANAGER-001`, `J-MANAGER-002`, `J-PLAYER-001` | `BR-OPS-001`, `BR-OPS-002`, `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003` | High | Registration and setup precede player discovery. |
| Financial management depends on Agendei Pay activation | `J-MANAGER-006`, `J-MANAGER-008`, `J-PAYMENT-005`, `J-PAYMENT-006` | `BR-PAYMENT-001`, `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-PAYMENT-010`, `BR-PAYMENT-016`, `BR-OPS-004`, `BR-OPS-005` | High | The finance surface becomes meaningful after payment credentialing and settlement exist. |

## Not in Scope
This document does not define Arena OS behavior, database schema, APIs, architecture, or implementation details.
