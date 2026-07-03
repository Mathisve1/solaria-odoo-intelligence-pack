# Workflow & Automation Summary — `industry_fsm` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `industry_fsm` — Field Service |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Task scheduled -> technician starts timer on site -> worksheet + materials -> customer signature -> stop timer -> invoice from the task — the full mobile arc.

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| My Tasks in mobile Server Action | project.task | code |
| My Tasks Server Action | project.task | code |
| Map Server Action | project.task | code |
| All Tasks Server Action | project.task | code |
| To Schedule Server Action | project.task | code |
| Planning by User Action | project.task | code |
| Planning by Project Server Action | project.task | code |
| Planning by Location Server Action | project.task | code |

## Mail templates shipped: 2

*Field Service: Intervention Scheduled*, *Field Service: Field Service Report*

## Integration surface
- Direct dependencies: `project_enterprise`, `timesheet_grid`, `base_geolocalize`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
