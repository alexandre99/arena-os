# CRM and Engagement Domain Model

## Scope
This file consolidates the conceptual CRM and engagement entities visible in the public Agendei reference docs, the consolidated business rules, and the user journeys.
It stays at the product-concept level only.
It is not a database schema, not an architecture model, and not an Arena OS document.

## Entities

### E-CRM-001 — Player / Client / User

- Status: Observed
- Confidence: High
- Domain areas: CRM, Engagement, Scheduling, Billing
- Description: The customer who browses courts, books, pays, invites friends, and coordinates matches.
- Primary responsibilities: Discover courts, create bookings, use booking-related features, communicate with the facility, buy day use, and use coupons.
- Related personas: Player, Prospect.
- Related business rules: BR-BOOKING-001, BR-BOOKING-002, BR-BOOKING-004, BR-BOOKING-005, BR-BOOKING-006, BR-PAYMENT-005, BR-PAYMENT-006, BR-PAYMENT-015, BR-OPS-015, BR-OPS-017, BR-OPS-018.
- Related journeys: J-PLAYER-001, J-PLAYER-002, J-PLAYER-003, J-PLAYER-004, J-PLAYER-005, J-PLAYER-006, J-PLAYER-007, J-PAYMENT-001, J-PAYMENT-002, J-PAYMENT-003, J-PAYMENT-004, J-CRM-001, J-CRM-004, J-CRM-005.
- Relationships: Creates bookings; can pay; can invite friends; can use coupons; can buy day use; can participate in match organization.
- Observable attributes/concepts: Browsing without account until booking, coupons, invitations, team sorting, day use.
- Inferred attributes/concepts: Booking history, profile identity, preferences.
- Public unknowns: Exact login method, identity reuse across facilities, and whether the payer profile differs from the booking profile.
- Source reference: `01-product-overview.md`, `02-personas.md`, `04-navigation.md`, `05-booking-lifecycle.md`, `09-payments-overview.md`, `14-customer-relationship-overview.md`, `15-client-profile-and-history.md`, `16-communication-and-chat.md`, `17-engagement-coupons-and-match-organization.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`, `29-user-journeys-overview.md`, `30-player-booking-journeys.md`, `32-payment-and-cancellation-journeys.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public docs show the customer mostly through booking, payment, and match-organizing behavior.

### E-CRM-002 — Customer Profile

- Status: Inferred
- Confidence: Medium
- Domain areas: CRM, Operations
- Description: The facility-facing view of a customer's identity and relationship.
- Primary responsibilities: Hold the customer identity used by the facility, support booking coordination, and provide a basis for communication and recurring relationships.
- Related personas: Manager, Staff, Player.
- Related business rules: BR-BOOKING-001, BR-OPS-015, BR-OPS-016, BR-PAYMENT-015.
- Related journeys: J-CRM-001, J-CRM-002, J-CRM-003, J-CRM-004.
- Relationships: Can be activated through a booking; can support recurring or monthly relationships.
- Observable attributes/concepts: Customer identity in booking context, coupons, recurring-player concept.
- Inferred attributes/concepts: Contact information, booking history, payment history, tags, customer status.
- Public unknowns: Exact profile screen, editable fields, merge behavior, and privacy controls.
- Source reference: `14-customer-relationship-overview.md`, `15-client-profile-and-history.md`, `16-communication-and-chat.md`, `24-business-rules-overview.md`, `29-user-journeys-overview.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public docs imply a profile concept, but do not show the full screen or field list.

### E-CRM-003 — Customer History

- Status: Inferred
- Confidence: Medium
- Domain areas: CRM, Operations, Billing
- Description: The accumulated record of customer interactions with the facility.
- Primary responsibilities: Preserve the relationship record across bookings, payments, cancellations, day use, and communication where visible.
- Related personas: Manager, Staff.
- Related business rules: BR-OPS-016, BR-PAYMENT-016, BR-BOOKING-015.
- Related journeys: J-CRM-001, J-CRM-002, J-CRM-003, J-CRM-004.
- Relationships: Accumulates after booking and payment activity; supports facility-side review of the customer relationship.
- Observable attributes/concepts: Booking history concept, recurring relationship concept, day use purchase concept.
- Inferred attributes/concepts: Payment timeline, cancellation history, support history, message history.
- Public unknowns: Exact history screens, retention behavior, and whether players can see the same history.
- Source reference: `15-client-profile-and-history.md`, `16-communication-and-chat.md`, `24-business-rules-overview.md`, `29-user-journeys-overview.md`, `33-engagement-and-crm-journeys.md`, `34-user-journeys-open-questions.md`
- Notes: The public docs point to history as a meaningful concept, but not as a public screen layout.

### E-CRM-004 — Chat / Message Channel

- Status: Observed
- Confidence: High
- Domain areas: CRM, Communication, Operations
- Description: The in-app communication channel between the facility and the customer.
- Primary responsibilities: Support booking coordination, customer communication, and operational follow-up.
- Related personas: Manager, Player, Staff, Partner.
- Related business rules: BR-OPS-015, BR-OPS-016.
- Related journeys: J-CRM-001, J-CRM-002.
- Relationships: Connects manager and client; can carry operational messages.
- Observable attributes/concepts: In-app chat, messages, direct communication channel.
- Inferred attributes/concepts: Message retention, threading model, attachment support, templates.
- Public unknowns: Whether chat is per booking or per customer, whether staff can access it, and whether it is retained for audit.
- Source reference: `03-modules.md`, `14-customer-relationship-overview.md`, `16-communication-and-chat.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `29-user-journeys-overview.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public docs expose the channel, but not the full retention or threading model.

### E-CRM-005 — Operational Notification

- Status: Observed
- Confidence: High
- Domain areas: CRM, Communication, Operations
- Description: An alert that informs the manager or customer when an operational event needs attention.
- Primary responsibilities: Notify about booking requests, day-use sales, and other operational events visible in the public flows.
- Related personas: Manager, Player, Staff, Partner.
- Related business rules: BR-BOOKING-007, BR-BOOKING-014, BR-OPS-016.
- Related journeys: J-CRM-002, J-MANAGER-004, J-MANAGER-005, J-PAYMENT-003, J-PAYMENT-004.
- Relationships: Can be triggered by booking or day-use events; can alert the manager that action is needed.
- Observable attributes/concepts: Booking request notification, day-use push notification, booking-event alert.
- Inferred attributes/concepts: Channel mix, read state, customer-facing notification behavior.
- Public unknowns: Whether notifications are push, email, WhatsApp, or in-app only; whether cancellation notices are sent.
- Source reference: `05-booking-lifecycle.md`, `16-communication-and-chat.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `29-user-journeys-overview.md`, `31-manager-operations-journeys.md`, `32-payment-and-cancellation-journeys.md`
- Notes: Booking-request and day-use alerts are public; booking-confirmation alerts are inferred.

### E-CRM-006 — Invited Friend

- Status: Observed
- Confidence: High
- Domain areas: CRM, Engagement
- Description: A person invited by the player to join the match.
- Primary responsibilities: Join the match context after being invited by the player.
- Related personas: Player, Invited Friend, Match participant.
- Related business rules: BR-OPS-017, BR-OPS-018.
- Related journeys: J-PLAYER-007, J-CRM-005.
- Relationships: Is invited by a player; can participate in the match context.
- Observable attributes/concepts: Friend invitations, match-organizing flow.
- Inferred attributes/concepts: Invite identity model, friend list behavior.
- Public unknowns: Invite delivery mechanism and whether the invitee must already be a customer.
- Source reference: `01-product-overview.md`, `03-modules.md`, `17-engagement-coupons-and-match-organization.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `29-user-journeys-overview.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public docs show invitations as a visible feature, but not the invite transport.

### E-CRM-007 — Match

- Status: Observed
- Confidence: High
- Domain areas: CRM, Engagement, Scheduling
- Description: The organized play context built around a booking.
- Primary responsibilities: Gather participants, coordinate teams, and turn a booking into a social play session.
- Related personas: Player, Invited Friend, Match participant.
- Related business rules: BR-OPS-017, BR-OPS-018.
- Related journeys: J-PLAYER-007, J-CRM-005.
- Relationships: Receives invited friends; can be organized around a booking.
- Observable attributes/concepts: Match organization flow, participant coordination, teams.
- Inferred attributes/concepts: Participant list, match state, join eligibility.
- Public unknowns: Whether match is separate from booking or embedded in it.
- Source reference: `01-product-overview.md`, `03-modules.md`, `17-engagement-coupons-and-match-organization.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `29-user-journeys-overview.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public docs position the match around the booking context.

### E-CRM-008 — Team Sorting

- Status: Observed
- Confidence: High
- Domain areas: CRM, Engagement
- Description: The feature that forms teams for the match.
- Primary responsibilities: Split or organize participants into teams around the booking context.
- Related personas: Player, Match participant.
- Related business rules: BR-OPS-018.
- Related journeys: J-PLAYER-007, J-CRM-005.
- Relationships: Supports match setup and participant organization.
- Observable attributes/concepts: Team sorting, match setup.
- Inferred attributes/concepts: Team rules, balancing logic, assignment order.
- Public unknowns: The algorithm and rules used to sort teams.
- Source reference: `01-product-overview.md`, `03-modules.md`, `17-engagement-coupons-and-match-organization.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `29-user-journeys-overview.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public docs identify the feature, but not the sorting logic.

### E-CRM-009 — Lesson / Escolinha Participation

- Status: Observed
- Confidence: Medium
- Domain areas: CRM, Operations, Engagement
- Description: The visible lesson or school-program participation concept shown in the public plan material.
- Primary responsibilities: Represent lesson or escolinha participation where the plan makes the feature visible.
- Related personas: Manager, Player, Student.
- Related business rules: BR-OPS-010, BR-OPS-011, BR-OPS-014.
- Related journeys: J-CRM-006.
- Relationships: Is visible in plan packaging; the participation workflow is not public.
- Observable attributes/concepts: Lesson / escolinha feature name, plan visibility.
- Inferred attributes/concepts: Enrollment, attendance, recurring instruction.
- Public unknowns: Exact workflow, participant lifecycle, and whether the feature is active or plan-visible only.
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `17-engagement-coupons-and-match-organization.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public pages name the feature, but do not show the participant flow.

### E-CRM-010 — Tournament Registration

- Status: Observed
- Confidence: Medium
- Domain areas: CRM, Operations, Engagement
- Description: The visible tournament-registration concept shown in the public plan material.
- Primary responsibilities: Represent tournament sign-up where the plan makes the feature visible.
- Related personas: Manager, Participants.
- Related business rules: BR-OPS-011, BR-OPS-014.
- Related journeys: J-CRM-006.
- Relationships: Is visible in plan packaging; the participant workflow is not public.
- Observable attributes/concepts: Tournament registration feature name, plan visibility.
- Inferred attributes/concepts: Bracket, registration window, fees.
- Public unknowns: Exact workflow, participant lifecycle, and whether the feature is active or plan-visible only.
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `17-engagement-coupons-and-match-organization.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public pages name the feature, but do not show the participant flow.

### E-CRM-011 — Testimonial / Social Proof

- Status: Observed
- Confidence: High
- Domain areas: CRM, Marketing
- Description: Public testimonial blocks and social-proof text used on landing pages.
- Primary responsibilities: Reinforce trust and support conversion for prospective users.
- Related personas: Prospect, Player, Manager.
- Related business rules: None directly consolidated.
- Related journeys: None directly consolidated.
- Relationships: Supports public product positioning.
- Observable attributes/concepts: Testimonial blocks, social-proof text, marketing support.
- Inferred attributes/concepts: Conversion intent, audience targeting.
- Public unknowns: Exact testimonial selection criteria and whether the content changes by audience.
- Source reference: `01-product-overview.md`, `03-modules.md`, `17-engagement-coupons-and-match-organization.md`, `24-business-rules-overview.md`, `29-user-journeys-overview.md`, `33-engagement-and-crm-journeys.md`
- Notes: This is marketing support, not a customer workflow.

## Relationships

### Player creates booking

- Relationship: A player creates a booking.
- Status: Observed
- Confidence: High
- Source entity: Player / Client / User
- Target entity: Booking / Agendamento
- Business meaning: The customer starts a reservation in the player-facing flow.
- Related rules: BR-BOOKING-004, BR-BOOKING-005, BR-BOOKING-006
- Related journeys: J-PLAYER-002, J-PLAYER-003, J-PLAYER-004
- Source reference: `05-booking-lifecycle.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `30-player-booking-journeys.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The booking may then follow online or local-payment branches.

### Booking creates customer relationship with facility

- Relationship: A booking creates a customer relationship with the facility.
- Status: Inferred
- Confidence: Medium
- Source entity: Booking / Agendamento
- Target entity: Customer Profile
- Business meaning: The booking makes the customer legible to the facility-side relationship record.
- Related rules: BR-BOOKING-001, BR-OPS-015, BR-OPS-016
- Related journeys: J-PLAYER-001, J-CRM-001, J-CRM-002
- Source reference: `14-customer-relationship-overview.md`, `15-client-profile-and-history.md`, `24-business-rules-overview.md`, `29-user-journeys-overview.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public docs imply the relationship, but do not show the profile screen.

### Manager communicates with client through chat

- Relationship: A manager communicates with a client through chat.
- Status: Observed
- Confidence: High
- Source entity: Chat / Message Channel
- Target entity: Customer Profile
- Business meaning: The in-app channel connects the facility and the customer around booking or support matters.
- Related rules: BR-OPS-015
- Related journeys: J-CRM-001
- Source reference: `03-modules.md`, `16-communication-and-chat.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public docs do not expose the exact threading model.

### Operational event may trigger notification

- Relationship: An operational event may trigger a notification.
- Status: Inferred
- Confidence: Medium
- Source entity: Booking / Agendamento
- Target entity: Operational Notification
- Business meaning: Booking and day-use events can generate alerts that require manager attention.
- Related rules: BR-BOOKING-007, BR-BOOKING-014, BR-OPS-016
- Related journeys: J-CRM-002, J-MANAGER-004, J-MANAGER-005
- Source reference: `05-booking-lifecycle.md`, `16-communication-and-chat.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `31-manager-operations-journeys.md`, `32-payment-and-cancellation-journeys.md`
- Notes: Booking-confirmation alerts are inferred; local-payment and day-use alerts are observed.

### Player invites friends

- Relationship: A player invites friends.
- Status: Observed
- Confidence: High
- Source entity: Player / Client / User
- Target entity: Invited Friend
- Business meaning: The match-organizing flow lets the customer bring other people into the booking context.
- Related rules: BR-OPS-017
- Related journeys: J-PLAYER-007, J-CRM-005
- Source reference: `01-product-overview.md`, `03-modules.md`, `17-engagement-coupons-and-match-organization.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `30-player-booking-journeys.md`, `33-engagement-and-crm-journeys.md`
- Notes: The invite transport and invitee identity model are not public.

### Invited friends participate in match context

- Relationship: Invited friends participate in the match context.
- Status: Observed
- Confidence: High
- Source entity: Invited Friend
- Target entity: Match
- Business meaning: Invitees become part of the coordinated game around the booked court time.
- Related rules: BR-OPS-017, BR-OPS-018
- Related journeys: J-PLAYER-007, J-CRM-005
- Source reference: `01-product-overview.md`, `03-modules.md`, `17-engagement-coupons-and-match-organization.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `30-player-booking-journeys.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public docs do not describe how non-bookers join.

### Player sorts teams

- Relationship: A player sorts teams.
- Status: Observed
- Confidence: High
- Source entity: Player / Client / User
- Target entity: Team Sorting
- Business meaning: The app helps organize participants into teams for the match.
- Related rules: BR-OPS-018
- Related journeys: J-PLAYER-007, J-CRM-005
- Source reference: `01-product-overview.md`, `03-modules.md`, `17-engagement-coupons-and-match-organization.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `30-player-booking-journeys.md`, `33-engagement-and-crm-journeys.md`
- Notes: The sorting logic is not public.

### Customer may become mensalista

- Relationship: A customer may become a mensalista.
- Status: Observed
- Confidence: High
- Source entity: Customer Profile
- Target entity: Monthly Player Relationship / Mensalista
- Business meaning: A customer can move into a recurring booking relationship on the schedule.
- Related rules: BR-BOOKING-009, BR-BOOKING-010, BR-OPS-003
- Related journeys: J-CRM-003, J-MANAGER-003
- Source reference: `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`, `14-customer-relationship-overview.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `27-operations-business-rules.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public docs do not define the commercial meaning of `mensalista`.

### Customer may use coupon

- Relationship: A customer may use a coupon.
- Status: Observed
- Confidence: High
- Source entity: Customer Profile
- Target entity: Coupon / Discount
- Business meaning: The customer can apply a discount instrument in the booking context.
- Related rules: BR-PAYMENT-015, BR-OPS-011, BR-OPS-012
- Related journeys: J-PLAYER-006, J-CRM-004
- Source reference: `06-scheduling-capabilities.md`, `12-financial-capabilities.md`, `17-engagement-coupons-and-match-organization.md`, `22-plans-tiers-and-feature-packaging.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`, `33-engagement-and-crm-journeys.md`
- Notes: The exact redemption screen and validation flow are not public.

### Customer may buy day use

- Relationship: A customer may buy day use.
- Status: Observed
- Confidence: High
- Source entity: Customer Profile
- Target entity: Day Use Purchase
- Business meaning: The customer can enter the separate daily reservation purchase branch.
- Related rules: BR-BOOKING-012, BR-BOOKING-013, BR-BOOKING-014
- Related journeys: J-PLAYER-005, J-CRM-002
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `12-financial-capabilities.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `30-player-booking-journeys.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public day-use flow is separate from the standard hourly booking branch.

### Lessons are visible but workflow unknown

- Relationship: Lessons are visible but the workflow is unknown.
- Status: Observed
- Confidence: Medium
- Source entity: Customer Profile
- Target entity: Lesson / Escolinha Participation
- Business meaning: The public plan pages show lessons as a feature concept, but not as a fully documented participant flow.
- Related rules: BR-OPS-010, BR-OPS-011, BR-OPS-014
- Related journeys: J-CRM-006
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `17-engagement-coupons-and-match-organization.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `33-engagement-and-crm-journeys.md`
- Notes: The feature name is public; the workflow is not.

### Tournaments are visible but workflow unknown

- Relationship: Tournaments are visible but the workflow is unknown.
- Status: Observed
- Confidence: Medium
- Source entity: Customer Profile
- Target entity: Tournament Registration
- Business meaning: The public plan pages show tournaments as a feature concept, but not as a fully documented participant flow.
- Related rules: BR-OPS-011, BR-OPS-014
- Related journeys: J-CRM-006
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `17-engagement-coupons-and-match-organization.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `33-engagement-and-crm-journeys.md`
- Notes: The feature name is public; the workflow is not.

### Testimonials support public product positioning

- Relationship: Testimonials support public product positioning.
- Status: Observed
- Confidence: High
- Source entity: Testimonial / Social Proof
- Target entity: Player / Client / User
- Business meaning: Public testimonial blocks and social-proof text help prospective users trust the product.
- Related rules: None directly consolidated.
- Related journeys: None directly consolidated.
- Source reference: `01-product-overview.md`, `03-modules.md`, `17-engagement-coupons-and-match-organization.md`, `24-business-rules-overview.md`, `29-user-journeys-overview.md`, `33-engagement-and-crm-journeys.md`
- Notes: This is marketing support rather than a customer workflow.

## Unknowns

- Exact customer profile screen and editable fields.
- Whether booking history, payment history, cancellation history, and day-use history are visible to players.
- Whether chat is per booking or per customer.
- Whether staff and partners can see messages.
- Exact notification channels and whether cancellation notices are sent.
- Exact invite delivery mechanism.
- Exact team-sorting rules.
- Whether invitees must already be customers.
- Whether lessons and tournaments are currently operational or only plan-visible.
- Exact customer-merge and identity behavior across facilities.

