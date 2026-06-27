# Scheduling Capabilities

## Scope
This file catalogs public scheduling features only.
Observed statements come from public pages and FAQs.
Inferred statements are labeled explicitly.

## Capabilities Inventory
| Capability name | Description | User/persona involved | Public evidence summary | Business value | Confidence level | Notes |
|---|---|---|---|---|---|---|
| Court availability | Players can see available time slots and choose a day and hour from a court agenda. | Player | The public App Agendei page says each court has a full agenda and the player chooses the day and time. | Enables court discovery and slot selection. | High | Core booking surface. |
| One-off reservations / agendamentos avulsos | Single, non-recurring reservations created by the facility and booked by players. | Manager, player | Public pages say the manager can receive and create avulso bookings. | Sells discrete time slots. | High | The exact slot-hold behavior is not public. |
| Fixed reservations / agendamentos fixos | Recurrent or reserved booking patterns that remain on the agenda. | Manager, player | Public pages explicitly mention fixed bookings alongside avulso bookings. | Supports recurring use of courts. | High | The recurrence rules are not public. |
| Monthly players / mensalistas | Public term for recurring players associated with fixed bookings. | Manager, player | Public pages use the term mensalistas together with fixed reservations. | Supports recurring revenue and retained customers. | High | The commercial model is not fully defined publicly. |
| Multiple courts | A single account can manage more than one court. | Manager, staff | Public pages say the operation can manage all courts in one app or site. | Scales the product to multi-court venues. | High | Administration capability more than a booking rule. |
| Day use | A separate daily reservation product sold by the facility. | Player, manager | The `Diária` page describes a day-based reservation that the client buys through the app. | Adds non-hourly revenue. | High | Public flow is a purchase flow, not a full screen-by-screen booking walkthrough. |
| Lessons / escolinha | Lesson or school programs visible in the pricing comparison. | Manager, player | The plan comparison lists `Gestão de Aulas e Escolinha`. | Extends scheduling beyond court rental. | Medium | Public workflow detail is not available. |
| Tournaments | Tournament registration visible in the pricing comparison. | Manager, player | The plan comparison lists `Inscrição de Torneios`. | Supports event participation and administration. | Medium | Public workflow detail is not available. |
| Cancellation penalties | Fee rules for late cancellation. | Manager, player | The payment page explains a tolerance window and a percentage-based penalty example. | Protects revenue from last-minute cancellations. | High | The default rule is not public. |
| Chat related to bookings | Message channel between the facility and the client. | Manager, player | Public pages describe a single communication channel in the app. | Reduces phone calls and fragmented communication. | High | The exact message flow is not public. |
| Coupons related to bookings | Discount coupons that can be used against bookings. | Manager, player | The App Agendei FAQ says players can use court discount coupons, and the plan page says managers can create personalized coupons. | Drives promotions and retention. | High | Exact redemption timing is not public. |
| Payment-linked scheduling | Booking confirmation depends on the payment method chosen. | Player, manager | The App Agendei FAQ says PIX and card confirm immediately, while local payment waits for manager acceptance. | Connects money collection to booking state. | High | Core operational rule. |
| Shared management of schedules | Multiple people can share control of the same schedule. | Manager, staff, partner | Public pages say different access profiles can be shared with employees and partners. | Delegation and collaborative operation. | High | Permission granularity is not public. |
| Staff schedule access | Employees can access the app to manage schedules. | Staff | The App Gestor FAQ says employees also get access to manage hours. | Lets staff handle daily operations. | High | Exact role boundaries are not public. |

## Capability Classification
- Core scheduling
  - Court availability
  - One-off reservations / agendamentos avulsos
  - Fixed reservations / agendamentos fixos
  - Monthly players / mensalistas
- Financially connected scheduling
  - Day use
  - Cancellation penalties
  - Coupons related to bookings
  - Payment-linked scheduling
- Communication support
  - Chat related to bookings
- Access / administration support
  - Multiple courts
  - Shared management of schedules
  - Staff schedule access
- Future or announced capability
  - None of the scheduling capabilities above are clearly future-only in public material.
  - The public plan page does show adjacent future items such as material rental, charge generation, and AI, but those are outside this scheduling inventory.
- Not enough public detail
  - Lessons / escolinha
  - Tournaments

## Not Publicly Observable
- Exact booking slot locking or expiration rules.
- Exact waitlist behavior.
- Exact conflict resolution when two users want the same slot.
- Exact booking edit and reschedule behavior.
- Exact coupon validation and stacking rules.
- Exact lesson and tournament workflows.
