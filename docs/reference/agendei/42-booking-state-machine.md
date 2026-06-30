# Booking State Machine

## Scope
This document consolidates the conceptual booking lifecycle for Agendei Quadras from the public discovery flow through confirmation, cancellation, and the publicly unknown edge cases.
It stays within the public-reference set only.

## SM-BOOKING-001 — Standard Booking Lifecycle

- Status: Observed
- Confidence: High
- Lifecycle subject: Hourly court booking from public discovery through confirmation and cancellation
- Domain areas: Scheduling, Billing, Operations
- Related entities: `E-SCHED-004`, `E-SCHED-005`, `E-BILL-003`, `E-BILL-004`, `E-BILL-005`, `E-BILL-006`, `E-SCHED-011`, `E-BILL-009`, `E-BILL-010`
- Related business rules: `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003`, `BR-BOOKING-004`, `BR-BOOKING-005`, `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-005`, `BR-PAYMENT-006`, `BR-PAYMENT-007`, `BR-OPS-016`
- Related journeys: `J-PLAYER-001`, `J-PLAYER-002`, `J-PLAYER-003`, `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003`, `J-PAYMENT-004`
- Source reference: `05-booking-lifecycle.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `29-user-journeys-overview.md`, `30-player-booking-journeys.md`, `31-manager-operations-journeys.md`, `32-payment-and-cancellation-journeys.md`, `35-domain-model-overview.md`, `36-scheduling-domain-model.md`, `37-billing-domain-model.md`, `39-operations-permissions-domain-model.md`
- Notes: The public docs show the discovery flow, the slot-selection flow, the payment branch, confirmation timing, and cancellation behavior. Exact internal status labels, slot-hold behavior, reschedule behavior, and no-show handling are not publicly confirmed.

### Conceptual States

| State | Status | Confidence | Meaning | Entry trigger | Exit trigger | Public unknowns |
|---|---|---|---|---|---|---|
| Browsing | Observed | High | The player is looking at courts, locations, and visible agendas before committing to a booking. | Player opens the public app and starts discovering courts. | Player selects a visible court, day, and time. | Exact search modes and filters are not public. |
| Slot Selected | Observed | High | The player has chosen a visible day and time on a court agenda. | Player selects an available slot. | Player starts the booking flow. | Whether a slot is held during checkout is not public. |
| Booking Started | Inferred | Medium | The booking checkout has begun, but the booking is not yet on a payment branch. | Player starts booking from a selected slot. | Player chooses a payment method. | The public docs do not expose a named state for this step. |
| Payment Method Selected | Observed | High | The player has chosen how the booking will be paid. | Player chooses PIX, card, or local payment. | Booking confirms immediately or waits for manager acceptance. | Exact internal label is not public. |
| Waiting for Manager Acceptance | Observed | High | The booking is pending manager review on the local-payment branch. | Player chooses pay-at-facility. | Manager accepts the request or the request remains unresolved. | Exact request screen and acceptance action are not public. |
| Confirmed | Observed | High | The booking is active and publicly treated as confirmed. | Online payment confirms immediately or the manager accepts the local-payment request. | The booking is cancelled or moves into an unknown edge case. | Whether confirmation can be reversed later is not public. |
| Cancelled | Observed | High | The booking has been terminated through the public cancellation flow. | A cancellation is processed. | The booking is closed. | Whether the player or facility initiates cancellation is not public. |
| Outcome Unknown | Not publicly confirmed | Low | The public docs do not explain what happens in reschedule or no-show branches. | A confirmed booking reaches an unpublicized edge case. | Unknown. | Reschedule, no-show, and other nonstandard outcomes are not publicly described. |

### Transitions

| From | To | Trigger | Condition | Outcome | Status | Confidence | Related rules | Related journeys | Notes |
|---|---|---|---|---|---|---|---|---|---|
| Browsing | Slot Selected | Player selects a court, day, and time. | The court is visible and the slot is available. | A specific bookable slot is chosen. | Observed | High | `BR-BOOKING-002`, `BR-BOOKING-003`, `BR-BOOKING-004` | `J-PLAYER-001`, `J-PLAYER-002`, `J-PLAYER-003`, `J-PLAYER-004` | Slot availability comes from the public agenda. |
| Slot Selected | Booking Started | Player starts the booking flow. | The selected slot remains available. | Booking checkout begins. | Inferred | Medium | `BR-BOOKING-004` | `J-PLAYER-002`, `J-PLAYER-003`, `J-PLAYER-004` | The public docs do not name this step directly. |
| Booking Started | Payment Method Selected | Player chooses how to pay. | Online payment or pay-at-facility is available. | The booking enters a payment branch. | Observed | High | `BR-BOOKING-005`, `BR-BOOKING-006`, `BR-PAYMENT-005`, `BR-PAYMENT-006`, `BR-PAYMENT-007` | `J-PLAYER-002`, `J-PLAYER-003`, `J-PLAYER-004`, `J-PAYMENT-001`, `J-PAYMENT-002`, `J-PAYMENT-003` | Payment choice determines the confirmation path. |
| Payment Method Selected | Confirmed | Player chooses PIX or card and the payment is accepted. | The booking was submitted through the online payment path. | The booking is confirmed immediately after scheduling. | Observed | High | `BR-BOOKING-005`, `BR-PAYMENT-005`, `BR-PAYMENT-006` | `J-PLAYER-002`, `J-PLAYER-003`, `J-PAYMENT-001`, `J-PAYMENT-002` | Confirmation is immediate, but settlement is separate. |
| Payment Method Selected | Waiting for Manager Acceptance | Player chooses pay at facility. | The local-payment branch is selected. | The request waits for manager review. | Observed | High | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007` | `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003` | The public docs distinguish this from instant online confirmation. |
| Waiting for Manager Acceptance | Confirmed | Manager accepts the local-payment request. | The manager receives and accepts the request. | The booking becomes confirmed. | Observed | High | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007` | `J-MANAGER-004`, `J-PAYMENT-003` | The exact acceptance screen is not public. |
| Confirmed | Cancelled | Booking is cancelled. | A cancellation is processed through the public booking flow. | The booking ends and cancellation rules may apply. | Observed | High | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013` | `J-PAYMENT-004` | Penalty and refund handling is documented separately in the payment state machine. |
| Confirmed | Outcome Unknown | Booking reaches a reschedule or no-show branch. | The public docs do not describe the edge case. | Outcome is not public. | Not publicly confirmed | Low | `BR-BOOKING-015`, `BR-BOOKING-016` | `J-PAYMENT-004` | Reschedule and no-show behavior remain open questions. |

### Public Unknowns
- Exact internal booking status labels are not publicly visible.
- Slot-hold behavior during checkout is not public.
- Whether the player can cancel before manager acceptance is not public.
- Whether reschedule is treated as an edit or as a new booking is not public.
- How no-shows are represented in the lifecycle is not public.
- Whether day use shares this booking-state model is not public.
