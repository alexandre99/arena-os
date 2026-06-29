# Manager Operations Journeys

## Scope
This document consolidates manager-side journeys from the existing public Agendei reference docs and consolidated business rules.
It stays within the public reference set and does not define Arena OS behavior.

## Journeys

### J-MANAGER-001 — Register facility and receive App Gestor access

- Status: Observed
- Confidence: High
- Primary persona: Manager
- Supporting personas: None
- Domain areas: Operations, Onboarding
- Trigger: Manager discovers App Gestor and starts the public registration flow.
- Preconditions: The public registration CTA is visible.
- Main success path:
  1. Manager opens the public App Gestor surface.
  2. Manager uses the public `Cadastrar minha quadra` entry point.
  3. Facility registration is submitted through the public site.
  4. The manager receives access to App Gestor after registration.
  5. The manager can continue into later onboarding steps if needed.
- Alternate paths:
  - A CPF-based registration path is publicly mentioned for facilities without CNPJ.
- Business rules used: `BR-OPS-001`, `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-PAYMENT-004`
- Expected outcome: The facility is registered and the manager can use the public manager app.
- Public unknowns:
  - Exact signup fields.
  - Exact mandatory documents.
  - Whether access is immediate or reviewed before use.
- Source reference: `04-navigation.md`, `10-agendei-pay.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`
- Notes:
  - The public docs show the registration path and access outcome, but not the full form or approval states.

### J-MANAGER-002 — Configure facility visibility in App Agendei

- Status: Inferred
- Confidence: Medium
- Primary persona: Manager
- Supporting personas: Player
- Domain areas: Operations, Scheduling
- Trigger: Manager finishes onboarding and prepares the court for player discovery.
- Preconditions: The facility is registered in App Gestor.
- Main success path:
  1. Manager configures the court in App Gestor.
  2. Manager completes the visibility-related setup.
  3. The court becomes visible to players in App Agendei.
  4. Players can find the court by location and see its agenda.
- Alternate paths:
  - The exact publish toggle or review workflow is not publicly confirmed.
- Business rules used: `BR-OPS-002`, `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003`
- Expected outcome: The facility can be discovered from the player app.
- Public unknowns:
  - Exact publish control.
  - Search-ranking logic.
  - Whether different visibility modes exist.
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `27-operations-business-rules.md`
- Notes:
  - The visibility step is inferred from public onboarding and player-discovery wording, not from a public publish screen.

### J-MANAGER-003 — Manage schedule and availability

- Status: Observed
- Confidence: High
- Primary persona: Manager
- Supporting personas: Staff, Player
- Domain areas: Scheduling, Operations
- Trigger: Manager opens the agenda in App Gestor.
- Preconditions: The facility is operating and has visible courts.
- Main success path:
  1. Manager opens schedule management.
  2. Manager creates one-off bookings.
  3. Manager creates fixed bookings.
  4. Manager manages mensalistas.
  5. Manager administers multiple courts from the same operation.
- Alternate paths:
  - Staff may participate in schedule management through shared access.
- Business rules used: `BR-BOOKING-008`, `BR-BOOKING-009`, `BR-BOOKING-010`, `BR-BOOKING-011`, `BR-OPS-003`, `BR-OPS-007`
- Expected outcome: The facility agenda reflects the manager's operational decisions.
- Public unknowns:
  - Whether all courts appear in one calendar view.
  - Exact edit/remove flows for fixed bookings.
  - Exact mensalista handling beyond the public recurring concept.
- Source reference: `03-modules.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `07-scheduling-entities.md`, `19-manager-operations-overview.md`, `21-shared-management-and-permissions.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `27-operations-business-rules.md`
- Notes:
  - The public docs treat agenda control, fixed bookings, mensalistas, and multiple courts as one operating surface.

### J-MANAGER-004 — Accept local-payment booking request

- Status: Observed
- Confidence: High
- Primary persona: Manager
- Supporting personas: Player
- Domain areas: Scheduling, Payments, Communication
- Trigger: A player submits a pay-at-facility booking request.
- Preconditions: The local-payment booking path is active.
- Main success path:
  1. Manager receives the local-payment request.
  2. Manager reviews the booking request.
  3. Manager accepts and confirms the request.
  4. The booking moves out of the pending branch.
- Alternate paths:
  - The public docs do not show the exact pending or decline statuses.
- Business rules used: `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-007`
- Expected outcome: The local-payment booking is confirmed by the manager.
- Public unknowns:
  - Exact approval screen.
  - Exact request-status labels.
  - Whether the manager can decline from the same screen.
- Source reference: `05-booking-lifecycle.md`, `09-payments-overview.md`, `16-communication-and-chat.md`, `19-manager-operations-overview.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`, `26-payment-business-rules.md`
- Notes:
  - The public reference makes the manager acceptance step explicit, but not the screen-level detail.

### J-MANAGER-005 — Create day use product

- Status: Observed
- Confidence: High
- Primary persona: Manager
- Supporting personas: Player
- Domain areas: Scheduling, Operations, Payments
- Trigger: Manager decides to offer day use.
- Preconditions: The day-use feature is available in App Gestor.
- Main success path:
  1. Manager opens the day-use creation flow.
  2. Manager defines the product name, day, court, duration, price, and payment form.
  3. Manager publishes the day use product.
  4. Player later buys the product as a separate purchase flow.
  5. The manager receives a push notification for the sale.
- Alternate paths:
  - Editing after publication is not publicly confirmed.
- Business rules used: `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014`
- Expected outcome: The facility can sell a separate daily reservation product.
- Public unknowns:
  - Whether day use can be edited after publication.
  - Whether day use blocks hourly agenda slots.
- Source reference: `04-navigation.md`, `05-booking-lifecycle.md`, `06-scheduling-capabilities.md`, `12-financial-capabilities.md`, `16-communication-and-chat.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `25-booking-business-rules.md`
- Notes:
  - The public docs show the creation fields and the purchase notification, but not the edit lifecycle.

### J-MANAGER-006 — Activate Agendei Pay

- Status: Observed
- Confidence: High
- Primary persona: Manager
- Supporting personas: None
- Domain areas: Payments, Operations
- Trigger: Manager starts the digital account onboarding flow.
- Preconditions: The facility has completed public registration and can access App Gestor.
- Main success path:
  1. Manager creates the digital account through credentialing in App Gestor.
  2. Manager completes the public approval flow.
  3. Approval can arrive in up to 10 minutes.
  4. PIX and card receipts are activated after approval.
- Alternate paths:
  - Facilities without CNPJ can use CPF in the public registration path.
- Business rules used: `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-PAYMENT-004`, `BR-OPS-004`
- Expected outcome: Agendei Pay is active and the facility can receive online booking money.
- Public unknowns:
  - Exact credentialing fields.
  - Exact approval and rejection states.
  - Exact required documents beyond the public mention of responsible-person documents.
- Source reference: `10-agendei-pay.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`
- Notes:
  - The public timing statement is the up-to-10-minutes approval window.

### J-MANAGER-007 — Share access with staff or partners

- Status: Observed
- Confidence: High
- Primary persona: Manager
- Supporting personas: Staff, Partner
- Domain areas: Operations, Permissions
- Trigger: Manager delegates daily operation work.
- Preconditions: The facility wants shared administration.
- Main success path:
  1. Manager creates shared access.
  2. Manager assigns a profile-based access arrangement.
  3. Staff members gain schedule-management access.
  4. Partners or co-managers receive shared operational access.
- Alternate paths:
  - Exact permission boundaries are not publicly confirmed.
- Business rules used: `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008`
- Expected outcome: Facility operations can be shared beyond the owner account.
- Public unknowns:
  - Exact role hierarchy.
  - Exact permission inheritance.
  - Whether staff or partners can access finance or payments.
- Source reference: `02-personas.md`, `03-modules.md`, `19-manager-operations-overview.md`, `21-shared-management-and-permissions.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`
- Notes:
  - The public docs confirm shared management and a staff schedule role, but not the full matrix.

### J-MANAGER-008 — Use financial/cash-flow management

- Status: Observed
- Confidence: High
- Primary persona: Manager
- Supporting personas: None
- Domain areas: Finance, Operations
- Trigger: Manager opens the financial surface in App Gestor.
- Preconditions: The facility uses the public manager surface and, for settlement flows, Agendei Pay is active.
- Main success path:
  1. Manager opens the finance or cash-flow area.
  2. Manager reviews revenue, expense, profit, and cash flow.
  3. Manager uses the transfer and repass tools when money needs to leave the digital account.
  4. The manager tracks the facility's financial position from the public surface.
- Alternate paths:
  - Exact reports and reconciliation screens are not publicly described.
- Business rules used: `BR-OPS-005`, `BR-PAYMENT-001`, `BR-PAYMENT-010`, `BR-PAYMENT-016`
- Expected outcome: The manager can observe and move money through the public financial surface.
- Public unknowns:
  - Report granularity.
  - Reconciliation detail.
  - Manual entry behavior.
- Source reference: `03-modules.md`, `10-agendei-pay.md`, `12-financial-capabilities.md`, `19-manager-operations-overview.md`, `22-plans-tiers-and-feature-packaging.md`, `24-business-rules-overview.md`, `26-payment-business-rules.md`, `27-operations-business-rules.md`
- Notes:
  - The public docs show finance as a core manager capability, but not the internal report structure.

## Journey Dependencies

| Dependency | Related journey IDs | Related rule IDs | Notes |
|---|---|---|---|
| Facility registration enables later visibility and finance flows | `J-MANAGER-001`, `J-MANAGER-002`, `J-MANAGER-006`, `J-MANAGER-008` | `BR-OPS-001`, `BR-OPS-002`, `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-OPS-004` | Registration is the first public entry point for the manager side. |
| Visibility setup enables player discovery | `J-MANAGER-002`, `J-PLAYER-001` | `BR-OPS-002`, `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003` | Players can only discover visible courts. |
| Shared access depends on profile-based permissions | `J-MANAGER-007`, `J-MANAGER-003`, `J-MANAGER-004` | `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008` | Staff scheduling depends on delegated access. |
| Day use sales depend on a manager-created product | `J-MANAGER-005`, `J-PLAYER-005` | `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014` | The product must exist before the player can buy it. |
| Agendei Pay activation enables online-payment settlement and finance visibility | `J-MANAGER-006`, `J-MANAGER-008` | `BR-PAYMENT-001`, `BR-PAYMENT-002`, `BR-PAYMENT-003`, `BR-PAYMENT-010`, `BR-PAYMENT-016` | Settlement and transfer behavior depend on the digital account. |

## Unknowns
- Exact signup fields and required documents.
- Exact visibility/publishing workflow.
- Exact staff and partner permission matrix.
- Whether staff or partners can touch finance or Agendei Pay.
- Exact day-use edit and publication rules.
- Exact finance reports and reconciliation screens.
- Exact lesson and tournament workflows behind the plan-visible feature names.
