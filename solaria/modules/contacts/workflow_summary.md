# Workflow & Automation Summary — `contacts` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `contacts` — Contacts |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Partner records have no state machine; lifecycle = data quality (dedup/merge, archiving) — governance topic, not workflow.

## Integration surface
- Direct dependencies: `base`, `mail`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
