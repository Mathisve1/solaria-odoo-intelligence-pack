# Views & Navigation Summary — `stock` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `stock` — Inventory |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Operations menu (Receipts, Deliveries, Internal, per warehouse) is generated from picking types — configuration shapes the UI.
- Forms for pickings with move lines, lots and packages carry the traceability demo.
- Many list/kanban views are operational worklists — good for showing daily warehouse life, not just setup.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Inventory | — | group_stock_manager,group_stock_user |
| Inventory / Configuration | — | group_stock_manager |
| Inventory / Configuration | — | group_stock_manager |
| Inventory / Configuration / Delivery | — | stock.group_stock_manager |
| Inventory / Configuration / Delivery / Package Types | action_package_type_view | stock.group_tracking_lot |
| Inventory / Configuration / Products | — | — |
| Inventory / Configuration / Products / Units & Packagings | product_uom_form_action | uom.group_uom |
| Inventory / Configuration / Products / menu_attribute_action | attribute_action | product.group_product_variant |
| Inventory / Configuration / Products / menu_product_category_config_stock | product_category_action_form | — |
| Inventory / Configuration / Products / menu_wms_barcode_nomenclature_all | action_barcode_nomenclature_form | base.group_no_one |
| Inventory / Configuration / Settings | action_stock_config_settings | base.group_system |
| Inventory / Configuration / Warehouse Management | — | stock.group_stock_manager |
| Inventory / Configuration / Warehouse Management / Operations Types | action_picking_type_list | — |
| Inventory / Configuration / Warehouse Management / Putaway Rules | action_putaway_tree | stock.group_stock_multi_locations |
| Inventory / Configuration / Warehouse Management / Routes | action_routes_form | stock.group_adv_location |
| Inventory / Configuration / Warehouse Management / Storage Categories | action_storage_category | stock.group_stock_multi_locations |
| Inventory / Configuration / Warehouse Management / menu_action_location_form | action_location_form | stock.group_stock_multi_locations |
| Inventory / Configuration / Warehouse Management / menu_action_rules_form | action_rules_form | stock.group_adv_location |
| Inventory / Configuration / Warehouse Management / menu_action_warehouse_form | action_warehouse_form | — |
| Inventory / Operations | — | — |
| Inventory / Operations / Adjustments | — | — |
| Inventory / Operations / Adjustments / Physical Inventory | action_view_inventory_tree | — |
| Inventory / Operations / Adjustments / Scrap | action_stock_scrap | — |
| Inventory / Operations / Procurement | — | — |
| Inventory / Operations / Procurement / Replenishment | action_replenishment | stock.group_stock_manager |
| Inventory / Operations / Procurement / menu_stock_references | action_stock_reference | base.group_no_one |
| Inventory / Operations / Transfers | — | — |
| Inventory / Operations / Transfers / Deliveries | method_action_picking_tree_outgoing | stock.group_stock_manager,stock.group_stock_user |
| Inventory / Operations / Transfers / Internal | method_action_picking_tree_internal | stock.group_stock_multi_locations |
| Inventory / Operations / Transfers / Receipts | method_action_picking_tree_incoming | stock.group_stock_manager,stock.group_stock_user |
| Inventory / Operations / stock.menu_procurement_compute | ir_cron_scheduler_action_ir_actions_server | base.group_no_one |
| Inventory / Overview | stock_picking_type_action | — |
| Inventory / Products | — | — |
| Inventory / Products / Packages | action_package_view | stock.group_tracking_lot |
| Inventory / Products / Product Variants | stock_product_normal_action | product.group_product_variant |
| Inventory / Products / Products | product_template_action_product | — |
| Inventory / Products / menu_action_production_lot_form | action_production_lot_form | stock.group_production_lot |
| Inventory / Reporting | — | group_stock_manager |
| Locations | action_view_quants | stock.group_stock_multi_locations,stock.group_tracking_owner,base.group_no_one |
| Moves Analysis | stock_move_action | — |
| Stock | action_product_stock_view | — |
| stock_move_line_menu | stock_move_line_action | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Putaway Rules | stock.putaway.rule | list |
| Putaway Rules | stock.putaway.rule | — |
| Putaway Rules | stock.putaway.rule | — |
| Inventory at Date | stock.quantity.history | form |
| Stock | product.product | list,form |
| Products | product.template | kanban,list,form |
| Product Variants | product.product | list,form,kanban |
| Settings | res.config.settings | form |
| Products | product.product | — |
| Locations | stock.location | list,form |
| Locations | stock.location | list,form |
| Locations | stock.location | list,form |
| Routes | stock.route | list,form |
| Lots / Serial Numbers | stock.lot | — |
| Lots/Serial Numbers | stock.lot | — |
| Moves History | stock.move.line | list,kanban,pivot,form |
| Moves Analysis | stock.move | — |
| Replenishment | stock.warehouse.orderpoint | list,kanban,form |
| Reordering Rules | stock.warehouse.orderpoint | list,kanban,form |
| Package Types | stock.package.type | — |
| Packages | stock.package | list,kanban,form |
| Operations Types | stock.picking.type | list,form |
| Inventory Overview | stock.picking.type | kanban,form |
| Transfers | stock.picking | list,kanban,form,calendar |
| Receipts | stock.picking | list,kanban,form,calendar,activity |
| Deliveries | stock.picking | list,kanban,form,calendar,activity |
| Internal Transfers | stock.picking | list,kanban,form,calendar |
| Send email | mail.compose.message | form |
| All Transfers | stock.picking | — |
| To Do | stock.picking | list,kanban,form,calendar |
| To Do | stock.picking | list,kanban,form,calendar |
| Waiting Transfers | stock.picking | list,kanban,form,calendar |
| Late Transfers | stock.picking | list,kanban,form,calendar |
| Backorders | stock.picking | list,kanban,form,calendar |
| Ready Moves | stock.move | — |
| Operations | stock.move.line | — |
| New Transfer | stock.picking | form |
| Locations | stock.quant | list,form |
| References | stock.reference | list,form |
| Rules | stock.rule | list,form |
| Scrap Orders | stock.scrap | list,form,kanban,pivot,graph |
| Storage Categories | stock.storage.category | list,form |
| Storage Category Capacity | stock.storage.category.capacity | list |
| Warehouses | stock.warehouse | — |
| Low on stock? Let's replenish. | product.replenish | form |

*…7 more actions omitted.*

## View inventory

- Primary views defined: 102 (form: 39, list: 30, search: 17, kanban: 8, graph: 3, pivot: 3, activity: 1, calendar: 1)
- Inheriting views (UI extensions of other modules): 27
- Richest UI objects: `stock.move` (form, graph, kanban, list, pivot, search); `stock.picking` (activity, calendar, form, kanban, list, search); `stock.move.line` (form, kanban, list, pivot, search); `stock.quant` (form, graph, list, pivot, search); `stock.lot` (form, kanban, list, search); `stock.warehouse.orderpoint` (form, kanban, list, search); `stock.package` (form, kanban, list, search); `stock.picking.type` (form, kanban, list, search); `stock.scrap` (form, kanban, list, search); `stock.location` (form, list, search); `stock.route` (form, list, search); `stock.reference` (form, list, search)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Return slip | stock.picking | qweb-pdf |
| Reception Report | stock.picking | qweb-pdf |
| Picking Operations | stock.picking | qweb-pdf |
| Delivery Slip | stock.picking | qweb-pdf |
| Packages | stock.picking | qweb-pdf |
| Count Sheet | stock.quant | qweb-pdf |
| Package Barcode with Contents | stock.package | qweb-pdf |
| Package Barcode with Contents | stock.package.history | qweb-pdf |
| Package Barcode (PDF) | stock.package | qweb-pdf |
| Package Barcode (PDF) | stock.package.history | qweb-pdf |
| Location Barcode | stock.location | qweb-pdf |
| Lot/Serial Number (PDF) | stock.lot | qweb-pdf |
| Operation type (PDF) | stock.picking.type | qweb-pdf |
| Product Routes Report | product.template | qweb-html |
| Product Label (ZPL) | product.product | qweb-text |
| Lot/Serial Number (ZPL) | stock.lot | qweb-text |
| Package Barcode (ZPL) | stock.package | qweb-text |
| Package Barcode (ZPL) | stock.package.history | qweb-text |
| Packaging Barcodes (ZPL) | product.uom | qweb-text |
| Operation type (ZPL) | stock.picking.type | qweb-text |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
