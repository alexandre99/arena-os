# Scheduling Domain Model

## Scope
This file consolidates the conceptual scheduling entities visible in the public Agendei reference docs, the consolidated business rules, and the user journeys.
It stays at the product-concept level only.
It is not a database schema, not an architecture model, and not an Arena OS document.

## Entities

### E-SCHED-001 — Facility / Quadra Esportiva

- Status: Observed
- Confidence: High
- Domain areas: Scheduling, Operations
- Description: The sports venue or operator that owns and runs the court operation.
- Primary responsibilities: Register the facility, host one or more courts, make the operation visible to players, and support bookings and day use.
- Related personas: Manager / Facility Owner, Staff / Employee, Player / Client / User.
- Related business rules: BR-BOOKING-011, BR-OPS-001, BR-OPS-002, BR-OPS-003.
- Related journeys: J-MANAGER-001, J-MANAGER-002, J-MANAGER-003, J-PLAYER-001, J-PLAYER-002, J-PLAYER-003.
- Relationships: Manages courts; is configured through the manager surface; can receive bookings and day-use sales.
- Observable attributes/concepts: Public registration path, multi-court operation, discovery in the player app.
- Inferred attributes/concepts: Location data, contact data, visibility settings.
- Public unknowns: Exact signup fields; whether access is immediate or reviewed; exact publish controls.
- Source reference: `01-product-overview.md`, `05-booking-lifecycle.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `27-operations-business-rules.md`, `29-user-journeys-overview.md`, `30-player-booking-journeys.md`, `31-manager-operations-journeys.md`
- Notes: Public pages also use `quadra esportiva` and `centro esportivo` wording.

### E-SCHED-002 — Court / Quadra

- Status: Observed
- Confidence: High
- Domain areas: Scheduling
- Description: The individual rentable court or playing surface inside a facility.
- Primary responsibilities: Expose a schedule, accept bookings, and support day-use allocation.
- Related personas: Player / Client / User, Manager / Facility Owner, Staff / Employee.
- Related business rules: BR-BOOKING-003, BR-BOOKING-004, BR-BOOKING-008, BR-BOOKING-009, BR-BOOKING-011, BR-BOOKING-013.
- Related journeys: J-PLAYER-001, J-PLAYER-002, J-PLAYER-003, J-PLAYER-004, J-PLAYER-005, J-MANAGER-002, J-MANAGER-003, J-MANAGER-005.
- Relationships: Exposes an agenda; can be selected from the agenda; can be used by one-off bookings, fixed bookings, and day use.
- Observable attributes/concepts: Public agenda, available slots, court-specific visibility.
- Inferred attributes/concepts: Sport type, price rules, court-specific exceptions.
- Public unknowns: Whether different visibility modes exist; whether courts have unique rules beyond the public agenda.
- Source reference: `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `29-user-journeys-overview.md`, `30-player-booking-journeys.md`, `31-manager-operations-journeys.md`
- Notes: A facility may manage more than one court from the same operation.

### E-SCHED-003 — Agenda / Schedule

- Status: Observed
- Confidence: High
- Domain areas: Scheduling
- Description: The court-facing schedule that shows what is available and what is already reserved.
- Primary responsibilities: Display availability, receive selected slots, and reflect one-off and fixed bookings.
- Related personas: Player / Client / User, Manager / Facility Owner, Staff / Employee.
- Related business rules: BR-BOOKING-003, BR-BOOKING-004, BR-BOOKING-008, BR-BOOKING-009, BR-BOOKING-011, BR-BOOKING-012, BR-BOOKING-015.
- Related journeys: J-PLAYER-001, J-PLAYER-002, J-PLAYER-003, J-PLAYER-004, J-MANAGER-003, J-MANAGER-005.
- Relationships: Contains available slots; is exposed by a court; is used to create bookings and day use.
- Observable attributes/concepts: Day, time, court, availability.
- Inferred attributes/concepts: Conflict handling, hold behavior, aggregated view across courts.
- Public unknowns: Whether one agenda view includes all courts; whether holds expire; exact edit and remove behavior.
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `29-user-journeys-overview.md`, `31-manager-operations-journeys.md`
- Notes: The agenda is the central scheduling surface for both players and managers.

### E-SCHED-004 — Available Time Slot / Horário Disponível

- Status: Observed
- Confidence: High
- Domain areas: Scheduling
- Description: A bookable opening in a court agenda.
- Primary responsibilities: Present a day and time that can be selected, then become a booking if taken.
- Related personas: Player / Client / User, Manager / Facility Owner.
- Related business rules: BR-BOOKING-003, BR-BOOKING-004.
- Related journeys: J-PLAYER-001, J-PLAYER-002, J-PLAYER-003, J-PLAYER-004.
- Relationships: Belongs to an agenda; can be selected by a player; can become a booking.
- Observable attributes/concepts: Visible day, visible time, visible court agenda.
- Inferred attributes/concepts: Hold expiration, conflict resolution, maximum duration.
- Public unknowns: The exact slot hold behavior and whether a slot can be partially reserved.
- Source reference: `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `30-player-booking-journeys.md`
- Notes: The public material shows visible slots but not the full slot lifecycle.

### E-SCHED-005 — Booking / Agendamento

- Status: Observed
- Confidence: High
- Domain areas: Scheduling, Billing, Operations
- Description: A reservation request or confirmed time slot tied to a court.
- Primary responsibilities: Capture the selected slot, carry the payment choice, and anchor confirmation or cancellation.
- Related personas: Player / Client / User, Manager / Facility Owner, Staff / Employee.
- Related business rules: BR-BOOKING-004, BR-BOOKING-005, BR-BOOKING-006, BR-BOOKING-007, BR-BOOKING-008, BR-BOOKING-009, BR-BOOKING-010, BR-BOOKING-011, BR-BOOKING-015, BR-BOOKING-016.
- Related journeys: J-PLAYER-002, J-PLAYER-003, J-PLAYER-004, J-MANAGER-003, J-MANAGER-004, J-PAYMENT-003, J-PAYMENT-004.
- Relationships: Can be created from a selected slot; can be confirmed immediately by online payment; can wait for manager acceptance when local payment is chosen; can be cancelled.
- Observable attributes/concepts: Day, time, court, confirmation outcome, payment method.
- Inferred attributes/concepts: Booking identifier, status history, participants, notes.
- Public unknowns: Exact booking status labels; whether the player can reschedule instead of cancelling; how no-shows are represented.
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `09-payments-overview.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`, `29-user-journeys-overview.md`, `30-player-booking-journeys.md`, `31-manager-operations-journeys.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public material shows both request and confirmed states, but not the full internal state list.

### E-SCHED-006 — One-off Booking / Agendamento Avulso

- Status: Observed
- Confidence: High
- Domain areas: Scheduling
- Description: A single non-recurring booking.
- Primary responsibilities: Reserve one time period without establishing a recurring pattern.
- Related personas: Manager / Facility Owner, Player / Client / User.
- Related business rules: BR-BOOKING-008, BR-OPS-003.
- Related journeys: J-MANAGER-003.
- Relationships: Is created by the manager; uses the agenda as a one-time reservation.
- Observable attributes/concepts: Single reservation, non-recurring use.
- Inferred attributes/concepts: Notes or exceptions, if any.
- Public unknowns: Exact edit and removal behavior after creation.
- Source reference: `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `31-manager-operations-journeys.md`
- Notes: The public docs use the term `agendamentos avulsos`.

### E-SCHED-007 — Fixed Booking / Agendamento Fixo

- Status: Observed
- Confidence: High
- Domain areas: Scheduling
- Description: A recurring booking pattern that remains part of the agenda.
- Primary responsibilities: Hold a repeating court period and support a recurring customer relationship.
- Related personas: Manager / Facility Owner, Player / Client / User.
- Related business rules: BR-BOOKING-009, BR-BOOKING-010, BR-OPS-003.
- Related journeys: J-MANAGER-003, J-CRM-003.
- Relationships: Is created by the manager; is associated with mensalistas and recurring schedule control.
- Observable attributes/concepts: Fixed reservation, recurring schedule.
- Inferred attributes/concepts: Recurrence rule, billing cadence, exceptions.
- Public unknowns: Whether the recurrence is calendar-based, billing-based, or both; whether one customer can hold multiple fixed slots.
- Source reference: `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `27-operations-business-rules.md`, `31-manager-operations-journeys.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public docs explicitly name `agendamentos fixos`.

### E-SCHED-008 — Monthly Player Relationship / Mensalista

- Status: Observed
- Confidence: High
- Domain areas: Scheduling, CRM
- Description: A recurring customer relationship associated with fixed bookings.
- Primary responsibilities: Represent the monthly or recurring player concept in the facility operation.
- Related personas: Manager / Facility Owner, Player / Client / User.
- Related business rules: BR-BOOKING-010, BR-OPS-003.
- Related journeys: J-MANAGER-003, J-CRM-003.
- Relationships: Is associated with recurring or fixed bookings; supports schedule stability.
- Observable attributes/concepts: `mensalistas`, recurring player concept.
- Inferred attributes/concepts: Subscription-like terms, reserved slot set, payment cycle.
- Public unknowns: Whether the term means recurring billing, recurring slot access, or both.
- Source reference: `02-personas.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`, `14-customer-relationship-overview.md`, `15-client-profile-and-history.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `27-operations-business-rules.md`
- Notes: The public material confirms the concept, but not the exact commercial meaning.

### E-SCHED-009 — Day Use Product / Diária

- Status: Observed
- Confidence: High
- Domain areas: Scheduling, Operations, Billing
- Description: A day-based product that grants access for a longer period than an hourly booking.
- Primary responsibilities: Package a daily reservation and define the facility, day, duration, price, and payment form.
- Related personas: Manager / Facility Owner, Player / Client / User.
- Related business rules: BR-BOOKING-012, BR-BOOKING-013, BR-BOOKING-014.
- Related journeys: J-MANAGER-005, J-PLAYER-005.
- Relationships: Is created by the manager; is sold as a separate purchase flow; triggers a manager notification when bought.
- Observable attributes/concepts: Name, day, court, duration, price, payment form.
- Inferred attributes/concepts: Capacity rule, slot blocking, check-in behavior.
- Public unknowns: Whether day use blocks hourly availability inside the same agenda; whether it can be edited after publication.
- Source reference: `03-modules.md`, `04-navigation.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `12-financial-capabilities.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `31-manager-operations-journeys.md`, `30-player-booking-journeys.md`
- Notes: The public flow is a separate purchase path, not an hourly booking screen walkthrough.

### E-SCHED-010 — Day Use Purchase

- Status: Observed
- Confidence: High
- Domain areas: Scheduling, Billing, Operations
- Description: The sale event for a day use product.
- Primary responsibilities: Record the daily purchase and notify the manager that the sale happened.
- Related personas: Player / Client / User, Manager / Facility Owner.
- Related business rules: BR-BOOKING-012, BR-BOOKING-014, BR-PAYMENT-005, BR-PAYMENT-006.
- Related journeys: J-PLAYER-005, J-MANAGER-005.
- Relationships: Follows the day use product; may use online payment methods in the public flow.
- Observable attributes/concepts: Separate purchase flow, manager push notification.
- Inferred attributes/concepts: Sale status, sale history, payment linkage.
- Public unknowns: Whether the sale uses the same status model as hourly bookings.
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `09-payments-overview.md`, `12-financial-capabilities.md`, `16-communication-and-chat.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public docs present day use as a distinct sale concept.

### E-SCHED-011 — Cancellation

- Status: Observed
- Confidence: High
- Domain areas: Scheduling, Billing
- Description: The termination of a booking before use.
- Primary responsibilities: End a booking, trigger the cancellation rule, and open the path to penalty or refund handling.
- Related personas: Player / Client / User, Manager / Facility Owner.
- Related business rules: BR-BOOKING-015, BR-BOOKING-016, BR-PAYMENT-011, BR-PAYMENT-012, BR-PAYMENT-013.
- Related journeys: J-PAYMENT-004.
- Relationships: Applies to a booking; can lead to a penalty and refund split.
- Observable attributes/concepts: Tolerance window, penalty percentage, refund split.
- Inferred attributes/concepts: Initiator, reason, exact status history.
- Public unknowns: Who can initiate cancellation; whether rescheduling avoids the penalty; how no-shows are treated.
- Source reference: `05-booking-lifecycle.md`, `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public example shows an 8-hour tolerance window and a 20% penalty.

### E-SCHED-012 — Cancellation Rule

- Status: Observed
- Confidence: High
- Domain areas: Scheduling, Billing
- Description: The public rule that evaluates whether a cancellation is late enough to trigger a penalty.
- Primary responsibilities: Compare cancellation timing with a tolerance window and apply the configured percentage.
- Related personas: Manager / Facility Owner, Player / Client / User.
- Related business rules: BR-BOOKING-015, BR-BOOKING-016, BR-PAYMENT-011, BR-PAYMENT-012, BR-PAYMENT-013, BR-PAYMENT-014.
- Related journeys: J-PAYMENT-004.
- Relationships: Evaluates cancellation timing; determines whether a penalty and refund split apply.
- Observable attributes/concepts: Tolerance window, percentage fee, example split.
- Inferred attributes/concepts: Formula, rounding, automation timing.
- Public unknowns: Whether the manager can change the tolerance window or percentage; whether the penalty is automatic or manual.
- Source reference: `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`, `34-user-journeys-open-questions.md`
- Notes: The published example uses 8 hours before the booking time and a 20% penalty.

## Relationships

### Facility manages courts

- Relationship: A facility manages one or more courts.
- Status: Observed
- Confidence: High
- Source entity: Facility / Quadra Esportiva
- Target entity: Court / Quadra
- Business meaning: The manager-side operation administers each rentable court within the same facility.
- Related rules: BR-BOOKING-011, BR-OPS-003
- Related journeys: J-MANAGER-003
- Source reference: `01-product-overview.md`, `19-manager-operations-overview.md`, `25-booking-business-rules.md`, `27-operations-business-rules.md`, `31-manager-operations-journeys.md`
- Notes: Public pages describe multi-court operation as a core feature.

### Court exposes agenda

- Relationship: A court exposes an agenda.
- Status: Observed
- Confidence: High
- Source entity: Court / Quadra
- Target entity: Agenda / Schedule
- Business meaning: Players and managers use the court schedule to see availability and make reservations.
- Related rules: BR-BOOKING-003, BR-BOOKING-004
- Related journeys: J-PLAYER-001, J-PLAYER-002, J-PLAYER-003, J-PLAYER-004
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`, `30-player-booking-journeys.md`
- Notes: The agenda is the primary public scheduling surface for a court.

### Agenda contains available slots

- Relationship: An agenda contains available time slots.
- Status: Observed
- Confidence: High
- Source entity: Agenda / Schedule
- Target entity: Available Time Slot / Horário Disponível
- Business meaning: Each court schedule presents the openings that can be selected for a booking.
- Related rules: BR-BOOKING-003, BR-BOOKING-004
- Related journeys: J-PLAYER-001, J-PLAYER-002, J-PLAYER-003, J-PLAYER-004
- Source reference: `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`, `25-booking-business-rules.md`, `30-player-booking-journeys.md`
- Notes: The public docs show visible openings but not the hold mechanics behind them.

### Player selects available slot

- Relationship: A player selects an available slot.
- Status: Observed
- Confidence: High
- Source entity: Player / Client / User
- Target entity: Available Time Slot / Horário Disponível
- Business meaning: The player chooses a day and time from the visible agenda before the booking is created.
- Related rules: BR-BOOKING-004
- Related journeys: J-PLAYER-002, J-PLAYER-003, J-PLAYER-004
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `30-player-booking-journeys.md`
- Notes: This is the standard starting point for the booking branch.

### Selected slot becomes booking

- Relationship: A selected slot becomes a booking.
- Status: Observed
- Confidence: High
- Source entity: Available Time Slot / Horário Disponível
- Target entity: Booking / Agendamento
- Business meaning: Once the player submits the choice, the selected opening turns into a reservation request or confirmed booking.
- Related rules: BR-BOOKING-004, BR-BOOKING-005, BR-BOOKING-006
- Related journeys: J-PLAYER-002, J-PLAYER-003, J-PLAYER-004
- Source reference: `05-booking-lifecycle.md`, `25-booking-business-rules.md`, `30-player-booking-journeys.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public docs show the transition but not the full internal state list.

### Manager creates one-off booking

- Relationship: A manager creates a one-off booking.
- Status: Observed
- Confidence: High
- Source entity: Manager / Facility Owner
- Target entity: One-off Booking / Agendamento Avulso
- Business meaning: The facility can reserve a single court period without recurrence.
- Related rules: BR-BOOKING-008, BR-OPS-003
- Related journeys: J-MANAGER-003
- Source reference: `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `19-manager-operations-overview.md`, `25-booking-business-rules.md`, `31-manager-operations-journeys.md`
- Notes: The public docs use the term `agendamentos avulsos`.

### Manager creates fixed booking

- Relationship: A manager creates a fixed booking.
- Status: Observed
- Confidence: High
- Source entity: Manager / Facility Owner
- Target entity: Fixed Booking / Agendamento Fixo
- Business meaning: The facility can reserve a recurring court period that stays on the agenda.
- Related rules: BR-BOOKING-009, BR-BOOKING-010, BR-OPS-003
- Related journeys: J-MANAGER-003, J-CRM-003
- Source reference: `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`, `19-manager-operations-overview.md`, `25-booking-business-rules.md`, `31-manager-operations-journeys.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public docs explicitly name `agendamentos fixos`.

### Monthly player is associated with recurring booking

- Relationship: A monthly player relationship is associated with recurring or fixed bookings.
- Status: Observed
- Confidence: High
- Source entity: Monthly Player Relationship / Mensalista
- Target entity: Fixed Booking / Agendamento Fixo
- Business meaning: The recurring customer concept sits on top of fixed bookings and long-running schedule control.
- Related rules: BR-BOOKING-009, BR-BOOKING-010, BR-OPS-003
- Related journeys: J-MANAGER-003, J-CRM-003
- Source reference: `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`, `14-customer-relationship-overview.md`, `25-booking-business-rules.md`, `27-operations-business-rules.md`, `33-engagement-and-crm-journeys.md`
- Notes: The commercial meaning of `mensalista` is still not publicly defined.

### Manager creates day use product

- Relationship: A manager creates a day use product.
- Status: Observed
- Confidence: High
- Source entity: Manager / Facility Owner
- Target entity: Day Use Product / Diária
- Business meaning: The facility defines a separate daily reservation product before it can be sold.
- Related rules: BR-BOOKING-012, BR-BOOKING-013
- Related journeys: J-MANAGER-005
- Source reference: `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `20-facility-onboarding-and-configuration.md`, `25-booking-business-rules.md`, `31-manager-operations-journeys.md`
- Notes: The public day-use page exposes the product setup fields directly.

### Player buys day use product

- Relationship: A player buys a day use product.
- Status: Observed
- Confidence: High
- Source entity: Player / Client / User
- Target entity: Day Use Purchase
- Business meaning: The player completes a separate daily purchase instead of the standard hourly booking branch.
- Related rules: BR-BOOKING-012, BR-BOOKING-014
- Related journeys: J-PLAYER-005
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `12-financial-capabilities.md`, `25-booking-business-rules.md`, `30-player-booking-journeys.md`
- Notes: The sale triggers a manager notification in the public flow.

### Booking may be cancelled

- Relationship: A booking may be cancelled.
- Status: Observed
- Confidence: High
- Source entity: Booking / Agendamento
- Target entity: Cancellation
- Business meaning: The booked time can be terminated before use.
- Related rules: BR-BOOKING-015, BR-BOOKING-016
- Related journeys: J-PAYMENT-004
- Source reference: `05-booking-lifecycle.md`, `11-cancellation-penalties-and-refunds.md`, `25-booking-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public material ties cancellation to penalty and refund behavior.

### Cancellation rule evaluates timing

- Relationship: The cancellation rule evaluates cancellation timing.
- Status: Observed
- Confidence: High
- Source entity: Cancellation Rule
- Target entity: Cancellation
- Business meaning: The rule compares the cancellation moment with a tolerance window and applies the published percentage.
- Related rules: BR-BOOKING-015, BR-BOOKING-016, BR-PAYMENT-011, BR-PAYMENT-012, BR-PAYMENT-013, BR-PAYMENT-014
- Related journeys: J-PAYMENT-004
- Source reference: `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public example uses 8 hours and a 20% penalty.

## Unknowns

- Exact booking status labels and state transitions.
- Whether the player can cancel directly or only the facility can process a cancellation.
- Whether rescheduling avoids a cancellation penalty.
- How no-shows are treated relative to cancellations.
- Whether day use blocks hourly slots inside the same agenda.
- Whether day use shares the same status model as hourly reservations.
- Whether one customer can hold more than one fixed booking across courts.
- Exact slot-hold behavior and expiry timing.
- Exact edit and removal behavior for one-off and fixed bookings.

