# Operations and Permissions Domain Model

## Scope
This file consolidates the conceptual operations and permissions entities visible in the public Agendei reference docs, the consolidated business rules, and the user journeys.
It stays at the product-concept level only.
It is not a database schema, not an architecture model, and not an Arena OS document.

## Entities

### E-OPS-001 — Manager / Facility Owner

- Status: Observed
- Confidence: High
- Domain areas: Operations, Permissions, Scheduling, Billing
- Description: The person responsible for the quadra operation.
- Primary responsibilities: Register the facility, configure visibility, manage schedules, handle payments and finance, create day use, share access, and review plan packaging.
- Related personas: Manager, Facility Owner.
- Related business rules: BR-OPS-001, BR-OPS-002, BR-OPS-003, BR-OPS-004, BR-OPS-005, BR-OPS-006, BR-OPS-007, BR-OPS-008, BR-OPS-009, BR-OPS-010, BR-OPS-011, BR-OPS-012, BR-OPS-013, BR-OPS-014, BR-OPS-015, BR-OPS-016.
- Related journeys: J-MANAGER-001, J-MANAGER-002, J-MANAGER-003, J-MANAGER-004, J-MANAGER-005, J-MANAGER-006, J-MANAGER-007, J-MANAGER-008.
- Relationships: Registers the facility; configures visibility; shares access; manages schedules and finance.
- Observable attributes/concepts: Public registration, multi-court administration, finance view, shared access, plan cards.
- Inferred attributes/concepts: Ownership rights, delegation limits, approval rights.
- Public unknowns: Exact approval and rejection states, exact delegation boundaries, and whether finance access can be shared.
- Source reference: `01-product-overview.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `21-shared-management-and-permissions.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `29-user-journeys-overview.md`, `31-manager-operations-journeys.md`, `32-payment-and-cancellation-journeys.md`, `33-engagement-and-crm-journeys.md`
- Notes: This entity covers the public manager-side operating role rather than an internal permission model.

### E-OPS-002 — Staff / Employee

- Status: Observed
- Confidence: High
- Domain areas: Operations, Permissions, Scheduling
- Description: The employee who helps run the facility under shared access.
- Primary responsibilities: Manage schedules and help with routine operational tasks where access is granted.
- Related personas: Staff, Employee.
- Related business rules: BR-OPS-003, BR-OPS-007, BR-OPS-008, BR-OPS-010, BR-OPS-012.
- Related journeys: J-MANAGER-003, J-MANAGER-007.
- Relationships: Can receive shared access; may manage schedules; sits inside the plan-visible staff-control capability.
- Observable attributes/concepts: Employee access, schedule management.
- Inferred attributes/concepts: Role scope, court scope, approval rights.
- Public unknowns: Whether staff can handle finance, payments, coupons, or account settings.
- Source reference: `02-personas.md`, `06-scheduling-capabilities.md`, `19-manager-operations-overview.md`, `21-shared-management-and-permissions.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `31-manager-operations-journeys.md`
- Notes: The public docs only confirm schedule-management access for employees.

### E-OPS-003 — Partner / Co-manager

- Status: Observed
- Confidence: High
- Domain areas: Operations, Permissions
- Description: The business partner who shares responsibility for the facility.
- Primary responsibilities: Share management responsibility with the owner and participate in delegated operation where access is granted.
- Related personas: Partner, Co-manager.
- Related business rules: BR-OPS-006, BR-OPS-008, BR-OPS-012.
- Related journeys: J-MANAGER-007.
- Relationships: Can receive shared access; sits inside the public shared-management model.
- Observable attributes/concepts: Shared management with partners, profile-based access.
- Inferred attributes/concepts: Ownership share, decision rights, financial access.
- Public unknowns: Exact co-owner rights, decision rights, and finance access.
- Source reference: `02-personas.md`, `19-manager-operations-overview.md`, `21-shared-management-and-permissions.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `31-manager-operations-journeys.md`
- Notes: The public docs mention partners but not the full role model.

### E-OPS-004 — Shared Access Profile

- Status: Inferred
- Confidence: Medium
- Domain areas: Operations, Permissions
- Description: The profile-based scope that governs delegated access for staff and partners.
- Primary responsibilities: Define what delegated users can do within the facility operation.
- Related personas: Manager, Staff, Partner.
- Related business rules: BR-OPS-006, BR-OPS-007, BR-OPS-008.
- Related journeys: J-MANAGER-007.
- Relationships: Defines access boundaries for delegated users.
- Observable attributes/concepts: Different access profiles, shared administration.
- Inferred attributes/concepts: Role hierarchy, permission inheritance, revocation behavior.
- Public unknowns: Whether profiles are predefined or custom, and what inheritance rules apply.
- Source reference: `02-personas.md`, `21-shared-management-and-permissions.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `31-manager-operations-journeys.md`
- Notes: The profile concept is public, but the exact matrix is not.

### E-OPS-005 — Staff Control

- Status: Observed
- Confidence: High
- Domain areas: Operations, Permissions
- Description: The public capability for controlling employee access.
- Primary responsibilities: Allow the facility to manage staff access inside the product.
- Related personas: Manager, Staff.
- Related business rules: BR-OPS-010, BR-OPS-012.
- Related journeys: J-MANAGER-007.
- Relationships: Belongs to the plan-visible capability set.
- Observable attributes/concepts: `Controle de Funcionários`, public plan visibility.
- Inferred attributes/concepts: Staff limits, role assignment, deactivation behavior.
- Public unknowns: Whether staff control includes finance or Agendei Pay permissions.
- Source reference: `03-modules.md`, `21-shared-management-and-permissions.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`
- Notes: The public docs expose the capability name but not the workflow.

### E-OPS-006 — Facility Registration

- Status: Observed
- Confidence: High
- Domain areas: Operations, Billing
- Description: The public signup path used to register the quadra and open App Gestor access.
- Primary responsibilities: Start the facility onboarding flow and create the entry point to the manager surface.
- Related personas: Manager, Facility Owner.
- Related business rules: BR-OPS-001, BR-PAYMENT-002, BR-PAYMENT-003, BR-PAYMENT-004.
- Related journeys: J-MANAGER-001, J-MANAGER-006.
- Relationships: Enables App Gestor access after public registration.
- Observable attributes/concepts: Public CTA, CPF or CNPJ registration path, approval timing.
- Inferred attributes/concepts: Mandatory documents, validation rules, review step.
- Public unknowns: Exact signup fields, whether access is immediate or reviewed, and the exact document set.
- Source reference: `04-navigation.md`, `10-agendei-pay.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `31-manager-operations-journeys.md`
- Notes: The public site repeatedly invites the facility to register the quadra.

### E-OPS-007 — Facility Visibility / Publishing

- Status: Inferred
- Confidence: Medium
- Domain areas: Operations, Scheduling
- Description: The visibility state that lets a configured facility appear to players in the public app.
- Primary responsibilities: Make the court discoverable in App Agendei after setup.
- Related personas: Manager, Player.
- Related business rules: BR-OPS-002, BR-BOOKING-001, BR-BOOKING-002, BR-BOOKING-003.
- Related journeys: J-MANAGER-002, J-PLAYER-001.
- Relationships: Enables player discovery.
- Observable attributes/concepts: Visibility setup, public discovery, agenda exposure.
- Inferred attributes/concepts: Publish toggle, search ranking, visibility modes.
- Public unknowns: Exact publish control, review workflow, and whether different visibility modes exist.
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `30-player-booking-journeys.md`, `31-manager-operations-journeys.md`
- Notes: The public docs imply visibility from onboarding and discovery, but do not show the publish screen.

### E-OPS-008 — Plan / Tier

- Status: Observed
- Confidence: High
- Domain areas: Operations, Billing
- Description: The public packaging structure that groups features into visible plan cards.
- Primary responsibilities: Package capabilities, surface announced features, and explain what the public pricing page offers.
- Related personas: Prospect, Manager, Facility Owner.
- Related business rules: BR-OPS-009, BR-OPS-010, BR-OPS-011, BR-OPS-012, BR-OPS-013, BR-OPS-014.
- Related journeys: J-MANAGER-008, J-CRM-006.
- Relationships: Packages operational capabilities, including staff control and other visible features.
- Observable attributes/concepts: Inicial, Padrão, Avançado, `Em breve` labels.
- Inferred attributes/concepts: Capability inheritance across tiers, commercial packaging behavior.
- Public unknowns: Exact upgrade behavior, billing cycle detail, and release timing for announced features.
- Source reference: `12-financial-capabilities.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `29-user-journeys-overview.md`, `33-engagement-and-crm-journeys.md`
- Notes: The public pricing page reads as a progressive package rather than isolated add-ons.

### E-OPS-009 — Central de Atendimento

- Status: Observed
- Confidence: Medium
- Domain areas: Operations, Support
- Description: The support capability surfaced on the public plan page.
- Primary responsibilities: Represent operator support or help access; the workflow is not public.
- Related personas: Prospect, Manager, Facility Owner.
- Related business rules: BR-OPS-009.
- Related journeys: None directly consolidated.
- Relationships: Is visible on the public plan page but operationally unclear.
- Observable attributes/concepts: `Central de Atendimento` plan feature.
- Inferred attributes/concepts: Human support, self-service support, or both.
- Public unknowns: Whether it is human-assisted, self-service, or a mixture.
- Source reference: `03-modules.md`, `19-manager-operations-overview.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`
- Notes: The feature name is public, but the operational model is not.

### E-OPS-010 — AI Management / Gestão Inteligente com IA

- Status: Observed
- Confidence: High
- Domain areas: Operations, Automation
- Description: The announced AI-assisted management capability shown on the Avançado plan.
- Primary responsibilities: Announce a future intelligent-management feature; the public material does not describe the workflow.
- Related personas: Prospect, Manager, Facility Owner.
- Related business rules: BR-OPS-014, BR-OPS-012.
- Related journeys: None directly consolidated.
- Relationships: Is announced as a coming-soon capability.
- Observable attributes/concepts: `Gestão Inteligente com IA`, `Em breve` label.
- Inferred attributes/concepts: Automation, decision support, management assistance.
- Public unknowns: Exact release timing and the operational workflow.
- Source reference: `03-modules.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`
- Notes: The public plan page announces the feature, but no workflow is visible.

## Relationships

### Manager registers facility

- Relationship: A manager registers the facility.
- Status: Observed
- Confidence: High
- Source entity: Manager / Facility Owner
- Target entity: Facility Registration
- Business meaning: The public signup flow begins when the facility owner registers the quadra.
- Related rules: BR-OPS-001, BR-PAYMENT-002, BR-PAYMENT-004
- Related journeys: J-MANAGER-001, J-MANAGER-006
- Source reference: `04-navigation.md`, `10-agendei-pay.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `31-manager-operations-journeys.md`
- Notes: The public CTA repeatedly invites the facility to register the quadra.

### Facility registration enables App Gestor access

- Relationship: Facility registration enables App Gestor access.
- Status: Observed
- Confidence: High
- Source entity: Facility Registration
- Target entity: App Gestor access
- Business meaning: A completed public registration opens the manager surface for later operations.
- Related rules: BR-OPS-001, BR-PAYMENT-002, BR-PAYMENT-003, BR-PAYMENT-004
- Related journeys: J-MANAGER-001, J-MANAGER-006
- Source reference: `10-agendei-pay.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `31-manager-operations-journeys.md`
- Notes: The access path is public; the exact approval state is not fully visible.

### Manager configures facility visibility

- Relationship: A manager configures facility visibility.
- Status: Observed
- Confidence: High
- Source entity: Manager / Facility Owner
- Target entity: Facility Visibility / Publishing
- Business meaning: The manager prepares the court so it can appear in the player app.
- Related rules: BR-OPS-002, BR-BOOKING-001, BR-BOOKING-002, BR-BOOKING-003
- Related journeys: J-MANAGER-002, J-PLAYER-001
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `27-operations-business-rules.md`, `31-manager-operations-journeys.md`
- Notes: The public docs imply this step, but do not show the publish control.

### Facility visibility enables player discovery

- Relationship: Facility visibility enables player discovery.
- Status: Inferred
- Confidence: Medium
- Source entity: Facility Visibility / Publishing
- Target entity: Player / Client / User
- Business meaning: Once the facility is visible, players can find it by location and inspect its agenda.
- Related rules: BR-OPS-002, BR-BOOKING-001, BR-BOOKING-002, BR-BOOKING-003
- Related journeys: J-MANAGER-002, J-PLAYER-001
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `20-facility-onboarding-and-configuration.md`, `30-player-booking-journeys.md`, `31-manager-operations-journeys.md`
- Notes: The discovery flow is visible, but the exact publish workflow is not.

### Manager shares access with staff

- Relationship: A manager shares access with staff.
- Status: Observed
- Confidence: High
- Source entity: Manager / Facility Owner
- Target entity: Staff / Employee
- Business meaning: The manager can delegate operational access to employees.
- Related rules: BR-OPS-006, BR-OPS-007, BR-OPS-008
- Related journeys: J-MANAGER-007
- Source reference: `02-personas.md`, `21-shared-management-and-permissions.md`, `27-operations-business-rules.md`, `31-manager-operations-journeys.md`
- Notes: The public docs explicitly mention employee access for schedule management.

### Manager shares access with partner/co-manager

- Relationship: A manager shares access with a partner or co-manager.
- Status: Observed
- Confidence: High
- Source entity: Manager / Facility Owner
- Target entity: Partner / Co-manager
- Business meaning: The manager can delegate operational access to a business partner.
- Related rules: BR-OPS-006, BR-OPS-008
- Related journeys: J-MANAGER-007
- Source reference: `02-personas.md`, `21-shared-management-and-permissions.md`, `27-operations-business-rules.md`, `31-manager-operations-journeys.md`
- Notes: The public docs confirm shared management, but not the full role matrix.

### Staff may manage schedules

- Relationship: Staff may manage schedules.
- Status: Observed
- Confidence: High
- Source entity: Staff / Employee
- Target entity: Schedule / Agenda
- Business meaning: Delegated employees can work on the facility agenda.
- Related rules: BR-OPS-007, BR-OPS-003, BR-OPS-010
- Related journeys: J-MANAGER-003, J-MANAGER-007
- Source reference: `06-scheduling-capabilities.md`, `21-shared-management-and-permissions.md`, `27-operations-business-rules.md`, `31-manager-operations-journeys.md`
- Notes: The public docs do not confirm broader staff permissions.

### Shared access profile defines access boundaries

- Relationship: A shared access profile defines access boundaries.
- Status: Inferred
- Confidence: Medium
- Source entity: Shared Access Profile
- Target entity: Staff / Employee
- Business meaning: The profile-based model limits what delegated users can do.
- Related rules: BR-OPS-006, BR-OPS-007, BR-OPS-008
- Related journeys: J-MANAGER-007
- Source reference: `21-shared-management-and-permissions.md`, `27-operations-business-rules.md`, `31-manager-operations-journeys.md`
- Notes: The public docs say profiles exist, but not the exact inheritance rules.

### Plan/tier packages capabilities

- Relationship: Plan tiers package capabilities.
- Status: Observed
- Confidence: High
- Source entity: Plan / Tier
- Target entity: Staff Control
- Business meaning: The public pricing cards bundle operational capabilities into visible tiers, including staff control as one example.
- Related rules: BR-OPS-009, BR-OPS-010, BR-OPS-011, BR-OPS-012, BR-OPS-013, BR-OPS-014
- Related journeys: J-MANAGER-008, J-CRM-006
- Source reference: `12-financial-capabilities.md`, `22-plans-tiers-and-feature-packaging.md`, `27-operations-business-rules.md`, `33-engagement-and-crm-journeys.md`
- Notes: Higher tiers are presented as broader capability packages rather than isolated add-ons.

### Staff control belongs to plan-visible capabilities

- Relationship: Staff control belongs to the plan-visible capabilities.
- Status: Observed
- Confidence: High
- Source entity: Staff Control
- Target entity: Plan / Tier
- Business meaning: The facility sees staff control surfaced as part of the public plan structure.
- Related rules: BR-OPS-010, BR-OPS-012
- Related journeys: J-MANAGER-007
- Source reference: `21-shared-management-and-permissions.md`, `22-plans-tiers-and-feature-packaging.md`, `27-operations-business-rules.md`
- Notes: The public docs show staff control in the Padrão and Avançado packaging.

### Central de atendimento is visible but operationally unclear

- Relationship: Central de atendimento is visible but operationally unclear.
- Status: Observed
- Confidence: Medium
- Source entity: Plan / Tier
- Target entity: Central de Atendimento
- Business meaning: The support feature appears on the public plan page, but its workflow is not described.
- Related rules: BR-OPS-009
- Related journeys: None directly consolidated.
- Source reference: `03-modules.md`, `22-plans-tiers-and-feature-packaging.md`, `27-operations-business-rules.md`
- Notes: The public docs do not say whether this is human-assisted, self-service, or both.

### AI management is announced but not detailed

- Relationship: AI management is announced but not detailed.
- Status: Observed
- Confidence: High
- Source entity: Plan / Tier
- Target entity: AI Management / Gestão Inteligente com IA
- Business meaning: The public pricing page advertises an AI-assisted management feature, but no workflow is public.
- Related rules: BR-OPS-014, BR-OPS-012
- Related journeys: None directly consolidated.
- Source reference: `03-modules.md`, `22-plans-tiers-and-feature-packaging.md`, `27-operations-business-rules.md`
- Notes: The public material marks the feature as coming soon.

## Unknowns

- Exact role hierarchy and permission inheritance rules.
- Whether staff or partners can access finance or Agendei Pay controls.
- Whether shared management includes all plan-visible capabilities in practice.
- Exact facility and court configuration screens.
- Exact publish controls for visibility.
- Exact approval and rejection states beyond the public wording.
- Whether central de atendimento is human-assisted, self-service, or both.
- Exact release timing and workflow for AI management.

