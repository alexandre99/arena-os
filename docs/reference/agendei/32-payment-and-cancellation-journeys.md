# Payment and Cancellation Journeys

## Scope
This document consolidates payment, settlement, repass, refund, and cancellation journeys from the existing public Agendei reference docs and consolidated business rules.
It stays within the public reference set and does not define Arena OS behavior.

## Journeys

### J-PAYMENT-001 — PIX booking payment and settlement

- Status: Observed
- Confidence: High
- Primary persona: Player
- Supporting personas: Manager
- Domain areas: Payments, Finance
- Trigger: Player chooses PIX during booking.
- Preconditions: The booking slot is selected and Agendei Pay is active for the facility.
- Main success path:
  1. Player selects the court, day, and time.
  2. Player chooses PIX as the payment method.
  3. Booking confirms immediately after scheduling.
  4. The PIX amount becomes available 24 hours after the scheduled time.
  5. Weekend availability moves to the next business day.
- Alternate paths:
  - PIX fee handling is public, but payment-failure and pending-state behavior are not.
- Business rules used: `BR-PAYMENT-005`, `BR-PAYMENT-008`, `BR-PAYMENT-009`
- Expected outcome: The booking is confirmed right away and the PIX money settles later.
- Public unknowns:
  - PIX QR-code or copy-and-paste experience.
  - Failed-payment handling.
  - Pending-state handling.
- Source reference: `09-payments-overview.md`, `10-agendei-pay.md`, `12-financial-capabilities.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`
- Notes:
  - The public timing rule is specific about PIX settlement and the weekend shift.

### J-PAYMENT-002 — Card booking payment and settlement

- Status: Observed
- Confidence: High
- Primary persona: Player
- Supporting personas: Manager
- Domain areas: Payments, Finance
- Trigger: Player chooses card during booking.
- Preconditions: The booking slot is selected and card payment is enabled.
- Main success path:
  1. Player selects the court, day, and time.
  2. Player chooses card as the payment method.
  3. Booking confirms immediately after scheduling.
  4. The card receivable becomes available 30 days after the match.
  5. Any later transfer or repass follows the digital-account flow.
- Alternate paths:
  - Card brand, installment, and authorization behavior are not publicly detailed.
- Business rules used: `BR-PAYMENT-006`, `BR-PAYMENT-009`, `BR-PAYMENT-010`
- Expected outcome: The booking is confirmed immediately and the receivable settles later.
- Public unknowns:
  - Card brand support.
  - Installment behavior.
  - Authorization and capture detail.
- Source reference: `09-payments-overview.md`, `10-agendei-pay.md`, `12-financial-capabilities.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`
- Notes:
  - The public docs separate booking confirmation from the 30-day receivable timing.

### J-PAYMENT-003 — Local payment booking

- Status: Observed
- Confidence: High
- Primary persona: Player
- Supporting personas: Manager
- Domain areas: Payments, Scheduling
- Trigger: Player chooses pay at the facility.
- Preconditions: The booking slot is selected and local payment is offered.
- Main success path:
  1. Player selects the court, day, and time.
  2. Player chooses pay at the facility.
  3. The request waits for manager acceptance.
  4. The booking is not immediately confirmed.
  5. Payment happens locally by cash or machine if the facility offers it that way.
- Alternate paths:
  - The settlement and repass path are not publicly described.
- Business rules used: `BR-PAYMENT-007`, `BR-BOOKING-006`, `BR-BOOKING-007`
- Expected outcome: The request remains pending until the manager confirms it.
- Public unknowns:
  - Exact local-payment methods in every facility.
  - Exact status names before acceptance.
  - Settlement or repayment behavior after local collection.
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`
- Notes:
  - This journey covers the pay-at-facility branch only; the manager confirmation is a separate journey.

### J-PAYMENT-004 — Cancellation penalty and partial refund

- Status: Observed
- Confidence: High
- Primary persona: Player
- Supporting personas: Manager
- Domain areas: Payments, Cancellation
- Trigger: A booking is cancelled.
- Preconditions: A booking exists and the cancellation rule is configured.
- Main success path:
  1. Booking exists.
  2. Cancellation occurs.
  3. The rule evaluates the tolerance window and percentage.
  4. In the public example, 20% is retained.
  5. In the public example, 80% is refunded immediately.
- Alternate paths:
  - The exact destination of the retained amount is not publicly confirmed.
- Business rules used: `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013`, `BR-PAYMENT-014`
- Expected outcome: Late cancellations can retain part of the value and refund the rest.
- Public unknowns:
  - Exact retained-value destination.
  - Who can initiate cancellation.
  - Whether rescheduling avoids the penalty.
  - Whether no-shows follow the same rule.
- Source reference: `05-booking-lifecycle.md`, `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`, `12-financial-capabilities.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`
- Notes:
  - The public example is 8 hours and 20%, but the generic tolerance and percentage remain configurable at a public level only in concept.

### J-PAYMENT-005 — Transfer/repass to facility

- Status: Observed
- Confidence: High
- Primary persona: Manager
- Supporting personas: None
- Domain areas: Payments, Finance
- Trigger: Online-payment money has settled into the digital account.
- Preconditions: The digital account exists and settled funds are available.
- Main success path:
  1. Online payment settles into the digital account.
  2. Manager transfers money to the facility's own bank account or to a third-party account.
  3. Transfers are free of charge in the public description.
  4. The facility can also keep money in the digital account until desired.
- Alternate paths:
  - Exact payout exceptions and withdrawal constraints are not publicly confirmed.
- Business rules used: `BR-PAYMENT-001`, `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-PAYMENT-010`
- Expected outcome: The facility can move settled money out of or keep it inside the digital account.
- Public unknowns:
  - Manual withdrawal timing.
  - Transfer exception handling.
  - Whether third-party destinations have special constraints.
- Source reference: `10-agendei-pay.md`, `12-financial-capabilities.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`
- Notes:
  - The public material describes both the digital-account holding pattern and free transfer behavior.

### J-PAYMENT-006 — Financial management and cash flow

- Status: Observed
- Confidence: High
- Primary persona: Manager
- Supporting personas: None
- Domain areas: Finance, Operations
- Trigger: Manager opens the finance surface or reviews the plan-visible financial package.
- Preconditions: The facility uses the public manager surface.
- Main success path:
  1. Manager opens the financial management area.
  2. Manager reviews revenue, expense, profit, and cash flow.
  3. Manager uses the public finance view to track the business.
  4. The financial picture is read alongside the settlement and repass flows.
- Alternate paths:
  - Exact report granularity and reconciliation screens are not public.
- Business rules used: `BR-PAYMENT-016`, `BR-OPS-005`, `BR-PAYMENT-001`
- Expected outcome: The manager can observe the facility's financial position through public finance concepts.
- Public unknowns:
  - Report detail.
  - Reconciliation screen structure.
  - Manual entry behavior.
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `19-manager-operations-overview.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`
- Notes:
  - This journey focuses on financial visibility rather than on the mechanics of payment confirmation.

## Journey Dependencies

| Dependency | Related journey IDs | Related rule IDs | Notes |
|---|---|---|---|
| PIX settlement depends on online booking payment | `J-PAYMENT-001` | `BR-PAYMENT-005`, `BR-PAYMENT-008`, `BR-PAYMENT-009` | Immediate booking confirmation is separate from later fund availability. |
| Card settlement depends on online booking payment | `J-PAYMENT-002` | `BR-PAYMENT-006`, `BR-PAYMENT-009`, `BR-PAYMENT-010` | The booking confirms immediately, but the receivable settles later. |
| Local payment depends on manager acceptance | `J-PAYMENT-003` | `BR-PAYMENT-007`, `BR-BOOKING-006`, `BR-BOOKING-007` | There is no automatic confirmation branch. |
| Cancellation and refund behavior depends on a configured rule | `J-PAYMENT-004` | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013`, `BR-PAYMENT-014` | The public example provides the only explicit split. |
| Transfer and repass behavior depends on settlement into the digital account | `J-PAYMENT-005`, `J-PAYMENT-006` | `BR-PAYMENT-001`, `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-PAYMENT-010`, `BR-PAYMENT-016` | Repasses happen after funds become available. |

## Unknowns
- Exact payment status names.
- Whether PIX uses QR code, copy-and-paste, or both.
- Whether card supports installments or debit.
- Whether local payment can be cash, machine, or both in every case.
- Exact payout exceptions and withdrawal timing.
- Whether weekend timing rules apply to card as well as PIX.
- Chargeback and dispute handling.
