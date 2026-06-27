# Customer Relationship Overview

## Scope
This document covers only public and observable customer relationship behavior in Agendei Quadras.
It is based on the public App Agendei, App Gestor, payment, day use, and plan pages.
Anything not visible there is labeled as inferred or not publicly confirmed.

## Customer Relationship Surfaces
- App Agendei player/client surface: the player browses courts, books, pays, invites friends, sorts teams, and may interact with coupons.
- App Gestor manager/facility surface: the facility manages bookings, local-payment approvals, chat, day use, coupons, fixed bookings, and shared access.
- Booking lifecycle: customer identity appears at booking time and in booking confirmation paths.
- Payment lifecycle: customer identity appears where payments are confirmed, settled, refunded, or paid locally.
- Chat/messages: the public site names a messaging channel between facility and client.
- Coupons/discounts: the player can use discount coupons and managers can create custom coupons.
- Day use purchase: the customer buys a daily reservation as a separate flow.
- Match organization: the player can invite friends and sort teams.
- Monthly players / mensalistas: recurring fixed-booking customers are publicly visible in scheduling and plan material.

## Visible Customer Concepts
| Concept | Description | Related surface | Related workflow | Confidence | Notes |
|---|---|---|---|---|---|
| Player / Cliente / Usuario | The player-side customer who looks for a court and uses the booking app. | App Agendei | Discovery, booking, payment, invitations, and team sorting | High | The public pages show browsing before account creation and booking as the point where the customer starts interacting operationally. |
| Manager / Facility relationship with clients | The facility-side relationship with the customer, including booking approval, communication, and promotional control. | App Gestor | Booking management, local-payment approval, chat, day use, and coupons | High | This is a relationship concept rather than a customer profile field. |
| Booking customer | The person attached to an individual booking. | Booking lifecycle | Create booking, confirm payment, or request local payment | High | Public pages expose the booking flow but not the exact record layout. |
| Paying customer | The customer as payer in online or local-payment flows. | Payment lifecycle | PIX, card, or pay-at-facility payment | High | Payment identity is visible only through the public flow, not through a profile screen. |
| Monthly player / mensalista | A recurring customer tied to fixed bookings. | App Gestor and scheduling pages | Fixed booking management and recurring schedule control | High | Public docs mention both `mensalistas` and `agendamentos fixos`. |
| Match participant | A person who joins a booked match as part of team organization. | App Agendei | Invite friends and sort teams | High | The participant is public in the match-organizing flow, not as a dedicated profile type. |
| Invited friend | A person invited into the match by the booking player. | App Agendei | Friend invitation and team composition | Medium | The invite behavior is public, but the invitee identity model is not shown. |
| Coupon user | The player who applies a discount coupon in the booking flow. | App Agendei and manager pages | Coupon redemption during booking | High | Public pages mention discount coupons for bookings. |
| Day use buyer | The customer who buys a daily reservation as a separate product. | Day use purchase flow | Day use purchase and manager notification | High | The public day-use page describes a separate purchase path rather than an hourly booking. |

## Customer Relationship Lifecycle
1. Observed (High): Player discovers a facility in App Agendei.
2. Observed (High): Player chooses a court, date, and time, and can browse before booking without an account.
3. Observed (High): Player creates a booking, or follows the separate day-use purchase branch.
4. Observed (High): Player pays online or selects local payment.
5. Observed (High): Facility receives the booking or payment request and confirms or approves it where needed.
6. Observed (High): Player may invite friends and sort teams for the match.
7. Observed (High): Facility may communicate through chat/messages and receive notifications.
8. Inferred (Medium): Player may return as a recurring customer through fixed bookings or mensalistas.

## Not Publicly Observable
- Exact customer profile fields.
- Exact customer history screen.
- Exact segmentation or tags.
- Exact CRM notes.
- Exact marketing automation.
- Exact customer merge or deduplication behavior.
- Exact profile visibility across multiple facilities.
- Exact privacy or retention controls for customer records.
