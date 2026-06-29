# Player Booking Journeys

## Scope
This document consolidates player-side booking journeys from the existing public Agendei reference docs and consolidated business rules.
It stays within the public reference set and does not define Arena OS behavior.

## Journeys

### J-PLAYER-001 — Browse and discover courts before account creation

- Status: Observed
- Confidence: High
- Primary persona: Player
- Supporting personas: None
- Domain areas: Discovery, Scheduling
- Trigger: Player opens App Agendei and starts looking for a place to play.
- Preconditions: A court is publicly visible in App Agendei.
- Main success path:
  1. Player opens App Agendei.
  2. Player browses the public app without creating an account.
  3. Player searches by location.
  4. Player opens a court listing and sees the agenda and available slots.
  5. Player reaches the point where booking will later require account creation.
- Alternate paths:
  - Other discovery filters are not publicly confirmed.
- Business rules used: `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003`
- Expected outcome: The player can evaluate courts before sign-up and move toward booking.
- Public unknowns:
  - Exact search UX and filters.
  - Exact point at which account creation becomes mandatory.
- Source reference: `01-product-overview.md`, `02-personas.md`, `04-navigation.md`, `05-booking-lifecycle.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`
- Notes:
  - The public docs show browsing without an account and later booking as the point where identity becomes operationally relevant.

### J-PLAYER-002 — Book a court with online PIX payment

- Status: Observed
- Confidence: High
- Primary persona: Player
- Supporting personas: Manager
- Domain areas: Scheduling, Payments
- Trigger: Player selects a court, day, and time, then chooses PIX.
- Preconditions: The court is visible, a slot is available, and online payment is enabled.
- Main success path:
  1. Player selects the court, day, and time from the agenda.
  2. Player submits the booking.
  3. Player chooses PIX as the payment method.
  4. Booking confirms immediately after scheduling.
  5. Settlement is handled later in the payment layer.
- Alternate paths:
  - If PIX recognition fails, the public docs do not describe the pending-state behavior.
- Business rules used: `BR-BOOKING-003`, `BR-BOOKING-004`, `BR-BOOKING-005`, `BR-PAYMENT-005`, `BR-PAYMENT-008`
- Expected outcome: The booking is confirmed immediately and the financial settlement occurs later.
- Public unknowns:
  - PIX QR-code or copy-and-paste experience.
  - Pending-state and failure handling.
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `10-agendei-pay.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`
- Notes:
  - Confirmation is public; settlement timing belongs to the payment journeys.

### J-PLAYER-003 — Book a court with online card payment

- Status: Observed
- Confidence: High
- Primary persona: Player
- Supporting personas: Manager
- Domain areas: Scheduling, Payments
- Trigger: Player selects a court, day, and time, then chooses card payment.
- Preconditions: The court is visible, a slot is available, and online card payment is enabled.
- Main success path:
  1. Player selects the court, day, and time from the agenda.
  2. Player submits the booking.
  3. Player chooses card as the payment method.
  4. Booking confirms immediately after scheduling.
  5. Settlement and repass handling continue in the payment layer.
- Alternate paths:
  - Card brand, installment, and authorization details are not publicly described.
- Business rules used: `BR-BOOKING-003`, `BR-BOOKING-004`, `BR-BOOKING-005`, `BR-PAYMENT-006`, `BR-PAYMENT-009`, `BR-PAYMENT-010`
- Expected outcome: The booking is confirmed immediately and card settlement follows the public timing rule.
- Public unknowns:
  - Card brand support.
  - Installment behavior.
  - Authorization and capture detail.
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `10-agendei-pay.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`
- Notes:
  - The public docs separate booking confirmation from the later settlement and transfer behavior.

### J-PLAYER-004 — Request booking with local payment

- Status: Observed
- Confidence: High
- Primary persona: Player
- Supporting personas: Manager
- Domain areas: Scheduling, Payments
- Trigger: Player chooses to pay at the facility.
- Preconditions: The court is visible, a slot is available, and local payment is offered.
- Main success path:
  1. Player selects the court, day, and time from the agenda.
  2. Player chooses pay at the facility.
  3. Player submits the booking request.
  4. The request is sent to the manager.
  5. The booking waits for manager acceptance instead of confirming immediately.
- Alternate paths:
  - The public docs do not show the exact request statuses or manager screen.
- Business rules used: `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007`
- Expected outcome: The booking remains pending until the manager accepts it.
- Public unknowns:
  - Exact approval screen.
  - Exact interim booking states.
  - Whether the local payment is cash, machine, or both in all cases.
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `16-communication-and-chat.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`
- Notes:
  - This journey ends before money movement; the payment layer is handled separately.

### J-PLAYER-005 — Buy day use product

- Status: Observed
- Confidence: High
- Primary persona: Player
- Supporting personas: Manager
- Domain areas: Scheduling, Operations, Payments
- Trigger: Player selects a day use product.
- Preconditions: The manager has already created the day use product.
- Main success path:
  1. Player opens the day use purchase flow.
  2. Player selects the public daily reservation product.
  3. Player buys the day use reservation.
  4. The sale is recorded as a separate day-based purchase.
  5. The manager receives a push notification for the sale.
- Alternate paths:
  - If the product was not created, the public docs do not show a fallback flow.
- Business rules used: `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014`
- Expected outcome: The player obtains a daily reservation and the manager is notified.
- Public unknowns:
  - Whether day use blocks hourly slots in the same agenda.
  - Whether day use shares the same status model as hourly reservations.
- Source reference: `03-modules.md`, `04-navigation.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `12-financial-capabilities.md`, `16-communication-and-chat.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`
- Notes:
  - The public docs present day use as a separate product branch rather than a standard hourly booking.

### J-PLAYER-006 — Use coupon during booking

- Status: Inferred
- Confidence: Medium
- Primary persona: Player
- Supporting personas: Manager
- Domain areas: Payments, Promotions
- Trigger: Player reaches a booking context where a coupon can be applied.
- Preconditions: A coupon exists and the booking context accepts it.
- Main success path:
  1. Player reaches the booking flow with a visible coupon opportunity.
  2. Player enters or applies the coupon.
  3. The booking reflects the discount if the coupon is eligible.
  4. Exact redemption timing remains public-unknown.
- Alternate paths:
  - Coupon limits, stacking, and applicability rules are not publicly confirmed.
- Business rules used: `BR-PAYMENT-015`, `BR-OPS-011`, `BR-OPS-012`
- Expected outcome: The player can use a valid discount coupon within the booking context.
- Public unknowns:
  - Exact coupon entry point.
  - Validity windows and limits.
  - Whether coupons apply to day use, hourly bookings, or both.
- Source reference: `06-scheduling-capabilities.md`, `12-financial-capabilities.md`, `17-engagement-coupons-and-match-organization.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`
- Notes:
  - The public material confirms booking-context coupon usage, but not the exact redemption screen or validation flow.

### J-PLAYER-007 — Invite friends and sort teams after booking

- Status: Observed
- Confidence: High
- Primary persona: Player
- Supporting personas: Invited friends, match participants
- Domain areas: Engagement, CRM
- Trigger: Player has a booking or booking context and wants to organize the match.
- Preconditions: The booking context exists.
- Main success path:
  1. Player opens the match-organization flow from the booking context.
  2. Player invites friends to join the match.
  3. The app sorts teams for the match.
  4. Invited people join as participants around the booking.
  5. The match is organized around the booked court time.
- Alternate paths:
  - The invite delivery mechanism is not publicly confirmed.
- Business rules used: `BR-OPS-017`, `BR-OPS-018`
- Expected outcome: The booking context is extended into a coordinated match with teams and participants.
- Public unknowns:
  - Invite delivery mechanism.
  - Friend list behavior.
  - Team-sorting algorithm.
- Source reference: `01-product-overview.md`, `03-modules.md`, `14-customer-relationship-overview.md`, `17-engagement-coupons-and-match-organization.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`
- Notes:
  - The public docs make the feature visible, but not the internal matching logic.

## Journey Dependencies

| Dependency | Related journey IDs | Related rule IDs | Notes |
|---|---|---|---|
| Court discovery precedes booking and payment | `J-PLAYER-001`, `J-PLAYER-002`, `J-PLAYER-003`, `J-PLAYER-004`, `J-PLAYER-005`, `J-PLAYER-006`, `J-PLAYER-007` | `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003` | The booking flows assume the player can first find a visible court. |
| Slot selection precedes the payment branch | `J-PLAYER-002`, `J-PLAYER-003`, `J-PLAYER-004` | `BR-BOOKING-003`, `BR-BOOKING-004` | The player selects a day and time before choosing a payment method. |
| Day use purchase depends on a manager-created product | `J-PLAYER-005` | `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014` | The day-use product must exist before the player can buy it. |
| Coupon use depends on booking context | `J-PLAYER-006` | `BR-PAYMENT-015`, `BR-OPS-011`, `BR-OPS-012` | The public docs place coupons inside the booking context, not as a separate surface. |
| Match organization depends on a booking context | `J-PLAYER-007` | `BR-OPS-017`, `BR-OPS-018` | Friend invitations and team sorting are tied to the booking journey. |
| Online payment branches depend on payment method selection | `J-PLAYER-002`, `J-PLAYER-003` | `BR-BOOKING-005`, `BR-PAYMENT-005`, `BR-PAYMENT-006` | PIX and card confirm immediately, but the settlement journeys differ. |

## Unknowns
- Exact location-search behavior and available filters.
- Exact point where account creation becomes mandatory.
- Exact coupon entry and validation flow.
- Exact local-payment approval screen and request statuses.
- Whether day use blocks hourly bookings in the same agenda.
- Whether day use uses the same status model as hourly reservations.
- Exact invite delivery mechanism and team-sorting rules.

