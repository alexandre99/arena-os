# Engagement and CRM Journeys

## Scope
This document consolidates engagement, customer relationship, and communication journeys from the existing public Agendei reference docs and consolidated business rules.
It stays within the public reference set and does not define Arena OS behavior.

## Journeys

### J-CRM-001 — Facility communicates with client through chat/messages

- Status: Observed
- Confidence: High
- Primary persona: Manager
- Supporting personas: Player, Staff, Partner
- Domain areas: CRM, Communication
- Trigger: Facility or client needs to communicate in the booking or relationship context.
- Preconditions: The public message channel is available.
- Main success path:
  1. Facility and client open the in-app chat or messages surface.
  2. The two sides exchange messages.
  3. The conversation supports booking or customer-relationship coordination.
  4. The interaction remains within the public communication channel.
- Alternate paths:
  - Staff and partner access to messages is not publicly detailed.
- Business rules used: `BR-OPS-015`
- Expected outcome: The facility and client can communicate directly in the product.
- Public unknowns:
  - Whether chat is per booking or per customer.
  - Whether messages are retained for audit.
  - Whether attachments or templates exist.
- Source reference: `03-modules.md`, `14-customer-relationship-overview.md`, `16-communication-and-chat.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`
- Notes:
  - The public docs expose the channel, but not the retention or per-thread model.

### J-CRM-002 — Manager receives operational notifications

- Status: Inferred
- Confidence: Medium
- Primary persona: Manager
- Supporting personas: Player
- Domain areas: CRM, Communication, Operations
- Trigger: A booking request, booking confirmation, or day use sale occurs.
- Preconditions: The relevant notification flow is available.
- Main success path:
  1. Manager receives a local-payment booking request notification.
  2. Manager receives a push notification when a day use product is sold.
  3. A booking confirmation notification may also be sent in the online-payment branch.
  4. Cancellation notification behavior remains publicly unknown.
- Alternate paths:
  - The exact channel mix is not public.
- Business rules used: `BR-OPS-016`, `BR-BOOKING-007`, `BR-BOOKING-014`
- Expected outcome: The manager is alerted when an operational event needs attention.
- Public unknowns:
  - Whether notifications are push, email, WhatsApp, or in-app only.
  - Whether cancellation notifications exist.
  - Whether online booking confirmations trigger a distinct notification.
- Source reference: `05-booking-lifecycle.md`, `16-communication-and-chat.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`
- Notes:
  - Local-payment and day-use alerts are observed; booking-confirmation alerts are inferred from the public booking flow.

### J-CRM-003 — Customer becomes recurring/monthly player

- Status: Inferred
- Confidence: Medium
- Primary persona: Manager
- Supporting personas: Player
- Domain areas: CRM, Scheduling
- Trigger: The facility establishes a recurring fixed-booking relationship.
- Preconditions: Fixed bookings or mensalistas are part of the facility's operating model.
- Main success path:
  1. Manager creates or maintains a fixed booking relationship.
  2. The customer is treated as a mensalista or recurring player.
  3. The recurring booking remains part of the schedule.
  4. The commercial meaning of the recurring relationship stays within the public concept level.
- Alternate paths:
  - Whether one customer can hold more than one fixed slot is not public.
- Business rules used: `BR-BOOKING-009`, `BR-BOOKING-010`, `BR-OPS-003`
- Expected outcome: The facility can keep a recurring customer relationship on the agenda.
- Public unknowns:
  - Whether mensalista means recurring billing, recurring slot, or both.
  - Whether monthly players can hold multiple fixed slots.
  - Whether recurrence is tied to one court or more than one court.
- Source reference: `02-personas.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`, `14-customer-relationship-overview.md`, `15-client-profile-and-history.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `27-operations-business-rules.md`
- Notes:
  - The public docs expose mensalistas as a recurring concept, but not the commercial model behind it.

### J-CRM-004 — Manager creates and player uses coupons

- Status: Inferred
- Confidence: Medium
- Primary persona: Manager
- Supporting personas: Player
- Domain areas: CRM, Promotions, Payments
- Trigger: Manager wants to offer a discount and the player reaches checkout.
- Preconditions: A coupon exists and the plan exposes the relevant creation capability.
- Main success path:
  1. Manager creates a custom coupon when the plan makes the feature available.
  2. Player reaches the booking context where a coupon can be used.
  3. Player applies the coupon during booking.
  4. The booking total reflects the discount if the coupon is valid.
  5. Coupon limits and stacking rules remain public-unknown.
- Alternate paths:
  - Coupon applicability to day use is not publicly confirmed.
- Business rules used: `BR-PAYMENT-015`, `BR-OPS-011`, `BR-OPS-012`
- Expected outcome: A valid coupon can reduce the booking total in the public booking context.
- Public unknowns:
  - Coupon limits.
  - Coupon stacking.
  - Coupon targeting rules.
  - Day-use applicability.
- Source reference: `06-scheduling-capabilities.md`, `12-financial-capabilities.md`, `17-engagement-coupons-and-match-organization.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`
- Notes:
  - The public docs show coupon creation and coupon use, but not the full redemption workflow.

### J-CRM-005 — Player organizes match after booking

- Status: Observed
- Confidence: High
- Primary persona: Player
- Supporting personas: Invited friends, Match participants
- Domain areas: CRM, Engagement, Scheduling
- Trigger: A booking context exists and the player wants to coordinate participants.
- Preconditions: The booking or court reservation exists.
- Main success path:
  1. Player opens the match-organization flow.
  2. Player invites friends to join the match.
  3. The app sorts teams for the match.
  4. Participants join around the booking.
  5. The match is organized around the booked time.
- Alternate paths:
  - Invite delivery and participant identity handling are not publicly confirmed.
- Business rules used: `BR-OPS-017`, `BR-OPS-018`
- Expected outcome: The booking becomes a coordinated match with participants and teams.
- Public unknowns:
  - Invite delivery mechanism.
  - Team-sorting algorithm.
  - Whether non-bookers can join.
- Source reference: `01-product-overview.md`, `03-modules.md`, `14-customer-relationship-overview.md`, `17-engagement-coupons-and-match-organization.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`
- Notes:
  - The public docs make the feature visible, but not the exact coordination workflow.

### J-CRM-006 — Player participates in lessons or tournaments

- Status: Inferred
- Confidence: Low
- Primary persona: Player
- Supporting personas: Manager, Participants
- Domain areas: CRM, Operations, Engagement
- Trigger: The facility exposes lesson or tournament features in a public plan tier.
- Preconditions: The relevant plan-visible feature is available.
- Main success path:
  1. Manager offers a lesson or tournament capability.
  2. Player or participant enters the feature as public visibility allows.
  3. The exact participation workflow remains unpublished.
  4. The feature serves the recurring engagement concept at a public level.
- Alternate paths:
  - The public docs do not show a detailed workflow.
- Business rules used: `BR-OPS-010`, `BR-OPS-011`, `BR-OPS-014`
- Expected outcome: The public reference shows lessons and tournaments as available feature concepts.
- Public unknowns:
  - Exact lesson workflow.
  - Exact tournament registration workflow.
  - Whether these flows are currently operational or only plan-visible.
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `17-engagement-coupons-and-match-organization.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`
- Notes:
  - The public site names the features, but not the participant journey.

## Journey Dependencies

| Dependency | Related journey IDs | Related rule IDs | Notes |
|---|---|---|---|
| Communication depends on an available messaging channel | `J-CRM-001` | `BR-OPS-015` | The public chat feature underpins client and facility communication. |
| Notifications depend on booking and day-use operational events | `J-CRM-002` | `BR-OPS-016`, `BR-BOOKING-007`, `BR-BOOKING-014` | The manager receives alerts when operational action is needed. |
| Recurring-customer behavior depends on fixed bookings and mensalistas | `J-CRM-003` | `BR-BOOKING-009`, `BR-BOOKING-010`, `BR-OPS-003` | The public docs expose the recurring concept, not the full commercial logic. |
| Coupon use depends on plan-visible coupon creation | `J-CRM-004` | `BR-PAYMENT-015`, `BR-OPS-011`, `BR-OPS-012` | Managers create coupons only where the public plan exposes it. |
| Match organization depends on booking context | `J-CRM-005` | `BR-OPS-017`, `BR-OPS-018` | Friend invitations and team sorting appear after a booking exists. |
| Lessons and tournaments depend on plan-visible feature packaging | `J-CRM-006` | `BR-OPS-010`, `BR-OPS-011`, `BR-OPS-014` | The public plan page names the feature concepts without workflow detail. |

## Unknowns
- Whether chat is per booking or per customer.
- Whether messages are retained for audit.
- Exact notification channels.
- Whether booking confirmation triggers a separate customer notification.
- The precise meaning of mensalista.
- Coupon limits, stacking, targeting, and day-use applicability.
- Exact invite delivery and team-sorting mechanics.
- Whether lessons and tournaments are currently operational or only plan-visible.
