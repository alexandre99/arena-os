# Business Rules Open Questions

## Purpose
This file tracks rule-level uncertainties that remain after consolidating the public Agendei reference docs.
It is limited to public-reference gaps and does not rely on private sources.

## Booking Rule Questions
- What exact booking statuses exist between request, confirmation, cancellation, and refund?
- Can the player cancel directly, or must the facility process the cancellation?
- What exact screen handles local-payment acceptance, and what is the manager action that confirms it?
- Can bookings be rescheduled without triggering a cancellation penalty?
- How are no-shows treated relative to cancellations?
- Does day use share the same status model as hourly reservations?

## Payment Rule Questions
- Does PIX use QR code, copy-and-paste, or both?
- Is card support limited to credit card, or does it also include debit or installments?
- Can one booking use more than one payment method?
- Do weekend settlement rules apply only to PIX, or also to card?
- What exact payout exceptions or manual withdrawal constraints exist?
- How are chargebacks or disputes handled?

## Cancellation and Refund Rule Questions
- Can the manager change the tolerance window or penalty percentage?
- Is the penalty applied automatically or manually?
- Are refunds immediate for every payment path, or only for some methods?
- Does rescheduling avoid the cancellation penalty?
- What exactly happens to the retained portion after a cancellation?

## Day Use Rule Questions
- Does day use block court availability inside the same agenda as hourly bookings?
- Can a day use product be edited after publication?
- Does a day use sale share the same booking-status model as an hourly reservation?
- Can the player buy day use without first moving through the standard booking flow?

## CRM and Communication Rule Questions
- Is chat per booking or per customer?
- Do staff and partners see messages?
- What customer history screens exist for bookings, payments, cancellations, and day use?
- Is booking history visible to players, managers, or both?
- Are notifications push, email, WhatsApp, or in-app only?
- How do friend invitations and team sorting work internally?

## Operations and Permission Rule Questions
- Which permissions can staff receive beyond schedule access?
- Which permissions can partners or co-managers receive?
- Are access profiles predefined or custom?
- Can a manager revoke access without affecting bookings?
- Does shared management include Agendei Pay and finance controls?
- What exact court fields exist in the manager setup flow?

## Plan and Tier Rule Questions
- Is billing monthly, annual, or both in practice?
- Does the free trial always last 15 days?
- Are announced features available now or only later?
- Are plan-specific permissions visible to managers?
- Do higher tiers always include lower-tier features?
- Is central de atendimento human-assisted, self-service, or both?

## Prioritized Investigation List

| Priority | Question | Why it matters | Related area | Suggested future source |
|---|---|---|---|---|
| High | What exact booking statuses exist between request, confirmation, cancellation, and refund? | This determines how the booking lifecycle is actually represented to users and managers. | Booking | Authenticated walkthrough or product video |
| High | What exact screen handles local-payment acceptance, and what is the manager action that confirms it? | This is the most important visible branch of the booking flow for pay-at-facility scenarios. | Booking | Authenticated walkthrough or demo call |
| High | Can bookings be rescheduled without triggering a cancellation penalty? | This affects customer experience and the meaning of the penalty rule. | Cancellation and Refund | Authenticated walkthrough or user interview |
| High | What exactly happens to the retained portion after a cancellation? | The public docs show the split, but not the final allocation of the retained value. | Cancellation and Refund | Public support article or authenticated walkthrough |
| High | Which permissions can staff and partners receive beyond schedule access? | This determines delegation boundaries and security. | Operations and Permission | Authenticated walkthrough |
| High | Does shared management include Agendei Pay and finance controls? | This determines whether shared users can touch money movement or only schedules. | Operations and Permission | Demo call or authenticated walkthrough |
| High | What exact meaning does mensualista have in practice? | It defines the recurring-customer model and whether it is calendar-based, billing-based, or both. | Booking | Demo call or product video |
| Medium | Are coupons limited by date, court, player, or number of uses? | This affects promotion rules and discount behavior. | CRM and Communication | Public support article or authenticated walkthrough |
| Medium | What customer history screens exist for bookings, payments, cancellations, and day use? | This determines how customers and managers review past interactions. | CRM and Communication | Authenticated walkthrough or product video |
| Medium | Is billing monthly, annual, or both in practice? | This affects interpretation of the public pricing page. | Plan and Tier | Public FAQ page or demo call |
| Medium | Is central de atendimento human-assisted, self-service, or both? | This determines whether the feature is a team, a channel, or both. | Operations and Permission | Public support article, app store screenshots, or user interview |
| Low | How do friend invitations and team sorting work internally? | It clarifies how the match-organization feature is actually executed. | CRM and Communication | Product video or user interview |
| Low | What are the exact notification channels for booking and day-use events? | It determines whether alerts are in-app, push, email, WhatsApp, or mixed. | CRM and Communication | Public FAQ page or app store screenshots |

