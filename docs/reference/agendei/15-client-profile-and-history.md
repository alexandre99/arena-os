# Client Profile and History

## Scope
This document is conceptual and based only on public product behavior.
It does not define a database model or an implementation schema.

## Client Identity
- Observed (High): App Agendei can be used without an account until the user wants to schedule.
- Observed (High): Booking is the point where customer identity becomes operationally relevant.
- Inferred (Medium): The booking record likely needs at least a display name or account identity, but the public pages do not expose the exact fields.
- Not publicly confirmed: Whether login is by phone, email, CPF, social account, or another method.
- Not publicly confirmed: Whether the same identity is reused across multiple facilities or scoped to one facility.
- Inferred (Low): Invitation identity likely maps back to the same customer identity used in booking, but the public pages do not show the mechanics.
- Not publicly confirmed: Whether the payer profile differs from the booking profile.

## Publicly Visible Profile Attributes
| Attribute or concept | Observable or inferred | Where it appears | Confidence | Notes |
|---|---|---|---|---|
| Name | Inferred | Booking flow, chat, and invitations | Medium | The public pages imply a named customer identity, but no public profile screen shows the field list. |
| Contact information | Not publicly observable | Not publicly visible | Low | The public product pages do not expose the contact fields used for login or notifications. |
| Location | Not publicly observable | Court discovery, not customer profile | Low | Location is public for finding facilities, not for a customer profile field. |
| Booking history | Inferred | Public app narrative and booking-related testimonial language | Medium | Public material points to booking history as a meaningful concept, but no public history screen is shown. |
| Payment history | Not publicly observable | Payment lifecycle | Low | Public pages describe payment handling, not a customer ledger or statement view. |
| Coupons | Observed | Booking flow and manager marketing pages | High | Discount coupons and custom coupon creation are public. |
| Invited friends | Inferred | Match organization | Medium | The invite-friends flow is public, but the invitee record model is not. |
| Mensalista / fixed-booking relationship | Observed | Scheduling and manager pages | High | Public docs mention `mensalistas` and fixed bookings as an operating concept. |
| Day use purchases | Observed | Day use purchase flow | High | The public day-use page describes a separate purchase path and manager notification. |

## Customer History
| History type | Status | Confidence | Notes |
|---|---|---|---|
| Booking history | Inferred | Medium | Public pages imply history matters, and the app is booking-centric, but the public site does not show the history screen. |
| Payment history | Not publicly confirmed | Low | Payments are public, but no customer payment-history view is public. |
| Cancellation history | Not publicly confirmed | Low | Cancellation penalties are public, but a per-customer cancellation timeline is not. |
| Day use purchase history | Not publicly confirmed | Low | The sale flow is public, but the buyer history view is not. |
| Chat or message history | Not publicly confirmed | Low | Chat is public, but retention and history visibility are not shown. |
| Recurring or monthly relationship | Observed | High | `Mensalistas` and fixed bookings are public scheduling concepts. |
| Tournament or lesson participation | Not publicly confirmed | Low | Tournaments and lessons appear in the plan comparison, but no customer participation history is public. |

## Relationship with Facility
- Booking relationship: observed; the facility receives, confirms, and manages bookings tied to the customer.
- Payment relationship: observed; the facility receives online payments through Agendei Pay and can also handle pay-at-facility bookings.
- Local-payment approval relationship: observed; the manager receives the request and confirms it.
- Chat relationship: observed; the public product names a messaging channel between facility and client.
- Coupon relationship: observed; players can use coupons and managers can create custom coupons.
- Recurring or monthly relationship: observed; fixed bookings and mensalistas indicate an ongoing customer relationship.

## Not a Data Model
This file is a functional reference only.
It is not a database schema and must not be used as implementation design.

## Not Publicly Observable
- Exact profile screen.
- Editable fields.
- Notes.
- Tags.
- Customer status.
- Customer blocking.
- Duplicate customer handling.
- Data retention.
- Privacy controls.
- Identity merge behavior across facilities.
