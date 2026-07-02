# Security & Access Summary — `stock` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `stock` — Inventory |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- User vs Manager plus feature-gating groups (multi-locations, lots, packages, UoM) — many 'features' are actually groups toggled by settings.
- Warehouse-level segregation is not shipped as default record rules — client-specific warehouse security is a design task.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| User | group_stock_user | group_user |
| Administrator | group_stock_manager | — |
| Manage Multiple Stock Locations | group_stock_multi_locations | — |
| Manage Multiple Warehouses | group_stock_multi_warehouses | — |
| Manage Lots / Serial Numbers | group_production_lot | — |
| Print GS1 Barcodes for Lot & Serial Numbers | group_stock_lot_print_gs1 | — |
| Display Serial & Lot Number in Delivery Slips | group_lot_on_delivery_slip | — |
| Manage Packages | group_tracking_lot | — |
| Manage Push and Pull inventory flows | group_adv_location | — |
| Manage Different Stock Owners | group_tracking_owner | — |
| A warning can be set on a partner (Stock) | group_warning_stock | — |
| Require a signature on your delivery orders | group_stock_sign_delivery | — |
| Use Reception Report | group_reception_report | — |

## Access rights (ir.model.access) — 77 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_stock_user | `stock_lot`, `stock_move_line`, `stock_orderpoint_snooze`, `stock_package`, `stock_picking`, `stock_return_picking_line` | `lot_label_layout`, `picking_label_type`, `product_replenish`, `stock_backorder_confirmation`, `stock_backorder_confirmation_line`, `stock_inventory_adjustment_name` +13 more | `barcodes.barcode_nomenclature`, `barcodes.barcode_rule`, `product.product_product`, `product.product_template`, `stock_package_type`, `stock_picking_type` +2 more |
| group_stock_manager | `barcodes.barcode_nomenclature`, `barcodes.barcode_rule`, `product.product_attribute`, `product.product_attribute_value`, `product.product_pricelist`, `stock_location` +15 more | `base.res_partner`, `product.update_product_attribute_value`, `stock_inventory_adjustment_name`, `stock_inventory_conflict`, `stock_inventory_warning`, `stock_quant_relocate` +2 more | — |
| group_user | `stock_move_line` | `stock.stock_reference` | `product_removal`, `report_stock_quantity`, `stock_location`, `stock_package`, `stock_picking_type`, `stock_putaway_rule` +6 more |
| group_partner_manager | — | — | `stock_location` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| stock_picking multi-company | — | `[('company_id', 'in', company_ids)]` |
| Stock Operation Type multi-company | — | `[('company_id','in', company_ids)]` |
| Stock Operation Type multi-company | — | `[('company_id','in', company_ids)]` |
| Stock Production Lot multi-company | — | `[('company_id', 'in', company_ids + [False])]` |
| Warehouse multi-company | stock.warehouse | `[('company_id', 'in', company_ids)]` |
| Location multi-company | stock.location | `[('company_id', 'in', company_ids + [False])]` |
| stock_move multi-company | — | `[('company_id', 'in', company_ids)]` |
| stock_move_line multi-company | — | `[('company_id', 'in', company_ids + [False])]` |
| stock_quant multi-company | stock.quant | `[('company_id', 'in', company_ids + [False])]` |
| stock_warehouse.orderpoint multi-company | — | `[('company_id', 'in', company_ids)]` |
| product_pulled_flow multi-company | stock.rule | `[('company_id', 'in', company_ids + [False])]` |
| stock_route multi-company | stock.route | `[('company_id', 'in', company_ids + [False])]` |
| stock_package multi-company | stock.package | `[('company_id', 'in', company_ids + [False])]` |
| stock_scrap_company multi-company | stock.scrap | `[('company_id', 'in', company_ids)]` |
| report_stock_quantity_flow multi-company | report.stock.quantity | `[('company_id', 'in', company_ids)]` |
| stock_storage_category multi-company | stock.storage.category | `[('company_id', 'in', company_ids + [False])]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
