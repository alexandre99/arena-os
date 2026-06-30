# Payment State Machine

## Scope
This document consolidates the conceptual payment lifecycle for Agendei Quadras, including online payment, settlement, repass, and the local-payment branch.
It stays within the public-reference set only.

## SM-PAYMENT-001 — Online Payment and Settlement Lifecycle

- Status: Observed
- Confidence: High
- Lifecycle subject: PIX and card booking payment from confirmation through settlement and repass
- Domain areas: Billing, Scheduling, Finance
- Related entities: `E-BILL-001`, `E-BILL-002`, `E-BILL-003`, `E-BILL-004`, `E-BILL-005`, `E-BILL-007`, `E-BILL-008`
- Related business rules: `BR-PAYMENT-001`, `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-PAYMENT-005`, `BR-PAYMENT-006`, `BR-PAYMENT-008`, `BR-PAYMENT-009`, `BR-PAYMENT-010`, `BR-PAYMENT-013`, `BR-PAYMENT-014`, `BR-PAYMENT-016`
- Related journeys: `J-PAYMENT-001`, `J-PAYMENT-002`, `J-PAYMENT-005`, `J-PAYMENT-006`
- Source reference: `09-payments-overview.md`, `10-agendei-pay.md`, `12-financial-capabilities.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `29-user-journeys-overview.md`, `32-payment-and-cancellation-journeys.md`, `35-domain-model-overview.md`, `37-billing-domain-model.md`, `31-manager-operations-journeys.md`, `20-facility-onboarding-and-configuration.md`
- Notes: The public docs clearly separate immediate booking confirmation from later fund availability and repass timing. Exact failure handling, reversal handling, and payment-method edge cases are not publicly confirmed.

### Conceptual States

| State | Status | Confidence | Meaning | Entry trigger | Exit trigger | Public unknowns |
|---|---|---|---|---|---|---|
| Payment Method Selected | Observed | High | The player has chosen PIX or card for the booking. | Player chooses an online payment method. | Payment is accepted or fails. | Whether multiple payment methods can be combined is not public. |
| Payment Confirmed | Observed | High | The online payment has been accepted in the public booking flow. | Online payment is approved. | The booking is confirmed or later reversed. | Exact status label shown to the player is not public. |
| Booking Confirmed | Observed | High | The booking is active after online payment. | Payment is confirmed in the online branch. | Settlement timing begins or the booking is cancelled. | Whether confirmation can later be reversed is not public. |
| Pending Settlement | Observed | High | Funds exist in the payment layer but are not yet available for transfer. | The scheduled match has not yet reached the settlement timing. | Funds become available in the digital account. | Exact pending-state label is not public. |
| Available for Repass | Observed | High | Funds can be moved out of the digital account. | Settlement timing is reached. | A transfer or repass is initiated. | Whether the same availability rule applies to every payout destination is not public. |
| Repassed | Observed | High | Funds have been moved to the facility or another destination outside the digital account. | Manager initiates a transfer or repass. | Money is no longer just waiting in the digital account. | Exact transfer timing rules beyond the public examples are not public. |
| Failed or Reversed Unknown | Not publicly confirmed | Low | The public docs do not show how failed online payments or later reversals are handled. | A payment does not complete or is later reversed. | Unknown. | Failure, reversal, dispute, and chargeback handling are not public. |

### Transitions

| From | To | Trigger | Condition | Outcome | Status | Confidence | Related rules | Related journeys | Notes |
|---|---|---|---|---|---|---|---|---|---|
| Payment Method Selected | Payment Confirmed | Player chooses PIX or card and the payment is accepted. | The booking is submitted through the online payment path. | The payment is accepted in the booking flow. | Observed | High | `BR-PAYMENT-005`, `BR-PAYMENT-006` | `J-PLAYER-002`, `J-PLAYER-003`, `J-PAYMENT-001`, `J-PAYMENT-002` | Online payment confirms immediately in public docs. |
| Payment Confirmed | Booking Confirmed | Online payment completes the booking. | The booking uses the online payment path. | The booking becomes active immediately. | Observed | High | `BR-BOOKING-005`, `BR-PAYMENT-005`, `BR-PAYMENT-006` | `J-PLAYER-002`, `J-PLAYER-003` | Confirmation timing is separate from settlement timing. |
| Booking Confirmed | Pending Settlement | The scheduled match has not yet reached the public availability window. | The receipt is not yet available for transfer. | The funds remain pending in the payment layer. | Observed | High | `BR-PAYMENT-008`, `BR-PAYMENT-009` | `J-PAYMENT-001`, `J-PAYMENT-002` | This is a timing state, not a failure state. |
| Pending Settlement | Available for Repass | Settlement timing is reached. | PIX reaches 24h after the scheduled time, weekend PIX reaches the next business day, or card reaches 30 days after the match. | Funds become available in the digital account. | Observed | High | `BR-PAYMENT-008`, `BR-PAYMENT-009`, `BR-PAYMENT-010` | `J-PAYMENT-001`, `J-PAYMENT-002`, `J-PAYMENT-005`, `J-PAYMENT-006` | The weekend PIX example is explicitly public. |
| Available for Repass | Repassed | Manager transfers or repasses the available value. | Funds are available in the digital account. | Money moves to a bank account or third-party account. | Observed | High | `BR-PAYMENT-010` | `J-PAYMENT-005`, `J-PAYMENT-006` | The public docs say transfers can be free of charge. |
| Payment Method Selected | Failed or Reversed Unknown | Online payment does not complete or is later reversed. | The public docs do not describe the failure path. | Outcome is not public. | Not publicly confirmed | Low | `BR-PAYMENT-013` | `J-PLAYER-002`, `J-PLAYER-003`, `J-PAYMENT-001`, `J-PAYMENT-002` | Chargeback and reversal behavior are not public. |
| Booking Confirmed | Failed or Reversed Unknown | A confirmed payment is disputed or reversed later. | The public docs do not describe the later reversal path. | Outcome is not public. | Not publicly confirmed | Low | `BR-PAYMENT-013` | `J-PAYMENT-001`, `J-PAYMENT-002`, `J-PAYMENT-005` | This is the post-confirmation reversal branch. |

### Public Unknowns
- Exact online failure states are not publicly visible.
- Whether PIX uses QR code, copy-and-paste, or both is not public.
- Whether card support includes debit or installments is not public.
- Whether weekend settlement rules apply only to PIX or also to card is not public.
- Exact chargeback, dispute, and reversal handling are not public.

## SM-PAYMENT-002 — Local Payment Lifecycle

- Status: Inferred
- Confidence: Medium
- Lifecycle subject: Pay-at-facility booking request through manager acceptance and local collection
- Domain areas: Billing, Scheduling, Operations
- Related entities: `E-BILL-006`, `E-SCHED-005`, `E-OPS-001`
- Related business rules: `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007`
- Related journeys: `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003`
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`, `29-user-journeys-overview.md`, `31-manager-operations-journeys.md`, `32-payment-and-cancellation-journeys.md`, `35-domain-model-overview.md`, `37-billing-domain-model.md`
- Notes: The public flow is visible, but the exact ordering of request acceptance, local collection, and final confirmation is not fully exposed.

### Conceptual States

| State | Status | Confidence | Meaning | Entry trigger | Exit trigger | Public unknowns |
|---|---|---|---|---|---|---|
| Local Payment Selected | Observed | High | The player has chosen pay at the facility instead of online payment. | Player selects the local-payment branch. | Manager review begins. | Exact label shown in the interface is not public. |
| Waiting for Manager Acceptance | Observed | High | The local-payment request is pending manager review. | Player submits the request. | Manager accepts, declines, or leaves the request unresolved. | Exact request expiration behavior is not public. |
| Accepted by Manager | Observed | High | The manager has accepted the local-payment request. | Manager accepts the request. | The booking is confirmed or the local payment is collected. | Exact acceptance screen and status wording are not public. |
| Confirmed | Observed | High | The booking is treated as confirmed on the local-payment branch. | The manager accepts the request. | The player completes the local payment or the booking is later cancelled. | The exact sequence between acceptance, payment, and confirmation is not public. |
| Paid at Facility | Inferred | Medium | The player completes payment in person or through the venue's local collection method. | The player pays at the facility after the request is accepted. | The booking remains complete or the request is declined/expired. | The public docs do not confirm whether payment is cash, machine, or another method. |
| Declined or Expired Unknown | Not publicly confirmed | Low | The public docs do not describe what happens when the local-payment request is rejected or expires. | The manager does not accept the request or the request times out. | Unknown. | Decline, timeout, and expiry behavior are not public. |

### Transitions

| From | To | Trigger | Condition | Outcome | Status | Confidence | Related rules | Related journeys | Notes |
|---|---|---|---|---|---|---|---|---|---|
| Local Payment Selected | Waiting for Manager Acceptance | Player chooses pay at facility. | The booking uses the local-payment branch. | A booking request is created for manager review. | Observed | High | `BR-BOOKING-006`, `BR-PAYMENT-007` | `J-PLAYER-004`, `J-PAYMENT-003` | This is the public pay-at-facility path. |
| Waiting for Manager Acceptance | Accepted by Manager | Manager receives and accepts the request. | The request reaches the manager surface. | The manager approves the booking request. | Observed | High | `BR-BOOKING-007`, `BR-PAYMENT-007` | `J-MANAGER-004`, `J-PAYMENT-003` | The exact approval screen is not public. |
| Accepted by Manager | Confirmed | Manager acceptance finalizes the booking. | The local-payment request is accepted. | The booking is treated as confirmed. | Observed | High | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007` | `J-MANAGER-004`, `J-PAYMENT-003` | The public docs do not spell out the exact UI wording. |
| Confirmed | Paid at Facility | Player completes the in-person payment. | The venue uses a local collection method. | Payment is collected at the facility. | Inferred | Medium | `BR-PAYMENT-007` | `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003` | The public docs mention paying at the venue but do not specify the payment instrument. |
| Waiting for Manager Acceptance | Declined or Expired Unknown | The request is not accepted or times out. | The public docs do not describe the branch. | Outcome is not public. | Not publicly confirmed | Low | `BR-PAYMENT-007` | `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003` | Decline and expiry behavior are not public. |

### Public Unknowns
- Exact local-payment acceptance workflow is not public.
- Whether local payment is cash, machine-based, or both is not public.
- Whether the manager can decline or the request can expire is not public.
- Whether the booking is considered confirmed before or after in-person payment is not public.
- Whether local payment can be reversed or refunded is not public.
