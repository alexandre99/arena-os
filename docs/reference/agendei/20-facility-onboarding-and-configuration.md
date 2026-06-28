# Facility Onboarding and Configuration

## Scope
This document covers only public onboarding and configuration behavior.
It does not describe private screens, APIs, or authenticated-only workflows beyond what is publicly visible.

## Facility Registration
- Public CTA / `cadastro da quadra`: the public site repeatedly invites the facility to `Cadastrar minha quadra`. Observed.
- Manager app access after registration: the public payment page says the facility registers on the site and receives access to `App Gestor Agendei`. Observed.
- Required facility data if public: the public pages do not list a full signup form. The payment page does say some documents from the responsible person are needed for `Agendei Pay` credentialing. Observed.
- Whether CPF/CNPJ appears publicly: yes. The public FAQ says a facility without CNPJ can use CPF during registration and that the digital account can be created as Pessoa Física or Pessoa Jurídica. Observed.
- Confidence level: High for the existence of the registration path and CPF/CNPJ support; Medium for the exact facility-data requirements because the public form is not shown.
- Unknowns: exact mandatory fields, validation rules, whether access is immediate, and whether a manual review step exists before the manager app is usable.

## Facility Visibility in App Agendei
- Relationship between `App Gestor` and `App Agendei`: the public site presents `App Gestor` as the manager surface and `App Agendei` as the player surface. Observed.
- Whether the facility appears to players after setup: yes. The public onboarding steps say the quadra must be configured in `App Gestor` to be seen in `App Agendei`. Observed.
- Whether visibility requires manager configuration: yes. The public site states the manager configures the quadra for player visibility. Observed.
- Observed: the player app lets users find courts by location and choose a day and hour from each court's full agenda.
- What is inferred: publishing likely depends on completing the public setup path and may depend on payment-account activation.
- What is unknown: exact publish toggle, review status, search ranking, and whether different visibility modes exist.

## Court Configuration
| Concept | Description | Observable or inferred | Confidence level | Notes |
|---|---|---|---|---|
| Facility / quadra esportiva | The business unit managed in the platform. | Observed | High | Public pages center the product on sports courts. |
| Multiple courts | One account can manage more than one court. | Observed | High | The public pages say courts are unlimited and can all be managed from the same app or site. |
| Schedule / agenda | The manager controls the booking calendar. | Observed | High | Public pages describe agenda control as a core function. |
| Available time slots | Players choose day and time from the court agenda. | Observed | High | The player page says each court has its complete agenda visible. |
| Fixed bookings | The facility can create recurring fixed schedules. | Observed | High | Public pages name `agendamentos fixos`. |
| Mensalistas | The facility can manage monthly recurring players. | Observed | High | Public pages use the term `mensalistas` directly. |
| Day use | The facility can create and sell daily reservations. | Observed | High | The day-use page shows manager-defined name, days, courts, duration, price, and payment method. |
| Payment method availability | The facility can offer PIX, card, or local payment. | Observed | High | Public pages describe online payment and payment at the venue. |
| Cancellation rules | The facility can define tolerance time and a percentage fee. | Observed | High | The public payment page shows this explicitly. |
| Coupons | The facility can use discounts and create custom coupons. | Observed | High | Public material mentions discounts and custom coupon creation. |
| Lessons / escolinha | Lesson and school-program management appears in the pricing page. | Observed | Medium | The workflow is not public, only the feature name is. |
| Tournaments | Tournament registration appears in the pricing page. | Observed | Medium | The participant workflow is not public, only the feature name is. |

## Agendei Pay Onboarding
- Digital account creation: the public payment page says the facility creates the digital account through `App Gestor` by completing credentialing. Observed.
- Credenciamento: the page explicitly uses credentialing as the onboarding step before activation. Observed.
- Approval timing if public: the public FAQ says approval can happen in up to 10 minutes. Observed.
- Relationship with online payment activation: after approval, the facility can activate PIX and card receipt. Observed.
- Scope note: this is the onboarding relationship only. Settlement timing, fees, and payout behavior are documented in `10-agendei-pay.md`.

## Not Publicly Observable
- Exact facility form fields.
- Exact court form fields.
- Opening-hours editor structure.
- Pricing editor structure.
- Exact cancellation-rule editor.
- Exact coupon editor structure.
- Exact day-use editor structure.
- Publishing status states.
- Approval and rejection states beyond the public wording.
- Required documents beyond the public mention of responsible-person documents.
