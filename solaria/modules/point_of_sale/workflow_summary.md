# Workflow & Automation Summary — `point_of_sale` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `point_of_sale` — Point of Sale |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Session open -> orders -> close & cash control -> accounting entries posted per session — the fiscal heartbeat of the store.
- Offline resilience then sync is the architectural selling point; refunds/returns flow back through stock.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| pos.order | state | draft → cancel → paid → done |
| pos.order | invoice_status | invoiced → to_invoice |
| report.pos.order | state | draft → paid → done → cancel |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Cancel Order | pos.order | code |
| Send Email | pos.order | code |

## Mail templates shipped: 1

*Point of Sale: Receipt*

## Integration surface
- Direct dependencies: `resource`, `stock_account`, `barcodes`, `html_editor`, `digest`, `phone_validation`, `partner_autocomplete`, `iot_base`, `google_address_autocomplete`
- Sequences configured: 1 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
