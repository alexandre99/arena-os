# Operations and Access State Machines

## Scope
This document consolidates the conceptual facility onboarding, player visibility, and shared-access lifecycles for Agendei Quadras from the public reference set only.
It does not define private behavior or implementation detail.

## SM-OPS-001 — Facility Onboarding and Visibility Lifecycle

- Status: Inferred
- Confidence: Medium
- Lifecycle subject: Public facility registration, manager access, court setup, and player visibility
- Domain areas: Operations, Scheduling, Billing
- Related entities: `E-OPS-006`, `E-OPS-007`, `E-SCHED-001`, `E-SCHED-002`
- Related business rules: `BR-OPS-001`, `BR-OPS-002`, `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003`
- Related journeys: `J-MANAGER-001`, `J-MANAGER-002`, `J-PLAYER-001`
- Source reference: `01-product-overview.md`, `04-navigation.md`, `05-booking-lifecycle.md`, `19-manager-operations-overview.md`, `20-facility-onboarding-and-configuration.md`, `24-business-rules-overview.md`, `27-operations-business-rules.md`, `29-user-journeys-overview.md`, `31-manager-operations-journeys.md`, `35-domain-model-overview.md`, `36-scheduling-domain-model.md`, `39-operations-permissions-domain-model.md`
- Notes: Public docs confirm registration and setup, but the exact publish or review path that makes the court visible is not public.

### Conceptual States

| State | Status | Confidence | Meaning | Entry trigger | Exit trigger | Public unknowns |
|---|---|---|---|---|---|---|
| Not Registered | Inferred | Medium | The facility has not yet entered the public onboarding path. | The public registration flow has not started. | Manager uses the public registration CTA. | This is a baseline state inferred from the public flow. |
| Registration Started | Observed | High | The manager has begun the public signup path for the facility. | Manager uses the public registration CTA. | Facility registration is completed. | Exact mandatory fields are not public. |
| Facility Registered | Observed | High | The facility has been registered through the public site. | Registration is completed. | App Gestor access is granted. | Whether the facility is subject to review before access is public is not confirmed. |
| App Gestor Access Granted | Observed | High | The manager can use the manager surface after registration. | Registration and credentialing complete. | The manager configures the facility. | The exact moment access becomes available is not public. |
| Facility Configured | Observed | High | The court and related operational setup have been completed in the manager surface. | Manager configures the facility. | The court becomes visible to players. | Exact configuration screens are not public. |
| Visible to Players | Inferred | Medium | The court appears in App Agendei and can be discovered by players. | The setup path is complete. | Visibility changes in an unknown way. | Exact publish controls, review state, and ranking behavior are not public. |
| Visibility Suspended Unknown | Not publicly confirmed | Low | The public docs do not explain what happens if visibility is removed or suspended. | Visibility is turned off or blocked by an unpublicized condition. | Unknown. | No public evidence confirms a hidden or suspended state, but it is a reasonable open question. |

### Transitions

| From | To | Trigger | Condition | Outcome | Status | Confidence | Related rules | Related journeys | Notes |
|---|---|---|---|---|---|---|---|---|---|
| Not Registered | Registration Started | Manager uses the public registration CTA. | The facility has not yet been registered. | Public onboarding begins. | Observed | High | `BR-OPS-001` | `J-MANAGER-001` | The public site repeatedly invites the facility to register the quadra. |
| Registration Started | Facility Registered | Facility registration occurs. | The signup steps are completed. | The facility record exists in the public onboarding flow. | Observed | High | `BR-OPS-001`, `BR-PAYMENT-002`, `BR-PAYMENT-004` | `J-MANAGER-001` | The exact form fields are not public. |
| Facility Registered | App Gestor Access Granted | Manager receives access to App Gestor. | Registration and onboarding credentials are complete. | The manager can use the manager surface. | Observed | High | `BR-OPS-001`, `BR-PAYMENT-002`, `BR-PAYMENT-003` | `J-MANAGER-001` | The access timing is public for the described onboarding path. |
| App Gestor Access Granted | Facility Configured | Manager configures the court. | The manager surface is available. | The facility is set up for operations. | Observed | High | `BR-OPS-002`, `BR-OPS-003` | `J-MANAGER-002`, `J-MANAGER-003` | Public docs do not show the exact setup steps. |
| Facility Configured | Visible to Players | The court is made discoverable to players. | Visibility depends on onboarding and configuration. | The court appears in App Agendei. | Inferred | Medium | `BR-OPS-002`, `BR-BOOKING-001`, `BR-BOOKING-002`, `BR-BOOKING-003` | `J-MANAGER-002`, `J-PLAYER-001` | The exact publish control is not public. |
| Visible to Players | Visibility Suspended Unknown | Visibility is removed or blocked. | The public docs do not describe the suspension path. | Player visibility changes in an unknown way. | Not publicly confirmed | Low | `BR-OPS-002` | `J-MANAGER-002`, `J-PLAYER-001` | No public evidence confirms this state, but it remains an open question. |

### Public Unknowns
- Exact publish controls are not public.
- Whether a review step exists before player visibility is not public.
- Whether App Gestor access is immediate after registration is not public.
- Whether Agendei Pay activation is required for visibility is not public.
- Whether a hidden or suspended visibility state exists is not public.

## SM-ACCESS-001 — Shared Access Lifecycle

- Status: Inferred
- Confidence: Medium
- Lifecycle subject: Shared operational access for staff and partners
- Domain areas: Operations, Permissions, Scheduling
- Related entities: `E-OPS-001`, `E-OPS-002`, `E-OPS-003`, `E-OPS-004`, `E-OPS-005`
- Related business rules: `BR-OPS-003`, `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008`, `BR-OPS-010`
- Related journeys: `J-MANAGER-003`, `J-MANAGER-007`
- Source reference: `02-personas.md`, `03-modules.md`, `21-shared-management-and-permissions.md`, `22-plans-tiers-and-feature-packaging.md`, `27-operations-business-rules.md`, `29-user-journeys-overview.md`, `31-manager-operations-journeys.md`, `35-domain-model-overview.md`, `39-operations-permissions-domain-model.md`
- Notes: Public docs confirm shared access exists and that staff can manage schedules, but exact permission boundaries and revocation behavior are not public.

### Conceptual States

| State | Status | Confidence | Meaning | Entry trigger | Exit trigger | Public unknowns |
|---|---|---|---|---|---|---|
| Access Not Shared | Inferred | Medium | The facility has not yet delegated access to staff or partners. | Shared management has not been configured. | Manager prepares a delegated role. | This baseline state is inferred from the public flow. |
| Access Profile Created | Inferred | Medium | A delegated access profile exists conceptually. | Manager sets up shared access. | Access is shared with staff or partners. | Whether profiles are predefined or custom is not public. |
| Access Shared with Staff | Observed | High | An employee has been granted shared access. | Manager shares access with staff. | Staff can manage schedules or access is revoked. | Broader staff permissions are not public. |
| Access Shared with Partner | Observed | High | A partner or co-manager has been granted shared access. | Manager shares access with a partner. | Permission boundaries become relevant or access is revoked. | Exact partner rights are not public. |
| Staff Can Manage Schedules | Observed | High | Staff can use the app to manage schedules. | Staff access includes schedule permission. | The access is revoked or the role changes. | Whether staff can manage finance, coupons, or Agendei Pay is not public. |
| Permission Boundary Unknown | Not publicly confirmed | Low | The public docs do not expose the full permission matrix. | Staff and partner access are compared in practice. | Unknown. | Exact role hierarchy and inheritance rules are not public. |
| Access Revoked Unknown | Not publicly confirmed | Low | The public docs do not describe how access removal works. | The manager removes delegated access. | Unknown. | Revocation, deactivation, and audit behavior are not public. |

### Transitions

| From | To | Trigger | Condition | Outcome | Status | Confidence | Related rules | Related journeys | Notes |
|---|---|---|---|---|---|---|---|---|---|
| Access Not Shared | Access Profile Created | Manager prepares a delegated role. | Shared management is being configured. | A delegated profile exists conceptually. | Inferred | Medium | `BR-OPS-006`, `BR-OPS-008` | `J-MANAGER-007` | The public docs imply profile-based delegation. |
| Access Profile Created | Access Shared with Staff | Manager shares access with employees. | A staff profile is selected. | The employee receives delegated access. | Observed | High | `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-010` | `J-MANAGER-007` | Staff schedule access is the only confirmed staff permission. |
| Access Profile Created | Access Shared with Partner | Manager shares access with a partner. | A partner profile is selected. | The partner receives delegated access. | Observed | High | `BR-OPS-006`, `BR-OPS-008` | `J-MANAGER-007` | Exact partner rights are not public. |
| Access Shared with Staff | Staff Can Manage Schedules | Staff opens the app and manages schedules. | Schedule-management permission exists. | Staff can work the agenda. | Observed | High | `BR-OPS-007`, `BR-OPS-003` | `J-MANAGER-003`, `J-MANAGER-007` | Broader staff powers are not public. |
| Access Shared with Partner | Permission Boundary Unknown | Partner access is compared with staff access. | The role matrix is not public. | The exact boundary remains unknown. | Not publicly confirmed | Low | `BR-OPS-008` | `J-MANAGER-007` | The public docs do not expose the full matrix. |
| Access Shared with Staff | Access Revoked Unknown | Manager removes delegated access. | The revocation workflow is not public. | Access may be removed. | Not publicly confirmed | Low | `BR-OPS-006`, `BR-OPS-008` | `J-MANAGER-007` | No public detail on deactivation is available. |
| Access Shared with Partner | Access Revoked Unknown | Manager removes partner access. | The revocation workflow is not public. | Access may be removed. | Not publicly confirmed | Low | `BR-OPS-006`, `BR-OPS-008` | `J-MANAGER-007` | No public detail on deactivation is available. |

### Public Unknowns
- Exact staff and partner permission boundaries are not public.
- Whether permission profiles are predefined or custom is not public.
- Whether shared access includes finance or Agendei Pay controls is not public.
- Whether managers can revoke access without affecting existing bookings is not public.
- Whether revocation has audit or notification behavior is not public.
