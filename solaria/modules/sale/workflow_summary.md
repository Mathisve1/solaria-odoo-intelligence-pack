# Workflow & Automation Summary — `sale` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `sale` — Sales |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Draft quotation -> sent -> sale (confirmed) -> locked/cancelled lifecycle drives everything downstream (delivery, invoice).
- Confirmation spawns deliveries (with sale_stock) and invoice candidates per invoicing policy — the handoff moments to demo.
- Online signature/payment on the portal can auto-confirm orders — configuration, not custom code.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| sale.order.line | invoice_status | upselling → invoiced → to invoice → no |
| sale.report | invoice_status | upselling → invoiced → to invoice → no |
| sale.report | line_invoice_status | upselling → invoiced → to invoice → no |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| automatic invoicing: send ready invoice | payment.transaction | 1 days |
| Sales: Send pending emails | sale.order | 1 days |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Mark Quotation as Sent | sale.order | code |
| Share | sale.order | code |
| Send an email | sale.order | code |

## Mail templates shipped: 4

*Sales: Send Quotation*, *Sales: Send Proforma*, *Sales: Order Confirmation*, *Sales: Payment Done*

## Integration surface
- Direct dependencies: `sales_team`, `account_payment`, `utm`
- Sequences configured: 1 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
