# Workflow & Automation Summary — `planning` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `planning` — Planning |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Plan (draft, internal) -> publish (employees notified) -> optional employee self-assignment on open shifts; copy-previous-week is the recurring gesture.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| planning.slot | state | draft → published |
| planning.analysis.report | state | draft → published |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Planning: generate next recurring shifts | planning.recurrency |  weeks |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Publish & Send | planning.slot | code |
| Reset to Draft | planning.slot | code |

## Mail templates shipped: 3

*Planning: New Shift*, *Planning: New Schedule*, *Planning: Shift Re-assigned*

## Integration surface
- Direct dependencies: `hr`, `hr_hourly_cost`, `web_gantt`, `digest`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
