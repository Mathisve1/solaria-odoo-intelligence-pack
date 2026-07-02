# Views & Navigation Summary — `mrp` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `mrp` — Manufacturing |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- BoM form (components + operations tabs) and MO form (components/work orders/traceability) are the anchor screens.
- Kanban/list of MOs by state supports the planning story; Gantt-level scheduling views come with Enterprise modules.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Configuration | — | group_mrp_manager |
| Configuration / Settings | action_mrp_configuration | base.group_system |
| Configuration / menu_mrp_routing_action | mrp_routing_action | group_mrp_routings |
| Configuration / menu_view_resource_search_mrp | mrp_workcenter_action | group_mrp_routings |
| Manufacturing | — | group_mrp_user,group_mrp_manager |
| Manufacturings | action_picking_tree_mrp_operation | stock.group_stock_manager,stock.group_stock_user |
| Operations | — | — |
| Operations / Scrap | action_stock_scrap | — |
| Operations / Unbuild Orders | mrp_unbuild | — |
| Operations / Work Orders | mrp_workorder_todo | group_mrp_routings |
| Operations / menu_mrp_production_action | mrp_production_action | — |
| Planning | — | — |
| Planning / menu_procurement_compute_mrp | ir_cron_scheduler_action_ir_actions_server | base.group_no_one |
| Products | — | — |
| Products / Lots/Serial Numbers | action_production_lot_form | stock.group_production_lot |
| Products / Product Variants | mrp_product_variant_action | product.group_product_variant |
| Products / Products | product_template_action | — |
| Products / menu_mrp_bom_form_action | mrp_bom_form_action | — |
| Reporting | — | — |
| Reporting / Work Orders | mrp_workorder_report | group_mrp_routings |
| Reporting / menu_mrp_workcenter_productivity_report | mrp_workcenter_productivity_report | group_mrp_routings |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Bills of Materials | mrp.bom | list,kanban,form |
| Bill of Materials | mrp.bom | — |
| Bill of Materials | mrp.bom | — |
| Manufacturing Orders | mrp.production | list,kanban,form,calendar,pivot,graph,activity |
| Manufacturing Orders | mrp.production | list,kanban,form |
| Manufacturing Orders | mrp.production | form |
| Operations | mrp.routing.workcenter | list,kanban,form |
| Stock Moves | stock.move.line | list,form |
| Unbuild Orders | mrp.unbuild | list,kanban,form,activity |
| Work Orders | mrp.workorder | list,form,pivot,graph,calendar |
| Overall Equipment Effectiveness | mrp.workcenter.productivity | graph,pivot,list,form |
| Productivity Losses | mrp.workcenter.productivity | list,form,graph,pivot |
| Work Orders Performance | mrp.workorder | graph,pivot,list,form |
| Work Orders Analysis | mrp.workorder | graph,pivot,list,form |
| Work Centers | mrp.workcenter | list,kanban,form |
| Work Centers Overview | mrp.workcenter | kanban,form |
| Overall Equipment Effectiveness | mrp.workcenter.productivity | graph,pivot,list,form |
| Work Orders | mrp.workorder | graph,pivot,list,form,calendar |
| Work Orders | mrp.workorder | list,form,calendar,pivot,graph |
| Work Orders Planning | mrp.workorder | list,form,calendar,pivot,graph |
| Work Orders Planning | mrp.workorder | list,form,calendar,pivot,graph |
| Work Orders | mrp.workorder | form |
| Work Orders | mrp.workorder | list,kanban,form,calendar,pivot,graph |
| Work Center Loads | mrp.workorder | graph,pivot |
| Products | product.template | kanban,list,form |
| Product Variants | product.product | kanban,list,form |
| stock.action_product_stock_view | — | — |
| Settings | res.config.settings | form |
| Inventory Moves | stock.move.line | list,form |
| Manufacturings | mrp.production | list,kanban,form,calendar,activity |
| Manufacturings | mrp.production | list,kanban,form,calendar,activity |
| Change Quantity To Produce | change.production.qty | form |
| Consumption Warning | mrp.consumption.warning | form |
| You produced less than the initial demand | mrp.production.backorder | form |
| Assign Serial Numbers | mrp.production.serials | form |
| Split productions | mrp.production.split.multi | form |
| Split production | mrp.production.split | form |
| Block Workcenter | mrp.workcenter.productivity | form |
| Block Workcenter | mrp.workcenter.productivity | form |

## View inventory

- Primary views defined: 55 (form: 18, search: 9, list: 8, kanban: 8, graph: 5, pivot: 4, calendar: 2, activity: 1)
- Inheriting views (UI extensions of other modules): 30
- Richest UI objects: `mrp.production` (activity, calendar, form, graph, kanban, list, pivot, search); `mrp.workorder` (calendar, form, graph, kanban, list, pivot, search); `mrp.workcenter.productivity` (form, graph, list, pivot, search); `mrp.bom` (form, kanban, list, search); `mrp.routing.workcenter` (form, kanban, list, search); `mrp.unbuild` (form, kanban, list, search); `mrp.workcenter` (form, kanban, list, search); `mrp.workcenter.productivity.loss` (form, kanban, list, search); `mrp.bom.byproduct` (form); `mrp.bom.line` (form); `change.production.qty` (form); `mrp.consumption.warning` (form)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Production Order | mrp.production | qweb-pdf |
| BoM Overview | mrp.bom | qweb-pdf |
| MO Overview | mrp.production | qweb-pdf |
| Finished Product Label (ZPL) | mrp.production | qweb-text |
| Finished Product Label (PDF) | mrp.production | qweb-pdf |
| Work Order | mrp.workorder | qweb-pdf |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
