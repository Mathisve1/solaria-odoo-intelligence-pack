# Workflow & Automation Summary — `hr` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `hr` — Employees |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Employee lifecycle is master-data centric (hire, department/job changes, departure with HR wizards); version/contract data underpins payroll (E).
- Most 'HR workflows' (leave approvals, expense approvals) live in sibling apps — hr itself is the hub.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| hr.employee | hr_presence_state | present → absent → archive → out_of_working_hour |
| hr.employee.public | hr_presence_state | present → absent → archive → out_of_working_hour |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| HR Employee: Notify Expiring Contract or Work Permit | hr.employee | 1 days |
| HR Employee: Update Current Version | hr.employee | 1 days |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Load Sample Data | hr.employee | code |
| Create User | hr.employee | code |
| Create User | hr.employee | code |

## Integration surface
- Direct dependencies: `base_setup`, `digest`, `phone_validation`, `resource_mail`, `web`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
