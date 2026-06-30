# Agendei Quadras Reference

## Purpose
This folder documents Agendei Quadras as a public reference product for functional reverse engineering.
It captures only what is visible on public pages and avoids authentication, private APIs, source code, architecture, or implementation detail.

## Scope
- Public website and landing pages
- Public app surfaces and visible feature descriptions
- Public FAQ, CTAs, screenshots, and app store links
- Observable booking, payment, onboarding, and management flows
- No private or authenticated behavior
- No product redesign, feature comparison, or improvement proposals

## Source Links
- [App Gestor Agendei](https://www.agendeiquadras.com.br/appGestor/)
- [App Agendei Quadras](https://www.agendeiquadras.com.br/appAgendei/)
- [Pagamento Online | Agendei Pay](https://www.agendeiquadras.com.br/appGestor/pagamento_online.html)
- [Diária (Day Use) | Gestor Agendei](https://www.agendeiquadras.com.br/diaria.html)
- [Copa Agendei Quadras | Promoção](https://www.agendeiquadras.com.br/planos.html)

## Documentation Structure
- `REFERENCE-SUMMARY.md` - executive summary and single entry point for the reference set
- `01-product-overview.md` - product purpose, audience, positioning, operating goals, and visible applications
- `02-personas.md` - visible personas, inferred permissions, and confidence levels
- `03-modules.md` - visible modules and their public responsibilities
- `04-navigation.md` - public navigation structure and observed user journeys
- `05-booking-lifecycle.md` - player and facility booking lifecycle, confirmation paths, and cancellation behavior
- `06-scheduling-capabilities.md` - public scheduling capability inventory and classification
- `07-scheduling-entities.md` - conceptual scheduling entities and their relationships
- `08-scheduling-open-questions.md` - public evidence gaps and follow-up questions
- `09-payments-overview.md` - public payment surfaces, methods, and booking confirmation impact
- `10-agendei-pay.md` - Agendei Pay positioning, digital account, PIX/card behavior, and repasses
- `11-cancellation-penalties-and-refunds.md` - public cancellation penalty model and refund behavior
- `12-financial-capabilities.md` - public financial feature inventory and conceptual entities
- `13-payments-open-questions.md` - payment-related evidence gaps and follow-up questions
- `14-customer-relationship-overview.md` - public customer relationship surfaces, concepts, and lifecycle
- `15-client-profile-and-history.md` - client identity, visible profile attributes, and history behavior
- `16-communication-and-chat.md` - public communication channels, chat behavior, and notification patterns
- `17-engagement-coupons-and-match-organization.md` - engagement features, coupons, retention concepts, and match organization
- `18-crm-open-questions.md` - CRM-related evidence gaps and open questions
- `19-manager-operations-overview.md` - manager-side operating model, responsibilities, and lifecycle
- `20-facility-onboarding-and-configuration.md` - onboarding, visibility, court configuration, and Agendei Pay setup
- `21-shared-management-and-permissions.md` - public role model, shared access, and permission areas
- `22-plans-tiers-and-feature-packaging.md` - public plans, tier packaging, and feature visibility
- `23-manager-operations-open-questions.md` - manager-operations evidence gaps and follow-up questions
- `24-business-rules-overview.md` - consolidated business-rules index, scope, dependencies, and confidence summary
- `25-booking-business-rules.md` - booking, scheduling, day use, and cancellation rules
- `26-payment-business-rules.md` - payment, Agendei Pay, settlement, refunds, coupons, and financial behavior
- `27-operations-business-rules.md` - onboarding, permissions, shared management, and plan-tier rules
- `28-business-rules-open-questions.md` - consolidated rule-level uncertainties and prioritized follow-up questions
- `29-user-journeys-overview.md` - consolidated journey inventory, dependencies, and source map
- `30-player-booking-journeys.md` - player-side booking journeys
- `31-manager-operations-journeys.md` - manager-side operations journeys
- `32-payment-and-cancellation-journeys.md` - payment, settlement, repass, refund, and cancellation journeys
- `33-engagement-and-crm-journeys.md` - engagement, communication, and CRM journeys
- `34-user-journeys-open-questions.md` - consolidated journey uncertainties and prioritized investigation list
- `35-domain-model-overview.md` - consolidated conceptual domain model overview
- `36-scheduling-domain-model.md` - scheduling domain entities, relationships, and unknowns
- `37-billing-domain-model.md` - billing and payment domain entities, relationships, and unknowns
- `38-crm-engagement-domain-model.md` - CRM and engagement domain entities, relationships, and unknowns
- `39-operations-permissions-domain-model.md` - operations and permissions domain entities, relationships, and unknowns
- `40-domain-model-open-questions.md` - consolidated domain-model uncertainties and prioritized investigation list
- `41-state-machines-overview.md` - consolidated conceptual lifecycle inventory, dependencies, and scope boundaries
- `42-booking-state-machine.md` - conceptual booking lifecycle
- `43-payment-state-machine.md` - conceptual payment, settlement, and local-payment lifecycles
- `44-cancellation-refund-state-machine.md` - conceptual cancellation, penalty, and refund lifecycle
- `45-day-use-state-machine.md` - conceptual day-use product and purchase lifecycle
- `46-operations-access-state-machine.md` - conceptual facility visibility and shared-access lifecycles
- `47-state-machines-open-questions.md` - consolidated state-machine uncertainties and prioritized investigation list
