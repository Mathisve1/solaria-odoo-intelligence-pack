# Marketing Automation (`marketing_automation`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `marketing_automation` |
| Display name | Marketing Automation |
| Source origin | **Enterprise** (extends Community `mass_mailing`) |
| Version scope | Odoo 19.0 |
| Dependencies | `mass_mailing` (+bridges: `marketing_automation_crm`, `_sms`, `_website_sale`, `_whatsapp`) |
| Functional domain | Marketing automation / journeys |
| Confidence | High for structures; deliverability and trigger timing need live validation |

## Business purpose
Turn one-shot mailings into orchestrated journeys: visual campaigns where target audiences (any Odoo record filter) enter on triggers and flow through timed/conditional activity trees (emails, SMS/WhatsApp via bridges, server actions) with per-node KPIs and A/B patterns — marketing logic on live ERP data.

## Main users / personas
Marketing managers (campaign design), demand gen (nurture flows), sales ops (handoff rules), CRM owners (data hygiene journeys), compliance (consent).

## Business problems solved
- Manual campaign sequencing → `marketing.campaign` (**draft → running → stopped**) with `marketing.activity` trees (delays, parent/child triggers, conditions).
- Blind sends → `marketing.trace` per participant/activity (**scheduled → processed → rejected/canceled/error**) — measurable at every node.
- Segments detached from reality → audiences are domain filters on live models (leads, customers, applicants… any model with the right setup — validate model coverage live).
- Risky launches → test mode (`marketing.campaign.test`, participant simulation).

## Main business processes (source-verified)
1. Design: pick target model+filter → build activity tree (mail/action nodes, delays, branch on opened/clicked/replied patterns — validate exact branch triggers live).
2. Test: test-participant run before launch.
3. Run: participants (`marketing.participant`: running → completed/unlinked) enter per trigger; traces execute.
4. Learn: per-node KPIs, link tracker menu, campaign reporting.

## Key functional capabilities
Multi-channel via bridges (SMS, WhatsApp E, social context), server-action nodes (do things in the ERP, not just send — e.g., create activity, update field), UTM integration (campaign/source), unsubscribe/blacklist handling from mass_mailing foundations.

## Fit with other modules
`mass_mailing` (content/sending engine, lists, consent), `crm` (lead journeys + `marketing_automation_crm`), `website_sale` (abandoned-cart style journeys via bridge), `whatsapp` (E), `sms`, events/social siblings; data feeds everything (segments on live fields).

## Community fallback
`mass_mailing` (one-shot campaigns, lists, basic automation-rule assists) — honest positioning: newsletters yes, journeys no.

## Configuration opportunities
Campaign templates, audience filters, sending domains/identities, consent/blacklist policies, UTM conventions.

## Studio / automation opportunities
Journeys ARE the automation layer here. Complement with automation rules for data hygiene (feeding segments). Studio: segment-driver fields (persona, lifecycle stage) — governed taxonomy.

## Custom development triggers
Real-time behavioral triggers from external products (event-stream ingestion), advanced personalization engines, multi-brand consent centers.

## External integration triggers
Corporate marketing clouds (boundary: ERP-data journeys in Odoo, brand campaigns there), CDPs, deliverability/ESP infrastructure choices.

## Common client questions
"Like HubSpot/Marketo?" — journey mechanics on ERP data: yes; content-marketing suite depth (landing-page analytics ecosystems, scoring suites): calibrate honestly. · "Trigger on any data?" — target models+filters are powerful; validate the specific model/event live. · "GDPR consent?" — mass_mailing consent/blacklist foundations + process design. · "WhatsApp journeys?" — bridge exists (E); commercial WhatsApp terms apply.

## Fit-gap considerations
Best where journeys act on ERP truth (customers who actually bought X, subscriptions lapsing, applicants idle). Gap zone: deep martech (attribution suites, ad orchestration). The server-action node is the sleeper feature — journeys that *do* ERP work, not just send mail.

## Deloitte demo angles
1. **Journey on truth:** "customers who bought X but not Y" filter → 3-node nurture with delay + branch → show per-node KPIs.
2. **Ops journey:** lapsing subscription → email + CS activity created automatically (server action node).
3. Test-mode walkthrough (governance credibility).

## Implementation watch-outs
- Sending domain/deliverability setup (SPF/DKIM) before any volume.
- Consent data migration and policy enforcement first.
- Segment taxonomy governance (fields that drive filters).
- Journey sprawl: review cadence for running campaigns.

## Risks and assumptions
Structures verified (campaign/activity/participant/trace state machines). Branch trigger specifics, model coverage and deliverability are runtime → validate. Enterprise licensing required.

## Validation checklist
- [ ] Deliverability infrastructure configured and warmed
- [ ] Consent/blacklist policy implemented and tested
- [ ] Two pilot journeys designed on real segments with KPIs
- [ ] Governance: who approves/reviews running journeys
