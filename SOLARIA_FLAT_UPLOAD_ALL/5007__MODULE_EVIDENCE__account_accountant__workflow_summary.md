# Workflow & Automation Summary — `account_accountant` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `account_accountant` — Invoicing |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Close rhythm: reconcile bank lines (auto-reconcile cron assists) → review → lock dates per role with governed exceptions → fiscal year handling.
- The auto-reconcile cron ('Try to reconcile automatically your statement lines') is the touchless-bank baseline — tune matching rules before promising rates.

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Try to reconcile automatically your statement lines | account.bank.statement.line | 1 days |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Statement | account.bank.statement | code |
| Reset to draft | account.bank.statement.line | code |

## Integration surface
- Direct dependencies: `account`, `mail_enterprise`, `web_tour`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
