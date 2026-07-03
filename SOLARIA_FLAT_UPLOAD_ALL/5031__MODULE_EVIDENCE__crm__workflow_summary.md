# Workflow & Automation Summary — `crm` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `crm` — CRM |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Business events: lead capture -> qualification (lead->opportunity type switch) -> staged pipeline -> won/lost (with lost reasons).
- Two shipped crons: predictive scoring recompute and rule-based lead assignment — 'intelligent CRM' is standard configuration here.
- Won/lost is not a stage but a status + stage interplay — train users; misuse breaks reporting.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| crm.lead | phone_state | correct → incorrect |
| crm.lead | email_state | correct → incorrect |
| crm.lead | won_status | won → lost → pending |
| crm.lead | stage_id | configurable stages via `crm.stage` |
| crm.activity.report | won_status | won → lost → pending |
| crm.activity.report | stage_id | configurable stages via `crm.stage` |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Predictive Lead Scoring: Recompute Automated Probabilities | crm.lead | 1 days |
| CRM: Lead Assignment | crm.team | 1 days |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Crm: My Pipeline | crm.team | code |
| Crm: Forecast | crm.team | code |

## Integration surface
- Direct dependencies: `base_setup`, `sales_team`, `mail`, `calendar`, `resource`, `utm`, `web_tour`, `contacts`, `digest`, `phone_validation`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
