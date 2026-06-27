# Payments Overview

## Scope
This document covers only public and observable payment behavior in Agendei Quadras.
Observed statements come from public pages and FAQs.
Inferred statements are labeled explicitly.
Anything not confirmed publicly is listed as unknown.

## Payment Surfaces
- `App Agendei` player payment surface: the player-facing booking flow where the user chooses how to pay for a booking.
- `App Gestor` manager payment configuration surface: the facility-facing area where Agendei Pay is configured, payment receipts are enabled, and financial behavior is managed.
- `Agendei Pay` public page: the public marketing page for the digital account, PIX/card receipt, transfers, and cancellation fees.
- `Diaria (Day Use)` payment surface: the public flow for buying a day-based reservation.
- Public pricing and plan page: the public page that packages payment, financial, and future billing capabilities into subscription plans.

## Payment Methods

### PIX
- Description: The player pays through the app using PIX.
- Who initiates it: The player.
- When it appears in the booking lifecycle: At booking time in `App Agendei`.
- Confirmation behavior: Booking is confirmed immediately after scheduling.
- Confidence level: High.
- Notes: The public payment page says PIX settlement reaches the digital account 24 hours after the scheduled time, or on the next business day for weekend bookings. The page also shows a transaction fee of 1% + R$0,99 on approved transactions.

### Card
- Description: The player pays through the app using credit card.
- Who initiates it: The player.
- When it appears in the booking lifecycle: At booking time in `App Agendei`.
- Confirmation behavior: Booking is confirmed immediately after scheduling.
- Confidence level: High.
- Notes: The public payment page says card settlement reaches the digital account 30 days after the match, with future anticipation of receivables mentioned publicly.

### Local payment / pay at facility
- Description: The player pays at the facility, either by machine or in cash at the venue.
- Who initiates it: The player, with manager acceptance required.
- When it appears in the booking lifecycle: At booking time in `App Agendei`.
- Confirmation behavior: Confirmation requires manager acceptance and confirmation.
- Confidence level: High.
- Notes: The public FAQ says the manager receives a notification to accept and confirm the request.

## Payment Impact on Booking Confirmation
| Payment method | Booking confirmation behavior | Manager action required | Publicly stated settlement/repass timing | Confidence | Notes |
|---|---|---|---|---|---|
| PIX | Confirmed immediately after scheduling | No | 24 hours after the scheduled time; next business day for weekend bookings | High | Public page also shows a transaction fee of 1% + R$0,99. |
| Card | Confirmed immediately after scheduling | No | 30 days after the match | High | Public text mentions future anticipation of receivables as a possible feature. |
| Local payment / pay at facility | Request is sent to the manager for acceptance and confirmation | Yes | Not publicly stated | High | Public text describes payment by machine or cash at the facility. |
| Day use purchase | Public page describes a purchase flow rather than a standard hourly booking | No public confirmation step described | Not publicly stated | Medium | The manager receives a push notification for each sale. |

## Payment-Related Business Concepts
- Digital account: The Agendei Pay account created for the facility to receive online payments and move funds.
- Credenciamento: The public onboarding and approval flow used to create the digital account.
- Online payment: Advance payment for a booking through the app, using PIX or card.
- Local payment: Payment at the facility instead of through the app.
- Repass: The public term for sending net values to the facility after settlement.
- Settlement: The time when funds become available in the digital account.
- Cancellation fee: A penalty charged when a cancellation happens outside the tolerated time window.
- Refund: Money returned to the customer, fully or partially, depending on the published example.
- Coupons: Discount instruments used in booking flows and configurable by managers.
- Day use purchase: A unitary daily reservation sold as a separate purchase flow.
- Cash flow: The financial view that tracks revenue, expense, and profit at the facility level.

## Not Publicly Observable
- Exact payment status names.
- Exact failed payment behavior.
- Exact chargeback behavior.
- Exact card installment behavior.
- Exact payout configuration.
- Exact reconciliation screens.
- Exact coupon validation rules.
- Exact local-payment terminal behavior beyond the public examples.
