# AO-ARENA-002 Product Modules

## 1. Purpose

Arena OS is divided into modules so each major business responsibility has one owner, the product stays understandable, and future expansion does not blur setup, bookings, money, customer context, communication, and external connections into one undifferentiated surface. This document is an ownership map, not a feature inventory.

Modularity matters because it keeps accountability clear, protects product simplicity, and makes it easier to expand only where the business has proven need. This official map intentionally simplifies the exploratory list: Administration is part of Operations, while Notifications and Reporting are shared capabilities rather than standalone modules.

Before any future capability is promoted into a new module, it must be evaluated through the Keep, Simplify, Improve, Replace, Remove lens from AO-ARENA-001.

## 2. Product Module Map

The table below defines the official Arena OS modules. Shared capabilities such as Notifications and Reporting are not listed as standalone modules here; they are owned by the modules that create the underlying event or data.

| Name | Purpose | Primary Personas | Business Value | Included in MVP | Depends On | Used By |
|---|---|---|---|---|---|---|
| Operations | Own the facility setup, governance, and operating readiness that make Arena OS usable. | Owner, Manager, Staff, Partner | Makes the business ready to sell and run with confidence. | Yes - Core MVP | None | Reservations, Payments, CRM, AI & Automation, Integrations |
| Reservations | Own the sellable time inventory and reservation lifecycle for courts and daily access. | Player, Manager, Reception, Teacher, Staff | Turns facility availability into booked business. | Yes - Core MVP | Operations | Payments, CRM, AI & Automation, Integrations |
| Payments | Own money collection, settlement, refunds, discounts, and revenue protection around reservations. | Player, Owner, Manager, Reception | Captures revenue and protects it from leakage. | Yes - Core MVP | Operations, Reservations | CRM, AI & Automation, Integrations, Operations |
| CRM | Own customer context, history, and relationship management around bookings and repeat use. | Manager, Reception, Staff, Owner | Keeps the operator close to the customer and reduces manual follow-up. | Yes - Core MVP | Operations, Reservations, Payments | Operations, AI & Automation, Integrations |
| AI & Automation | Own assisted decisions, summaries, recommendations, and repetitive-work reduction across the product. | Owner, Manager, Reception, Staff | Saves time and improves consistency without replacing responsibility. | Yes - Supporting MVP | Operations, Reservations, Payments, CRM | Operations, Reservations, Payments, CRM |
| Integrations | Own the connection to Responde Fácil and other approved external products that extend Arena OS. | Owner, Manager, Staff | Lets Arena OS stay focused while specialized products do specialized work. | Yes - Supporting MVP | Operations, Reservations, Payments, CRM | Operations, Reservations, Payments, CRM, AI & Automation |

## 3. Module Overview

### Operations

#### Purpose

Operations exists to establish the facility as a usable business inside Arena OS. It is the home for facility setup, access, and operating readiness so the rest of the product has a clear business owner and a trustworthy operational context.

#### Responsibilities

- Define the facility's operating identity.
- Own onboarding, visibility, shared access, staff control, and plan entitlements.
- Keep managers and owners oriented with clear operational visibility.
- Set the business conditions required for the other modules to work.

#### What It Owns

- Facility profile and commercial identity.
- Courts as managed business assets.
- Visibility and publishing status.
- Shared access profiles and staff access.
- Plan and tier entitlements.
- Operating settings that prepare the facility to sell bookings.

#### What It Does NOT Own

- Bookings, time slots, or reservation status.
- Payment collection, settlement, refunds, discounts, or other money movement.
- Customer history or relationship records.
- The delivery of notifications or the presentation of reporting outputs.
- Customer service as a standalone product; Arena OS integrates with Responde Fácil instead of owning that domain.

#### Primary Personas

- Owner
- Manager
- Staff
- Partner

#### Future Evolution

- Broader multi-facility governance if Arena OS expands beyond a single venue.
- Additional operational programs if they prove to be recurring business needs.
- Deeper facility configuration only when it simplifies management rather than adding clutter.

### Reservations

#### Purpose

Reservations exists to convert facility availability into bookable business and to manage the reservation lifecycle with clarity. It is the module that turns time on a court into a sellable and trustworthy promise.

#### Responsibilities

- Manage sellable availability.
- Own reservation creation and reservation state.
- Support recurring reservations and day-use reservation formats.
- Handle reservation changes and cancellations as reservation concerns.
- Keep the booking promise simple and dependable.

#### What It Owns

- Availability.
- Slots.
- Bookings.
- Fixed or recurring reservation commitments.
- Day-use reservations.
- Cancellation status.
- Reservation timing rules.

#### What It Does NOT Own

- Facility onboarding or visibility.
- Payment settlement, refunds, discounts, or other financial truth.
- Customer relationship history.
- Notification delivery.
- Business reporting outputs.

#### Primary Personas

- Player
- Manager
- Reception
- Teacher
- Staff

#### Future Evolution

- Additional reservation formats if they prove to be real booking problems.
- Broader recurring patterns when the market shows repeated need.
- Event-based reservation types only if they still belong to the reservation promise.

### Payments

#### Purpose

Payments exists to manage how Arena OS collects, protects, and settles money around reservations and related sales. It is the module that gives the facility a trustworthy commercial outcome.

#### Responsibilities

- Manage payment methods and payment outcomes.
- Own settlement timing and money availability.
- Handle refunds and cancellation penalties.
- Apply discounts and coupons where money is affected.
- Support revenue protection for the business.

#### What It Owns

- Payment events.
- Settlement timing.
- Refund outcomes.
- Penalty retention.
- Discount application.
- Transfer and repass records.
- Revenue-related monetary truth.

#### What It Does NOT Own

- Availability, slots, or booking truth.
- Facility governance or access control.
- Customer relationship records.
- Notification delivery.
- Customer service as a standalone product.

#### Primary Personas

- Player
- Owner
- Manager
- Reception

#### Future Evolution

- Additional payment methods only when they fit the core commercial model.
- More revenue-protection tools if facilities repeatedly need them.
- Additional ancillary sales only when they strengthen the operating model.

### CRM

#### Purpose

CRM exists to keep customer relationship context available to the operator so the facility can communicate and retain players without losing context. It is the module that helps Arena OS remember the people behind the bookings.

#### Responsibilities

- Own customer context and customer history.
- Keep communication context usable for the operator.
- Support recurring customer relationships.
- Support match organization as a relationship activity around bookings.
- Preserve the facility's memory of who the customer is and how they interact.

#### What It Owns

- Customer relationship history.
- Conversation context.
- Match participation context.
- Repeat-customer identity at the facility.
- Relationship notes tied to the customer.

#### What It Does NOT Own

- Booking inventory or reservation state.
- Money movement or payment truth.
- Facility setup or access control.
- Notification delivery.
- Support as a standalone product.

#### Primary Personas

- Manager
- Reception
- Staff
- Owner

#### Future Evolution

- Segmentation if it clearly improves repeat use.
- Richer relationship memory if operators consistently need it.
- Retention support only when it strengthens the core facility relationship.

### AI & Automation

#### Purpose

AI & Automation exists to reduce manual work and improve decision quality with assistance that stays subordinate to the operator. It should make people faster and more confident, not replace their responsibility.

#### Responsibilities

- Summarize useful information.
- Recommend next actions.
- Draft repetitive content.
- Automate repetitive work where the rules are clear.
- Support operators across the product without becoming the owner of the work.

#### What It Owns

- Assistance outputs.
- Suggested next actions.
- Automated repetitive tasks.
- Operator-facing summaries.

#### What It Does NOT Own

- Source truth for bookings, payments, or customer records.
- Facility policy or approval authority.
- Final business decisions.
- External product ownership.

#### Primary Personas

- Owner
- Manager
- Reception
- Staff

#### Future Evolution

- Proactive guidance if the product repeatedly proves it saves time.
- Issue prevention if the same operational pain appears often.
- Forecasting and prioritization only when they improve the core operating model.

### Integrations

#### Purpose

Integrations exists to connect Arena OS to specialized external products and services instead of rebuilding them inside the core product. It keeps Arena OS focused while letting the business benefit from tools that already do one job well.

#### Responsibilities

- Own the relationship with Responde Fácil.
- Connect Arena OS to other approved external products when they add clear business value.
- Extend the product without taking over the core business rules.
- Preserve the distinction between Arena OS ownership and external service ownership.

#### What It Owns

- Integration relationships.
- External handoff commitments.
- Approved connector availability as a business concept.

#### What It Does NOT Own

- Booking rules.
- Payment rules.
- Customer relationship records.
- The business rules of connected products.
- Customer service as a product owned by Arena OS.

#### Primary Personas

- Owner
- Manager
- Staff

#### Future Evolution

- More specialist external connections only when they extend the core operating model.
- New partnerships only when they support the product vision and do not create module clutter.

## 4. Module Relationships

- Operations is the starting point. Facility identity, access, and readiness must exist before bookings, payments, or customer relationships can matter.
- Reservations depends on Operations because courts and visibility must exist before a booking can be created.
- Payments depends on Operations and Reservations because money is collected against a facility that is already configured and a sale or reservation that already exists.
- CRM depends on Operations, Reservations, and Payments because customer context is built from bookings, cancellations, and money interactions.
- AI & Automation depends on the other modules because it should amplify existing work, not invent its own business truth.
- Integrations depends on the core modules because it extends their business promise into Responde Fácil and other approved external products.
- Notifications and reporting are shared product capabilities, not standalone modules. They are triggered by the owning modules and should never become competing sources of truth.

## 5. MVP Module Prioritization

### Core MVP

- Operations belongs here because the product cannot exist without facility setup, access, and operating readiness.
- Reservations belongs here because booking is the core value-creation engine.
- Payments belongs here because Arena OS must collect and protect money around bookings from day one.
- CRM belongs here because communication and repeat-use context are part of the product promise, not a later add-on.

### Supporting MVP

- AI & Automation belongs here because the constitution allows narrow AI assistance that saves time, but it must amplify the core rather than define it.
- Integrations belongs here because Arena OS must integrate with Responde Fácil instead of rebuilding customer service, and other specialist connections only add value when the core is already clear.

### Future Modules

- None in the current official catalog. Notifications and reporting remain shared capabilities, not separate modules.

### Experimental

- None. Experimental work should be confined to an approved module until it proves durable business value.

## 6. Ownership Principles

1. Every business capability has one owner.
2. Shared concepts have one authoritative module.
3. A module owns business meaning, not screens, labels, or delivery channels.
4. Operations owns setup, access, and readiness.
5. Reservations owns availability and reservation state.
6. Payments owns money movement, settlement, refunds, discounts, and revenue protection.
7. CRM owns customer relationship context and communication history.
8. AI & Automation assists people but never replaces accountability or source truth.
9. Integrations extend Arena OS through approved external products, but never own core business rules.
10. Notifications and reporting are outputs of the owning modules, not separate owners of the same truth.

## 7. Module Evolution Rules

1. A capability deserves a new module only when it has a distinct business promise, a distinct owner, and a distinct success measure.
2. Keep a capability inside an existing module when it uses the same source of truth or only changes a variation of the same business decision.
3. Do not create a module for a notification type, dashboard, report, or integration alone.
4. If two modules can claim the same business decision, simplify the boundary before adding a new one.
5. To avoid module proliferation, keep the module count small and let validated business need justify any expansion.
6. If a proposal can be explained cleanly as Keep, Simplify, Improve, Replace, or Remove inside an existing module, it should stay there.

## 8. Non-Goals

This document intentionally does not define:

- Workflows.
- Business rules.
- Screen layouts.
- UI behavior.
- APIs.
- Data models.
- Technical architecture.
- Permissions matrices.
- State machines.
- Release timing.
- Provider selection details.
- Pricing mechanics.

## 9. Next Specifications

### AO-ARENA-003 Reservations

This specification will define the business scope, ownership boundaries, and priority decisions for availability, bookings, recurring reservations, day use, and cancellation handling. Its job is to make clear what Reservations owns and how it stays distinct from Payments and Operations.

### AO-ARENA-004 Payments

This specification will define the commercial scope for payment collection, settlement, refunds, discounts, and revenue protection. Its job is to establish the financial ownership boundary for Arena OS and keep money-related concepts separate from reservations and reporting outputs.

### AO-ARENA-005 CRM

This specification will define the customer-relationship scope for player context, history, communication, and repeat-use support. Its job is to establish what Arena OS remembers about people and how that memory stays separate from bookings and payments.

### AO-ARENA-006 Operations

This specification will define the facility operating scope for onboarding, access, visibility, staff control, and plan packaging. Its job is to make clear how Arena OS governs the business itself without duplicating Reservations or Payments.

### AO-ARENA-007 AI & Automation

This specification will define the product role of AI as an assistant that summarizes, recommends, drafts, and automates repetitive work. Its job is to set the limits of AI ownership so automation supports people without becoming the source of business truth.

### AO-ARENA-008 Integrations

This specification will define how Arena OS connects to specialized external products, including Responde Fácil, without rebuilding them. Its job is to clarify the business boundary between the core product and external services.

### AO-ARENA-009 Domain Boundaries

This specification will define the formal ownership boundaries between modules, shared capabilities, and adjacent concepts. Its job is to prevent duplicated responsibility and to resolve overlaps, including shared capabilities such as Notifications and Reporting when they do not justify a module of their own.

### AO-ARENA-010 Architecture Foundations

This specification will define the product-level guardrails that keep the approved module boundaries stable and make future growth predictable. Its job is to support the official product design without reopening ownership every time a new capability appears.
