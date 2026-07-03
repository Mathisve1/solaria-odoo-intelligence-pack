# Workflow & Automation Summary — `stock` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `stock` — Inventory |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Picking lifecycle: draft -> waiting/confirmed -> assigned (reserved) -> done; moves underneath carry quantity truth.
- Routes/rules (pull/push) generate chained operations (e.g., receipt -> quality/putaway) — process design = route configuration.
- Reordering rules + scheduler cron generate replenishment (RFQs/MOs) — the 'self-driving warehouse' baseline.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| stock.move | state | draft → waiting → confirmed → partially_available → assigned → done → cancel |
| stock.picking | state | draft → waiting → confirmed → assigned → done → cancel |
| stock.picking | products_availability_state | available → expected → late |
| stock.scrap | state | draft → done |
| report.stock.quantity | state | forecast → in → out |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Procurement: run scheduler | stock.rule | 1 days |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Routes | product.template | code |
| Replenish | product.product | code |
| Replenish | product.template | code |
| Revert Inventory Adjustment | stock.move.line | code |
| Replenishment | stock.warehouse.orderpoint | code |
| Validate | stock.picking | code |
| Unreserve | stock.picking | code |
| Labels | stock.picking | code |
| Lock/Unlock | stock.picking | code |
| Scrap | stock.picking | code |
| stock.click_dashboard_graph | stock.picking | code |
| stock.method_action_picking_tree_incoming | stock.picking | code |
| stock.method_action_picking_tree_outgoing | stock.picking | code |
| stock.method_action_picking_tree_internal | stock.picking | code |
| Install Barcode | stock.picking.type | code |

## Mail templates shipped: 1

*Shipping: Send by Email*

## Integration surface
- Direct dependencies: `product`, `barcodes_gs1_nomenclature`, `digest`
- Sequences configured: 4 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
