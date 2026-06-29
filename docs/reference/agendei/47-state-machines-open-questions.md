# State Machines Open Questions

## Purpose
This file tracks lifecycle and state uncertainties from the public Agendei reference docs, business rules, journeys, and domain model.
It stays within public-reference gaps and does not rely on private sources.

## Booking State Questions
- What exact booking status labels exist between slot selection, confirmation, cancellation, and refund?
- Is `Booking Started` a visible customer state or only a conceptual step in the booking flow?
- Can the player cancel directly from the public app, or does the facility have to process the cancellation?
- Can a booking be rescheduled without creating a new cancellation penalty?
- How are no-shows represented relative to cancellations?

## Payment State Questions
- Does PIX always confirm instantly, or can payment recognition create a pending state first?
- Is card confirmation always immediate even though settlement is delayed?
- Does a booking ever show more than one payment method at the same time?
- What exact state changes happen if a payment is reversed after confirmation?
- What exact failure state is shown if an online payment does not complete?

## Cancellation and Refund State Questions
- Is the penalty applied automatically or manually?
- Are refunds immediate for every payment path, or only for the published example?
- What exactly happens to the retained cancellation amount after the split?
- Can the retained amount be repassed later, or does it stay with the platform?
- Does the cancellation flow differ for local payment, PIX, and card?

## Day Use State Questions
- Does day use share the same status model as hourly reservations?
- Is the day-use product visible immediately after manager setup, or is there a publish step?
- What exactly happens when the day-use reservation is consumed?
- Can day use be cancelled or refunded, and if so, under what rule?

## Operations and Visibility State Questions
- What exact court visibility or publish workflow makes a facility appear to players?
- Does facility visibility depend only on onboarding, or also on Agendei Pay activation?
- Is App Gestor access immediate after registration, or subject to review?
- What exact facility fields are required at signup?
- What changes the visibility state from player-visible back to hidden or suspended, if anything?

## Shared Access State Questions
- Which permissions can staff receive beyond schedule access?
- Which permissions can partners or co-managers receive?
- Are access profiles predefined or custom?
- Can a manager revoke access without affecting existing bookings?
- Does shared management include Agendei Pay and finance controls in practice?

## Cross-State Questions
- Does booking confirmation depend on payment-method selection only, or also on booking visibility and manager-side permissions?
- Can coupons be applied to day use as well as hourly bookings?
- Can day use and hourly bookings coexist on the same court agenda without conflict?
- How do booking confirmation notifications interact with chat and other operational alerts?
- Are settlement, transfer, and repass treated as distinct states or just as timing milestones?

## Prioritized Investigation List

| Priority | Question | Why it matters | Related state machine | Related entities | Related rules | Related journeys | Suggested future source |
|---|---|---|---|---|---|---|---|
| High | What exact booking statuses exist between slot selection, confirmation, cancellation, and refund? | This determines how the booking lifecycle is actually represented to users and managers. | `SM-BOOKING-001` | `E-SCHED-004`, `E-SCHED-005`, `E-BILL-003`, `E-BILL-009`, `E-BILL-010` | `BR-BOOKING-004`, `BR-BOOKING-005`, `BR-BOOKING-006`, `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013` | `J-PLAYER-002`, `J-PLAYER-003`, `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003`, `J-PAYMENT-004` | Authenticated walkthrough or product video |
| High | What exact screen handles local-payment acceptance, and what manager action confirms it? | This is the most important visible branch of the pay-at-facility journey. | `SM-PAYMENT-002` | `E-BILL-006`, `E-SCHED-005`, `E-OPS-001` | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007` | `J-MANAGER-004`, `J-PAYMENT-003` | Authenticated walkthrough or demo call |
| High | What exactly happens to the retained cancellation amount? | The public docs show the split, but not the final allocation of the retained value. | `SM-CANCEL-001` | `E-BILL-007`, `E-BILL-009`, `E-BILL-010` | `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013` | `J-PAYMENT-004` | Public support article or authenticated walkthrough |
| High | What exact publish or visibility workflow makes a court appear to players? | This determines how the public discovery journey is actually enabled. | `SM-OPS-001` | `E-OPS-006`, `E-OPS-007`, `E-SCHED-001`, `E-SCHED-002` | `BR-OPS-001`, `BR-OPS-002`, `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003` | `J-MANAGER-001`, `J-MANAGER-002`, `J-PLAYER-001` | Product video or authenticated walkthrough |
| High | Which permissions can staff and partners receive beyond schedule access? | This defines delegation boundaries and operational security. | `SM-ACCESS-001` | `E-OPS-002`, `E-OPS-003`, `E-OPS-004`, `E-OPS-005` | `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008`, `BR-OPS-010` | `J-MANAGER-007` | Authenticated walkthrough |
| High | Does shared management include Agendei Pay and finance controls in practice? | This determines whether delegated users can touch money movement or only schedules. | `SM-ACCESS-001`, `SM-PAYMENT-001` | `E-OPS-004`, `E-BILL-001`, `E-BILL-012` | `BR-OPS-004`, `BR-OPS-005`, `BR-OPS-006`, `BR-PAYMENT-010`, `BR-PAYMENT-016` | `J-MANAGER-007`, `J-MANAGER-008`, `J-PAYMENT-005`, `J-PAYMENT-006` | Demo call or authenticated walkthrough |
| High | What exact meaning does `mensalista` have in practice? | It defines the recurring-customer model and whether it is calendar-based, billing-based, or both. | `SM-BOOKING-001` | `E-SCHED-007`, `E-SCHED-008`, `E-CRM-002` | `BR-BOOKING-009`, `BR-BOOKING-010` | `J-MANAGER-003`, `J-CRM-003` | Demo call or product video |
| Medium | Does day use share the same status model as hourly reservations? | This determines whether the day-use flow behaves like a booking or like a separate sale. | `SM-DAYUSE-001` | `E-SCHED-009`, `E-SCHED-010`, `E-CRM-005` | `BR-BOOKING-012`, `BR-BOOKING-014`, `BR-OPS-016` | `J-PLAYER-005`, `J-MANAGER-005` | Product video or authenticated walkthrough |
| Medium | Are coupons limited by date, court, player, or number of uses? | This affects promotion behavior and booking totals. | `SM-PAYMENT-001` | `E-BILL-011`, `E-CRM-002` | `BR-PAYMENT-015`, `BR-OPS-011`, `BR-OPS-012` | `J-PLAYER-006`, `J-CRM-004` | Public support article or authenticated walkthrough |
| Medium | What customer history screens exist for bookings, payments, cancellations, and day use? | This affects support, relationship tracking, and customer self-service. | `SM-BOOKING-001`, `SM-PAYMENT-001`, `SM-CANCEL-001`, `SM-DAYUSE-001` | `E-CRM-002`, `E-CRM-003`, `E-SCHED-010`, `E-BILL-003` | `BR-OPS-016`, `BR-PAYMENT-016` | `J-CRM-001`, `J-CRM-002`, `J-CRM-003` | Authenticated walkthrough or product video |
| Medium | What exact failure state is shown if an online payment does not complete? | This determines whether failed checkout is recoverable or blocks the booking. | `SM-PAYMENT-001` | `E-BILL-003`, `E-BILL-004`, `E-BILL-005` | `BR-PAYMENT-005`, `BR-PAYMENT-006`, `BR-PAYMENT-013` | `J-PLAYER-002`, `J-PLAYER-003`, `J-PAYMENT-001`, `J-PAYMENT-002` | Authenticated walkthrough or public FAQ page |
| Low | How do friend invitations and team sorting work internally? | It clarifies how the match-organization feature is executed in practice. | `SM-OPS-001` | `E-CRM-006`, `E-CRM-007`, `E-CRM-008` | `BR-OPS-017`, `BR-OPS-018` | `J-PLAYER-007`, `J-CRM-005` | Product video or user interview |
| Low | What exact notification channels are used for booking and day-use events? | It determines whether alerts are push, email, WhatsApp, or in-app only. | `SM-BOOKING-001`, `SM-DAYUSE-001` | `E-CRM-005` | `BR-OPS-016`, `BR-BOOKING-007`, `BR-BOOKING-014` | `J-CRM-002`, `J-MANAGER-004`, `J-MANAGER-005` | Public FAQ page or app store screenshots |
| Low | What exact meaning does `central de atendimento` have in practice? | It determines whether the feature is a team, a channel, or both. | `SM-OPS-001`, `SM-ACCESS-001` | `E-OPS-009`, `E-OPS-008` | `BR-OPS-009` | None directly consolidated | Public support article or user interview |
