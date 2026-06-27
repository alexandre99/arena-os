# Communication and Chat

## Scope
This file covers only publicly visible communication behavior.
It is limited to the channels and triggers that can be seen on public pages.

## Public Communication Channels
| Channel name | Who communicates with whom | Trigger | Purpose | Confidence | Notes |
|---|---|---|---|---|---|
| In-app chat / messages | Player/client and facility manager, with possible staff or partner access not publicly detailed | Booking or support context | Direct conversation about the booking or the customer relationship | High | The public site names `Chat de mensagens` as a visible module. |
| Booking notifications | System to customer, and system to manager | Booking creation, confirmation, or request state changes | Inform each side that a booking was created or needs action | Medium | The confirmation logic is public, but the exact notification channel is not. |
| Local-payment booking request notification | System to manager | Player chooses pay-at-facility | Request approval and confirmation | High | The public FAQ says the manager receives the request to accept and confirm it. |
| Day use purchase push notification | System to manager | Day use sale | Notify the manager that a day-use product was sold | High | The public day-use page explicitly mentions a push notification for each sale. |
| Public contact/support channel | Prospect or customer to support | Questions, onboarding, or assistance requests | Reach the company or request help | Medium | The public site exposes contact navigation, but the exact transport mix is not fully visible in the product flow. |

## Chat de Mensagens
- Purpose: direct communication between the customer and the facility.
- Involved personas: player/client and manager/facility; staff and partners are not publicly detailed.
- Likely relationship with bookings: the public product places chat alongside booking and agenda features, so the channel appears to support booking-related coordination.
- Observed: the public site explicitly names the messaging feature.
- Inferred: messages are likely used for booking questions, confirmation follow-up, and operational coordination.
- Unknown: whether chat is per booking or per customer, whether it supports attachments, whether it has templates, and whether staff can access it.

## Notifications
- Local-payment booking request notification: observed; the manager receives a notification to accept and confirm the booking request.
- Day use purchase push notification: observed; the manager receives a push notification for each sale.
- Booking confirmation notification: inferred; online bookings confirm immediately after scheduling, but the public pages do not show a dedicated customer notification format.
- Cancellation notification: not publicly confirmed; cancellation penalties are public, but notification behavior is not shown.

## Communication Boundaries
- It is not public whether chat is per booking or per customer.
- It is not public whether staff can chat or only view.
- It is not public whether chat supports attachments.
- It is not public whether chat has templates or canned responses.
- It is not public whether chat history is retained for audit purposes.
- It is not public whether notifications are push, email, WhatsApp, or in-app only.
- It is not public whether messages are auditable.

## Not Publicly Observable
- Exact notification channels.
- Exact message retention rules.
- Exact read or delivery status behavior.
- Exact support workflow behind the public contact entry point.
- Exact permissions for staff, partners, or other shared-access users in communication flows.
