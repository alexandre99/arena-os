# Billing Domain Model

## Scope
This file consolidates the conceptual billing and payment entities visible in the public Agendei reference docs, the consolidated business rules, and the user journeys.
It stays at the product-concept level only.
It is not a database schema, not an architecture model, and not an Arena OS document.

## Entities

### E-BILL-001 — Agendei Pay

- Status: Observed
- Confidence: High
- Domain areas: Billing, Operations
- Description: The financial layer used to receive online booking payments, handle settlement, and support transfers and cancellation handling.
- Primary responsibilities: Receive PIX and card payments, manage the digital account, support repasses, and handle cancellation-value movement.
- Related personas: Manager / Facility Owner, Player / Client / User, Facility / Quadra Esportiva.
- Related business rules: BR-PAYMENT-001, BR-PAYMENT-002, BR-PAYMENT-003, BR-PAYMENT-008, BR-PAYMENT-009, BR-PAYMENT-010, BR-PAYMENT-011, BR-PAYMENT-012, BR-PAYMENT-013, BR-PAYMENT-014, BR-OPS-004.
- Related journeys: J-MANAGER-006, J-PAYMENT-001, J-PAYMENT-002, J-PAYMENT-004, J-PAYMENT-005, J-MANAGER-008.
- Relationships: Hosts the digital account; receives settled money; supports repasses and cancellation-value handling.
- Observable attributes/concepts: PIX receipts, card receipts, transfers, cancellation-fee explanation, digital account.
- Inferred attributes/concepts: Settlement layer, payout layer, financial ledger behavior.
- Public unknowns: Provider identity, exact payout exceptions, exact dispute handling, and ledger detail.
- Source reference: `09-payments-overview.md`, `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`, `12-financial-capabilities.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public wording makes the settlement-layer reading plausible, but the internal mechanics are not public.

### E-BILL-002 — Digital Account

- Status: Observed
- Confidence: High
- Domain areas: Billing, Operations
- Description: The facility account created through Agendei Pay credentialing to receive and hold money.
- Primary responsibilities: Receive settled funds, store money until transfer, and support payout destinations.
- Related personas: Manager / Facility Owner, Facility / Quadra Esportiva.
- Related business rules: BR-PAYMENT-002, BR-PAYMENT-003, BR-PAYMENT-004, BR-PAYMENT-008, BR-PAYMENT-009, BR-PAYMENT-010, BR-OPS-004.
- Related journeys: J-MANAGER-006, J-PAYMENT-001, J-PAYMENT-002, J-PAYMENT-005.
- Relationships: Receives funds after settlement; can send money to a bank account or keep it available in the account.
- Observable attributes/concepts: CPF or CNPJ registration, approval timing, free transfers, bank-account transfer option.
- Inferred attributes/concepts: Settlement wallet, account balance, available funds.
- Public unknowns: Exact provider behind the account, manual withdrawal flow, and payout exception handling.
- Source reference: `10-agendei-pay.md`, `12-financial-capabilities.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`
- Notes: Public pages say a facility can keep money in the account until desired.

### E-BILL-003 — Payment

- Status: Observed
- Confidence: High
- Domain areas: Billing, Scheduling
- Description: The money movement attached to a booking or day use sale.
- Primary responsibilities: Carry the payment method, determine booking confirmation behavior, and connect to settlement and refund handling.
- Related personas: Player / Client / User, Manager / Facility Owner.
- Related business rules: BR-BOOKING-005, BR-BOOKING-006, BR-BOOKING-007, BR-PAYMENT-005, BR-PAYMENT-006, BR-PAYMENT-007, BR-PAYMENT-008, BR-PAYMENT-009, BR-PAYMENT-010, BR-PAYMENT-011, BR-PAYMENT-012, BR-PAYMENT-013, BR-PAYMENT-014, BR-PAYMENT-015.
- Related journeys: J-PLAYER-002, J-PLAYER-003, J-PLAYER-004, J-PLAYER-005, J-PAYMENT-001, J-PAYMENT-002, J-PAYMENT-003, J-PAYMENT-004, J-PAYMENT-005.
- Relationships: Uses a payment method; may confirm a booking immediately or wait for manager acceptance; later moves into settlement.
- Observable attributes/concepts: PIX, card, local payment, settlement timing, fees.
- Inferred attributes/concepts: Transaction status, payout linkage, reversal behavior.
- Public unknowns: Exact payment status names, card brand support, installment support, and combined-method behavior.
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`, `12-financial-capabilities.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `29-user-journeys-overview.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public docs separate confirmation timing from later settlement timing.

### E-BILL-004 — PIX Payment

- Status: Observed
- Confidence: High
- Domain areas: Billing
- Description: The in-app PIX transaction used during booking.
- Primary responsibilities: Confirm the booking immediately and settle funds later according to the public timing rule.
- Related personas: Player / Client / User, Manager / Facility Owner.
- Related business rules: BR-PAYMENT-005, BR-PAYMENT-008, BR-PAYMENT-014.
- Related journeys: J-PLAYER-002, J-PAYMENT-001.
- Relationships: Confirms the booking immediately; settles into the digital account after the scheduled time.
- Observable attributes/concepts: Immediate confirmation, 24-hour availability timing, weekend timing shift, approved-transaction fee.
- Inferred attributes/concepts: Settlement rail, receipt ledger.
- Public unknowns: Whether PIX uses QR code, copy-and-paste, or both; failure and pending-state handling.
- Source reference: `09-payments-overview.md`, `10-agendei-pay.md`, `12-financial-capabilities.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public example also shows a 1% + R$0,99 fee on approved PIX transactions.

### E-BILL-005 — Card Payment

- Status: Observed
- Confidence: High
- Domain areas: Billing
- Description: The in-app card transaction used during booking.
- Primary responsibilities: Confirm the booking immediately and settle the receivable later.
- Related personas: Player / Client / User, Manager / Facility Owner.
- Related business rules: BR-PAYMENT-006, BR-PAYMENT-009.
- Related journeys: J-PLAYER-003, J-PAYMENT-002.
- Relationships: Confirms the booking immediately; settles after the public 30-day timing rule.
- Observable attributes/concepts: Immediate confirmation, 30-day receivable timing.
- Inferred attributes/concepts: Authorization, capture, and receivable anticipation.
- Public unknowns: Card brand support, installment behavior, authorization/capture detail, and chargeback handling.
- Source reference: `09-payments-overview.md`, `10-agendei-pay.md`, `12-financial-capabilities.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public docs mention future receivables anticipation, but not the current operational detail.

### E-BILL-006 — Local Payment

- Status: Observed
- Confidence: High
- Domain areas: Billing, Scheduling
- Description: The pay-at-facility option where the customer pays in person by cash or machine.
- Primary responsibilities: Keep the booking pending until the manager accepts the request.
- Related personas: Player / Client / User, Manager / Facility Owner.
- Related business rules: BR-BOOKING-006, BR-BOOKING-007, BR-PAYMENT-007.
- Related journeys: J-PLAYER-004, J-MANAGER-004, J-PAYMENT-003.
- Relationships: Waits for manager acceptance before confirmation; may be paid locally at the venue.
- Observable attributes/concepts: Pay-at-facility branch, manager approval, in-person collection.
- Inferred attributes/concepts: Local payment can be cash, machine, or both depending on the facility.
- Public unknowns: Exact local-payment options in every facility, exact pending states, and post-collection settlement behavior.
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public docs separate this branch from app-based confirmation.

### E-BILL-007 — Repass / Transfer

- Status: Observed
- Confidence: High
- Domain areas: Billing, Operations
- Description: The movement of money out of the digital account to a bank account or another account.
- Primary responsibilities: Send settled funds to the facility or another destination after availability.
- Related personas: Manager / Facility Owner, Facility / Quadra Esportiva.
- Related business rules: BR-PAYMENT-010, BR-PAYMENT-001, BR-OPS-004.
- Related journeys: J-PAYMENT-005, J-MANAGER-008.
- Relationships: Follows settlement; can send money to the facility's bank account or a third-party account.
- Observable attributes/concepts: Free transfer description, bank-account destination, third-party destination.
- Inferred attributes/concepts: Payout schedule, transfer ledger, destination validation.
- Public unknowns: Manual withdrawal timing, transfer exceptions, and third-party destination constraints.
- Source reference: `10-agendei-pay.md`, `12-financial-capabilities.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public pages also say the facility can leave money in the digital account.

### E-BILL-008 — Settlement / Availability

- Status: Observed
- Confidence: High
- Domain areas: Billing
- Description: The point at which received money becomes available in the digital account.
- Primary responsibilities: Define when PIX or card funds are available for repass or retention.
- Related personas: Manager / Facility Owner, Facility / Quadra Esportiva.
- Related business rules: BR-PAYMENT-008, BR-PAYMENT-009, BR-PAYMENT-010.
- Related journeys: J-PAYMENT-001, J-PAYMENT-002, J-PAYMENT-005.
- Relationships: Is enabled by payment timing; enables repasses after funds become available.
- Observable attributes/concepts: 24-hour PIX timing, 30-day card timing, weekend shift for PIX.
- Inferred attributes/concepts: Availability ledger, business-day handling.
- Public unknowns: Whether weekend timing applies to card as well as PIX.
- Source reference: `09-payments-overview.md`, `10-agendei-pay.md`, `12-financial-capabilities.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: Settlement timing is separate from booking confirmation timing.

### E-BILL-009 — Cancellation Penalty

- Status: Observed
- Confidence: High
- Domain areas: Billing, Scheduling
- Description: The retained-value mechanism that applies when a cancellation happens outside the tolerated window.
- Primary responsibilities: Retain part of the booking value and leave the rest for refund handling.
- Related personas: Player / Client / User, Manager / Facility Owner.
- Related business rules: BR-BOOKING-015, BR-BOOKING-016, BR-PAYMENT-011, BR-PAYMENT-012, BR-PAYMENT-013, BR-PAYMENT-014.
- Related journeys: J-PAYMENT-004.
- Relationships: May retain part of a payment; is evaluated together with the cancellation rule.
- Observable attributes/concepts: Tolerance window, percentage fee, 8h / 20% public example.
- Inferred attributes/concepts: Retained-amount destination, rounding, automation timing.
- Public unknowns: Exact destination of the retained amount and whether the rule is automatic or manual.
- Source reference: `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public wording clearly shows the split, but not every downstream allocation step.

### E-BILL-010 — Refund

- Status: Observed
- Confidence: High
- Domain areas: Billing, Scheduling
- Description: The non-penalized amount returned to the customer after a cancellation.
- Primary responsibilities: Return the part of the payment that is not kept by the cancellation penalty.
- Related personas: Player / Client / User, Manager / Facility Owner.
- Related business rules: BR-BOOKING-015, BR-BOOKING-016, BR-PAYMENT-011, BR-PAYMENT-012, BR-PAYMENT-013.
- Related journeys: J-PAYMENT-004.
- Relationships: Returns the non-penalized amount to the customer after cancellation.
- Observable attributes/concepts: Immediate refund in the public example, 80% public split.
- Inferred attributes/concepts: Method-specific refund timing.
- Public unknowns: Exact refund timing by payment method.
- Source reference: `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public example says the refund happens immediately in the illustrated case.

### E-BILL-011 — Coupon / Discount

- Status: Observed
- Confidence: High
- Domain areas: Billing, CRM
- Description: A discount instrument that can reduce the booking total in the booking context.
- Primary responsibilities: Apply a discount when a valid coupon is used and support promotional behavior.
- Related personas: Player / Client / User, Manager / Facility Owner.
- Related business rules: BR-PAYMENT-015, BR-OPS-011, BR-OPS-012.
- Related journeys: J-PLAYER-006, J-CRM-004.
- Relationships: Applies a discount in the booking context; can be created by managers when the plan exposes the feature.
- Observable attributes/concepts: Discount coupons, custom coupons, booking-context use.
- Inferred attributes/concepts: Validity windows, limits, targeting, stacking.
- Public unknowns: Exact coupon entry point, limit rules, and whether coupons apply to day use.
- Source reference: `06-scheduling-capabilities.md`, `12-financial-capabilities.md`, `17-engagement-coupons-and-match-organization.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public docs confirm coupon use and custom coupon creation, but not the full redemption workflow.

### E-BILL-012 — Cash Flow / Financial Management

- Status: Observed
- Confidence: High
- Domain areas: Billing, Operations
- Description: The manager-facing view of revenue, expense, profit, and cash flow.
- Primary responsibilities: Summarize financial behavior and help the facility track its business position.
- Related personas: Manager / Facility Owner.
- Related business rules: BR-PAYMENT-016, BR-OPS-005, BR-PAYMENT-001.
- Related journeys: J-MANAGER-008, J-PAYMENT-006.
- Relationships: Summarizes payments, settlements, and transfers at the facility level.
- Observable attributes/concepts: Revenue, expense, profit, cash flow, finance view.
- Inferred attributes/concepts: Report granularity, reconciliation detail, manual entry behavior.
- Public unknowns: Exact report structure and reconciliation screens.
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `19-manager-operations-overview.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: Public docs frame finance as a core manager capability.

### E-BILL-013 — Charge / Cobrança

- Status: Observed
- Confidence: Medium
- Domain areas: Billing, Operations
- Description: The publicly announced charge-generation capability shown on the plan page.
- Primary responsibilities: Announce a future charge or billing workflow; the public material does not describe the operational steps.
- Related personas: Prospect, Manager / Facility Owner.
- Related business rules: BR-PAYMENT-017, BR-OPS-013.
- Related journeys: J-MANAGER-008.
- Relationships: Is announced as a coming-soon capability on the plan page.
- Observable attributes/concepts: `Gerador de Cobranças`, coming soon label.
- Inferred attributes/concepts: Charge workflow, invoice-like behavior.
- Public unknowns: Whether it is invoicing, billing, or another collections artifact.
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`
- Notes: Public detail is limited to the announcement.

### E-BILL-014 — Material Rental Revenue

- Status: Observed
- Confidence: Medium
- Domain areas: Billing, Operations
- Description: The publicly announced ancillary-revenue concept for renting materials.
- Primary responsibilities: Represent a future revenue category; the public material does not describe the workflow.
- Related personas: Prospect, Manager / Facility Owner.
- Related business rules: BR-PAYMENT-018, BR-OPS-013.
- Related journeys: J-MANAGER-008.
- Relationships: Is announced as a coming-soon capability on the plan page.
- Observable attributes/concepts: `Aluguel de materiais`, coming soon label.
- Inferred attributes/concepts: Inventory-linked rental workflow, ancillary sale.
- Public unknowns: Exact rental workflow, item categories, and whether this is active or only announced.
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`
- Notes: Public detail is limited to the announcement.

## Relationships

### Booking uses payment method

- Relationship: A booking uses a payment method.
- Status: Observed
- Confidence: High
- Source entity: Booking / Agendamento
- Target entity: Payment
- Business meaning: The payment choice is part of the booking flow and determines the confirmation path.
- Related rules: BR-BOOKING-005, BR-BOOKING-006, BR-BOOKING-007, BR-PAYMENT-005, BR-PAYMENT-006, BR-PAYMENT-007
- Related journeys: J-PLAYER-002, J-PLAYER-003, J-PLAYER-004, J-PAYMENT-003
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`, `30-player-booking-journeys.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public docs separate online payment from pay-at-facility behavior.

### PIX confirms booking immediately

- Relationship: PIX payment confirms the booking immediately.
- Status: Observed
- Confidence: High
- Source entity: PIX Payment
- Target entity: Booking / Agendamento
- Business meaning: The player gets an immediate confirmation when PIX is chosen during booking.
- Related rules: BR-PAYMENT-005, BR-BOOKING-005
- Related journeys: J-PLAYER-002, J-PAYMENT-001
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `10-agendei-pay.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: Settlement happens later, but confirmation is immediate.

### Card confirms booking immediately

- Relationship: Card payment confirms the booking immediately.
- Status: Observed
- Confidence: High
- Source entity: Card Payment
- Target entity: Booking / Agendamento
- Business meaning: The player gets an immediate confirmation when card payment is chosen during booking.
- Related rules: BR-PAYMENT-006, BR-BOOKING-005
- Related journeys: J-PLAYER-003, J-PAYMENT-002
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `10-agendei-pay.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The receivable settles later than the booking confirmation.

### Local payment waits for manager acceptance

- Relationship: Local payment waits for manager acceptance.
- Status: Observed
- Confidence: High
- Source entity: Local Payment
- Target entity: Booking / Agendamento
- Business meaning: Pay-at-facility requests remain pending until the manager accepts them.
- Related rules: BR-PAYMENT-007, BR-BOOKING-006, BR-BOOKING-007
- Related journeys: J-PLAYER-004, J-MANAGER-004, J-PAYMENT-003
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `19-manager-operations-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`, `31-manager-operations-journeys.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public docs do not show the exact approval screen.

### Payment settles after public timing rules

- Relationship: A payment settles after the public timing rules.
- Status: Observed
- Confidence: High
- Source entity: Payment
- Target entity: Settlement / Availability
- Business meaning: The payment becomes available later than the booking confirmation, according to the public timing rules.
- Related rules: BR-PAYMENT-008, BR-PAYMENT-009, BR-PAYMENT-010
- Related journeys: J-PAYMENT-001, J-PAYMENT-002, J-PAYMENT-005
- Source reference: `09-payments-overview.md`, `10-agendei-pay.md`, `12-financial-capabilities.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: PIX and card have different availability timing.

### Settlement enables repass

- Relationship: Settlement enables repass.
- Status: Observed
- Confidence: High
- Source entity: Settlement / Availability
- Target entity: Repass / Transfer
- Business meaning: Money can be transferred only after it has become available in the digital account.
- Related rules: BR-PAYMENT-010, BR-OPS-004
- Related journeys: J-PAYMENT-005, J-MANAGER-008
- Source reference: `10-agendei-pay.md`, `12-financial-capabilities.md`, `19-manager-operations-overview.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public docs describe free transfers after settlement.

### Repass sends money to digital account or bank account

- Relationship: Repass sends money to a digital account or bank account.
- Status: Observed
- Confidence: High
- Source entity: Repass / Transfer
- Target entity: Digital Account
- Business meaning: The facility can move money to its own bank account or keep it in the digital account until desired.
- Related rules: BR-PAYMENT-010, BR-OPS-004
- Related journeys: J-PAYMENT-005, J-MANAGER-008
- Source reference: `10-agendei-pay.md`, `12-financial-capabilities.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public text also mentions third-party accounts.

### Cancellation penalty may retain part of payment

- Relationship: A cancellation penalty may retain part of a payment.
- Status: Observed
- Confidence: High
- Source entity: Cancellation Penalty
- Target entity: Payment
- Business meaning: Late cancellation can keep a percentage of the paid value instead of refunding it all.
- Related rules: BR-BOOKING-015, BR-BOOKING-016, BR-PAYMENT-011, BR-PAYMENT-012, BR-PAYMENT-013, BR-PAYMENT-014
- Related journeys: J-PAYMENT-004
- Source reference: `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public example uses a 20% retention and 80% refund.

### Refund returns non-penalized amount to customer

- Relationship: A refund returns the non-penalized amount to the customer.
- Status: Observed
- Confidence: High
- Source entity: Refund
- Target entity: Player / Client / User
- Business meaning: The customer receives back the part of the value that is not kept by the cancellation penalty.
- Related rules: BR-BOOKING-015, BR-BOOKING-016, BR-PAYMENT-011, BR-PAYMENT-012, BR-PAYMENT-013
- Related journeys: J-PAYMENT-004
- Source reference: `10-agendei-pay.md`, `11-cancellation-penalties-and-refunds.md`, `26-payment-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public example says the refund happens immediately in the illustrated case.

### Coupon applies discount in booking context

- Relationship: A coupon applies a discount in the booking context.
- Status: Observed
- Confidence: High
- Source entity: Coupon / Discount
- Target entity: Booking / Agendamento
- Business meaning: A valid coupon reduces the booking total during checkout.
- Related rules: BR-PAYMENT-015, BR-OPS-011, BR-OPS-012
- Related journeys: J-PLAYER-006, J-CRM-004
- Source reference: `06-scheduling-capabilities.md`, `12-financial-capabilities.md`, `17-engagement-coupons-and-match-organization.md`, `22-plans-tiers-and-feature-packaging.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`, `33-engagement-and-crm-journeys.md`
- Notes: The exact redemption point is not public.

### Cash flow summarizes financial behavior

- Relationship: Cash flow summarizes financial behavior.
- Status: Observed
- Confidence: High
- Source entity: Cash Flow / Financial Management
- Target entity: Payment
- Business meaning: The financial view summarizes the payments, settlements, expenses, and transfers that make up the facility's money movement.
- Related rules: BR-PAYMENT-016, BR-OPS-005, BR-PAYMENT-001
- Related journeys: J-MANAGER-008, J-PAYMENT-006
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `19-manager-operations-overview.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`, `32-payment-and-cancellation-journeys.md`
- Notes: The public docs do not expose the report breakdown.

### Charge generator is announced but not detailed

- Relationship: The plan tier announces a charge generator.
- Status: Observed
- Confidence: Medium
- Source entity: Plan / Tier
- Target entity: Charge / Cobrança
- Business meaning: The public pricing page surfaces charge generation as a coming-soon capability without workflow detail.
- Related rules: BR-PAYMENT-017, BR-OPS-013
- Related journeys: J-MANAGER-008
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `22-plans-tiers-and-feature-packaging.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`
- Notes: The public docs do not confirm operational availability.

### Material rental is announced but not detailed

- Relationship: The plan tier announces material rental.
- Status: Observed
- Confidence: Medium
- Source entity: Plan / Tier
- Target entity: Material Rental Revenue
- Business meaning: The public pricing page surfaces material rental as a coming-soon ancillary-revenue capability without workflow detail.
- Related rules: BR-PAYMENT-018, BR-OPS-013
- Related journeys: J-MANAGER-008
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `22-plans-tiers-and-feature-packaging.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`
- Notes: The public docs do not confirm operational availability.

## Unknowns

- Exact payment status names.
- Exact payment failure and pending-state behavior.
- Whether PIX uses QR code, copy-and-paste, or both.
- Whether card support includes debit or installments.
- Whether one booking can use more than one payment method.
- Whether weekend settlement rules apply only to PIX or also to card.
- Exact payout exceptions and manual withdrawal timing.
- Exact destination of retained cancellation amounts.
- Exact chargeback and dispute handling.
- Exact coupon limits, stacking, and day-use applicability.
- Exact reporting detail in the financial view.
- Exact charge-generator workflow behind the coming-soon label.
- Exact material-rental workflow behind the coming-soon label.

