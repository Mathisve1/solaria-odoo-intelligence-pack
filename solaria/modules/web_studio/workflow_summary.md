# Workflow & Automation Summary — `web_studio` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `web_studio` — Studio |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Studio approval rules add an approval state machine on actions (rules → entries → requests with delegation) — a no-code approval layer to check BEFORE building custom approvals; validate rule expressiveness live.
- Studio Export packages customizations as a module — the governance artifact for migrating Studio work between environments.

## Integration surface
- Direct dependencies: `base_automation`, `base_import_module`, `mail`, `web`, `web_enterprise`, `html_editor`, `web_map`, `web_gantt`, `web_cohort`, `sms`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
