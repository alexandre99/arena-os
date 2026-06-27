# Engagement, Coupons and Match Organization

## Scope
This document covers customer engagement features visible in public sources.
It focuses on what the player-facing and manager-facing public pages expose.

## Engagement Capabilities Inventory
| Capability name | Description | User/persona involved | Public evidence summary | Business value | Confidence level | Notes |
|---|---|---|---|---|---|---|
| Inviting friends | The player can invite other people to join the match. | Player, invited friend | App Agendei public page lists friend invitations as a visible feature. | Makes the booking social and helps fill the court. | High | The invite transport and invitee identity model are not public. |
| Match organization | The player can organize the match around the booking. | Player | App Agendei public page describes match organization as part of the player flow. | Reduces coordination work for the customer. | High | Public pages show the feature, but not the workflow details. |
| Team sorting | The app can sort teams for the match. | Player and match participants | App Agendei public page explicitly mentions team sorting. | Simplifies game setup and reduces manual coordination. | High | The algorithm or rules are not public. |
| Discount coupons | Players can use discount coupons from the court. | Player, manager | Public product pages mention discount coupons in the booking context. | Supports promotions and repeat usage. | High | Exact coupon entry and validation are not public. |
| Custom coupon creation | Managers can create personalized coupons. | Manager | The public plan page lists custom coupon creation in the advanced tier. | Supports targeted promotions and retention offers. | High | The public page ties it to the Avancado plan. |
| Day use as engagement and revenue product | The facility can sell a daily reservation as a separate purchase path. | Player, manager | The day-use page describes a separate purchase flow and manager notification. | Adds a flexible revenue product and a low-friction access option. | High | This is not the same as a normal hourly booking. |
| Monthly players / mensalistas as retention model | The manager can manage recurring fixed bookings for monthly customers. | Player, manager | Scheduling docs and public manager pages mention `mensalistas` and fixed bookings. | Creates recurring relationships and schedule stability. | High | Public pages do not show a dedicated subscription billing workflow. |
| Tournaments | Tournament registration appears in the public plan comparison. | Manager, participants | The plan page lists tournament registration as a feature. | Supports events and recurring customer engagement. | Medium | The participant lifecycle is not publicly visible. |
| Lessons / escolinha | Lesson and school-program management appears in the public plan comparison. | Manager, students | The plan page lists lesson and school management as a feature. | Supports recurring instruction programs and repeat attendance. | Medium | The public workflow is not visible. |
| Testimonials / social proof | Public pages use testimonials from players and facility operators. | Prospect, player, manager | Landing pages include testimonial blocks and social proof text. | Reinforces trust and conversion. | High | This is marketing support, not a customer workflow. |

## Coupons and Discounts
- Who can create coupons if public: managers can create custom coupons.
- Who can use coupons if public: players can use court discount coupons.
- Where coupons appear in the lifecycle: the public pages indicate they are part of the booking context, but the exact entry point is not shown.
- Whether coupons relate to bookings: yes; the public pages frame them as booking discounts.
- Whether custom coupons are tied to a plan tier if public: yes; custom coupon creation is listed in the Avancado plan.
- Unknown rules: limits, stacking, validity windows, targeting, one-time use, court-specific rules, and day-use applicability.

## Match Organization
- Inviting friends: observed; the player can invite friends from the app.
- Sorting teams: observed; the app can sort teams for the match.
- Relationship with booking: inferred; these features appear in the booking-oriented player flow rather than as a separate social app.
- What is observed: the public pages explicitly mention friend invitations and team sorting.
- What is inferred: the match is likely organized around a booking or court reservation.
- What is unknown: invite delivery mechanism, friend list storage, whether non-bookers can join, and the exact team-sorting rules.

## Retention Concepts
| Concept | Status | Confidence | Notes |
|---|---|---|---|
| Fixed bookings / agendamentos fixos | Observed | High | Public scheduling material and manager pages mention fixed bookings. |
| Mensalistas | Observed | High | Public material explicitly names monthly players / mensualistas. |
| Coupons | Observed | High | Discount coupons and custom coupons are public. |
| Lessons / escolinha | Observed | Medium | The feature is public in the plan comparison, but the retention flow is not visible. |
| Tournaments | Observed | Medium | The feature is public in the plan comparison, but the participant lifecycle is not visible. |
| Day use | Observed | High | The product has a separate day-use purchase flow. |
| Chat | Observed | High | The public site names a messaging channel. |

## Not Publicly Observable
- Coupon limits.
- Coupon stacking.
- Campaign targeting.
- Loyalty points.
- Referral mechanics.
- Customer segmentation.
- Ranking.
- Social graph behavior.
- Friend list behavior.
- Tournament participant lifecycle.
