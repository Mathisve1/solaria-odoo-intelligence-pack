# Views & Navigation Summary — `stock_barcode` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `stock_barcode` — Barcode |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- The app is a mobile scanning UI, not backend menus — demo on a phone/scanner with GS1 barcodes; backend views here are minimal by design.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| stock_barcode_menu | stock_barcode_action_main_menu | stock.group_stock_user |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Operations | stock.picking | kanban,form |
| Product Barcodes | product.product | list |
| Operations | stock.picking.type | kanban |
| Open picking form | stock.picking | form |

## View inventory

- Primary views defined: 9 (form: 5, kanban: 3, list: 1)
- Inheriting views (UI extensions of other modules): 11
- Richest UI objects: `stock.quant` (form, kanban); `product.product` (list); `stock.move.line` (form); `stock.picking.type` (kanban); `stock.picking` (form); `stock.scrap` (form); `stock_barcode.cancel.operation` (form)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
