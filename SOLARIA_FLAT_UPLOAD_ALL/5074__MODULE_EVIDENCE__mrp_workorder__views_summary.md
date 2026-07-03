# Views & Navigation Summary — `mrp_workorder` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `mrp_workorder` — MRP II |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Shop Floor app is the demo: operator tablet view, start/pause work order, register production, quality check inline — rehearse on a touchscreen.
- Planning by Work Center Gantt is the planner view — show queue rebalancing by drag.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Overview | mrp_workcenter_kanban_action | mrp.group_mrp_routings |
| Shop Floor | — | group_mrp_wo_shop_floor |
| Work Orders | — | mrp.group_mrp_routings |
| Work Orders / Planning by Production | action_mrp_workorder_dependencies_production | — |
| Work Orders / Planning by Workcenter | action_mrp_workorder_dependencies_workcenter | — |
| menu_shop_floor | action_mrp_display | mrp.group_mrp_user |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| mrp.mrp_production_action | — | list,kanban,form,gantt,calendar,pivot,graph,activity |
| mrp.action_work_orders | — | list,form,gantt,pivot,graph,calendar |
| mrp.mrp_workorder_workcenter_report | — | graph,pivot,list,form,gantt |
| mrp.mrp_workorder_report | — | graph,pivot,list,form,gantt |
| Work Orders | mrp.workorder | kanban,list,form |
| mrp.mrp_workorder_todo | — | list,kanban,form,calendar,pivot,graph,gantt |
| mrp.action_mrp_routing_time | — | graph,pivot,list,form,gantt,calendar |
| mrp.action_mrp_workorder_production_specific | — | list,form,gantt,calendar,pivot,graph |
| mrp.action_mrp_workorder_workcenter | — | gantt,list,form,calendar,pivot,graph |
| mrp.action_mrp_workorder_production | — | gantt,list,form,calendar,pivot,graph |
| Select Employee | hr.employee.public | list |
| Overview | stock.picking.type | kanban |

## View inventory

- Primary views defined: 17 (form: 7, list: 3, search: 3, gantt: 3, kanban: 1)
- Inheriting views (UI extensions of other modules): 28
- Richest UI objects: `mrp.production` (form, gantt, list, search); `quality.point` (form, list, search); `hr.employee` (list, search); `mrp.workorder` (form, gantt); `quality.check` (form); `stock.picking.type` (kanban); `mrp_production.additional.workorder` (form); `propose.change` (form)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
