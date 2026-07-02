# CRM (`crm`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `crm` |
| Display name | CRM |
| Source origin | **Community** (Enterprise extends via `crm_enterprise`, `ai_crm`, `voip_crm`, `social_crm`, `appointment_crm`, `marketing_automation_crm`) |
| Version scope | Odoo 19.0 |
| Dependencies | `sales_team`, `mail`, `calendar`, `contacts`, `utm`, `phone_validation`, `digest`, `resource` |
| Functional domain | CRM |
| Confidence | High for structures (source-verified); behavior details need demo validation |

## Business purpose
Manage the demand funnel: capture leads from any channel, qualify them into opportunities, drive them through a staged pipeline with disciplined follow-up, and convert them into customers and quotations — with revenue expectation visible at every step.

## Main users / personas
Sales reps (own pipeline), sales team leads, sales/commercial directors (forecast, win rates), marketing (lead handover, UTM attribution), inside sales/SDRs (qualification).

## Business problems solved
- Leads scattered across inboxes and spreadsheets; no follow-up discipline (activities enforce next steps).
- No forecast reliability (staged pipeline with expected revenue and probability, incl. predictive scoring).
- No lead-source ROI visibility (UTM tracking built in via `utm.mixin` on `crm.lead`).
- Slow lead response (assignment rules + daily assignment cron are standard).

## Main business processes
1. **Lead capture** — manual, email gateway, website forms (`website_crm`), livechat; deduplication support.
2. **Qualification** — lead → opportunity conversion (`type` field lead/opportunity; partner matching/creation).
3. **Pipeline management** — configurable stages (`crm.stage`), kanban-first UX, activities as the follow-up engine.
4. **Win/loss** — won/lost status with lost reasons (`crm.lost.reason`) feeding win-rate analysis.
5. **Assignment** — team- and rule-based lead distribution (cron "CRM: Lead Assignment").
6. **Forecast & analysis** — pipeline analysis pivots, activity reports, expected revenue by close date.

## Key functional capabilities (source-verified structures)
- `crm.lead` is one model for both leads and opportunities (70+ fields incl. tracked stage, revenue, probability, contact data, UTM fields).
- Predictive lead scoring: `crm.lead.scoring.frequency` + daily recompute cron — standard Community, configuration-activated.
- Recurring revenue plans on opportunities (`crm.recurring.plan`) for MRR-style pipelines.
- Lost reasons, tags, priorities; multi-team with member assignment quotas.
- Meetings integration (calendar), phone/email state validation fields.

## Fit with other modules
- `sale`/`sale_crm`: opportunity → quotation with attribution; `sales_team` is shared with Sales.
- `mail`: chatter, activities, email gateway are the process backbone.
- `website_crm` (forms), `mass_mailing`/`marketing_automation` (E) for nurture, `ai_crm` (E) for AI lead creation, `voip` (E) for calling, `appointment` (E) meeting booking.

## Standard in 19.0 (Community)
Pipeline, stages, activities, lead/opportunity split, scoring, assignment rules, lost reasons, reporting pivots, email integration, UTM attribution. The lead layer itself is toggled by configuration (Leads setting / "Show Lead Menu" group).

## Enterprise-specific additions
Extended reporting views (`crm_enterprise`), AI lead creation from emails/livechat (`ai_crm`, `ai_crm_livechat`), VoIP calling, social lead capture, automation journeys, appointment-to-lead. Tag these as Enterprise in client conversations.

## Configuration opportunities
Stages per team, lost reasons, scoring fields selection, assignment rules/quotas, activity types & plans, email aliases per team, lead enrichment settings (IAP), recurring revenue plans.

## Studio / automation opportunities
- Automation rules (Community `base_automation`): SLA-style escalations ("no activity in 5 days → alert manager"), auto-tagging, stage-entry notifications.
- Studio (E): extra qualification fields, industry-specific lead layouts — govern field sprawl.
- AI fields / AI server actions (E): summarize lead context, draft responses (validate live).

## Custom development triggers
Genuine scoring algorithms beyond the native predictive model; complex territory/quota engines; integrations with proprietary lead sources at volume. Challenge anything else first.

## External integration triggers
Marketing clouds (if the client insists on keeping one), external data providers beyond IAP enrichment, telephony platforms not covered by VoIP (E).

## Common client questions
"Can leads auto-route by region/product?" (yes — assignment rules, validate rule expressiveness live) · "Duplicate handling?" (dedup assistant + merge; test on real data) · "Forecasting?" (expected revenue + probability + pivots; Enterprise adds nicer analytics) · "Can we score leads?" (native predictive scoring — configuration).

## Fit-gap considerations
- CRM fit is usually high; gaps concentrate in exotic scoring, quota/commission (→ `partner_commission` E or custom), and marketing-suite expectations.
- If the client compares to Salesforce: position process discipline + ERP continuity (lead→cash in one platform) rather than feature parity.

## Deloitte demo angles
1. **Speed story:** email arrives → lead auto-created → activity scheduled → drag to stage → quotation in 3 clicks (with `sale`).
2. **Manager story:** pipeline analysis pivot; lost-reason pareto; team assignment fairness.
3. **Enterprise uplift:** AI lead from livechat transcript; call from the lead (VoIP); nurture journey handoff — label as Enterprise.

## Implementation watch-outs
- Stage design ≠ methodology redesign: 5–7 stages max, exit criteria documented.
- Legacy lead import: quality-gate before import; dead leads poison scoring.
- Won/lost semantics vs stage semantics — train explicitly (source: `won_status` field is distinct from stage).
- Activity discipline is a change-management topic, not a feature.

## Risks and assumptions
Structures verified in source; exact scoring math, dedup behavior and assignment fairness are runtime behaviors → validate in demo DB. Multi-company lead visibility governed by record rule — test in group setups.

## Validation checklist
- [ ] Lead settings (leads on/off) match client funnel
- [ ] Assignment rules cover the client's routing matrix in a live test
- [ ] Scoring behavior reviewed on representative data
- [ ] Duplicate strategy tested with real lead lists
- [ ] Edition decision for AI/VoIP/journey features confirmed with licensing
