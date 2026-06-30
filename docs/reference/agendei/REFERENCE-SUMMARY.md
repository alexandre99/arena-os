# Agendei Quadras Reference Summary

This document consolidates the public Agendei reference set into a single entry point. It summarizes only what is already documented across AO-REFERENCE-001 through AO-REFERENCE-009 and keeps the remaining unknowns in the open-question docs.

## 1. Executive Summary

Agendei Quadras is a sports court booking and management platform centered on two public surfaces: `App Agendei` for players and `App Gestor` for facility operators. The public reference set also documents `Agendei Pay` as the financial layer for online receipts, settlement, transfers, and cancellation handling. The product serves players, facility managers, staff, and partners who need to discover courts, reserve time, manage operations, and handle money movement.

This reference documentation exists to consolidate the public functional behavior already observed across the Agendei reference set. It collects the product scope, personas, modules, navigation, booking lifecycle, payment flow, financial capabilities, customer relationship behavior, manager operations, business rules, user journeys, conceptual domain model, and conceptual state machines into one entry point. The set is intentionally public-only and leaves unresolved behavior in the open-question docs.

## 2. Product Scope

| Area | Short description | Primary objective | Main docs |
|---|---|---|---|
| Scheduling | Court agendas, availability, one-off and fixed bookings, mensalistas, day use, and cancellation behavior. | Connect players to bookable slots and let managers control the agenda. | [05-booking-lifecycle.md](05-booking-lifecycle.md), [06-scheduling-capabilities.md](06-scheduling-capabilities.md), [07-scheduling-entities.md](07-scheduling-entities.md) |
| Billing | PIX, card, local payment, settlement, Agendei Pay, refunds, coupons, and cash flow. | Manage money movement, confirmation timing, and revenue protection. | [09-payments-overview.md](09-payments-overview.md), [10-agendei-pay.md](10-agendei-pay.md), [11-cancellation-penalties-and-refunds.md](11-cancellation-penalties-and-refunds.md), [12-financial-capabilities.md](12-financial-capabilities.md) |
| CRM | Customer relationship behavior, profile/history concepts, chat, notifications, and match organization. | Support direct communication and repeat usage around bookings. | [14-customer-relationship-overview.md](14-customer-relationship-overview.md), [15-client-profile-and-history.md](15-client-profile-and-history.md), [16-communication-and-chat.md](16-communication-and-chat.md), [17-engagement-coupons-and-match-organization.md](17-engagement-coupons-and-match-organization.md) |
| Operations | Facility onboarding, visibility, shared access, plans, staff control, and multi-court management. | Let facilities register, publish, delegate, and operate the product. | [19-manager-operations-overview.md](19-manager-operations-overview.md), [20-facility-onboarding-and-configuration.md](20-facility-onboarding-and-configuration.md), [21-shared-management-and-permissions.md](21-shared-management-and-permissions.md), [22-plans-tiers-and-feature-packaging.md](22-plans-tiers-and-feature-packaging.md) |
| Engagement | Friend invites, team sorting, coupons, lessons, tournaments, and day-use as a separate customer-facing flow. | Make bookings social and support retention-oriented usage. | [17-engagement-coupons-and-match-organization.md](17-engagement-coupons-and-match-organization.md), [33-engagement-and-crm-journeys.md](33-engagement-and-crm-journeys.md) |

## 3. Personas

**Player.** The player is the customer who discovers courts, selects slots, books, pays, buys day use, invites friends, sorts teams, and uses coupons. This is the demand-side role in the product and is documented across [01-product-overview.md](01-product-overview.md), [02-personas.md](02-personas.md), [04-navigation.md](04-navigation.md), [05-booking-lifecycle.md](05-booking-lifecycle.md), and [17-engagement-coupons-and-match-organization.md](17-engagement-coupons-and-match-organization.md).

**Facility Manager.** The manager or owner registers the facility, configures visibility, controls schedules, receives and confirms bookings, activates Agendei Pay, manages cash flow, and shares access. This is the primary operator role documented across [01-product-overview.md](01-product-overview.md), [19-manager-operations-overview.md](19-manager-operations-overview.md), [20-facility-onboarding-and-configuration.md](20-facility-onboarding-and-configuration.md), [21-shared-management-and-permissions.md](21-shared-management-and-permissions.md), and [31-manager-operations-journeys.md](31-manager-operations-journeys.md).

**Staff.** Staff are delegated employees with publicly confirmed schedule-management access under shared management. The public docs do not confirm broader staff permissions, but they do show staff as part of delegated operation. See [02-personas.md](02-personas.md), [21-shared-management-and-permissions.md](21-shared-management-and-permissions.md), and [27-operations-business-rules.md](27-operations-business-rules.md).

**Partner / co-manager.** Partners or co-managers share responsibility for the facility through shared access. The public material confirms the role exists and that access can be profile-based, but it does not expose the full permission boundary. See [02-personas.md](02-personas.md), [21-shared-management-and-permissions.md](21-shared-management-and-permissions.md), and [31-manager-operations-journeys.md](31-manager-operations-journeys.md).

## 4. Business Capabilities

| Capability | Short description | Related documentation |
|---|---|---|
| Court booking | Players select a visible court slot and create a booking. | [05-booking-lifecycle.md](05-booking-lifecycle.md), [25-booking-business-rules.md](25-booking-business-rules.md), [30-player-booking-journeys.md](30-player-booking-journeys.md) |
| Availability management | Courts expose public agendas and available slots. | [04-navigation.md](04-navigation.md), [06-scheduling-capabilities.md](06-scheduling-capabilities.md), [36-scheduling-domain-model.md](36-scheduling-domain-model.md) |
| Fixed bookings | Managers create recurring reservations that remain on the agenda. | [05-booking-lifecycle.md](05-booking-lifecycle.md), [07-scheduling-entities.md](07-scheduling-entities.md), [25-booking-business-rules.md](25-booking-business-rules.md) |
| Monthly players | Public recurring-player concept linked to fixed bookings and mensalistas. | [02-personas.md](02-personas.md), [14-customer-relationship-overview.md](14-customer-relationship-overview.md), [15-client-profile-and-history.md](15-client-profile-and-history.md) |
| Day use | Separate day-based reservation product created by the manager and bought by the player. | [03-modules.md](03-modules.md), [05-booking-lifecycle.md](05-booking-lifecycle.md), [12-financial-capabilities.md](12-financial-capabilities.md) |
| Online payment | PIX and card payment in the booking flow with immediate confirmation. | [09-payments-overview.md](09-payments-overview.md), [10-agendei-pay.md](10-agendei-pay.md), [26-payment-business-rules.md](26-payment-business-rules.md) |
| Local payment | Pay-at-facility booking branch that waits for manager acceptance. | [05-booking-lifecycle.md](05-booking-lifecycle.md), [09-payments-overview.md](09-payments-overview.md), [31-manager-operations-journeys.md](31-manager-operations-journeys.md) |
| Agendei Pay | Digital account and financial layer for receipts, settlement, transfers, and cancellation handling. | [10-agendei-pay.md](10-agendei-pay.md), [12-financial-capabilities.md](12-financial-capabilities.md), [37-billing-domain-model.md](37-billing-domain-model.md) |
| Cash flow | Manager-facing financial view of revenue, expense, profit, and cash flow. | [12-financial-capabilities.md](12-financial-capabilities.md), [19-manager-operations-overview.md](19-manager-operations-overview.md), [26-payment-business-rules.md](26-payment-business-rules.md) |
| Cancellation penalties | Late cancellations can retain part of the value according to a tolerance window and percentage. | [11-cancellation-penalties-and-refunds.md](11-cancellation-penalties-and-refunds.md), [25-booking-business-rules.md](25-booking-business-rules.md), [44-cancellation-refund-state-machine.md](44-cancellation-refund-state-machine.md) |
| Refunds | Non-penalized amount returned to the customer after cancellation. | [11-cancellation-penalties-and-refunds.md](11-cancellation-penalties-and-refunds.md), [26-payment-business-rules.md](26-payment-business-rules.md), [44-cancellation-refund-state-machine.md](44-cancellation-refund-state-machine.md) |
| Coupons | Discount instruments used in booking flows; managers can create custom coupons in the advanced tier. | [17-engagement-coupons-and-match-organization.md](17-engagement-coupons-and-match-organization.md), [22-plans-tiers-and-feature-packaging.md](22-plans-tiers-and-feature-packaging.md), [26-payment-business-rules.md](26-payment-business-rules.md) |
| Shared management | Delegated access for staff and partners, with staff schedule access publicly confirmed. | [21-shared-management-and-permissions.md](21-shared-management-and-permissions.md), [27-operations-business-rules.md](27-operations-business-rules.md), [46-operations-access-state-machine.md](46-operations-access-state-machine.md) |
| Multi-court management | One account or app manages more than one court. | [03-modules.md](03-modules.md), [19-manager-operations-overview.md](19-manager-operations-overview.md), [25-booking-business-rules.md](25-booking-business-rules.md) |
| Chat | In-app communication channel between the facility and the customer. | [16-communication-and-chat.md](16-communication-and-chat.md), [14-customer-relationship-overview.md](14-customer-relationship-overview.md), [33-engagement-and-crm-journeys.md](33-engagement-and-crm-journeys.md) |
| Engagement | Friend invitations, match organization, and team sorting around bookings. | [17-engagement-coupons-and-match-organization.md](17-engagement-coupons-and-match-organization.md), [30-player-booking-journeys.md](30-player-booking-journeys.md), [33-engagement-and-crm-journeys.md](33-engagement-and-crm-journeys.md) |

## 5. Core Business Rules

- Browsing is available before account creation, and booking is the point where identity becomes operationally relevant. [04-navigation.md](04-navigation.md), [05-booking-lifecycle.md](05-booking-lifecycle.md)
- Courts are found by location, and each court exposes its agenda and available slots. [04-navigation.md](04-navigation.md), [06-scheduling-capabilities.md](06-scheduling-capabilities.md)
- A booking is created from a selected slot on the visible agenda. [05-booking-lifecycle.md](05-booking-lifecycle.md), [25-booking-business-rules.md](25-booking-business-rules.md)
- PIX and card confirm bookings immediately after scheduling. [05-booking-lifecycle.md](05-booking-lifecycle.md), [09-payments-overview.md](09-payments-overview.md), [26-payment-business-rules.md](26-payment-business-rules.md)
- Local payment does not confirm automatically and waits for manager acceptance. [05-booking-lifecycle.md](05-booking-lifecycle.md), [09-payments-overview.md](09-payments-overview.md), [26-payment-business-rules.md](26-payment-business-rules.md)
- The manager receives the local-payment request and can accept it. [05-booking-lifecycle.md](05-booking-lifecycle.md), [16-communication-and-chat.md](16-communication-and-chat.md), [31-manager-operations-journeys.md](31-manager-operations-journeys.md)
- Managers can create one-off bookings, fixed bookings, and mensualista relationships. [05-booking-lifecycle.md](05-booking-lifecycle.md), [07-scheduling-entities.md](07-scheduling-entities.md), [25-booking-business-rules.md](25-booking-business-rules.md)
- Facilities can manage multiple courts from one account. [03-modules.md](03-modules.md), [19-manager-operations-overview.md](19-manager-operations-overview.md), [27-operations-business-rules.md](27-operations-business-rules.md)
- Day use is a separate manager-defined daily product and purchase flow. [03-modules.md](03-modules.md), [05-booking-lifecycle.md](05-booking-lifecycle.md), [25-booking-business-rules.md](25-booking-business-rules.md)
- Cancellation penalties use a tolerance window and percentage fee. [11-cancellation-penalties-and-refunds.md](11-cancellation-penalties-and-refunds.md), [25-booking-business-rules.md](25-booking-business-rules.md), [44-cancellation-refund-state-machine.md](44-cancellation-refund-state-machine.md)
- The public example uses 8 hours and 20 percent, with 80 percent refunded immediately. [11-cancellation-penalties-and-refunds.md](11-cancellation-penalties-and-refunds.md), [26-payment-business-rules.md](26-payment-business-rules.md)
- PIX funds become available 24 hours after the scheduled time, with weekend availability moving to the next business day. [09-payments-overview.md](09-payments-overview.md), [10-agendei-pay.md](10-agendei-pay.md), [26-payment-business-rules.md](26-payment-business-rules.md)
- Card funds become available 30 days after the match. [09-payments-overview.md](09-payments-overview.md), [10-agendei-pay.md](10-agendei-pay.md), [26-payment-business-rules.md](26-payment-business-rules.md)
- Transfers and repasses move available money from the digital account to bank or third-party accounts, and the facility can keep money in the account until desired. [10-agendei-pay.md](10-agendei-pay.md), [12-financial-capabilities.md](12-financial-capabilities.md), [26-payment-business-rules.md](26-payment-business-rules.md)
- Facility onboarding starts on the public site, App Gestor access follows registration, and visibility must be configured before player discovery. [19-manager-operations-overview.md](19-manager-operations-overview.md), [20-facility-onboarding-and-configuration.md](20-facility-onboarding-and-configuration.md), [27-operations-business-rules.md](27-operations-business-rules.md)
- Agendei Pay activation follows credentialing and approval before PIX and card receipts can be enabled. [10-agendei-pay.md](10-agendei-pay.md), [20-facility-onboarding-and-configuration.md](20-facility-onboarding-and-configuration.md), [27-operations-business-rules.md](27-operations-business-rules.md)
- Shared access can be created for staff and partners, and staff schedule management is publicly confirmed. [21-shared-management-and-permissions.md](21-shared-management-and-permissions.md), [27-operations-business-rules.md](27-operations-business-rules.md), [46-operations-access-state-machine.md](46-operations-access-state-machine.md)
- Operational events such as local-payment requests and day-use sales generate manager-facing notifications, and chat is the public communication channel. [16-communication-and-chat.md](16-communication-and-chat.md), [27-operations-business-rules.md](27-operations-business-rules.md)
- Plan tiers package capabilities cumulatively, and some features are explicitly marked as coming soon. [22-plans-tiers-and-feature-packaging.md](22-plans-tiers-and-feature-packaging.md), [27-operations-business-rules.md](27-operations-business-rules.md)

## 6. Primary User Journeys

- Player: Browse courts -> Choose slot -> Book -> Pay -> Play. The public flow starts in `App Agendei`, uses a visible court agenda, and branches into PIX, card, or local payment. [04-navigation.md](04-navigation.md), [05-booking-lifecycle.md](05-booking-lifecycle.md), [30-player-booking-journeys.md](30-player-booking-journeys.md)
- Manager: Register facility -> Configure courts -> Receive bookings -> Receive payments -> Operate facility. The public manager flow starts on the website, opens `App Gestor`, activates Agendei Pay, and then covers agenda control, finance, cancellations, day use, and shared access. [19-manager-operations-overview.md](19-manager-operations-overview.md), [20-facility-onboarding-and-configuration.md](20-facility-onboarding-and-configuration.md), [31-manager-operations-journeys.md](31-manager-operations-journeys.md)
- Day use: Manager defines the daily product -> Player buys it -> Manager receives a push notification. [05-booking-lifecycle.md](05-booking-lifecycle.md), [16-communication-and-chat.md](16-communication-and-chat.md), [31-manager-operations-journeys.md](31-manager-operations-journeys.md)
- Local payment: Player selects pay at facility -> Manager accepts the request -> Booking confirms. [05-booking-lifecycle.md](05-booking-lifecycle.md), [09-payments-overview.md](09-payments-overview.md), [32-payment-and-cancellation-journeys.md](32-payment-and-cancellation-journeys.md)
- Cancellation: Booking is cancelled -> The rule is evaluated -> Penalty or refund handling occurs. [11-cancellation-penalties-and-refunds.md](11-cancellation-penalties-and-refunds.md), [32-payment-and-cancellation-journeys.md](32-payment-and-cancellation-journeys.md), [44-cancellation-refund-state-machine.md](44-cancellation-refund-state-machine.md)
- Coupons and engagement: Manager creates coupons -> Player uses them during booking -> Player can also invite friends and sort teams around the booking. [17-engagement-coupons-and-match-organization.md](17-engagement-coupons-and-match-organization.md), [22-plans-tiers-and-feature-packaging.md](22-plans-tiers-and-feature-packaging.md), [33-engagement-and-crm-journeys.md](33-engagement-and-crm-journeys.md)

## 7. Conceptual Domain Overview

| Domain | Core entities | Summary | Main docs |
|---|---|---|---|
| Scheduling | Facility, Court, Agenda, Available Slot, Booking, One-off Booking, Fixed Booking, Monthly Player Relationship, Day Use Product, Cancellation. | The scheduling domain covers visible availability, court reservations, recurring reservations, and day use. | [35-domain-model-overview.md](35-domain-model-overview.md), [36-scheduling-domain-model.md](36-scheduling-domain-model.md), [42-booking-state-machine.md](42-booking-state-machine.md), [45-day-use-state-machine.md](45-day-use-state-machine.md) |
| Billing | Agendei Pay, Digital Account, Payment, PIX Payment, Card Payment, Local Payment, Repass/Transfer, Settlement, Cancellation Penalty, Refund, Coupon/Discount, Cash Flow, Charge, Material Rental Revenue. | The billing domain covers receipts, settlement, money movement, refunds, and plan-visible financial features. | [35-domain-model-overview.md](35-domain-model-overview.md), [37-billing-domain-model.md](37-billing-domain-model.md), [43-payment-state-machine.md](43-payment-state-machine.md), [44-cancellation-refund-state-machine.md](44-cancellation-refund-state-machine.md) |
| CRM | Player, Customer Profile, Customer History, Chat/Message Channel, Operational Notification, Invited Friend, Match, Team Sorting, Lesson Participation, Tournament Registration. | The CRM domain covers customer relationship behavior, communication, and match organization. | [35-domain-model-overview.md](35-domain-model-overview.md), [38-crm-engagement-domain-model.md](38-crm-engagement-domain-model.md), [16-communication-and-chat.md](16-communication-and-chat.md), [17-engagement-coupons-and-match-organization.md](17-engagement-coupons-and-match-organization.md) |
| Operations | Manager, Staff, Partner, Shared Access Profile, Staff Control, Facility Registration, Visibility/Publishing, Plan/Tier, Central de Atendimento, AI Management. | The operations domain covers onboarding, visibility, delegation, support, and plan packaging. | [35-domain-model-overview.md](35-domain-model-overview.md), [39-operations-permissions-domain-model.md](39-operations-permissions-domain-model.md), [41-state-machines-overview.md](41-state-machines-overview.md), [46-operations-access-state-machine.md](46-operations-access-state-machine.md) |

## 8. Lifecycle Overview

| Lifecycle | High-level sequence | What the docs show |
|---|---|---|
| Booking | Browsing -> Slot Selected -> Payment Method Selected -> Confirmed or Waiting for Manager Acceptance -> Cancelled | The public docs show discovery, slot selection, payment branching, confirmation, and cancellation, but not the full internal status list. |
| Payment and Settlement | Payment Method Selected -> Payment Confirmed -> Pending Settlement -> Available for Repass -> Repassed | PIX and card confirm immediately, but settlement happens later and follows different timing rules. |
| Refund | Cancellation Requested -> Rule Evaluated -> Partial Refund Issued -> Cancelled | The public example shows the retained/refunded split, while the retained amount destination remains unclear. |
| Facility and Visibility | Not Registered -> Registration Started -> Facility Registered -> App Gestor Access Granted -> Facility Configured -> Visible to Players -> Player Discovery | Public onboarding and visibility setup are documented, but the exact publish and review workflow is not. |
| Shared Access | Access Not Shared -> Access Profile Created -> Access Shared with Staff or Partner -> Staff Can Manage Schedules | Shared management exists and staff schedule access is public, but the permission matrix is not. |

## 9. Major Public Unknowns

- Booking status labels, reschedule behavior, no-show handling, and who can initiate cancellation.
- Local-payment acceptance screen, decline or expiry behavior, and the exact role of manager confirmation.
- Staff and partner permission boundaries, including whether finance or Agendei Pay controls can be shared.
- The exact meaning of `mensalista` in practice.
- The exact publish or visibility workflow that makes a court appear to players.
- The final destination of the retained cancellation amount.
- Day-use status handling, agenda blocking, consumption, and cancellation/refund behavior.
- Coupon limits, stacking, applicability to day use, and the internal invite/team-sorting mechanics.
- Whether lessons and tournaments are operational workflows or only plan-visible concepts.

## 10. Documentation Map

| Area | Main documents |
|---|---|
| Product | [01-product-overview.md](01-product-overview.md), [02-personas.md](02-personas.md), [03-modules.md](03-modules.md), [04-navigation.md](04-navigation.md) |
| Scheduling | [05-booking-lifecycle.md](05-booking-lifecycle.md), [06-scheduling-capabilities.md](06-scheduling-capabilities.md), [07-scheduling-entities.md](07-scheduling-entities.md), [08-scheduling-open-questions.md](08-scheduling-open-questions.md) |
| Billing | [09-payments-overview.md](09-payments-overview.md), [10-agendei-pay.md](10-agendei-pay.md), [11-cancellation-penalties-and-refunds.md](11-cancellation-penalties-and-refunds.md), [12-financial-capabilities.md](12-financial-capabilities.md), [13-payments-open-questions.md](13-payments-open-questions.md) |
| CRM | [14-customer-relationship-overview.md](14-customer-relationship-overview.md), [15-client-profile-and-history.md](15-client-profile-and-history.md), [16-communication-and-chat.md](16-communication-and-chat.md), [17-engagement-coupons-and-match-organization.md](17-engagement-coupons-and-match-organization.md), [18-crm-open-questions.md](18-crm-open-questions.md) |
| Operations | [19-manager-operations-overview.md](19-manager-operations-overview.md), [20-facility-onboarding-and-configuration.md](20-facility-onboarding-and-configuration.md), [21-shared-management-and-permissions.md](21-shared-management-and-permissions.md), [22-plans-tiers-and-feature-packaging.md](22-plans-tiers-and-feature-packaging.md), [23-manager-operations-open-questions.md](23-manager-operations-open-questions.md) |
| Business Rules | [24-business-rules-overview.md](24-business-rules-overview.md), [25-booking-business-rules.md](25-booking-business-rules.md), [26-payment-business-rules.md](26-payment-business-rules.md), [27-operations-business-rules.md](27-operations-business-rules.md), [28-business-rules-open-questions.md](28-business-rules-open-questions.md) |
| User Journeys | [29-user-journeys-overview.md](29-user-journeys-overview.md), [30-player-booking-journeys.md](30-player-booking-journeys.md), [31-manager-operations-journeys.md](31-manager-operations-journeys.md), [32-payment-and-cancellation-journeys.md](32-payment-and-cancellation-journeys.md), [33-engagement-and-crm-journeys.md](33-engagement-and-crm-journeys.md), [34-user-journeys-open-questions.md](34-user-journeys-open-questions.md) |
| Domain Model | [35-domain-model-overview.md](35-domain-model-overview.md), [36-scheduling-domain-model.md](36-scheduling-domain-model.md), [37-billing-domain-model.md](37-billing-domain-model.md), [38-crm-engagement-domain-model.md](38-crm-engagement-domain-model.md), [39-operations-permissions-domain-model.md](39-operations-permissions-domain-model.md), [40-domain-model-open-questions.md](40-domain-model-open-questions.md) |
| State Machines | [41-state-machines-overview.md](41-state-machines-overview.md), [42-booking-state-machine.md](42-booking-state-machine.md), [43-payment-state-machine.md](43-payment-state-machine.md), [44-cancellation-refund-state-machine.md](44-cancellation-refund-state-machine.md), [45-day-use-state-machine.md](45-day-use-state-machine.md), [46-operations-access-state-machine.md](46-operations-access-state-machine.md), [47-state-machines-open-questions.md](47-state-machines-open-questions.md) |

## 11. Recommended Reading Order

1. [REFERENCE-SUMMARY.md](REFERENCE-SUMMARY.md) - start here for the consolidated view of the reference set.
2. [24-business-rules-overview.md](24-business-rules-overview.md) - use this to understand the behavioral rules that tie the docs together.
3. [29-user-journeys-overview.md](29-user-journeys-overview.md) - read this to see the end-to-end player and manager flows.
4. [35-domain-model-overview.md](35-domain-model-overview.md) - use this to see how the conceptual entities are grouped by domain.
5. [41-state-machines-overview.md](41-state-machines-overview.md) - read this to understand the lifecycle view of bookings, payments, access, and day use.
6. Area-specific docs - read the detailed scheduling, billing, CRM, operations, journey, domain, and state-machine docs after the summaries.

This order starts with the consolidated views that reduce duplication, then moves into the detailed area docs once the product shape, behavior, and lifecycles are clear.

## 12. Key Takeaways

- Scheduling is the core product surface: players discover courts, choose slots, and managers control avulso bookings, fixed bookings, mensalistas, and day use.
- Billing is tightly coupled to scheduling: PIX and card confirm immediately, local payment waits for manager acceptance, and settlement happens later.
- Agendei Pay is the financial layer for receipts, digital accounts, transfers, repasses, cancellation handling, and the manager finance view.
- CRM is booking-centric: chat, notifications, coupons, and match organization support the booking relationship rather than a standalone CRM model.
- Operations are manager-centric: facility onboarding, player visibility, shared access, multi-court administration, and plan packaging define the public operating surface.
- The reference set presents a complete public functional summary, while the remaining unknowns are intentionally isolated in the open-question docs.
