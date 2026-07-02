# Helpdesk (`helpdesk`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `helpdesk` |
| Display name | Helpdesk |
| Source origin | **Enterprise** (no Community equivalent app in 19.0) |
| Version scope | Odoo 19.0 |
| Dependencies | `mail`, `utm`, `rating`, `resource`, `portal`, `digest` (+bridges: `helpdesk_stock`, `helpdesk_account`, `helpdesk_timesheet`, `website_helpdesk`, `crm_helpdesk`) |
| Functional domain | Helpdesk / customer service |
| Confidence | High for structures; SLA computation and assignment behavior need live validation |

## Business purpose
Run customer service as a managed process: multi-channel ticket intake, team-based queues with stages, SLA policies with status tracking, satisfaction ratings — connected to the rest of the ERP (returns, credit notes, timesheets, field service) instead of floating in a separate tool.

## Main users / personas
Support agents, team leads (SLA/queues), customer service managers, customers (portal/email/livechat), ops/finance (returns, refunds via bridges).

## Business problems solved
- Tickets in shared inboxes → `helpdesk.ticket` with teams (`helpdesk.team`), stages, priorities, tags.
- No service commitments → `helpdesk.sla` policies + `helpdesk.sla.status` per ticket (SLA engine is a first-class model — source-verified).
- No quality signal → ratings ("Show Customer Ratings" group), analysis reports (tickets, SLA).
- Service disconnected from operations → bridges: product returns (`helpdesk_stock`), refunds (`helpdesk_account`), billable support time (`helpdesk_timesheet`), escalate to field service.

## Main business processes (source-verified)
1. Intake: email alias per team, website forms/portal (`website_helpdesk`), livechat (+AI agents E), CRM handoff (`crm_helpdesk`).
2. Triage/assignment: team queues; auto-assignment group ("Auto Assigment" — balanced/random methods; validate options live).
3. Resolution through stages with SLA timers; canned responses via mail templates; knowledge integration for answers.
4. Closure: rating email, analysis (SLA success rate, closing time).

## Key functional capabilities
Multiple teams with own pipelines/settings, SLA per team/priority/stage targets, tag assignment model (`helpdesk.tag.assignment`, 19.0 patterns), portal ticket tracking, digests/KPIs, per-team feature toggles (menus reveal team-level options).

## Fit with other modules
`knowledge` (E, answer articles), `industry_fsm` (E, on-site escalation), `stock`/`account` bridges (returns/credits), `timesheet` (billable support), `im_livechat`+`ai_livechat` (E), `website` (help center patterns via `website_helpdesk`+forum/slides bridges — check catalog).

## Community fallback (be honest)
No Helpdesk app in Community 19.0. Workarounds (project as ticket board, crm misuse) lose SLA/ratings/bridges — position them as compromises, not equivalents.

## Configuration opportunities
Teams (channels, members, assignment method), stages+templates, SLA policies, ratings on/off, portal visibility, canned responses, help center components per team.

## Studio / automation opportunities
Automation: escalation chains (SLA warning → team lead activity), VIP routing, auto-tagging by keywords (deterministic), reopen handling. AI (E): livechat agents, reply drafting — human-send by default. Studio: ticket classification fields (asset, severity matrices) — keep SLA logic in SLA policies.

## Custom development triggers
Deep ITSM needs (CMDB, change management) — Odoo Helpdesk is customer-service-grade, not a full ITSM; entitlement/contract-based support logic beyond bridges; complex warranty adjudication.

## External integration triggers
Telephony/CCaaS platforms, ITSM suites coexistence, product registration/IoT telemetry feeds, external knowledge bases (prefer native Knowledge first).

## Common client questions
"SLA per customer tier?" — SLA policies + team/priority design; validate matrix expressiveness live. · "Customer portal?" — native tickets view. · "Auto-assign fairly?" — assignment methods shipped; validate semantics. · "Can support hours be billed?" — timesheet bridge → sale items. · "Deflection?" — knowledge + livechat AI (E) + help center; measure honestly.

## Fit-gap considerations
Excellent for customer service and light internal service desks. Gap zone: ITIL-grade ITSM, entitlement engines, warranty claims adjudication. The ERP-bridge story (return + credit note from a ticket) is the differentiator vs Zendesk-class tools — lead with it.

## Deloitte demo angles
1. **Email-to-resolution:** email → ticket → SLA countdown visible → canned response → solved → rating request.
2. **ERP muscle:** from the same ticket: create return order + credit note — competitors need 3 systems.
3. **Manager view:** SLA analysis pivot, workload per agent, rating trend.

## Implementation watch-outs
- Team topology (by product/region/tier) decided before SLA design.
- SLA realism: measure current baseline before committing targets.
- Knowledge content readiness for deflection promises.
- Portal/brand tone in templates and rating emails.

## Risks and assumptions
Structures verified. SLA timer semantics (business hours, pauses), assignment fairness and livechat AI quality are runtime → validate. Helpdesk is Enterprise — edition/licensing must be confirmed.

## Validation checklist
- [ ] Team/queue design + assignment method tested with real volumes
- [ ] SLA matrix reproduced in policies and verified on sample tickets
- [ ] Return/credit bridges demoed with ops+finance present
- [ ] Deflection stack (knowledge, livechat/AI) scoped with content plan
