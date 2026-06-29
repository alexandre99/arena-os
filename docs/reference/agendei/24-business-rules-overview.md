# Business Rules Overview

## Scope
This document consolidates business rules from the existing Agendei public-reference docs only.
It is limited to what is visible in the public reference set and separates observed facts from inferred rules.
It does not define Arena OS behavior.

## Source Documents

### Product overview
- `01-product-overview.md`
- `02-personas.md`
- `03-modules.md`
- `04-navigation.md`

### Scheduling
- `05-booking-lifecycle.md`
- `06-scheduling-capabilities.md`
- `07-scheduling-entities.md`
- `08-scheduling-open-questions.md`

### Billing
- `09-payments-overview.md`
- `10-agendei-pay.md`
- `11-cancellation-penalties-and-refunds.md`
- `12-financial-capabilities.md`
- `13-payments-open-questions.md`

### CRM
- `14-customer-relationship-overview.md`
- `15-client-profile-and-history.md`
- `16-communication-and-chat.md`
- `17-engagement-coupons-and-match-organization.md`
- `18-crm-open-questions.md`

### Manager operations
- `19-manager-operations-overview.md`
- `20-facility-onboarding-and-configuration.md`
- `21-shared-management-and-permissions.md`
- `22-plans-tiers-and-feature-packaging.md`
- `23-manager-operations-open-questions.md`

## Rule Categories
- Booking rules: discovery, slot selection, booking creation, confirmation, recurring bookings, and cancellation behavior before money movement.
- Payment rules: payment methods, settlement timing, repasses, fees, coupons, refunds, and financial behavior.
- Cancellation and refund rules: late-cancellation tolerance, penalty percentages, refund splits, and retained-value handling.
- Day use rules: the separate daily purchase and reservation product.
- Customer/CRM rules: customer identity, profile history, notifications, chat, and match-related customer interactions.
- Communication rules: message flow, booking notifications, and manager alerts.
- Manager operation rules: onboarding, court visibility, schedule control, finance, and daily administration.
- Permission/shared-management rules: staff access, partner access, profile-based control, and role boundaries.
- Plan/tier rules: capability packaging, tier visibility, and announced features.

## Cross-Domain Dependencies

| Dependency | Related rule IDs | Confidence | Notes |
|---|---|---|---|
| Booking confirmation depends on payment method | `BR-BOOKING-004`, `BR-BOOKING-005`, `BR-BOOKING-006`, `BR-BOOKING-007`, `BR-PAYMENT-005`, `BR-PAYMENT-006`, `BR-PAYMENT-007` | High | PIX and card confirm immediately; local payment waits for manager acceptance. |
| Day use depends on a manager-created product | `BR-BOOKING-012`, `BR-BOOKING-013`, `BR-BOOKING-014` | High | The daily product must exist before the player can buy it, and the manager receives the sale notification. |
| Cancellation penalty depends on timing and configured percentage | `BR-BOOKING-015`, `BR-BOOKING-016`, `BR-PAYMENT-011`, `BR-PAYMENT-012`, `BR-PAYMENT-013` | High | The public example shows the 8h / 20% split, while the retained-value destination remains ambiguous. |
| Shared management depends on onboarding and profile-based access | `BR-OPS-001`, `BR-OPS-006`, `BR-OPS-007`, `BR-OPS-008` | High | Access sharing sits on top of facility registration and manager-side profile control. |
| Custom coupon creation depends on plan visibility | `BR-OPS-011`, `BR-OPS-012` | High | The feature is publicly tied to the Avancado tier and is not shown as a standalone add-on. |
| Match organization depends on the player booking context | `BR-OPS-015`, `BR-OPS-017`, `BR-OPS-018` | Medium | Friend invitations and team sorting appear in the player flow rather than as a separate product surface. |
| Financial visibility depends on Agendei Pay activation and manager packaging | `BR-PAYMENT-001`, `BR-PAYMENT-002`, `BR-OPS-004`, `BR-OPS-005`, `BR-OPS-009` | Medium | Money movement becomes operational once the digital account is created and enabled. |

## Rule Confidence Summary

| Area | Number of observed rules | Number of inferred rules | Number of not publicly confirmed rules | Main uncertainty |
|---|---|---|---|---|
| Scheduling | 16 | 0 | 0 | Exact reschedule, no-show, and cancellation edge-case behavior. |
| Billing | 16 | 1 | 1 | Exact retained-amount destination, payout exceptions, and future announced feature scope. |
| Operations | 9 | 2 | 0 | Exact publish/visibility workflow and onboarding/configuration details. |
| Permissions | 2 | 1 | 0 | Exact staff and partner permission boundaries and revocation behavior. |
| CRM | 1 | 1 | 0 | Customer history visibility, profile fields, and chat retention scope. |
| Engagement | 2 | 0 | 0 | Invite delivery and team-sorting mechanics. |

## Not in Scope
This document does not define Arena OS behavior, database schema, APIs, architecture, implementation details, or product redesign.
