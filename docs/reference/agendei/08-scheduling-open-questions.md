# Scheduling Open Questions

## Purpose
This file tracks what could not be confirmed from public sources.
It is limited to observable gaps in the public booking and scheduling material.

## Player App Questions
- How does location search work in practice: city list, map, radius, or filters?
- Can the player complete most of the booking flow before signing in, or is login required earlier than the public FAQ suggests?
- Where in the player journey are coupons entered and validated?
- Can the player see booking history or upcoming bookings from the public app surface?

## Manager App Questions
- What screen receives a local-payment booking request, and what exact action confirms it?
- How are fixed bookings created, edited, and removed?
- Can a manager see all courts in one calendar view, or only one court at a time?
- How do staff and partner permissions differ in the manager app?

## Payment and Confirmation Questions
- Does PIX always confirm instantly, or can payment recognition create a pending state?
- Is card booking confirmation immediate even though settlement is delayed?
- Does day use share the same booking-status model as hourly reservations?
- What happens if a payment is reversed after a booking has already been confirmed?

## Cancellation Questions
- Can the player cancel directly, or does the facility have to process the cancellation?
- Is the penalty applied automatically or manually?
- Are refunds immediate for every payment path, or only for some methods?
- How are no-shows treated relative to cancellations?

## Recurrence and Monthly Player Questions
- Does `mensalista` mean a monthly billing relationship, a recurring fixed slot, or both?
- Can one monthly player hold more than one fixed slot?
- Are monthly reservations tied to one court, one facility, or multiple courts?
- Can a monthly reservation coexist with one-off reservations on the same agenda?

## Permissions Questions
- What can staff edit versus only view?
- What can partners do that staff cannot?
- Are permissions scoped by facility, by court, or by feature?
- Can the owner revoke access without affecting existing bookings?

## Evidence Gaps
| Missing information | Why it matters | Suggested future source |
|---|---|---|
| Exact booking status lifecycle labels and transitions | This determines how requests, confirmations, cancellations, and refunds move through the system. | Authenticated walkthrough or product video |
| Exact local-payment approval screen and manager action sequence | This is the most important visible branch of the booking flow for pay-at-facility scenarios. | Authenticated walkthrough or demo call |
| Cancellation rule configuration, defaults, and exception handling | This defines late-fee policy, customer expectations, and refund behavior. | Public support article or authenticated walkthrough |
| No-show handling and whether it differs from cancellation | This affects revenue loss, penalties, and support handling. | User interview or demo call |
| Booking edit and reschedule flow | This determines how users change an existing booking without canceling it. | Authenticated walkthrough |
| Exact meaning of `mensalista` and recurrence mechanics | This defines the recurring-reservation model and whether it is calendar-based, billing-based, or both. | Demo call or product video |
| Staff and partner permission granularity | This affects delegation, security, and shared operations. | Authenticated walkthrough |
| Coupon application flow and constraints | This affects discount eligibility, booking totals, and redemption timing. | Public support article or authenticated walkthrough |
| How day use relates to the hourly booking model | This matters for agenda blocking, revenue recognition, and customer experience. | Product video or authenticated walkthrough |
