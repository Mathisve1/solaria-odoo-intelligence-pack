# Views & Navigation Summary — `planning` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `planning` — Planning |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Gantt view is the product: drag shifts, copy previous week, publish — rehearse these gestures for demos.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Planning | — | base.group_user |
| Planning / Configuration | — | planning.group_planning_manager |
| Planning / Configuration / Employees | open_view_employee_list_my | planning.group_planning_manager |
| Planning / Configuration / Materials | planning_action_resources | planning.group_planning_manager |
| Planning / Configuration / Roles | planning_action_roles | planning.group_planning_manager |
| Planning / Configuration / Settings | planning_action_settings | base.group_system |
| Planning / Configuration / Shift Templates | planning_action_shift_template | planning.group_planning_manager |
| Planning / My Planning | planning_action_my_calendar | — |
| Planning / Open Shifts | planning_action_open_shifts | planning.group_planning_manager |
| Planning / Reporting | — | planning.group_planning_user |
| Planning / Reporting / Planning Analysis | planning_report_action_analysis | planning.group_planning_user |
| Planning / Schedule | — | planning.group_planning_manager,planning.group_planning_user |
| Planning / Schedule / By Resource | planning_action_schedule_by_resource | — |
| Planning / Schedule / By Role | planning_action_schedule_by_role | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Planning Analysis | planning.analysis.report | pivot,graph |
| My Planning | planning.slot | calendar,gantt,list,form,kanban |
| My Planning | planning.slot | gantt,calendar,list,form |
| Schedule by Resource | planning.slot | gantt,calendar,list,form,kanban,pivot,graph |
| Schedule by Role | planning.slot | gantt,calendar,list,form,kanban,pivot,graph |
| Settings | res.config.settings | form |
| Roles | planning.role | list,kanban,form |
| Shift Templates | planning.slot.template | list,kanban,form |
| Open Shifts | planning.slot | calendar,gantt,list,form,kanban,pivot,graph |
| Materials | resource.resource | list,kanban,form |
| Preview Planning | planning.preview | form |
| Publish & Send the Schedule by Email | planning.send | form |

## View inventory

- Primary views defined: 27 (form: 9, kanban: 4, pivot: 3, list: 3, search: 3, graph: 2, calendar: 2, gantt: 1)
- Inheriting views (UI extensions of other modules): 24
- Richest UI objects: `planning.slot` (calendar, form, gantt, graph, kanban, list, pivot, search); `planning.slot.template` (form, kanban, list, search); `planning.role` (form, kanban, list, search); `planning.analysis.report` (graph, pivot); `hr.employee.public` (form); `resource.resource` (kanban); `planning.preview` (form); `planning.send` (form)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Planning | planning.slot | qweb-pdf |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
