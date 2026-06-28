# Plans, Tiers and Feature Packaging

## Scope
This file documents only publicly visible packaging and plan-related behavior.
It does not infer commercial terms beyond what is shown on the public pricing page and related public pages.

## Public Plans
The public pricing page is presented as `Copa Agendei Quadras` and shows three visible plans.
The page also advertises shared benefits above the cards: no per-client charge, free unlimited withdrawals, and no loyalty or penalty.

| Plan name | Visible price if public | Target usage if inferable | Included features | Missing / excluded features if public | Trial information if public | Confidence level | Notes |
|---|---|---|---|---|---|---|---|
| Inicial (`Essencial`) | `R$ 177,90/mês` or `R$ 151,21/mês` billed annually | Basic manager operation for a small or starting facility. Inferred. | Unlimited courts; unlimited bookings; digital account; cash flow; central de atendimento; shared page benefits like no per-client charge and free unlimited withdrawals. | The public card does not list staff control, lessons/escolinha, tournaments, custom coupons, material rental, billing generator, or AI management. | `Testar Grátis`; the public manager site also advertises 15 free days. | High | The page also says `Cobrado anualmente` and `15% OFF na primeira renovação`. |
| Padrão | `R$ 247,90/mês` or `R$ 210,71/mês` billed annually | Facility operation with delegated staff and lesson workflows. Inferred. | Everything from Inicial; staff control; lessons/escolinha; shared page benefits. | Tournament registration and custom coupon creation are not on this card; material rental, billing generator, and AI management are marked `Em breve`. | `Testar Grátis`; the public manager site also advertises free trial access. | High | The page labels this plan `Mais escolhido`. |
| Avançado | `R$ 317,90/mês` or `R$ 270,21/mês` billed annually | Facility operation with tournaments and promotional tooling. Inferred. | Everything from Padrão; tournament registration; custom coupon creation; shared page benefits. | `Gestão Inteligente com IA` is still marked `Em breve`; material rental and billing generator remain marked `Em breve` in the inherited lower-tier set. | `Testar Grátis`; the public manager site also advertises free trial access. | High | The page labels this plan `Completo`. |

## Feature Packaging
| Feature | Plan/tier visibility | Operational area | Status | Confidence | Notes |
|---|---|---|---|---|---|
| Scheduling / agenda | All tiers | Scheduling | Included | High | Public pages describe agenda control as a core function. |
| Online payment | All tiers; no separate tier break shown | Payments | Included | High | Public pages present payment online as part of the platform. |
| Agendei Pay | Platform-level; no separate tier break shown | Payments / settlement | Included | Medium | Public pages treat it as the payment layer rather than a separate add-on. |
| Cash flow | Inicial and above | Finance | Included | High | Listed on the Inicial card and inherited by higher tiers. |
| Multi-court management | All tiers | Operations | Included | High | The pricing page says `Quadras ilimitadas`. |
| Central de atendimento | Inicial and above | Support | Included | High | Publicly shown on the Inicial card. |
| Staff control | Padrão and Avançado | Operations | Tier-specific | High | Listed on the Padrão card. |
| Lessons / escolinha | Padrão and Avançado | Operations | Tier-specific | High | Listed on the Padrão card. |
| Tournament registration | Avançado | Operations / events | Tier-specific | High | Listed on the Avançado card. |
| Custom coupon creation | Avançado | Promotions | Tier-specific | High | Listed on the Avançado card. |
| Day use | Publicly visible on manager pages; no tier break shown on the pricing page | Day use | Not enough public detail | High | The feature is public, but the pricing page does not assign it to a tier. |
| Material rental | Padrão and Avançado | Ancillary revenue | Announced / Em breve | High | Marked `Em breve` on the pricing page. |
| Billing generator | Padrão and Avançado | Billing / collections | Announced / Em breve | High | Marked `Em breve` on the pricing page. |
| AI management | Avançado | Automation | Announced / Em breve | High | Marked `Em breve` on the pricing page as `Gestão Inteligente com IA`. |

## Relationship Between Plans and Operations
- Observed: the public pricing page packages the platform in progressive operational tiers rather than in isolated feature add-ons.
- Observed: the Inicial plan covers core booking, digital-account, cash-flow, support, and unlimited-court needs.
- Observed: the Padrão plan adds staff control and lesson/school management.
- Observed: the Avançado plan adds tournament registration and custom coupon creation.
- Observed: some features are explicitly marked `Em breve`, so the page separates available capabilities from announced ones.
- Inferred: the plan structure seems to broaden the operational surface as a facility becomes more administratively complex.

## Not Publicly Observable
- Billing cycle details beyond the annual-billing wording shown on the page.
- Cancellation of subscription.
- Upgrade / downgrade behavior.
- Usage limits.
- Court-count limits beyond `Quadras ilimitadas`.
- Staff limits.
- Transaction fees per plan.
- Plan-specific permissions.
- Exact release dates for announced features.
