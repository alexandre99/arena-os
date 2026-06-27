# Financial Capabilities

## Scope
This file catalogs public financial features only.
Observed statements come from public pages and FAQs.
Inferred statements are labeled explicitly.
Anything not confirmed publicly is listed as unknown.

## Capabilities Inventory
| Capability name | Description | User/persona involved | Public evidence summary | Business value | Confidence level | Notes | Classification |
|---|---|---|---|---|---|---|---|
| Online booking payments | Player can pay for a booking during scheduling, using PIX or card. | Player, manager | App Agendei FAQ says PIX or card confirm immediately; App Gestor page says the client can pay online. | Reduces manual collection and confirms bookings. | High | Umbrella capability; PIX, card, and local payment are separate rows below. | Payment collection |
| PIX | PIX payment directly in the app. | Player | Public pages describe PIX payment in-app and 24-hour settlement after the match time. | Fast payment and fast booking confirmation. | High | The public page shows a transaction fee of 1% + R$0,99 on approved transactions. | Payment collection |
| Card | Credit card payment directly in the app. | Player | Public pages say card is supported and confirms immediately after scheduling. | Reduces friction for prepaid bookings. | High | Public timing says settlement happens 30 days after the match. | Payment collection |
| Local payment | Pay at the facility by machine or cash. | Player, manager | Public page says the player can pay in machine or cash at the facility. | Supports offline collection and manager-controlled confirmation. | High | Manager acceptance is required for confirmation. | Payment collection |
| Agendei Pay digital account | Account created through credenciamento to receive funds. | Manager, facility | Public page and FAQ describe account creation, approval in up to 10 minutes, and receipt of online payments. | Centralizes online receipts and payouts. | High | Publicly supports CPF or CNPJ registration. | Settlement / repass |
| Transfers / repasses | Free transfers from the digital account to bank or third-party accounts, or direct bank receipt. | Manager, facility | Public page says transfers are free and net values are sent automatically. | Gives the facility access to collected money. | High | PIX and card have different settlement timing. | Settlement / repass |
| Cancellation penalties | Late-cancellation fee with tolerance window and percentage. | Manager, player | Public payment page gives an 8h / 20% example. | Protects revenue from last-minute cancellations. | High | Linked to Agendei Pay. | Revenue protection |
| Refunds | Non-penalized amount returned to the customer. | Player, manager | Public cancellation example says 80% is refunded immediately. | Preserves customer trust while enforcing policy. | Medium | Method-specific timing is not public. | Revenue protection |
| Cash flow / financial management | View of revenue, expense, and profit on the facility side. | Manager | App Gestor and plan page both mention cash flow and financial management. | Helps managers track daily business performance. | High | Public page says control the cash from anywhere. | Financial management |
| Day use payments | Separate daily purchase flow for day-use reservations. | Player, manager | Day use page says the customer buys the daily reservation individually and can pay by PIX or card. | Opens a non-hourly revenue stream. | High | Manager receives push notifications for purchases. | Payment collection |
| Coupons and discounts | Players can use discount coupons and facilities can offer discounts. | Player, manager | App Gestor FAQ says players use discount coupons; App Gestor page mentions discounts. | Supports promotions and customer retention. | High | Exact redemption rules are not public. | Discount / promotion |
| Custom coupon creation | Managers can create personalized coupons. | Manager | Plan page lists `Criação de Cupons Personalizados` in the top plan tier. | Enables targeted promotions. | High | The public plan page ties it to the Avancado tier. | Discount / promotion |
| Billing generator / gerador de cobranças | Announced charge-generation feature. | Manager | Plan page marks `Gerador de Cobranças` as `Em breve`. | Suggests a future invoicing or charge workflow. | Medium | Public detail is limited to the announcement. | Future or announced capability |
| Material rental | Announced ancillary rental feature. | Manager | Plan page marks `Aluguel de materiais` as `Em breve`. | Adds possible ancillary revenue. | Medium | Public detail is limited to the announcement. | Future or announced capability |
| Plan / pricing relationship | Public plans package payment, finance, and upcoming features into tiers. | Prospect, manager | Plan page shows subscription tiers, free trial, and feature differences. | Explains what financial features are bundled commercially. | High | This is a packaging relationship, not a transaction flow. | Financial management |

## Capability Classification
Primary classifications used above:
- Payment collection: online booking payments, PIX, card, local payment, and day use payments.
- Settlement / repass: Agendei Pay digital account and transfers / repasses.
- Revenue protection: cancellation penalties and refunds.
- Financial management: cash flow / financial management and plan / pricing relationship.
- Discount / promotion: coupons and discounts, plus custom coupon creation.
- Future or announced capability: billing generator / gerador de cobranças and material rental.

## Financial Entities
| Entity name | Description | Related persona | Related capability | Observable attributes | Inferred attributes | Confidence level |
|---|---|---|---|---|---|---|
| Payment | Generic booking or day use monetary event. | Player, manager | Online booking payments, day use payments, refunds | Can be PIX, card, or local; tied to booking or day use; confirmation may depend on method. | Likely recorded as a transaction linked to a booking. | High |
| PIX payment | PIX-backed transaction. | Player, manager | PIX | In-app, confirms immediately, settles in 24 hours or next business day on weekends. | Uses the PIX rail and may be represented as a booking payment record. | High |
| Card payment | Credit card transaction. | Player, manager | Card | In-app, confirms immediately, settles after 30 days. | Likely processed through Agendei Pay and a card network, but the provider is not public. | High |
| Local payment | Pay-at-facility payment. | Player, manager | Local payment | Machine or cash at the facility; requires manager acceptance. | May not pass through the online settlement flow. | High |
| Digital account | Agendei Pay account for the facility. | Manager, facility | Agendei Pay digital account | Created via credenciamento; can use CPF or CNPJ; receives and stores funds; supports free transfers. | Functions as the settlement wallet. | High |
| Repass / transfer | Movement of net values out of the digital account. | Manager | Transfers / repasses | Free to bank or third-party accounts; automatic timing rules; bank receipt option. | Likely scheduled payout processing. | High |
| Cancellation penalty | Fee rule for late cancellations. | Manager, player | Cancellation penalties | Uses a tolerance window and percentage; public example is 8h / 20%. | May be configurable per facility. | High |
| Refund | Money returned to the customer. | Player, manager | Refunds | Public example says 80% is refunded immediately. | Method-specific timing is likely different, but not public. | Medium |
| Coupon | Discount instrument. | Manager, player | Coupons and discounts | Players can use coupons; managers can create personalized coupons. | May have rules, limits, and redemption timing. | High |
| Day use purchase | Unit purchase of a daily reservation. | Player, manager | Day use payments | Manager defines name, days, courts, duration, value, and payment method; buyer purchases individually; push notification on sale. | Behaves like a ticket or entry pass. | High |
| Charge / cobrança | Publicly announced charge-generation artifact. | Manager | Billing generator / gerador de cobranças | Plan page marks it as coming soon. | May be an invoice or bill-generation object. | Medium |
| Cash flow entry | Revenue, expense, or profit record in financial views. | Manager | Cash flow / financial management | Public pages mention receipts, expenses, profit, and cash flow. | Likely aggregates booking payments and payouts. | High |

## Not a Data Model
This file is a functional reference only.
It is not a database schema and must not be used as implementation design.

## Not Publicly Observable
- Exact payment status names.
- Exact failed payment behavior.
- Exact chargeback behavior.
- Exact card installment behavior.
- Exact payout configuration.
- Exact reconciliation screens.
- Exact coupon validation rules.
- Exact billing-generator workflow beyond the public announcement.
- Exact material-rental workflow beyond the public announcement.
