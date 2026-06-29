# Payment Business Rules

## Scope
This document consolidates payment, Agendei Pay, settlement, repass, refund, coupon, and financial rules from the public Agendei reference docs.
It stays within the public reference set and does not define implementation detail.

## Rules

### BR-PAYMENT-001 — Agendei Pay functions as the financial layer behind online bookings
- Status: Inferred
- Confidence: Medium
- Domain area: Billing
- Trigger: Facility uses online booking payments.
- Condition: Agendei Pay is enabled for the facility.
- Outcome: The public payment layer handles receipt, settlement, and repasses for online bookings.
- Involved personas: Manager, facility, player.
- Affected concepts/entities: Agendei Pay, digital account, booking payment, repass.
- Source reference: `09-payments-overview.md`, `10-agendei-pay.md`
- Notes: The public wording is explicit about the payment layer, while the settlement-layer reading is inferred.

### BR-PAYMENT-002 — Facility creates a digital account through credentialing in App Gestor
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: Facility starts the Agendei Pay onboarding flow.
- Condition: The manager is registering the quadra through the public credentialing path.
- Outcome: A digital account is created for the facility.
- Involved personas: Manager, facility.
- Affected concepts/entities: Digital account, credentialing, App Gestor.
- Source reference: `04-navigation.md`, `10-agendei-pay.md`, `20-facility-onboarding-and-configuration.md`
- Notes: The account is created from the manager side, not from the player side.

### BR-PAYMENT-003 — Account approval can happen in up to 10 minutes
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: Facility completes the public registration and credentialing steps.
- Condition: The approval process is running normally.
- Outcome: The public material says approval can happen in up to 10 minutes.
- Involved personas: Manager, facility.
- Affected concepts/entities: Approval, onboarding, digital account.
- Source reference: `10-agendei-pay.md`, `20-facility-onboarding-and-configuration.md`
- Notes: This is the only public timing statement for onboarding approval.

### BR-PAYMENT-004 — Facilities without CNPJ can register using CPF
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: Facility registers for Agendei Pay.
- Condition: The facility does not have a CNPJ.
- Outcome: CPF can be used for registration.
- Involved personas: Manager, facility.
- Affected concepts/entities: CPF, CNPJ, person type, digital account.
- Source reference: `10-agendei-pay.md`, `20-facility-onboarding-and-configuration.md`
- Notes: The public FAQ also mentions Pessoa Fisica and Pessoa Juridica support.

### BR-PAYMENT-005 — PIX booking confirms immediately after scheduling
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: Player pays with PIX in App Agendei.
- Condition: The booking is submitted with PIX selected.
- Outcome: The booking is confirmed immediately after scheduling.
- Involved personas: Player, manager.
- Affected concepts/entities: PIX payment, booking confirmation, digital account settlement.
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `10-agendei-pay.md`
- Notes: Settlement timing is separate from confirmation timing.

### BR-PAYMENT-006 — Card booking confirms immediately after scheduling
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: Player pays with card in App Agendei.
- Condition: The booking is submitted with card selected.
- Outcome: The booking is confirmed immediately after scheduling.
- Involved personas: Player, manager.
- Affected concepts/entities: Card payment, booking confirmation, receivables.
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `10-agendei-pay.md`
- Notes: The public page says receivables can be anticipated in the future, but that is not part of the current rule.

### BR-PAYMENT-007 — Local payment does not confirm automatically
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: Player chooses pay-at-facility during booking.
- Condition: The payment is to happen in person or by machine at the venue.
- Outcome: The booking does not confirm automatically and waits for manager acceptance.
- Involved personas: Player, manager.
- Affected concepts/entities: Local payment, provisional booking, manager acceptance.
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `19-manager-operations-overview.md`
- Notes: This is the non-online confirmation branch.

### BR-PAYMENT-008 — PIX funds become available 24h after the scheduled time
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: A PIX booking reaches its scheduled time.
- Condition: The match has completed and the public settlement timing applies.
- Outcome: Funds become available in the digital account 24 hours later, or on the next business day for weekend bookings.
- Involved personas: Manager, facility.
- Affected concepts/entities: PIX settlement, digital account, business day timing.
- Source reference: `09-payments-overview.md`, `10-agendei-pay.md`, `12-financial-capabilities.md`
- Notes: The public page gives a weekend example that points to Monday after 11h.

### BR-PAYMENT-009 — Card funds become available 30 days after the match
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: A card booking reaches settlement.
- Condition: The booking was paid by card.
- Outcome: Funds become available in the digital account 30 days after the match.
- Involved personas: Manager, facility.
- Affected concepts/entities: Card settlement, digital account, receivables.
- Source reference: `09-payments-overview.md`, `10-agendei-pay.md`, `12-financial-capabilities.md`
- Notes: Public material also mentions future receivables anticipation.

### BR-PAYMENT-010 — Transfers and repasses can go to the digital account or bank accounts
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: Facility withdraws or moves collected money.
- Condition: Funds are available in the digital account.
- Outcome: The facility can transfer money to its own bank account or to third-party accounts free of charge.
- Involved personas: Manager, facility.
- Affected concepts/entities: Repass, transfer, digital account, bank account.
- Source reference: `10-agendei-pay.md`, `12-financial-capabilities.md`
- Notes: The public material also says the facility can keep money in the digital account until desired.

### BR-PAYMENT-011 — Cancellation penalties can retain a percentage and return the rest
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: A cancellation happens.
- Condition: The booking falls outside the tolerated cancellation window.
- Outcome: A percentage can be retained and the remainder returned to the customer.
- Involved personas: Player, manager.
- Affected concepts/entities: Cancellation penalty, refund, retained amount.
- Source reference: `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`
- Notes: The public cancellation rule is presented as a revenue-protection mechanism.

### BR-PAYMENT-012 — The public example uses 8h tolerance and 20% penalty
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: A booking is cancelled within the published example window.
- Condition: The example penalty rule applies.
- Outcome: 20% is retained and 80% is refunded immediately.
- Involved personas: Player, manager.
- Affected concepts/entities: Cancellation example, refund, penalty percentage.
- Source reference: `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`
- Notes: This is the only explicit public example.

### BR-PAYMENT-013 — The exact destination of the retained cancellation amount is not publicly confirmed
- Status: Not publicly confirmed
- Confidence: Low
- Domain area: Billing
- Trigger: The public cancellation example applies a penalty.
- Condition: The 20/80 split has been described, but the retained-value path is not fully spelled out.
- Outcome: The public docs do not clearly identify whether the retained portion remains with Agendei Pay, is repassed later, or is otherwise allocated.
- Involved personas: Player, manager.
- Affected concepts/entities: Cancellation penalty, repass, retained amount, refund.
- Source reference: `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`
- Notes: The split is explicit; the final destination of the retained portion is not.

### BR-PAYMENT-014 — PIX approved transactions incur a 1% + R$0,99 fee
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: PIX payment is approved.
- Condition: The transaction completes successfully.
- Outcome: The public page shows a transaction fee of 1% + R$0,99.
- Involved personas: Player, manager.
- Affected concepts/entities: PIX fee, approved transaction, payout net value.
- Source reference: `09-payments-overview.md`, `10-agendei-pay.md`
- Notes: The fee is publicly described on the payment page.

### BR-PAYMENT-015 — Players can use court discount coupons and managers can create custom coupons through plan packaging
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: Player checks out or manager reviews promotion tools.
- Condition: A court coupon exists, and the manager has access to the relevant plan packaging.
- Outcome: The player can apply a discount coupon, and the manager can create personalized coupons when the advanced tier exposes the feature.
- Involved personas: Player, manager.
- Affected concepts/entities: Coupon, booking total, plan tier, discount.
- Source reference: `06-scheduling-capabilities.md`, `12-financial-capabilities.md`, `17-engagement-coupons-and-match-organization.md`, `22-plans-tiers-and-feature-packaging.md`
- Notes: The exact redemption step and coupon builder workflow are not public.

### BR-PAYMENT-016 — Cash flow and financial management are publicly visible to managers
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: Manager opens the finance surface or plan page.
- Condition: The facility uses the public manager tools.
- Outcome: Revenue, expense, profit, and cash flow are visible.
- Involved personas: Manager.
- Affected concepts/entities: Cash flow, financial management, finance view.
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `19-manager-operations-overview.md`, `22-plans-tiers-and-feature-packaging.md`
- Notes: The public docs do not show report granularity.

### BR-PAYMENT-017 — Billing generator is announced as coming soon
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: Prospect reviews the public plan page.
- Condition: The feature card is marked Em breve.
- Outcome: The billing generator is publicly announced but not operationally detailed.
- Involved personas: Prospect, manager.
- Affected concepts/entities: Billing generator, coming soon feature, plan packaging.
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `22-plans-tiers-and-feature-packaging.md`
- Notes: The public docs do not describe the workflow.

### BR-PAYMENT-018 — Material rental is announced as coming soon
- Status: Observed
- Confidence: High
- Domain area: Billing
- Trigger: Prospect reviews the public plan page.
- Condition: The feature card is marked Em breve.
- Outcome: The material rental capability is publicly announced but not operationally detailed.
- Involved personas: Prospect, manager.
- Affected concepts/entities: Material rental, coming soon feature, plan packaging.
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `22-plans-tiers-and-feature-packaging.md`
- Notes: The public docs do not describe the workflow.

## Rule Dependencies

| Dependency | Related rule IDs | Confidence | Notes |
|---|---|---|---|
| Booking confirmation depends on the payment method chosen | `BR-PAYMENT-005`, `BR-PAYMENT-006`, `BR-PAYMENT-007`, `BR-BOOKING-005`, `BR-BOOKING-006`, `BR-BOOKING-007` | High | Instant confirmation applies to online payment; local payment waits for manager acceptance. |
| Settlement timing depends on the payment method and settlement date | `BR-PAYMENT-008`, `BR-PAYMENT-009`, `BR-PAYMENT-010` | High | PIX and card have different availability timing, and repasses move money out of the digital account. |
| Cancellation refunds depend on the penalty rule and repass flow | `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013` | High | The public example makes the refund split explicit, while the retained-amount destination is ambiguous. |
| Coupon usage depends on checkout and plan packaging | `BR-PAYMENT-015`, `BR-OPS-011`, `BR-OPS-012` | High | Players use coupons in the booking flow, while managers get creation tooling through plan visibility. |
| Financial reporting depends on Agendei Pay and settlement | `BR-PAYMENT-001`, `BR-PAYMENT-002`, `BR-PAYMENT-010`, `BR-PAYMENT-016` | Medium | The manager surface can show finance only after the account and transfer path exist. |
| Announced billing features depend on plan packaging | `BR-PAYMENT-017`, `BR-PAYMENT-018`, `BR-OPS-013`, `BR-OPS-014` | High | The public plan page advertises these as future capabilities rather than detailed workflows. |

## Unknowns
- Exact payment status names and pending-state handling.
- Whether PIX uses QR code, copy-and-paste, or both.
- Whether card support is limited to credit card or also includes debit or installments.
- Whether a booking can use more than one payment method.
- Whether weekend settlement rules apply only to PIX or also to card.
- Exact payout exceptions, manual withdrawal timing, and chargeback handling.

