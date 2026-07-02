# Workflow & Automation Summary — `project` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `project` — Project |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Tasks move across configurable stages per project; state field (in progress/changes requested/approved/done) adds a cross-project status layer in 19.0.
- Milestones can gate invoicing (with sales integration) — the billing bridge is a flow, not a report.
- Rating/portal touchpoints turn projects client-facing — decide what customers see.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| project.project | last_update_status | on_track → at_risk → off_track → on_hold → to_define → done |
| project.project | stage_id | configurable stages via `project.project.stage` |
| project.task | state | 01_in_progress → 02_changes_requested → 03_approved → 04_waiting_normal |
| project.task | stage_id | configurable stages via `project.task.type` |
| project.task.stage.personal | stage_id | configurable stages via `project.task.type` |
| project.task.type | rating_status | stage → periodic |
| project.update | status | on_track → at_risk → off_track → on_hold → done |
| report.project.task.user | state | 01_in_progress → 1_done → 04_waiting_normal → 03_approved → 1_canceled → 02_changes_requested |
| report.project.task.user | stage_id | configurable stages via `project.task.type` |
| project.task.burndown.chart.report | state | 01_in_progress → 1_done → 04_waiting_normal → 03_approved → 1_canceled → 02_changes_requested |
| project.task.burndown.chart.report | stage_id | configurable stages via `project.task.type` |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Project Stage: Send rating | project.task.type |  days |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Delete | project.project.stage | code |
| Convert to Template | project.project | code |
| Delete | project.task.type | code |
| Convert to Task/Sub-Task | project.task | code |
| Convert to Template | project.task | code |

## Mail templates shipped: 2

*Project: Request Acknowledgment*, *Project: Task Rating Request*

## Integration surface
- Direct dependencies: `analytic`, `base_setup`, `mail`, `portal`, `rating`, `resource`, `web`, `web_tour`, `digest`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
