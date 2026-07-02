# Workflow & Automation Summary — `documents` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `documents` — Documents |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- File enters workspace (upload/email alias) -> tagged -> workflow action converts to business object (bill, task, contract) — the DMS as a process inbox.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| documents.document | thumbnail_status | present → error → client_generated → restricted |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Documents: Access Tracking | documents.access.tracking | 1 months |

## Mail templates shipped: 3

*Document: Document Request*, *Document Request: Reminder*, *Document: Document Share*

## Integration surface
- Direct dependencies: `base`, `mail`, `portal`, `web_enterprise`, `attachment_indexation`, `digest`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
