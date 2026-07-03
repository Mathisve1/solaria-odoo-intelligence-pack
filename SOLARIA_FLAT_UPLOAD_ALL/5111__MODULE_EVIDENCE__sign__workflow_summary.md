# Workflow & Automation Summary — `sign` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `sign` — Sign |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Template -> request with roles -> sent -> signed/completed with audit log; expiry/reminder crons keep requests moving.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| sign.log | request_state | shared → sent → signed → refused → canceled → expired |
| sign.request | state | shared → sent → signed → canceled → expired |
| sign.request.item | state | sent → completed → canceled |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Sign: Send mail reminder | sign.request | 1 days |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Template Sample Contract.pdf trigger | sign.template | code |

## Integration surface
- Direct dependencies: `mail`, `attachment_indexation`, `portal`, `sms`, `certificate`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
