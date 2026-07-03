# Workflow & Automation Summary — `base` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `base` — Base |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Platform automations: scheduled actions registry, module install/upgrade lifecycle — relevant to architects and admins.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| ir.actions.server | state | object_write → object_create → object_copy → code → webhook → multi |
| ir.actions.todo | state | open → done |
| ir.model | state | manual → base |
| ir.model.fields | state | manual → base |
| res.users.deletion | state | todo → done → fail |
| base.language.export | state | choose → get |
| base.module.update | state | init → done |
| base.partner.merge.automatic.wizard | state | option → selection → finished |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Base: Auto-vacuum internal data | ir.autovacuum | 1 days |
| Base: Portal Users Deletion | res.users.deletion | 1 days |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Config: Run Remaining Action Todo | res.config | code |

## Integration surface
- Direct dependencies: 
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
