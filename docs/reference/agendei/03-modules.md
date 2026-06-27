# Modules

The public site presents both top-level application surfaces and standalone feature cards.
This file documents both so the inventory stays complete without guessing beyond what is public.

## Top-Level Applications

### App Agendei Quadras
- Purpose: player-facing booking app
- Observed responsibilities: court discovery, slot selection, booking, payment, and match coordination
- Main visible features: search by location, choose day and time, book without calling the facility, pay by PIX or card, organize a match, invite friends, sort teams, browse without an account until booking is needed, app store availability
- Business value: drives demand and converts players into bookings
- Confidence: High

### App Gestor Agendei
- Purpose: facility operations app
- Observed responsibilities: manage bookings, court schedules, payments, cancellations, finance, day use, and shared access
- Main visible features: agenda control, multiple-court management, Agendei Pay integration, shared management with staff and partners, public onboarding to a digital account, feature cards for the operational modules below
- Business value: centralizes day-to-day operations and monetization
- Confidence: High

### Agendei Pay / Pagamento Online
- Purpose: digital account and payment layer
- Observed responsibilities: receive booking payments, handle PIX and card receipts, manage transfers, apply cancellation penalties
- Main visible features: conta digital, TED gratuita, PIX payments, card payments, liquid settlement to bank or digital account, cancellation-fee retention, separate pay-in-person versus pay-through-app flow
- Business value: captures and settles money from bookings
- Confidence: High

## Operational Modules

### Gestão de horários
- Purpose: core booking calendar
- Observed responsibilities: receive and create agendamentos avulsos and fixos (mensalistas), track available slots
- Main visible features: schedule creation, booking requests, confirmed slots
- Business value: core revenue engine
- Confidence: High

### Múltiplas quadras
- Purpose: manage more than one court from a single account
- Observed responsibilities: administer all courts in the facility
- Main visible features: one app or site manages all courts
- Business value: scales the product to multi-court operators
- Confidence: High

### Multa por cancelamentos
- Purpose: recover revenue from late cancellations
- Observed responsibilities: apply cancellation fees based on tolerance rules
- Main visible features: cancellation penalty, retained amount, automatic refund and repass logic
- Business value: protects revenue and discourages no-shows
- Confidence: High

### Chat de mensagens
- Purpose: direct communication channel between facility and client
- Observed responsibilities: message the client about bookings
- Main visible features: a single messaging channel in the app
- Business value: reduces reliance on phone calls and scattered messages
- Confidence: High

### Diária (Day Use)
- Purpose: day-based access product
- Observed responsibilities: manager creates day passes, client buys a daily reservation, system notifies the manager
- Main visible features: set name, days, courts, duration, price, payment form; customer selects a daily pass in App Agendei; push notification on purchase
- Business value: enables non-hourly sales and new revenue streams
- Confidence: High

### Gestão financeira / Fluxo de caixa
- Purpose: financial oversight of the facility
- Observed responsibilities: track revenues, expenses, profit, and cash flow
- Main visible features: cash-flow view in the plan page and financial management on the app
- Business value: gives operational visibility into the business
- Confidence: High

### Gestão compartilhada
- Purpose: shared administration across people and roles
- Observed responsibilities: create access profiles and share management with employees and partners
- Main visible features: different access profiles, shared control
- Business value: supports delegation and collaborative operation
- Confidence: High

### Central de Atendimento
- Purpose: support and assistance channel
- Observed responsibilities: included as a plan feature; no workflow is publicly observable
- Main visible features: listed in the `Inicial` plan as `Central de Atendimento`
- Business value: support for operators
- Confidence: Medium

### Controle de funcionários
- Purpose: staff access and control
- Observed responsibilities: manage employee access
- Main visible features: shown in the paid plan comparison
- Business value: lets the facility delegate tasks to staff
- Confidence: Medium

### Gestão de aulas e escolinha
- Purpose: manage lesson and school programs
- Observed responsibilities: visible in the plan comparison; no public workflow detail
- Main visible features: listed in the paid plan comparison
- Business value: supports recurring instruction programs
- Confidence: Medium

### Inscrição de torneios
- Purpose: tournament registration
- Observed responsibilities: visible in the plan comparison; no public workflow detail
- Main visible features: listed in the paid plan comparison
- Business value: supports event administration
- Confidence: Medium

### Cupons e descontos / Criação de cupons personalizados
- Purpose: create and apply promotional discounts
- Observed responsibilities: the manager can create custom coupons; players can use coupons from the court
- Main visible features: discount coupons for bookings, custom coupon creation
- Business value: promotions, acquisition, and loyalty
- Confidence: High

### Aluguel de materiais
- Purpose: material rental
- Observed responsibilities: visible as a coming-soon plan item
- Main visible features: shown as `Aluguel de Materiais (Em breve)`
- Business value: potential ancillary revenue
- Confidence: High

### Gerador de cobranças
- Purpose: create charges
- Observed responsibilities: visible as a coming-soon plan item
- Main visible features: shown as `Gerador de Cobranças (Em breve)`
- Business value: billing and collections support
- Confidence: High

### Gestão inteligente com IA
- Purpose: intelligent management assistance
- Observed responsibilities: visible as a coming-soon plan item
- Main visible features: shown as `Gestão Inteligente com IA (Em breve)`
- Business value: future automation or decision support, but not yet publicly detailed
- Confidence: High
