# Navigation

This file maps the public navigation only.
Anything that happens after authentication or inside the logged-in apps is not documented unless it is publicly visible.

## Global Header Navigation

### App Gestor pages
- `App Agendei`
- `Como Funciona?`
- `Pagamento Online`
- `Contato`
- `Ver Plano`
- `Blog`
- `Cadastrar minha quadra`

### App Agendei page
- `Passo a Passo`
- `Novidades`
- `Galeria`
- `Depoimentos`
- `FAQ`
- `Contato`
- `BAIXAR`
- `Cadastre sua quadra`

### Day Use page
- `App Gestor`
- `Funcionalidades`
- `Pagamento Online`
- `Contato`
- `Ver Plano`
- `Blog`
- `Cadastrar minha quadra`

## Secondary Sections

### App Gestor landing page
- `Modernize a sua quadra esportiva`
- `Novidades`
- `Funcionalidades`
- `Por que escolher o Agendei Quadras?`
- `Já alcançamos`
- `Feito para você`
- `Depoimentos`
- `Blog`
- `FAQ`

### App Agendei landing page
- `Passo a passo`
- `Novidades`
- `Galeria`
- `Depoimentos`
- `BAIXE O APP GRÁTIS`
- `FAQ`

### Agendei Pay page
- `A Conta Digital da sua Quadra`
- `A Solução Financeira para sua Quadra Esportiva`
- `Conheça todas as funcionalidades do Agendei Pay`
- `Como funciona o Pagamento`
- `Como funcionam os Repasses`
- `Passo a passo`
- `Perguntas Frequentes`

### Diária page
- `O que é Diária?`
- `Como funciona a venda de Diária`
- `Funcionalidades do App`
- `Depoimentos`

## Observable Cross-Links
- `App Gestor` page points to `App Agendei` and `Pagamento Online`
- `App Agendei` page points to `Conheça o Gestor Agendei`
- `Pagamento Online` page points to `Conhecer o App Para Clientes`
- `Diária` page points to `Cadastrar Minha Quadra`
- `Ver Plano` leads to the public pricing and comparison page

## Main Observed Journeys

### Player journey
- Open `App Agendei`
- Find a court by location
- Choose the day and time
- Book the slot
- Pay by PIX or card, or request local payment
- If the payment is immediate, the booking confirms automatically
- If the payment is local, the manager must accept and confirm the request
- Optionally invite friends and sort teams

### Facility journey
- Open `App Gestor` or the public manager pages
- Register the quadra from the site
- Receive access to the manager app
- Configure the quadra so it is visible in `App Agendei`
- Create the Agendei Pay account through credenciamento
- Activate PIX and card receipts
- Manage schedules, cancellations, day use, finance, and shared access

### Day Use journey
- Create the daily product in App Gestor
- Set name, day, courts, duration, price, and payment form
- The player buys the daily access in App Agendei
- The manager receives a push notification

## Relationship Between Modules
- `App Agendei` is the demand side for players
- `App Gestor` is the operations side for facilities
- `Agendei Pay` handles the money movement behind online bookings
- `Gestão de horários`, `Múltiplas quadras`, `Multa por cancelamentos`, `Chat de mensagens`, `Diária`, `Gestão financeira`, `Gestão compartilhada`, `Central de Atendimento`, `Controle de funcionários`, `Gestão de aulas e escolinha`, `Inscrição de torneios`, `Cupons e descontos`, `Aluguel de materiais`, `Gerador de cobranças`, and `Gestão inteligente com IA` are the visible operational areas exposed through the manager surface

## Not Publicly Observable
- Internal menus after sign-in inside `App Agendei`. Not publicly observable.
- Internal menus after sign-in inside `App Gestor`. Not publicly observable.
- Any API call sequence or backend processing. Not publicly observable.
