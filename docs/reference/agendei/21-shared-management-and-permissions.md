# Shared Management and Permissions

## Scope
This document covers only publicly visible role and access behavior.
It does not assert a full internal RBAC model.

## Visible Roles
| Role | Role description | Publicly visible responsibilities | Inferred permissions | Confidence level | Unknowns |
|---|---|---|---|---|---|
| Manager / facility owner | The person responsible for the quadra operation. | Register the facility, configure visibility, manage schedules, bookings, finance, day use, cancellations, messages, and shared access. | Broad access across the public manager features. | High | Exact ownership rights, approval rights, and delegation limits are not public. |
| Staff / funcionário / colaborador | Employee who helps run the facility. | The public FAQ says employees can access the app to manage schedules. | Schedule access and routine operational tasks under shared management. | Medium | Whether staff can handle finance, payments, coupons, or account settings is not public. |
| Partner / sócio / co-gestor | Business partner who shares responsibility for the facility. | Public pages say management can be shared with partners and different access profiles can be created. | Shared operational access; exact scope is not public. | Medium | Exact co-owner rights, decision rights, and financial access are not public. |
| Central de atendimento | Support surface or service channel mentioned in the pricing page. | Public pricing page lists `Central de Atendimento` as a plan feature. | Support/help access is plausible, but the operational model is not public. | Low | It is not clear whether this is a human team, in-app support, or both. |
| Player / client | External user, not internal staff. | Finds courts, books slots, pays, invites friends, and sorts teams. | No internal management permissions are public. | High | Identity, login method, and any support-related rights are not public. |

## Shared Management
- Different access profiles: the public site says managers can create different access profiles. Observed.
- Access sharing with staff: the FAQ says employees also have access to manage schedules. Observed.
- Access sharing with partners: the public site says management can be shared with partners / `sócios`. Observed.
- Schedule management by employees if visible: yes, this is the one staff permission stated publicly. Observed.
- Relationship with multi-court management: the same public surface says one account can manage one or many courts, so shared access appears to sit on top of a multi-court operation. Inferred.
- What is observed: the public site names shared management, staff access, partner access, and schedule access.
- What is inferred: staff and partner access likely depends on profile-based permissions rather than a single all-or-nothing login.
- What is unknown: the exact role hierarchy, permission inheritance, and whether profiles are prebuilt or custom.

## Permission Areas
| Area | Manager | Staff | Partner/co-manager | Public evidence level | Notes |
|---|---|---|---|---|---|
| Schedule management | Observed | Observed | Inferred | Observed | Employees are explicitly said to manage schedules; partners are mentioned more generally. |
| Booking approval | Observed | Not publicly confirmed | Not publicly confirmed | Observed | Manager approval is public for local-payment requests. |
| Finance / cash flow | Observed | Not publicly confirmed | Not publicly confirmed | Observed | Finance is a public manager area, but role split is not shown. |
| Agendei Pay | Observed | Not publicly confirmed | Not publicly confirmed | Observed | Credentialing and activation are documented through the manager surface. |
| Coupon creation | Observed | Not publicly confirmed | Not publicly confirmed | Observed | Custom coupons are public in the advanced tier. |
| Day use management | Observed | Not publicly confirmed | Not publicly confirmed | Observed | Day use creation is public; role split is not. |
| Chat / messages | Observed | Not publicly confirmed | Not publicly confirmed | Observed | The public site shows a single communication channel, but not role boundaries. |
| Lessons / escolinha | Observed | Not publicly confirmed | Not publicly confirmed | Observed | The feature is public in the pricing page. |
| Tournament registration | Observed | Not publicly confirmed | Not publicly confirmed | Observed | The feature is public in the pricing page. |
| Staff control | Observed | Not publicly confirmed | Not publicly confirmed | Observed | `Controle de Funcionários` is public in the pricing page. |
| Plan management | Observed | Not publicly confirmed | Not publicly confirmed | Observed | The public site does not show any staff or partner control over subscription settings. |

## Staff Control
- Control of employees if visible: yes. `Controle de Funcionários` appears in the public pricing page, and the FAQ says employees can also access the app to manage schedules. Observed.
- Plan / tier relationship if visible: staff control is listed in the `Padrão` plan and inherited by `Avançado`. Observed.
- What staff can do if public: the public site only confirms schedule-management access.
- Unknowns: whether staff can approve bookings, manage finance, use Agendei Pay, create coupons, or edit plan settings.

## Not Publicly Observable
- Exact RBAC model.
- Exact permission toggles.
- Audit logs.
- Invitation workflow.
- Password and account lifecycle.
- Staff deactivation behavior.
- Partner ownership rights.
- Permission inheritance rules.
- Multi-facility access rules.
