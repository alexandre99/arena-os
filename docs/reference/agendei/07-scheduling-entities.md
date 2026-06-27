# Scheduling Entities

## Scope
The entities below are conceptual and based only on public product behavior.
They are not a database design.
Observed attributes come from public pages and FAQs.
Inferred attributes are labeled explicitly.

## Entity Inventory
| Entity name | Description | Related persona | Related capabilities | Observable attributes | Inferred attributes | Confidence level | Notes |
|---|---|---|---|---|---|---|---|
| Facility / Quadra esportiva | The sports venue or operator that owns the court operation. | Manager, staff | Multiple courts, shared management, day use, payment-linked scheduling | Can register from the public site, can appear in `App Agendei`, can create `Agendei Pay`, can receive booking requests | Location data, contact data, payment account, visibility settings | High | Public pages also use `centro esportivo` language. |
| Court / Quadra | The individual rentable court or playing surface. | Player, manager | Court availability, one-off reservations, fixed reservations, day use | Has an agenda and available time slots | Sport type, price rules, court-specific exceptions | High | A facility may have more than one court. |
| Player / Cliente | The person looking for and booking a court. | Player | Court availability, one-off reservations, payment-linked scheduling, coupons, team sorting | Can browse without an account, choose day and time, pay by PIX/card/local, invite friends | Account profile, booking history, saved preferences | High | Public pages also call this role `jogador` or `usuário`. |
| Booking / Agendamento | A reservation request or confirmed time slot. | Player, manager | One-off reservations, fixed reservations, payment-linked scheduling, cancellations | Has a day, time, court, and a confirmation outcome | Booking identifier, status history, participants, notes | High | Public pages show both request and confirmed states. |
| Available time slot / Horário disponível | A bookable opening in a court agenda. | Player, manager | Court availability, one-off reservations | Visible day, time, and court agenda | Hold expiration, conflict resolution, maximum duration | High | The exact hold mechanics are not public. |
| Fixed booking / Agendamento fixo | A recurring or reserved booking pattern. | Manager, player | Fixed reservations, monthly players | Public pages explicitly mention fixed bookings | Recurrence rule, billing cadence, exceptions | Medium | Public pages confirm existence, not the recurrence model. |
| Monthly player / Mensalista | A recurring customer associated with fixed bookings. | Manager, player | Fixed reservations, monthly players | Public pages use the term `mensalistas` | Subscription-like terms, reserved slot set, payment cycle | Medium | The exact commercial meaning is not defined publicly. |
| Payment | The money movement attached to a booking or day use sale. | Player, manager | Payment-linked scheduling, cancellation penalties, day use | PIX, card, local payment, digital account settlement timing | Transaction status, payout ledger, reversals | High | Includes `Agendei Pay` and local payment at the facility. |
| Cancellation | The termination of a booking before use. | Player, manager | Cancellations, cancellation penalties | Late cancellation example is publicly described | Initiator, reason, exact status history | High | No-show handling is separate and not public. |
| Cancellation penalty | The fee retained when a booking is canceled too late. | Player, manager | Cancellation penalties, payment-linked scheduling | Tolerance window and percentage-based penalty example | Formula, rounding, automation timing | High | The public example uses 8 hours and 20%. |
| Day use product / Diária | A day-based product that grants access for a longer period than an hourly booking. | Player, manager | Day use, payment-linked scheduling | Name, available days, courts included, duration, price, payment form | Capacity rule, slot blocking, check-in behavior | High | The public flow is a purchase flow, not an hourly booking screen walkthrough. |
| Staff / Funcionário | Staff member who manages schedules under shared access. | Manager, staff | Shared management of schedules, staff schedule access | Employees can access the app to manage hours | Role scope, court scope, approval rights | High | Exact permissions are not public. |
| Partner / Sócio | Business partner who shares management responsibility. | Manager, partner | Shared management of schedules | Shared management with partners is publicly visible | Ownership share, role scope, approval rights | High | The permission model is not public. |
| Coupon | A discount instrument applied to bookings. | Player, manager | Coupons related to bookings | Players can use discount coupons; managers can create personalized coupons | Validity period, stacking rules, eligibility rules | High | The exact redemption moment is not public. |
| Lesson / Aula | A class or school program associated with the facility. | Manager, player | Lessons / escolinha | Visible in the plan comparison | Schedule pattern, enrollment, pricing | Medium | Workflow is not public. |
| Tournament registration | Event or competition registration. | Manager, player | Tournaments | Visible in the plan comparison | Bracket, registration window, fees | Medium | Workflow is not public. |

## Entity Relationships
- **Observed:** A facility may have multiple courts.
- **Observed:** A player may create a booking.
- **Observed:** A booking may be confirmed immediately when PIX or card is chosen.
- **Observed:** A booking may wait for manager acceptance when local payment is chosen.
- **Observed:** A cancellation may trigger a penalty and partial refund or retention.
- **Observed:** A facility may sell day use products separately from hourly bookings.
- **Observed:** A facility may share schedule management with staff and partners.
- **Observed:** A coupon may discount a booking.
- **Inferred:** A monthly player likely relates to a fixed booking pattern, but the exact commercial and calendar relationship is not publicly defined.
- **Not publicly confirmed:** A lesson or tournament registration may connect to the same agenda system, but the relationship to court slots is not described publicly.

## Not a Data Model
This file is conceptual only.
It must not be used as a database schema, implementation design, or API contract.
