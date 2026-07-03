# Workflow & Automation Summary — `hr_timesheet` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `hr_timesheet` — Task Logs |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Daily/weekly entry against tasks; the flow moment is approval (Enterprise grid) and the handoff to invoicing (sale_timesheet) or costing (analytic lines).

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Delete | hr.employee | code |

## Integration surface
- Direct dependencies: `hr`, `hr_hourly_cost`, `analytic`, `project`, `uom`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
