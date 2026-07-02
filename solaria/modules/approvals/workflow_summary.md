# Workflow & Automation Summary — `approvals` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `approvals` — Approvals |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Request new -> submitted -> approved/refused (approver matrix per category), with optional document proof; feeds purchase via bridge.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| approval.approver | status | new → pending → waiting → approved → refused → cancel |
| approval.request | request_status | new → pending → approved → refused → cancel |
| approval.request | user_status | new → pending → waiting → approved → refused → cancel |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Open Approval Category | approval.category | code |
| Force Approval | approval.request | code |

## Integration surface
- Direct dependencies: `mail`, `hr`, `product`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
