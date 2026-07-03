# Workflow & Automation Summary — `quality` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `quality` — Quality Base (pack merges: `quality`, `quality_control`) |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Core flow: control point (what/where/when to check, per operation type/product) → quality check auto-created in operations → pass/fail → quality alert (team, stage, reason) on failure.
- Check types (test_type model incl. spreadsheet-based worksheets via quality_control) define the operator experience — validate available types live.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| quality.check | quality_state | none → pass → fail |
| quality.alert | stage_id | configurable stages via `quality.alert.stage` |
| stock.move.line | check_state | no_checks → in_progress → pass → fail |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Quality Alert | stock.picking | code |
| Quality Check | stock.picking | code |

## Integration surface
- Direct dependencies: `quality`, `spreadsheet_edition`, `stock`
- Sequences configured: 3 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
