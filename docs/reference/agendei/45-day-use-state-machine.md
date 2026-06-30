# Day Use State Machine

## Scope
This document consolidates the conceptual day-use product and purchase lifecycle for Agendei Quadras from the public reference set only.
It does not define private behavior or implementation detail.

## SM-DAYUSE-001 — Day Use Product and Purchase Lifecycle

- Status: Inferred
- Confidence: Medium
- Lifecycle subject: Manager-defined daily reservation product through player purchase and downstream usage handling
- Domain areas: Scheduling, Operations, Billing
- Related entities: `E-SCHED-009`, `E-SCHED-010`, `E-BILL-003`, `E-CRM-005`
- Related business rules: `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014`
- Related journeys: `J-MANAGER-005`, `J-PLAYER-005`
- Source reference: `03-modules.md`, `04-navigation.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `12-financial-capabilities.md`, `16-communication-and-chat.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `29-user-journeys-overview.md`, `30-player-booking-journeys.md`, `31-manager-operations-journeys.md`, `35-domain-model-overview.md`, `36-scheduling-domain-model.md`, `38-crm-engagement-domain-model.md`
- Notes: Public docs clearly show the manager-defined product, the player purchase branch, and the manager notification. The consumption, cancellation, and refund branches are not publicly detailed.

### Conceptual States

| State | Status | Confidence | Meaning | Entry trigger | Exit trigger | Public unknowns |
|---|---|---|---|---|---|---|
| Product Not Created | Inferred | Medium | The facility has not yet set up a day-use product. | The manager has not created the product. | The manager creates the product. | Exact visibility before creation is not public. |
| Product Configured | Observed | High | The manager has defined the day-use product details. | Manager creates the day-use product. | The product becomes available for purchase. | Exact internal label is not public. |
| Available for Purchase | Inferred | Medium | The player can buy the daily reservation product. | Product setup is complete. | The player buys the day-use product. | The public docs do not show an explicit publish control. |
| Purchased | Observed | High | The day-use sale has completed. | Player buys the daily reservation. | Manager is notified or the day-use date reaches usage. | Whether the purchase shares the same state model as hourly bookings is not public. |
| Manager Notified | Observed | High | The manager receives the public push notification for the day-use sale. | The purchase completes. | The usage date arrives or an unpublicized branch occurs. | Exact notification channel is not public beyond the push wording. |
| Consumption / Usage Unknown | Not publicly confirmed | Low | The public docs do not explain how the reservation is consumed or tracked on the day of use. | The day-use date arrives or the customer uses the reservation. | Unknown. | Usage tracking and court blocking are not public. |
| Refund / Cancellation Unknown | Not publicly confirmed | Low | The public docs do not show how day-use cancellation or refund works. | A cancellation or refund is requested. | Unknown. | Refund timing and penalty behavior are not public. |

### Transitions

| From | To | Trigger | Condition | Outcome | Status | Confidence | Related rules | Related journeys | Notes |
|---|---|---|---|---|---|---|---|---|---|
| Product Not Created | Product Configured | Manager creates the day-use product. | The facility wants to offer a daily reservation. | The day-use product is defined. | Observed | High | `BR-BOOKING-013` | `J-MANAGER-005` | The public day-use page lists the setup fields. |
| Product Configured | Available for Purchase | Manager finishes setup and the product is visible to players. | The product is live in the public flow. | Players can buy the day-use product. | Inferred | Medium | `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014` | `J-MANAGER-005`, `J-PLAYER-005` | The public docs do not show an explicit publish step. |
| Available for Purchase | Purchased | Player buys the day-use product. | The public sale flow is completed. | The sale completes. | Observed | High | `BR-BOOKING-012`, `BR-BOOKING-014` | `J-PLAYER-005` | Day use is a separate purchase branch. |
| Purchased | Manager Notified | The purchase completes. | Push notification is enabled. | The manager receives an alert. | Observed | High | `BR-BOOKING-014` | `J-MANAGER-005`, `J-PLAYER-005` | The public docs explicitly mention the notification. |
| Manager Notified | Consumption / Usage Unknown | The day-use date arrives or the reservation is used. | The public docs do not describe the consumption rules. | Usage handling is not public. | Not publicly confirmed | Low | `BR-BOOKING-012`, `BR-BOOKING-014` | `J-MANAGER-005`, `J-PLAYER-005` | Usage and agenda-blocking behavior are not public. |
| Purchased | Refund / Cancellation Unknown | A cancellation or refund is requested. | The public docs do not define the branch. | Refund handling is not public. | Not publicly confirmed | Low | `BR-BOOKING-012`, `BR-BOOKING-014` | `J-MANAGER-005`, `J-PLAYER-005` | Cancellation behavior for day use is not documented. |

### Public Unknowns
- Whether day use blocks court availability like an hourly booking is not public.
- Whether day use shares the same status model as hourly reservations is not public.
- How the reserved day is consumed or tracked is not public.
- Whether day use can be cancelled or refunded is not public.
- Whether day use can be purchased with the same payment branches as hourly bookings is not public.
