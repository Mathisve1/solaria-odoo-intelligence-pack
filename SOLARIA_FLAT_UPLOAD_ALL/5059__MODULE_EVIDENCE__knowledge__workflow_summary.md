# Workflow & Automation Summary — `knowledge` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `knowledge` — Knowledge |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Create/organize articles (workspace/private) -> share/invite -> embed live views; no state machine — governance is editorial, not technical.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| knowledge.article | stage_id | configurable stages via `knowledge.article.stage` |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Articles | knowledge.article | code |

## Integration surface
- Direct dependencies: `web`, `digest`, `html_editor`, `mail`, `portal`, `web_unsplash`, `web_hierarchy`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
