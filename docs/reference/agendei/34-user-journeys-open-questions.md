# User Journeys Open Questions

## Purpose
This file tracks journey uncertainties from the public Agendei reference docs and the consolidated business rules.
It stays within public-reference gaps and does not rely on private sources.

## Player Journey Questions
- What exact search modes exist in App Agendei beyond location-based discovery?
- At what exact point does booking require account creation?
- Where exactly does coupon entry happen in the booking flow?
- Can the player see booking history or upcoming bookings from the public app surface?
- Does day use share the same status model as hourly reservations?
- How are friend invitations delivered to invited people?
- What rules drive the team-sorting behavior?

## Manager Journey Questions
- What exact facility fields are required at signup?
- Is App Gestor access immediate after registration or subject to review?
- Which documents are mandatory for the responsible person?
- What exact court visibility or publish workflow makes a facility appear to players?
- How are fixed bookings created, edited, and removed?
- Which permissions can staff receive beyond schedule access?
- Which permissions can partners or co-managers receive?
- Does shared management include Agendei Pay and finance controls?
- What exact finance reports are visible in the manager surface?
- How do lessons and tournaments work operationally?

## Payment and Cancellation Journey Questions
- Does PIX use QR code, copy-and-paste, or both?
- Is card payment limited to credit card, or does debit or installment support also exist?
- What exact payment options exist for local payment at the facility?
- What exact booking statuses exist for paid, pending, accepted, cancelled, refunded, and no-show flows?
- Can the manager override the automatic confirmation rule for PIX or card bookings?
- Do weekend settlement rules apply only to PIX, or also to card?
- Can funds be withdrawn instantly at any time, or only after settlement?
- Who can initiate cancellation?
- Can rescheduling avoid the cancellation penalty?
- What exactly happens to the retained cancellation amount?
- How are chargebacks or disputes handled?

## CRM and Engagement Journey Questions
- Is chat per booking or per customer?
- Do staff and partners see messages?
- What customer history screens exist for bookings, payments, cancellations, and day use?
- Is payment history visible as a customer statement or ledger?
- Are notifications push, email, WhatsApp, or in-app only?
- Are booking confirmations and cancellation notices sent automatically?
- Does mensalista mean recurring billing, a fixed booking relationship, or both?
- Can coupons be limited by date, court, player, or number of uses?
- Can coupons stack with other discounts?
- Are coupons usable for day use, only hourly bookings, or both?
- How do lessons and tournaments work for participants in practice?
- Are lessons and tournaments currently operational or only plan-visible?

## Cross-Journey Questions
- Does facility visibility require onboarding only, or also Agendei Pay activation?
- Does shared management include finance and Agendei Pay controls in practice?
- Can the same customer hold more than one fixed booking across courts?
- Can day use and hourly bookings coexist on the same court agenda?
- How do booking confirmation notifications interact with chat and other operational alerts?
- Can coupons be applied to day use as well as hourly bookings?

## Prioritized Investigation List

| Priority | Question | Why it matters | Related journey | Related rules | Suggested future source |
|---|---|---|---|---|---|
| High | What exact booking statuses exist between request, confirmation, cancellation, and refund? | This determines the booking lifecycle states that users and managers actually see. | `J-PLAYER-004`, `J-PAYMENT-003`, `J-PAYMENT-004` | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-BOOKING-015`, `BR-PAYMENT-011`, `BR-PAYMENT-013` | Authenticated walkthrough or product video |
| High | What exact screen handles local-payment acceptance, and what is the manager action that confirms it? | This is the key visible branch of the pay-at-facility journey. | `J-MANAGER-004`, `J-PAYMENT-003` | `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007` | Authenticated walkthrough or demo call |
| High | Can bookings be rescheduled without triggering a cancellation penalty? | This changes the practical meaning of the cancellation rule. | `J-PAYMENT-004` | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012` | Authenticated walkthrough or user interview |
| High | What exactly happens to the retained cancellation amount? | The public docs show the split but not the final allocation of the retained portion. | `J-PAYMENT-004` | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013` | Public support article or authenticated walkthrough |
| High | Which permissions can staff and partners receive beyond schedule access? | This defines delegation boundaries and operational security. | `J-MANAGER-007`, `J-CRM-001` | `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008` | Authenticated walkthrough |
| High | Does shared management include Agendei Pay and finance controls? | This determines whether delegated users can touch money movement. | `J-MANAGER-007`, `J-MANAGER-008` | `BR-OPS-005`, `BR-OPS-006`, `BR-PAYMENT-010`, `BR-PAYMENT-016` | Demo call or authenticated walkthrough |
| High | What exact meaning does mensalista have in practice? | It defines the recurring-customer model and how schedules are represented. | `J-CRM-003`, `J-MANAGER-003` | `BR-BOOKING-009`, `BR-BOOKING-010` | Demo call or product video |
| High | What exact publish or visibility workflow makes a court appear to players? | This determines how the public discovery journey is actually enabled. | `J-MANAGER-002`, `J-PLAYER-001` | `BR-OPS-001`, `BR-OPS-002`, `BR-BOOKING-001`, `BR-BOOKING-002` | Product video or authenticated walkthrough |
| Medium | Are coupons limited by date, court, player, or number of uses? | This affects promotion behavior and booking totals. | `J-PLAYER-006`, `J-CRM-004` | `BR-PAYMENT-015`, `BR-OPS-011`, `BR-OPS-012` | Public support article or authenticated walkthrough |
| Medium | What customer history screens exist for bookings, payments, cancellations, and day use? | This affects support, relationship tracking, and customer self-service. | `J-CRM-001`, `J-CRM-003`, `J-CRM-004` | `BR-OPS-015`, `BR-OPS-016` | Authenticated walkthrough or product video |
| Medium | Does day use share the same status model as hourly reservations? | This determines whether the day-use flow behaves like a booking or like a separate sale. | `J-PLAYER-005`, `J-CRM-002` | `BR-BOOKING-012`, `BR-BOOKING-014`, `BR-OPS-016` | Product video or authenticated walkthrough |
| Low | How do friend invitations and team sorting work internally? | It clarifies how the match-organization feature is executed in practice. | `J-PLAYER-007`, `J-CRM-005` | `BR-OPS-017`, `BR-OPS-018` | Product video or user interview |
| Low | What exact notification channels are used for booking and day-use events? | It determines whether alerts are push, email, WhatsApp, or in-app only. | `J-CRM-002` | `BR-OPS-016`, `BR-BOOKING-007`, `BR-BOOKING-014` | Public FAQ page or app store screenshots |
| Low | Are lessons and tournaments currently operational or only plan-visible? | It affects whether the public plan page reflects active workflows or roadmap items. | `J-CRM-006`, `J-MANAGER-003` | `BR-OPS-010`, `BR-OPS-011`, `BR-OPS-014` | Public support article or product video |
