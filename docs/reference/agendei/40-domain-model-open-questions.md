# Domain Model Open Questions

## Purpose
This file tracks conceptual-domain uncertainties from the public Agendei reference docs, the consolidated business rules, and the user journeys.
It stays within public-reference gaps and does not rely on private sources.

## Scheduling Entity Questions
- What exact booking statuses exist between request, confirmation, cancellation, and refund?
- Can the player cancel directly, or must the facility process the cancellation?
- Can bookings be rescheduled without triggering a cancellation penalty?
- What exact slot-hold behavior exists before booking confirmation?
- Does day use block court availability inside the same agenda as hourly bookings?
- Does day use share the same status model as hourly reservations?
- Can one customer hold more than one fixed booking across courts?
- How are no-shows treated relative to cancellations?

## Billing Entity Questions
- Does PIX use QR code, copy-and-paste, or both?
- Is card support limited to credit card, or does it include debit or installments?
- Can one booking use more than one payment method?
- Do weekend settlement rules apply only to PIX, or also to card?
- What exact payout exceptions or manual withdrawal constraints exist?
- What exactly happens to the retained cancellation amount?
- Are coupons limited by date, court, player, or number of uses?
- Can coupons apply to day use as well as hourly bookings?
- What exactly is the charge generator announced on the plan page?
- What exactly is the material-rental workflow behind the coming-soon label?

## CRM and Engagement Entity Questions
- Is chat per booking or per customer?
- Do staff and partners see messages?
- What customer history screens exist for bookings, payments, cancellations, and day use?
- Is booking history visible to players, managers, or both?
- Are notifications push, email, WhatsApp, or in-app only?
- How do friend invitations and team sorting work internally?
- What is the exact lesson and tournament participation workflow?
- Are testimonials purely marketing, or tied to public profile sections?

## Operations and Permission Entity Questions
- Which permissions can staff receive beyond schedule access?
- Which permissions can partners or co-managers receive?
- Are access profiles predefined or custom?
- Can a manager revoke access without affecting bookings?
- Does shared management include Agendei Pay and finance controls?
- What exact court fields exist in the manager setup flow?
- What exactly does central de atendimento mean in practice?
- When will AI management actually be available?

## Cross-Domain Relationship Questions
- Does facility visibility require onboarding only, or also Agendei Pay activation?
- Can coupons be applied to day use as well as hourly bookings?
- Can day use and hourly bookings coexist on the same court agenda?
- Can the same customer hold multiple fixed bookings across courts?
- How do booking confirmation notifications interact with chat and other operational alerts?
- Does shared management include finance and Agendei Pay controls in practice?

## Prioritized Investigation List

| Priority | Question | Why it matters | Related entities | Related rules | Related journeys | Suggested future source |
|---|---|---|---|---|---|---|
| High | What exact booking statuses exist between request, confirmation, cancellation, and refund? | This determines how the booking lifecycle is actually represented to users and managers. | `E-SCHED-005`, `E-BILL-003`, `E-BILL-009`, `E-BILL-010` | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-BOOKING-015`, `BR-PAYMENT-011`, `BR-PAYMENT-013` | `J-PLAYER-004`, `J-MANAGER-004`, `J-PAYMENT-003`, `J-PAYMENT-004` | Authenticated walkthrough or product video |
| High | What exact screen handles local-payment acceptance, and what manager action confirms it? | This is the most important visible branch of the pay-at-facility journey. | `E-BILL-006`, `E-CRM-005`, `E-SCHED-005` | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007` | `J-MANAGER-004`, `J-PAYMENT-003` | Authenticated walkthrough or demo call |
| High | What exactly happens to the retained cancellation amount? | The public docs show the split, but not the final allocation of the retained value. | `E-BILL-009`, `E-BILL-010`, `E-BILL-007` | `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013` | `J-PAYMENT-004` | Public support article or authenticated walkthrough |
| High | Which permissions can staff and partners receive beyond schedule access? | This determines delegation boundaries and operational security. | `E-OPS-002`, `E-OPS-003`, `E-OPS-004`, `E-OPS-005` | `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008`, `BR-OPS-010` | `J-MANAGER-007` | Authenticated walkthrough |
| High | Does shared management include Agendei Pay and finance controls? | This determines whether delegated users can touch money movement or only schedules. | `E-OPS-004`, `E-OPS-006`, `E-BILL-001`, `E-BILL-012` | `BR-OPS-004`, `BR-OPS-005`, `BR-OPS-006`, `BR-PAYMENT-010`, `BR-PAYMENT-016` | `J-MANAGER-007`, `J-MANAGER-008` | Demo call or authenticated walkthrough |
| High | What exact meaning does mensalista have in practice? | It defines the recurring-customer model and whether it is calendar-based, billing-based, or both. | `E-SCHED-008`, `E-SCHED-007`, `E-CRM-002` | `BR-BOOKING-009`, `BR-BOOKING-010` | `J-MANAGER-003`, `J-CRM-003` | Demo call or product video |
| High | What exact publish or visibility workflow makes a court appear to players? | This determines how the public discovery journey is actually enabled. | `E-OPS-007`, `E-SCHED-002`, `E-SCHED-003`, `E-SCHED-004` | `BR-OPS-001`, `BR-OPS-002`, `BR-BOOKING-001`, `BR-BOOKING-002` | `J-MANAGER-002`, `J-PLAYER-001` | Product video or authenticated walkthrough |
| Medium | Are coupons limited by date, court, player, or number of uses? | This affects promotion behavior and booking totals. | `E-BILL-011`, `E-CRM-002` | `BR-PAYMENT-015`, `BR-OPS-011`, `BR-OPS-012` | `J-PLAYER-006`, `J-CRM-004` | Public support article or authenticated walkthrough |
| Medium | What customer history screens exist for bookings, payments, cancellations, and day use? | This affects support, relationship tracking, and customer self-service. | `E-CRM-002`, `E-CRM-003`, `E-SCHED-010`, `E-BILL-003` | `BR-OPS-016`, `BR-PAYMENT-016` | `J-CRM-001`, `J-CRM-002`, `J-CRM-003` | Authenticated walkthrough or product video |
| Medium | Does day use share the same status model as hourly reservations? | This determines whether the day-use flow behaves like a booking or like a separate sale. | `E-SCHED-009`, `E-SCHED-010`, `E-SCHED-005`, `E-CRM-005` | `BR-BOOKING-012`, `BR-BOOKING-014`, `BR-OPS-016` | `J-PLAYER-005`, `J-CRM-002` | Product video or authenticated walkthrough |
| Medium | Are lessons and tournaments currently operational or only plan-visible? | It affects whether the public plan page reflects active workflows or roadmap items. | `E-CRM-009`, `E-CRM-010`, `E-OPS-010`, `E-OPS-008` | `BR-OPS-010`, `BR-OPS-011`, `BR-OPS-014` | `J-CRM-006` | Public FAQ page or product video |
| Medium | What exact notification channels are used for booking and day-use events? | It determines whether alerts are push, email, WhatsApp, or in-app only. | `E-CRM-005`, `E-CRM-004`, `E-SCHED-010` | `BR-OPS-016`, `BR-BOOKING-007`, `BR-BOOKING-014` | `J-CRM-002`, `J-MANAGER-004`, `J-MANAGER-005` | Public FAQ page or app store screenshots |
| Low | How do friend invitations and team sorting work internally? | It clarifies how the match-organization feature is executed in practice. | `E-CRM-006`, `E-CRM-007`, `E-CRM-008` | `BR-OPS-017`, `BR-OPS-018` | `J-PLAYER-007`, `J-CRM-005` | Product video or user interview |
| Low | What exact meaning does central de atendimento have in practice? | It determines whether the feature is a team, a channel, or both. | `E-OPS-009`, `E-OPS-008` | `BR-OPS-009` | None directly consolidated | Public support article or user interview |
| Low | When will AI management be available? | It clarifies whether the announced feature is roadmap-only or nearing release. | `E-OPS-010`, `E-OPS-008` | `BR-OPS-014` | None directly consolidated | Public FAQ page or product video |

