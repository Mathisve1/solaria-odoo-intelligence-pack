# Workflow & Automation Summary — `sale_subscription` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `sale_subscription` — Subscriptions |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Quotation -> confirmed subscription -> recurring invoice cron per plan -> renewal/upsell orders -> churn logging on close.
- Payment failures/dunning intersect with Enterprise accounting follow-ups — design the collections path end-to-end.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| payment.transaction | renewal_state | draft → pending → authorized → cancel |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Sale Subscription: subscriptions expiration | sale.order | 1 weeks |
| Sale Subscription: generate recurring invoices and payments | sale.order | 1 days |
| Sale Subscription: send reminder for subscriptions with no token | sale.order | 1 days |
| Sale Subscription: Update KPI | sale.order | 1 weeks |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Change customer | sale.order | code |
| Pause Subscription | sale.order | code |

## Mail templates shipped: 4

*Subscription: Payment Failure*, *Subscription: Payment Reminder*, *Subscription: Rating Request*, *Subscription: Default Email Alert*

## Integration surface
- Direct dependencies: `account_accountant`, `sale_management`, `portal`, `web_cohort`, `rating`, `sms`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
