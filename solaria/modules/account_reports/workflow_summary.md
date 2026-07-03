# Workflow & Automation Summary — `account_reports` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `account_reports` — Accounting Reports |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Two shipped crons matter: automated account-return generation/refresh per company (the 19.0 tax-return workflow engine) and scheduled report sending — both belong in close runbooks.
- Report chain: operational postings → report handlers compute → drill-down back to entries; variants/comparisons are configuration.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| account.return | audit_status | ongoing → done → paused |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Generate or refresh account return for every companies | account.return.type | 1 days |
| Send account reports automatically | account.report | 1 days |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Create Menu Item | account.report | code |
| Open Tax Return | account.return | code |
| Create Composite Report | account.report | code |
| Open Tax Return | account.return | code |
| Open Customer Statements | res.partner | code |

## Mail templates shipped: 4

*Customer Statement*, *Tax payment*, *Follow Up Report*, *Tax Return Deadline*

## Integration surface
- Direct dependencies: `account_accountant`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
