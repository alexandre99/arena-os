# Operations Business Rules

## Scope
This document consolidates facility onboarding, manager operations, permissions, shared management, plan-tier packaging, and configuration rules from the public Agendei reference docs.
It stays within the public reference set and does not define internal RBAC or implementation detail.

## Rules

### BR-OPS-001 — Facility registers through the public site and receives App Gestor access
- Status: Observed
- Confidence: High
- Domain area: Operations
- Trigger: Facility starts the public signup flow.
- Condition: The quadra is registered through the public site.
- Outcome: The facility receives access to App Gestor.
- Involved personas: Manager, facility.
- Affected concepts/entities: Facility registration, App Gestor access, public signup.
- Source reference: `04-navigation.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`
- Notes: The public CTA repeatedly invites the facility to register the quadra.

### BR-OPS-002 — Facility configuration is required before the court becomes visible in App Agendei
- Status: Inferred
- Confidence: Medium
- Domain area: Operations
- Trigger: Manager finishes onboarding and setup.
- Condition: The court has been configured in App Gestor.
- Outcome: The court can appear in App Agendei for players.
- Involved personas: Manager, player.
- Affected concepts/entities: Visibility, facility setup, player discovery.
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `20-facility-onboarding-and-configuration.md`
- Notes: The public docs imply the visibility flow, but the exact publish control is not public.

### BR-OPS-003 — Manager controls schedules, bookings, mensalistas, and multiple courts
- Status: Observed
- Confidence: High
- Domain area: Operations
- Trigger: Manager uses App Gestor.
- Condition: The facility is operating normally.
- Outcome: The manager can manage schedules, bookings, fixed bookings, mensalistas, and all courts from one account.
- Involved personas: Manager, staff.
- Affected concepts/entities: Agenda, fixed booking, mensalista, multiple courts.
- Source reference: `03-modules.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `19-manager-operations-overview.md`
- Notes: This is the core manager-side operating rule.

### BR-OPS-004 — Manager activates Agendei Pay after credentialing and approval
- Status: Observed
- Confidence: High
- Domain area: Operations
- Trigger: Manager finishes Agendei Pay onboarding.
- Condition: Credentialing is completed and approved.
- Outcome: PIX and card receipts can be activated.
- Involved personas: Manager, facility.
- Affected concepts/entities: Agendei Pay activation, credentialing, receipt enabling.
- Source reference: `10-agendei-pay.md`, `20-facility-onboarding-and-configuration.md`, `19-manager-operations-overview.md`
- Notes: The public material ties activation to the digital-account onboarding flow.

### BR-OPS-005 — Manager uses the manager surface to manage finance and cash flow
- Status: Observed
- Confidence: High
- Domain area: Operations
- Trigger: Manager opens finance tools in App Gestor.
- Condition: The facility needs financial visibility.
- Outcome: Revenue, expense, profit, and cash flow can be managed from the manager surface.
- Involved personas: Manager.
- Affected concepts/entities: Finance view, cash flow, management surface.
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `19-manager-operations-overview.md`
- Notes: The public docs present finance as a core operational area.

### BR-OPS-006 — Manager can share access with staff and partners
- Status: Observed
- Confidence: High
- Domain area: Permissions
- Trigger: Manager delegates daily operation tasks.
- Condition: The facility wants shared administration.
- Outcome: The manager can create shared access for employees and partners.
- Involved personas: Manager, staff, partner.
- Affected concepts/entities: Shared management, access sharing, delegated operation.
- Source reference: `02-personas.md`, `03-modules.md`, `21-shared-management-and-permissions.md`
- Notes: The public docs explicitly mention staff and partner access.

### BR-OPS-007 — Employees can access the app to manage schedules
- Status: Observed
- Confidence: High
- Domain area: Permissions
- Trigger: Facility grants staff access.
- Condition: The employee is included in shared management.
- Outcome: The employee can manage schedules in the app.
- Involved personas: Staff, manager.
- Affected concepts/entities: Employee access, schedule management, shared control.
- Source reference: `02-personas.md`, `06-scheduling-capabilities.md`, `21-shared-management-and-permissions.md`
- Notes: The public docs do not confirm broader staff permissions.

### BR-OPS-008 — Shared access is profile-based, but exact permission boundaries are not public
- Status: Inferred
- Confidence: Medium
- Domain area: Permissions
- Trigger: Manager configures shared administration.
- Condition: Different access profiles are created for staff or partners.
- Outcome: Access is likely scoped by profile rather than being all-or-nothing.
- Involved personas: Manager, staff, partner.
- Affected concepts/entities: Access profile, permission scope, delegation.
- Source reference: `02-personas.md`, `21-shared-management-and-permissions.md`
- Notes: The exact role matrix and inheritance rules are not public.

### BR-OPS-009 — The Inicial plan includes unlimited courts, unlimited bookings, digital account, cash flow, and central de atendimento
- Status: Observed
- Confidence: High
- Domain area: Operations
- Trigger: Prospect reviews the public pricing page.
- Condition: The Inicial plan card is visible.
- Outcome: The plan packages core operation, finance, and support capabilities.
- Involved personas: Prospect, manager.
- Affected concepts/entities: Plan tier, unlimited courts, support, cash flow.
- Source reference: `12-financial-capabilities.md`, `19-manager-operations-overview.md`, `22-plans-tiers-and-feature-packaging.md`
- Notes: The public docs do not explain the central de atendimento workflow.

### BR-OPS-010 — The Padrão plan adds staff control and lessons/escolinha
- Status: Observed
- Confidence: High
- Domain area: Operations
- Trigger: Prospect reviews the Padrão plan card.
- Condition: The facility needs delegated staff access or lesson management.
- Outcome: Staff control and lesson/school management become available in the plan.
- Involved personas: Prospect, manager.
- Affected concepts/entities: Staff control, lessons, escolinha, plan packaging.
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `21-shared-management-and-permissions.md`, `22-plans-tiers-and-feature-packaging.md`
- Notes: The public docs show the feature names but not the workflow.

### BR-OPS-011 — The Avancado plan adds tournament registration and custom coupon creation
- Status: Observed
- Confidence: High
- Domain area: Operations
- Trigger: Prospect reviews the Avancado plan card.
- Condition: The facility wants event registration or more advanced promotional tooling.
- Outcome: Tournament registration and custom coupon creation are available in the advanced tier.
- Involved personas: Prospect, manager.
- Affected concepts/entities: Tournament registration, custom coupon, advanced tier.
- Source reference: `03-modules.md`, `17-engagement-coupons-and-match-organization.md`, `22-plans-tiers-and-feature-packaging.md`
- Notes: The public docs do not show the workflow for either feature.

### BR-OPS-012 — Plan capabilities are cumulative across tiers
- Status: Inferred
- Confidence: High
- Domain area: Operations
- Trigger: Prospect compares the public plan cards.
- Condition: Higher tiers are shown above lower tiers.
- Outcome: Higher tiers include the capabilities of lower tiers plus additional features.
- Involved personas: Prospect, manager.
- Affected concepts/entities: Tier packaging, feature inheritance, plan comparison.
- Source reference: `12-financial-capabilities.md`, `22-plans-tiers-and-feature-packaging.md`
- Notes: This is the clearest reading of the public pricing layout.

### BR-OPS-013 — Billing generator and material rental are announced as coming soon
- Status: Observed
- Confidence: High
- Domain area: Operations
- Trigger: Prospect reviews the public plan page.
- Condition: The features are marked Em breve.
- Outcome: The platform advertises future billing and ancillary-rental capabilities without workflow detail.
- Involved personas: Prospect, manager.
- Affected concepts/entities: Billing generator, material rental, roadmap feature.
- Source reference: `03-modules.md`, `12-financial-capabilities.md`, `22-plans-tiers-and-feature-packaging.md`
- Notes: The public docs do not confirm operational availability.

### BR-OPS-014 — AI management is announced as coming soon in the Avancado tier
- Status: Observed
- Confidence: High
- Domain area: Operations
- Trigger: Prospect reviews the Avancado plan card.
- Condition: The AI feature is shown as Em breve.
- Outcome: The public site announces intelligent management assistance without describing the workflow.
- Involved personas: Prospect, manager.
- Affected concepts/entities: AI management, plan packaging, roadmap feature.
- Source reference: `03-modules.md`, `22-plans-tiers-and-feature-packaging.md`
- Notes: The public material does not explain whether the feature is operational or purely announced.

### BR-OPS-015 — Chat/messages provide direct communication between facility and client
- Status: Observed
- Confidence: High
- Domain area: CRM
- Trigger: Facility or client needs to communicate about a booking or relationship.
- Condition: The public message channel is available.
- Outcome: The two sides can communicate in-app.
- Involved personas: Manager, player, staff, partner.
- Affected concepts/entities: Chat, messages, communication channel.
- Source reference: `03-modules.md`, `16-communication-and-chat.md`, `19-manager-operations-overview.md`
- Notes: The public docs do not expose the exact transport or retention model.

### BR-OPS-016 — Booking notifications inform the customer and manager when action is needed
- Status: Inferred
- Confidence: Medium
- Domain area: CRM
- Trigger: A booking is created, confirmed, or changes request state.
- Condition: The public booking flow implies notification handling.
- Outcome: The system informs the customer and the manager about the booking event.
- Involved personas: Player, manager.
- Affected concepts/entities: Booking notification, customer alert, manager alert.
- Source reference: `04-navigation.md`, `16-communication-and-chat.md`
- Notes: The exact notification channel is not public.

### BR-OPS-017 — Player can invite friends as part of match organization
- Status: Observed
- Confidence: High
- Domain area: Engagement
- Trigger: Player organizes a match around a booking.
- Condition: The public player features are available.
- Outcome: The player can invite friends to join the match.
- Involved personas: Player, invited friend.
- Affected concepts/entities: Invitations, participants, match organization.
- Source reference: `01-product-overview.md`, `03-modules.md`, `17-engagement-coupons-and-match-organization.md`
- Notes: The invite delivery mechanism is not public.

### BR-OPS-018 — The app can sort teams for the match
- Status: Observed
- Confidence: High
- Domain area: Engagement
- Trigger: Player uses the match-organization feature.
- Condition: Teams need to be formed around the booking.
- Outcome: The app can sort teams for the match.
- Involved personas: Player, match participants.
- Affected concepts/entities: Team sorting, match setup, participants.
- Source reference: `01-product-overview.md`, `03-modules.md`, `17-engagement-coupons-and-match-organization.md`
- Notes: The algorithm or rules are not public.

## Rule Dependencies

| Dependency | Related rule IDs | Confidence | Notes |
|---|---|---|---|
| Public visibility depends on registration and configuration | `BR-OPS-001`, `BR-OPS-002` | High | The facility must register and then configure the court before players can see it. |
| Financial operations depend on Agendei Pay activation | `BR-OPS-004`, `BR-OPS-005`, `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-PAYMENT-004`, `BR-PAYMENT-010` | High | The finance surface becomes operational after credentialing and account approval. |
| Shared access depends on profile-based permissions | `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008` | High | The public docs imply role-scoped delegation, but do not expose the full matrix. |
| Plan capabilities are cumulative across tiers | `BR-OPS-009`, `BR-OPS-010`, `BR-OPS-011`, `BR-OPS-012`, `BR-OPS-013`, `BR-OPS-014` | High | The pricing page reads as a progressive package rather than isolated add-ons. |
| Communication and engagement depend on the player/facility relationship context | `BR-OPS-015`, `BR-OPS-016`, `BR-OPS-017`, `BR-OPS-018` | Medium | The public messaging and match-organization features appear alongside booking and management flows. |
| Custom coupon creation depends on advanced-tier visibility | `BR-OPS-011`, `BR-OPS-012` | High | The coupon tooling is tied to the advanced plan rather than a standalone control. |

## Unknowns
- Exact RBAC model and permission inheritance rules.
- Exact facility and court configuration screens.
- Exact publish and visibility controls for player discovery.
- Whether shared management includes Agendei Pay and finance controls in practice.
- Exact workflow behind central de atendimento.
- Exact lesson and tournament workflows.
- Exact release timing for announced features.

