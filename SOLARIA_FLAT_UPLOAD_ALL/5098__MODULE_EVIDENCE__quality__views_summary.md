# Views & Navigation Summary — `quality` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `quality` — Quality Base (pack merges: `quality`, `quality_control`) |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Quality worklists live in the Quality app menus (Control Points, Checks, Alerts by team); the wow-moment is a check appearing automatically inside a receipt/manufacturing operation.
- Alert kanban with configurable stages mirrors helpdesk-style triage — familiar UX for quality teams.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Quality | — | quality.group_quality_user |
| Quality / Configuration | — | quality.group_quality_manager |
| Quality / Configuration / Quality Alert Stages | quality_alert_stage_action | base.group_no_one |
| Quality / Configuration / Quality Spreadsheet Templates | quality_spreadsheet_template_action_config | — |
| Quality / Configuration / Quality Tags | quality_tag_action | base.group_no_one |
| Quality / Configuration / Quality Teams | quality_alert_team_action_config | — |
| Quality / Overview | quality_alert_team_action | — |
| Quality / Products | — | — |
| Quality / Products / Lots/Serial Numbers | action_production_lot_form | stock.group_production_lot |
| Quality / Products / Product Variants | product_normal_action | product.group_product_variant |
| Quality / Products / Products | product_template_action_product | — |
| Quality / Quality Control | — | — |
| Quality / Quality Control / Control Points | quality_point_action | quality.group_quality_manager |
| Quality / Quality Control / Quality Alerts | quality_alert_action_check | — |
| Quality / Quality Control / Quality Checks | quality_check_action_main | — |
| Quality / Reporting | — | quality.group_quality_manager |
| Quality / Reporting / menu_quality_alert_report | quality_alert_action_report | — |
| Quality / Reporting / menu_quality_check_report | quality_check_action_report | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Quality Alerts | quality.alert | kanban,list,form,pivot,graph,calendar |
| Quality Alerts | quality.alert | kanban,list,form,pivot,graph,calendar,activity |
| Quality Alerts Analysis | quality.alert | graph,pivot,kanban,list,form,calendar |
| Quality Checks SPC | quality.check | graph |
| Quality Checks | quality.check | list,form |
| Quality Checks | quality.check | list,form |
| Quality Checks | quality.check | list,form |
| Quality Checks | quality.check | list,kanban,form,pivot,graph,activity |
| Quality Check Analysis | quality.check | graph,pivot,kanban,list,form |
| Quality Overview | quality.alert.team | kanban,form |
| Quality Teams | quality.alert.team | list,kanban,form |
| Quality Spreadsheet Templates | quality.spreadsheet.template | list |
| Quality Tags | quality.tag | list,form |
| Quality Alert Stages | quality.alert.stage | list,kanban,form |
| Control Points | quality.point | list,kanban,form |
| Quality Check | quality.check.wizard | form |

## View inventory

- Primary views defined: 29 (list: 7, form: 6, kanban: 6, search: 4, pivot: 2, graph: 2, activity: 1, calendar: 1)
- Inheriting views (UI extensions of other modules): 12
- Richest UI objects: `quality.check` (activity, form, graph, kanban, list, pivot, search); `quality.alert` (calendar, form, graph, kanban, list, pivot, search); `quality.point` (form, kanban, list, search); `quality.alert.team` (form, kanban, list); `quality.tag` (list, search); `quality.alert.stage` (kanban, list); `quality.spreadsheet.template` (list); `quality.check.wizard` (form)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Worksheet Report - External (PDF) | quality.check | qweb-pdf |
| Worksheet Report - Internal (PDF) | quality.check | qweb-pdf |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
