# Workflow & Automation Summary — `base_automation` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `base_automation` — Automation Rules |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- One engine: base.automation with a check-and-execute cron plus in-transaction triggers (create/update/delete/time-based/webhook patterns — validate trigger list live in 19.0).
- Rules fire actions (server actions, emails, activities) — every rule is part of the process design and belongs in the customization registry.

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Automation Rules: check and execute | base.automation | 4 hours |

## Integration surface
- Direct dependencies: `base`, `digest`, `resource`, `mail`, `sms`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
