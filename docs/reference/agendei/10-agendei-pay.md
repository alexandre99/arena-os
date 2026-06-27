# Agendei Pay

## Scope
This document covers only publicly described Agendei Pay behavior.
Observed statements come from public pages and FAQs.
Inferred statements are labeled explicitly.
Anything not confirmed publicly is listed as unknown.

## Product Purpose
- Observed: Agendei Pay is presented as the financial layer for a sports facility.
- Observed: the public page says it lets the facility receive online booking payments by PIX and card, move funds, and handle cancellation penalties.
- Observed: the public pitch is that the facility can receive money without needing a traditional bank setup as the only path.
- Inferred (Medium): Agendei Pay acts as the settlement and payout layer behind online bookings.

## Digital Account
- Observed: the facility creates the digital account through `App Gestor` by going through a public credenciamento flow.
- Observed: the public page says some documents from the responsible person are required to finish the registration.
- Observed: the public FAQ says account approval can happen in up to 10 minutes.
- Observed: the public FAQ says a facility without a CNPJ can use CPF during registration.
- Observed: the digital account belongs to the quadra/facility and is used to receive money from online bookings.
- Observed: the public page says the facility can keep money in the digital account, withdraw when desired, or transfer funds out.
- Observed: the public page says the facility can receive payments directly in a bank account as an alternative.
- Observed: the relationship with repasses is explicit: when the customer pays through the app, Agendei Pay sends the net values to the facility's digital account or bank account.

## PIX
- Observed: players pay PIX directly in `App Agendei` during the booking flow.
- Observed: the booking is confirmed immediately after scheduling when PIX is chosen.
- Observed: the public payment page says PIX amounts become available in the digital account 24 hours after the scheduled time.
- Observed: for weekend bookings, the same public page says availability moves to the next business day, with an example that points to Monday after 11h.
- Observed: the public page also shows a transaction fee of 1% + R$0,99 on approved PIX transactions.
- Confidence level: High.
- Unknowns: the exact QR-code or copy-paste experience, payment failure handling, and any pending-state behavior are not public.

## Card
- Observed: players pay by credit card directly in `App Agendei` during the booking flow.
- Observed: the booking is confirmed immediately after scheduling when card payment is chosen.
- Observed: the public payment page says card values become available in the digital account 30 days after the match.
- Observed: the same page mentions anticipation of receivables as a future possibility.
- Confidence level: High.
- Unknowns: card brand support, installment behavior, authorization capture details, and chargeback handling are not public.

## Transfers and Repasses
- Observed: the public page says the facility can transfer money from the digital account to its own bank account or to third-party accounts free of charge.
- Observed: the public page also says the facility can choose to receive values directly in a bank account.
- Observed: net repasses are automatic when the receipt date is reached.
- Observed: PIX and card have different timing rules, with PIX reaching availability much sooner than card.
- Observed: the public material shows a weekend-specific timing rule for PIX.
- Confidence level: High.
- Unknowns: the provider behind the digital account, manual withdrawal flow, payout exceptions, and ledger details are not public.

## Agendei Pay and Cancellation Penalties
- Observed: Agendei Pay is the public surface used to explain cancellation penalties.
- Observed: the public example says cancellations after 8 hours before the booking time incur a 20% fee.
- Observed: the same example says 80% is refunded immediately.
- Observed: the visible story is that Agendei Pay handles the money split around the cancellation event.
- For the full cancellation and refund behavior, see `11-cancellation-penalties-and-refunds.md`.

## Not Publicly Observable
- Account provider or payment institution.
- KYC rules beyond the public mention of documents.
- Fee structure beyond the public PIX transaction example.
- Failed payout handling.
- Manual withdrawal flow.
- Exact ledger behavior.
- Exact exception handling for disputed or reversed payments.
