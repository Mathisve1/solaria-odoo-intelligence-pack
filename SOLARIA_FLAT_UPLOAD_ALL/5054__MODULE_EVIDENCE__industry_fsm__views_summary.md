# Views & Navigation Summary — `industry_fsm` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `industry_fsm` — Field Service |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- My Tasks map/list with start/stop timer, worksheet and 'create invoice' button — built for a phone demo.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Activity Plans | mail_activity_plan_action_config_project_task_plan | industry_fsm.group_fsm_manager |
| Activity Types | mail_activity_type_action_config_project_types | industry_fsm.group_fsm_manager |
| Field Service | — | industry_fsm.group_fsm_user |
| Field Service / All Tasks | — | industry_fsm.group_fsm_manager |
| Field Service / All Tasks / All Tasks | project_task_all_fsm_server_action | industry_fsm.group_fsm_manager |
| Field Service / All Tasks / To Schedule | project_task_to_schedule_fsm_server_action | industry_fsm.group_fsm_manager |
| Field Service / Configuration | — | industry_fsm.group_fsm_manager |
| Field Service / My Tasks | — | industry_fsm.group_fsm_user |
| Field Service / My Tasks / Map | project_task_fsm_map_server_action | industry_fsm.group_fsm_user |
| Field Service / My Tasks / Tasks | project_task_fsm_server_action | industry_fsm.group_fsm_user |
| Field Service / Planning | — | industry_fsm.group_fsm_manager |
| Field Service / Planning / By Location | project_task_fsm_planning_groupby_location_server_action | industry_fsm.group_fsm_manager |
| Field Service / Planning / By Project | project_task_fsm_planning_groupby_project_server_action | industry_fsm.group_fsm_manager |
| Field Service / Planning / By User | project_task_fsm_planning_groupby_user_server_action | industry_fsm.group_fsm_manager |
| Field Service / Reporting | — | — |
| Field Service / Reporting / Customer Ratings | rating_rating_action_fsm | — |
| Field Service / Reporting / Tasks Analysis | project_task_user_action_report_fsm | — |
| Projects | project_project_action_only_fsm | industry_fsm.group_fsm_manager |
| Settings | res_config_settings_action_fsm | base.group_system |
| Stages | project_task_type_action_fsm | industry_fsm.group_fsm_manager |
| Tags | project_tags_action | industry_fsm.group_fsm_manager |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Tasks Analysis | report.project.task.user.fsm | graph,pivot |
| My Tasks | project.task | kanban,list,map,calendar,gantt,form,graph,pivot,activity |
| My Tasks | project.task | kanban,list,map,calendar,gantt,form,graph,pivot,activity |
| Map | project.task | map,calendar,gantt,kanban,list,pivot,graph,activity,form |
| Map | project.task | map,calendar,gantt,kanban,list,pivot,graph,activity,form |
| All Tasks | project.task | list,kanban,map,calendar,gantt,activity,pivot,graph,form |
| All Tasks | project.task | list,kanban,map,calendar,gantt,activity,pivot,graph,form |
| To Schedule | project.task | list,kanban,map,calendar,gantt,activity,pivot,graph,form |
| To Schedule | project.task | list,kanban,map,calendar,gantt,activity,pivot,graph,form |
| Tasks | project.task | kanban,list,gantt,calendar,map,pivot,graph,form,activity |
| Planning by User | project.task | gantt,calendar,map,list,kanban,activity,pivot,graph,form |
| Planning by User | project.task | gantt,calendar,map,list,kanban,activity,pivot,graph,form |
| Planning by Project | project.task | gantt,calendar,map,list,kanban,activity,pivot,graph |
| Planning by Project | project.task | gantt,calendar,map,list,kanban,pivot,graph,activity |
| Planning by Location | project.task | gantt,calendar,map,list,kanban,pivot,graph,activity |
| Planning by Location | project.task | gantt,calendar,map,list,kanban,activity,pivot,graph |
| Settings | res.config.settings | form |
| Create a Project | project.project | form |
| Projects | project.project | list,kanban,form |
| Stages | project.task.type | list,kanban,form |
| Customer Ratings | rating.rating | kanban,list,pivot,graph,form |

## View inventory

- Primary views defined: 4 (form: 2, list: 1, calendar: 1)
- Inheriting views (UI extensions of other modules): 51
- Richest UI objects: `report.project.task.user.fsm` (list); `project.task` (calendar); `account.analytic.line` (form); `project.task.stop.timers.wizard` (form)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Field Service Report | project.task | qweb-pdf |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
