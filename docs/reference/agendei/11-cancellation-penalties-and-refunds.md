# Cancellation Penalties and Refunds

## Scope
This document covers only public cancellation and refund behavior in Agendei Quadras.
Observed statements come from public pages and FAQs.
Inferred statements are labeled explicitly.
Anything not confirmed publicly is listed as unknown.

## Public Cancellation Penalty Model
- Observed: the public payment page says the manager can define a cancellation rule using a tolerance window and a percentage fee.
- Observed: the published example uses a tolerance window of 8 hours before the booking time.
- Observed: the published example applies a 20% penalty.
- Observed: the published example says 80% is refunded immediately to the customer.
- Observed: the visible story is that the retained portion is handled through Agendei Pay's repass flow.
- Confidence level: High.
- Example: if a booking is cancelled within the example window, 20% is kept by the cancellation rule and 80% is returned immediately.
- Notes: the public wording is slightly ambiguous about the exact destination of the retained 20%, but the 20% / 80% split is explicit.

## Cancellation Penalty Lifecycle
1. **Observed:** A booking exists.
2. **Observed:** A cancellation occurs.
3. **Observed:** The cancellation rule is evaluated against the tolerance window and percentage.
4. **Observed:** If the cancellation is outside the tolerated window, a penalty is applied.
5. **Observed:** The customer receives the non-penalized amount back immediately in the public example.
6. **Not publicly confirmed:** The exact destination of the retained amount is not fully clear from the public wording, although the text places it in the Agendei Pay repass flow.

## Refund Behavior

### PIX refund
- Observed: the public cancellation example says 80% is refunded immediately.
- Observed: the public material does not isolate a PIX-specific refund path for cancellations.
- Confidence level: Medium.

### Card refund
- Observed: the public material does not describe card refund timing separately from the cancellation example.
- Confidence level: Low.

### Local payment refund
- Observed: the public material does not describe a local-payment refund flow.
- Confidence level: Low.

### Day use refund
- Observed: the public material does not describe a day use refund flow.
- Confidence level: Low.

## Revenue Protection
- Observed: the public marketing message frames cancellation penalties as protection against last-minute cancellations and lost revenue.
- Observed: the rule lets the facility retain part of the value when a cancellation happens outside the tolerance window.
- Observed: the customer still receives the non-penalized portion back in the published example.
- Business value: this limits revenue loss while keeping a visible refund behavior for the customer.

## Not Publicly Observable
- Who can initiate cancellation.
- Whether the manager can override the penalty.
- Exact refund timing by payment method.
- Whether no-show triggers the same rule.
- Whether reschedule avoids penalty.
- Dispute behavior.
- Partial refund behavior beyond the published example.
