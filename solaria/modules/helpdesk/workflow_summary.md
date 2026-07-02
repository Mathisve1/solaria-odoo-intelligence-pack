# Workflow & Automation Summary — `helpdesk` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `helpdesk` — Helpdesk |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Ticket: new -> in progress -> solved/closed under SLA timers; per-team automations (assignment methods) shape the flow.
- Email/portal/livechat intake is configuration; escalation to tasks/FSM via bridges.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| helpdesk.sla | stage_id | configurable stages via `helpdesk.stage` |
| helpdesk.sla.status | status | failed → reached → ongoing |
| helpdesk.ticket | kanban_state | normal → done → blocked |
| helpdesk.ticket | stage_id | configurable stages via `helpdesk.stage` |
| helpdesk.sla.report.analysis | sla_status | failed → reached → ongoing |
| helpdesk.sla.report.analysis | kanban_state | normal → done → blocked |
| helpdesk.sla.report.analysis | stage_id | configurable stages via `helpdesk.stage` |
| helpdesk.ticket.report.analysis | kanban_state | normal → done → blocked |
| helpdesk.ticket.report.analysis | stage_id | configurable stages via `helpdesk.stage` |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Helpdesk Ticket: Automatically close the tickets | helpdesk.team | 1 days |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Delete | helpdesk.stage | code |
| Preview | helpdesk.ticket | code |

## Mail templates shipped: 3

*Helpdesk: Ticket Received*, *Helpdesk: Ticket Closed*, *Helpdesk: Ticket Rating Request*

## Integration surface
- Direct dependencies: `base_setup`, `mail`, `utm`, `rating`, `web_tour`, `web_cohort`, `resource`, `portal`, `digest`
- Sequences configured: 1 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
