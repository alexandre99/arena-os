# Booking Business Rules

## Scope
This document consolidates booking, scheduling, availability, day use, monthly player, and cancellation rules from the public Agendei reference docs.
It covers the booking journey before money movement is settled in the payment layer.

## Rules

### BR-BOOKING-001 — Browse before account creation
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Player opens App Agendei and starts browsing courts.
- Condition: The player has not started scheduling a time yet.
- Outcome: The player can browse the public app without creating an account.
- Involved personas: Player.
- Affected concepts/entities: Player account, court discovery, browsing flow.
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `01-product-overview.md`
- Notes: Booking is the public point where account creation becomes necessary.

### BR-BOOKING-002 — Find courts by location
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Player searches for a place to play.
- Condition: The search starts from the public app surface.
- Outcome: Courts are found by location.
- Involved personas: Player.
- Affected concepts/entities: Court discovery, location search, facility listing.
- Source reference: `01-product-overview.md`, `04-navigation.md`, `05-booking-lifecycle.md`
- Notes: The public material presents location-based discovery as the first step.

### BR-BOOKING-003 — Each court exposes its agenda publicly
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Player opens a court listing.
- Condition: The court is visible in App Agendei.
- Outcome: The player can see the court agenda and available slots.
- Involved personas: Player.
- Affected concepts/entities: Court agenda, availability, time slot.
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`
- Notes: The agenda is visible to the player before the booking is created.

### BR-BOOKING-004 — Choose day and time from the agenda
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Player selects a court on the agenda.
- Condition: A slot is available on the selected day.
- Outcome: The player chooses the day and time that will become the booking.
- Involved personas: Player.
- Affected concepts/entities: Booking, agenda slot, selected time.
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`
- Notes: This is the standard booking creation entry point.

### BR-BOOKING-005 — Online PIX or card payment confirms the booking immediately
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Player completes the booking using PIX or card.
- Condition: The booking is submitted through App Agendei with online payment.
- Outcome: The booking is confirmed immediately after scheduling.
- Involved personas: Player, manager.
- Affected concepts/entities: Booking confirmation, online payment, PIX, card.
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `10-agendei-pay.md`
- Notes: The public docs separate this path from pay-at-facility bookings.

### BR-BOOKING-006 — Local payment bookings wait for manager acceptance
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Player chooses to pay at the facility.
- Condition: The booking is created with local payment selected.
- Outcome: The request waits for manager acceptance and confirmation.
- Involved personas: Player, manager.
- Affected concepts/entities: Local payment booking, approval, booking request.
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `09-payments-overview.md`
- Notes: The public FAQ distinguishes this path from instant online confirmation.

### BR-BOOKING-007 — Manager receives the local-payment booking request
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Player submits a pay-at-facility booking.
- Condition: The local-payment path is selected.
- Outcome: The manager receives the request and can accept it.
- Involved personas: Manager, player.
- Affected concepts/entities: Booking request, manager notification, acceptance step.
- Source reference: `05-booking-lifecycle.md`, `16-communication-and-chat.md`, `19-manager-operations-overview.md`
- Notes: The exact request screen is not public.

### BR-BOOKING-008 — Manager can create one-off bookings
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Manager edits the agenda.
- Condition: The booking is a single non-recurring reservation.
- Outcome: The manager can create an avulso booking.
- Involved personas: Manager.
- Affected concepts/entities: One-off reservation, agenda, booking slot.
- Source reference: `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `19-manager-operations-overview.md`
- Notes: The public docs use the term `agendamentos avulsos`.

### BR-BOOKING-009 — Manager can create fixed bookings
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Manager configures a recurring booking pattern.
- Condition: The booking is intended to remain on the agenda.
- Outcome: The manager can create fixed bookings.
- Involved personas: Manager, player.
- Affected concepts/entities: Fixed booking, recurring reservation, agenda control.
- Source reference: `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`, `19-manager-operations-overview.md`
- Notes: The public docs explicitly name `agendamentos fixos`.

### BR-BOOKING-010 — Manager can manage mensalistas
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Manager handles a recurring customer relationship.
- Condition: The customer is treated as a monthly player.
- Outcome: The manager can manage mensalistas as part of the booking agenda.
- Involved personas: Manager, player.
- Affected concepts/entities: Mensalista, recurring customer, fixed booking.
- Source reference: `02-personas.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`
- Notes: The public material links mensalistas to fixed bookings.

### BR-BOOKING-011 — Facility can manage multiple courts
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Manager operates a multi-court facility.
- Condition: The facility has more than one court.
- Outcome: One account or app can manage all courts.
- Involved personas: Manager, staff.
- Affected concepts/entities: Facility, multiple courts, shared agenda administration.
- Source reference: `01-product-overview.md`, `03-modules.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `19-manager-operations-overview.md`
- Notes: The public pricing material also describes unlimited courts.

### BR-BOOKING-012 — Day use is a separate daily purchase and reservation product
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Facility offers a daily access product.
- Condition: The facility wants to sell access outside the standard hourly booking flow.
- Outcome: Day use exists as a separate product branch.
- Involved personas: Player, manager.
- Affected concepts/entities: Day use, daily reservation, product flow.
- Source reference: `03-modules.md`, `04-navigation.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `12-financial-capabilities.md`
- Notes: The public pages present day use as its own purchase path.

### BR-BOOKING-013 — Manager defines the day use product details
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Manager creates a new day use product.
- Condition: The product is being set up in App Gestor.
- Outcome: The manager sets the name, day, court, duration, price, and payment form.
- Involved personas: Manager.
- Affected concepts/entities: Day use product, court, duration, price, payment form.
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `20-facility-onboarding-and-configuration.md`
- Notes: The public day-use page exposes the setup fields directly.

### BR-BOOKING-014 — Day use purchase triggers a manager notification
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: Player buys a day use product.
- Condition: The sale completes through the public player flow.
- Outcome: The manager receives a push notification for the sale.
- Involved personas: Player, manager.
- Affected concepts/entities: Day use sale, manager alert, push notification.
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `16-communication-and-chat.md`, `19-manager-operations-overview.md`
- Notes: This is a distinct alert path from local-payment booking requests.

### BR-BOOKING-015 — Cancellation penalties use a tolerance window and percentage
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: A booking is cancelled.
- Condition: The cancellation falls outside the tolerated window.
- Outcome: A penalty can be applied according to the configured percentage.
- Involved personas: Player, manager.
- Affected concepts/entities: Cancellation, tolerance window, penalty percentage.
- Source reference: `05-booking-lifecycle.md`, `11-cancellation-penalties-and-refunds.md`, `12-financial-capabilities.md`
- Notes: The public pages describe the rule, but not every configuration possibility.

### BR-BOOKING-016 — Public cancellation example uses 8h tolerance and 20% penalty
- Status: Observed
- Confidence: High
- Domain area: Scheduling
- Trigger: A cancellation happens inside the published example window.
- Condition: The example rule is applied.
- Outcome: 20% is retained and 80% is refunded immediately.
- Involved personas: Player, manager.
- Affected concepts/entities: Cancellation penalty, refund, retained amount.
- Source reference: `05-booking-lifecycle.md`, `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`
- Notes: This is the only explicit public example; the default rule is not public.

## Rule Dependencies

| Dependency | Related rule IDs | Confidence | Notes |
|---|---|---|---|
| Booking confirmation depends on payment method | `BR-BOOKING-004`, `BR-BOOKING-005`, `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-005`, `BR-PAYMENT-006`, `BR-PAYMENT-007` | High | Instant confirmation applies only to online PIX/card; local payment waits for manager acceptance. |
| Monthly player handling depends on fixed bookings | `BR-BOOKING-009`, `BR-BOOKING-010` | High | The public material links mensalistas to recurring fixed bookings. |
| Day use sale depends on a manager-created day use product | `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014` | High | The daily product must exist before the player can buy it. |
| Cancellation penalty depends on timing and percentage | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013` | High | The public example shows the 8h / 20% case, and the retained-value destination is not fully explicit. |
| Multi-court booking operations depend on facility-level setup | `BR-BOOKING-011`, `BR-OPS-001`, `BR-OPS-002`, `BR-OPS-003` | Medium | Public material implies visibility and management are tied to manager-side setup. |

## Unknowns
- Exact booking status labels and state transitions.
- Exact local-payment acceptance screen and confirmation action.
- Whether the player can cancel directly or only the facility can process the cancellation.
- Whether rescheduling avoids a cancellation penalty.
- How no-shows are treated relative to cancellations.
- Whether day use shares the same status model as hourly reservations.

