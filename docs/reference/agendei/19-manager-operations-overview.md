# Manager Operations Overview

## Scope
This document covers only public and observable manager/facility behavior in Agendei Quadras.
Anything inside authenticated screens, private APIs, or unlisted workflows is out of scope.

## Manager Operation Surfaces
- `App Gestor Agendei` - public manager surface for schedule control, bookings, finance, cancellations, day use, chat, shared access, and multi-court administration. Observed.
- Public registration / `cadastro da quadra` - public entry point for facility signup. Observed.
- `Agendei Pay` onboarding - public credenciamento and account-activation flow for online payment receipt. Observed.
- Plan / pricing page - public tier packaging and feature comparison. Observed.
- Day use manager flow - public daily-pass creation and sales flow. Observed.
- Shared management - public access-sharing flow for staff and partners. Observed.
- Staff access - public mention that employees can also access the app to manage schedules. Observed.
- Multi-court management - public claim that all courts can be managed from one account or app. Observed.

## Manager Responsibilities
| Responsibility | Description | Related public source/surface | Confidence level | Notes |
|---|---|---|---|---|
| Register facility | Start the facility onboarding flow from the public site. | Public `Cadastrar minha quadra` CTA; `Pagamento Online` page | High | The public site says the manager registers the quadra by site and receives access to `App Gestor`. |
| Configure facility visibility | Set up the quadra so it appears in `App Agendei`. | `Pagamento Online` page; `App Agendei` page | High | The public onboarding steps explicitly connect manager setup to player visibility. The exact publish control is not public. |
| Manage schedules | Create and manage the agenda for the facility. | `App Gestor Agendei` page; pricing page | High | Public material repeatedly frames agenda control as a core manager task. |
| Manage one-off bookings | Handle avulso bookings. | `App Gestor Agendei` page; pricing page | High | The public site names `agendamentos avulsos` directly. |
| Manage fixed bookings | Handle fixed recurring bookings. | `App Gestor Agendei` page; pricing page | High | Public material names `agendamentos fixos` directly. |
| Manage monthly players / mensalistas | Handle recurring monthly customer relationships. | `App Gestor Agendei` page; pricing page | High | The public site uses the term `mensalistas`. |
| Manage multiple courts | Administer all courts from one account or app. | `App Gestor Agendei` page; pricing page; FAQ | High | Public pages say the manager can handle 1 or 100 courts. |
| Receive and approve local-payment booking requests | Receive booking requests that will be paid at the venue and confirm them manually. | `App Gestor Agendei` FAQ; booking lifecycle docs | High | The public model distinguishes local payment from app payment; local payment waits for manager acceptance. |
| Activate online payments | Create Agendei Pay and enable PIX/card receipts. | `Pagamento Online` page | High | The public onboarding flow places activation after credentialing and approval. |
| Manage cancellation penalties | Define cancellation tolerance and fee rules. | `Pagamento Online` page | High | The public page shows penalty handling as a manager capability. |
| Manage day use | Create and sell daily reservations. | `Diária (Day Use)` page; `App Gestor Agendei` page | High | Public pages show the manager creating daily products and receiving purchase notifications. |
| Manage finance / cash flow | Track revenue, expenses, profit, and cash flow. | `App Gestor Agendei` page; pricing page; day use page | High | The public site presents finance as a core operational area. |
| Use chat / messages | Communicate with clients inside the platform. | `App Gestor Agendei` page; pricing page | High | The public site describes a single communication channel. |
| Create custom coupons if public | Create personalized coupons for promotions. | Pricing page | High | The public plan page lists custom coupon creation in the advanced tier. |
| Share access with staff or partners | Create different access profiles for employees and partners. | `App Gestor Agendei` page; pricing page; FAQ | High | Public pages explicitly mention shared management with employees and partners. |
| Manage lessons / escolinha if public | Manage lesson and school-program workflows. | Pricing page | Medium | The feature is public, but the actual workflow is not visible. |
| Manage tournament registration if public | Manage tournament sign-up workflows. | Pricing page | Medium | The feature is public, but the actual workflow is not visible. |

## Operational Lifecycle
1. Facility discovers `App Gestor`. Observed. The public site presents the manager app as the facility surface and points to `Cadastrar minha quadra`.
2. Facility registers through the public site. Observed. The `Pagamento Online` page says the quadra is registered on the site.
3. Facility receives access to `App Gestor`. Observed. The public onboarding flow says registration leads to manager access.
4. Facility configures the quadra for visibility in `App Agendei`. Observed. The public onboarding flow states this directly.
5. Facility manages schedules, bookings, monthly players, and multiple courts. Observed. These are named manager functions on public pages.
6. Facility creates `Agendei Pay` through credenciamento and activates PIX/card after approval. Observed. The public payment page describes this sequence.
7. Facility shares access with staff or partners. Observed. The public site describes different access profiles and shared management.
8. Facility manages revenue, cancellations, day use, chat, and promotions. Observed. These surfaces are publicly listed as manager capabilities.

## Not Publicly Observable
- Exact internal dashboard layout.
- Exact configuration screens and field names.
- Exact role model and permission inheritance rules.
- Exact audit logs or activity history.
- Exact facility approval process beyond public onboarding wording.
- Exact court publishing workflow and search-ranking logic.
- Exact state transitions for requests, approvals, and declines.
