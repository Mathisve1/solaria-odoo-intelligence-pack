# Workflow & Automation Summary — `account` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `account` — Invoicing |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- account.move lifecycle: draft -> posted (immutable accounting) -> optional reversal; payment state tracks paid/partial/in-payment.
- Community ships operational flows (invoice, bill, payment, basic bank import); dunning automation and reconciliation-at-scale live in Enterprise modules.
- Tax and journal configuration determine posting behavior — 'workflow issues' in finance are usually configuration issues.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| account.lock_exception | state | active → revoked → expired |
| account.move | state | draft → posted → cancel |
| account.payment | state | draft → in_process → paid → canceled → rejected |
| account.invoice.report | state | draft → posted → cancel |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Account: Post draft entries with auto_post enabled and accounting date up to today | account.move | 1 days |
| Send invoices automatically | account.move | 1 days |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Share | account.move | code |
| Unmerge account | account.account | code |
| Move to Account | account.move.line | code |
| Change Period | account.move.line | code |
| Switch into invoice/credit note | account.move | code |
| Pay | account.move | code |
| (Un)Block Payment | account.move | code |
| Data Inalterability Check | res.company | code |
| Review Entries | account.move | code |
| Post Payments | account.payment | code |
| Unreconcile | account.move.line | code |
| Confirm Entries | account.move | code |

## Mail templates shipped: 7

*Invoice: Sending*, *Payment: Payment Receipt*, *Credit Note: Sending*, *Self-billing invoice: Sending*, *Self-billing credit note: Sending*, *New eInvoices Notification*, *Journal Notification*

## Integration surface
- Direct dependencies: `base_setup`, `onboarding`, `product`, `analytic`, `portal`, `digest`
- Sequences configured: 1 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
