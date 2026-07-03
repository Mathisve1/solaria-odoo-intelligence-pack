# Workflow & Automation Summary — `marketing_automation` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `marketing_automation` — Marketing Automation |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Campaign draft -> running: participants enter on trigger, walk the activity tree (mail/server action branches with delays/conditions) -> KPIs per node; test mode exists for safe rehearsal.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| marketing.campaign | state | draft → running → stopped |
| marketing.participant | state | running → completed → unlinked |
| marketing.trace | state | scheduled → processed → rejected → canceled → error |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Marketing Automation: sync participants | marketing.campaign | 12 hours |
| Marketing Automation: execute activities | marketing.campaign | 1 hours |

## Integration surface
- Direct dependencies: `mass_mailing`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
