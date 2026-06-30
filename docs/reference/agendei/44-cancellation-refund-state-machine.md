# Cancellation and Refund State Machine

## Scope
This document consolidates the conceptual cancellation, penalty, and refund lifecycle for Agendei Quadras from the public reference set only.
It does not define private behavior or implementation detail.

## SM-CANCEL-001 — Cancellation Penalty and Refund Lifecycle

- Status: Observed
- Confidence: High
- Lifecycle subject: Booking cancellation, penalty evaluation, refund split, and retained-value handling
- Domain areas: Scheduling, Billing
- Related entities: `E-SCHED-005`, `E-SCHED-011`, `E-SCHED-012`, `E-BILL-009`, `E-BILL-010`
- Related business rules: `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013`
- Related journeys: `J-PAYMENT-004`
- Source reference: `05-booking-lifecycle.md`, `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`, `29-user-journeys-overview.md`, `32-payment-and-cancellation-journeys.md`, `35-domain-model-overview.md`, `36-scheduling-domain-model.md`, `37-billing-domain-model.md`
- Notes: The public example shows an 8h tolerance window, a 20% penalty, and an immediate 80% refund. The destination of the retained amount, no-show handling, and reschedule handling are not publicly confirmed.

### Conceptual States

| State | Status | Confidence | Meaning | Entry trigger | Exit trigger | Public unknowns |
|---|---|---|---|---|---|---|
| Booking Confirmed | Observed | High | The booking is active before cancellation starts. | A booking has already been confirmed. | The player cancels the booking. | Whether the player or facility can initiate cancellation is not public. |
| Cancellation Requested | Observed | High | A cancellation request has been initiated. | The booking is cancelled in the public flow. | The cancellation rule is evaluated. | Whether cancellation is automatic or manual is not public. |
| Cancellation Rule Evaluated | Observed | High | The tolerance window and percentage rule have been checked. | The cancellation request is processed. | The no-penalty or penalty branch is chosen. | Exact default configuration beyond the public example is not public. |
| No Penalty Applied | Inferred | Medium | The cancellation falls inside the tolerated window or uses a zero-penalty setup. | The rule evaluation resolves in favor of the customer. | The booking is closed without retention. | The public docs imply this branch but do not show it directly. |
| Penalty Applied | Observed | High | A percentage of the value is retained because the cancellation was late. | The cancellation is outside the tolerated window. | A partial refund is issued. | The exact default percentage outside the published example is not public. |
| Partial Refund Issued | Observed | High | The non-penalized amount is returned to the customer. | The penalty branch has been applied. | The retained amount remains unresolved in the public docs. | Whether the refund is always immediate is not fully public beyond the example. |
| Retained Amount Destination Unknown | Not publicly confirmed | Low | The public docs do not identify the final destination of the retained value. | The retained portion remains after the refund split. | Unknown. | The retained amount may remain with the platform, be repassed later, or be allocated in another way. |
| Cancelled | Observed | High | The booking is fully closed after the cancellation flow. | The cancellation process completes. | Unknown. | Whether a cancelled booking can be reopened is not public. |

### Transitions

| From | To | Trigger | Condition | Outcome | Status | Confidence | Related rules | Related journeys | Notes |
|---|---|---|---|---|---|---|---|---|---|
| Booking Confirmed | Cancellation Requested | Player cancels the booking. | A confirmed booking exists. | The cancellation flow begins. | Observed | High | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013` | `J-PAYMENT-004` | The public docs establish cancellation on confirmed bookings. |
| Cancellation Requested | Cancellation Rule Evaluated | The cancellation rule is checked. | A tolerance window and percentage rule exist. | The system or manager evaluates the penalty outcome. | Observed | High | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012` | `J-PAYMENT-004` | The public example is the clearest documented branch. |
| Cancellation Rule Evaluated | No Penalty Applied | The cancellation falls inside the tolerated window. | The public docs imply a no-penalty branch. | No amount is retained. | Inferred | Medium | `BR-BOOKING-015`, `BR-PAYMENT-011` | `J-PAYMENT-004` | The public material does not show this branch directly. |
| No Penalty Applied | Cancelled | The cancellation completes without retention. | The full-return branch applies. | The booking closes with a full return implied. | Inferred | Medium | `BR-BOOKING-015`, `BR-BOOKING-016` | `J-PAYMENT-004` | The no-penalty branch is derived from the tolerance model. |
| Cancellation Rule Evaluated | Penalty Applied | The cancellation falls outside the tolerated window. | The configured percentage applies. | A retained amount is calculated. | Observed | High | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012` | `J-PAYMENT-004` | The published example uses 20%. |
| Penalty Applied | Partial Refund Issued | The non-penalized portion is returned. | The public example applies. | 80% is refunded immediately in the example. | Observed | High | `BR-PAYMENT-011`, `BR-PAYMENT-012` | `J-PAYMENT-004` | Immediate refund timing is explicitly public in the example. |
| Partial Refund Issued | Retained Amount Destination Unknown | The retained portion remains after the split. | The public docs do not identify the final allocation. | The destination of the retained value remains ambiguous. | Not publicly confirmed | Low | `BR-PAYMENT-013` | `J-PAYMENT-004` | The split is explicit; the retained-value destination is not. |
| Retained Amount Destination Unknown | Cancelled | The cancellation process is fully completed. | The booking is closed after the split. | The booking ends. | Observed | High | `BR-BOOKING-015`, `BR-PAYMENT-013` | `J-PAYMENT-004` | This captures the booking state after the money split is handled. |

### Public Unknowns
- Exact cancellation initiator rights are not publicly visible.
- Whether penalty calculation is automatic or manual is not public.
- Whether refunds are immediate for every payment path is not public.
- Whether no-shows use the same rule as cancellations is not public.
- Whether reschedule avoids the penalty is not public.
- The final destination of the retained amount is not publicly confirmed.
