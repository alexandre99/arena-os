# Booking Lifecycle

## Scope
This document covers only public and observable booking behavior in Agendei Quadras.
Observed statements come from public pages and FAQs.
Inferred statements are labeled explicitly.
Anything not confirmed publicly is listed as unknown.

## Player Booking Journey
1. **Observed (High):** The player starts from `App Agendei`.
   The public page says the app can be explored without an account until the user wants to schedule a time.
2. **Observed (High):** The player finds courts by location.
   The public page presents location-based discovery as the first step for finding a court in the city.
3. **Observed (High):** Each court exposes a full agenda, and the player chooses the day and time slot.
4. **Observed (High):** The player submits the booking.
5. **Observed (High):** If the player chooses PIX or card, the booking is confirmed immediately after scheduling.
6. **Observed (High):** If the player chooses payment at the facility, the request is sent to the manager for acceptance and confirmation.
7. **Observed (High):** The player can invite friends to the match.
8. **Observed (High):** The app can sort teams for the match.
9. **Inferred (Medium):** Discount coupons may be part of the player flow because the public pages say players can use court discount coupons, but the exact redemption step is not public.

## Facility Booking Journey
1. **Observed (High):** The facility registers the quadra from the public site.
2. **Inferred (Medium):** After registration, the facility configures the court so it appears in `App Agendei`.
   The public pages imply this relationship, but the setup screen is not public.
3. **Observed (High):** The manager creates an `Agendei Pay` digital account through credenciamento.
   The public payment page says approval can happen in up to 10 minutes and then PIX or card receipt can be activated.
4. **Observed (High):** The facility receives booking requests in `App Gestor`.
5. **Observed (High):** For local-payment bookings, the manager accepts and confirms the request.
6. **Observed (High):** The manager manages avulso and fixed bookings, including mensalistas, across one or many courts.
7. **Observed (High):** The manager handles cancellations through the cancellation-fee rule.
8. **Observed (High):** The manager can enable day use as a separate sale flow.
9. **Observed (High):** The manager can share schedule administration with employees and partners.

## Booking Confirmation Paths
| Path | Observable trigger | Confirmation behavior | Manager action required | Confidence | Notes |
|---|---|---|---|---|---|
| Online PIX payment | Player chooses PIX in `App Agendei` during booking | Booking is confirmed immediately after scheduling | None for confirmation | High | Public payment text says PIX settlement reaches the digital account 24 hours after the scheduled time, or on the next business day for weekend bookings. |
| Online card payment | Player chooses card in `App Agendei` during booking | Booking is confirmed immediately after scheduling | None for confirmation | High | Public payment text says card settlement reaches the digital account 30 days after the match. |
| Local payment / pay at facility | Player chooses payment at the facility | The request waits for manager acceptance and confirmation | Yes | High | The public FAQ does not expose the exact intermediate status names. |
| Day use purchase | Player buys a `Diária` in `App Agendei` | The public page describes the sale as a purchase and says the manager receives a push notification for each sale | None publicly described | Medium | This is a day-based reservation product rather than a standard hourly booking. |

## Cancellation Behavior
### Observed
- Cancellation penalties are publicly visible.
- The manager can define a cancellation rule using a tolerance window and a percentage.
- The public payment page gives an example where cancellations within 8 hours of the slot incur a 20% fee.
- In that example, 20% is retained by `Agendei Pay` and 80% is refunded to the customer immediately.
- Public marketing text frames the feature as protection against late cancellations and lost revenue.

### Inferred or Unknown
- It is not publicly confirmed whether players can cancel directly or whether the facility must process the cancellation.
- The default tolerance window and penalty percentage are not public; only an example is shown.
- No-show handling, late-arrival handling, and exact refund timing for every payment path are not public.
- The exact edit and reschedule flow is not public.

## Not Publicly Observable
- Exact internal booking status names and transitions.
- Exact approval screen for local-payment bookings.
- Exact cancellation rule configuration options beyond the public example.
- Exact no-show handling.
- Exact booking edit and reschedule flow.
- Exact waitlist or conflict-resolution behavior.
- Exact coupon validation flow.
