# Views & Navigation Summary — `project` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `project` — Project |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Project kanban with stage columns and task kanban are the visual core; burndown-style analysis via pivot views.
- Per-project task views (embedded actions) show how each project can feel like its own workspace.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Activity Plans | mail_activity_plan_action_config_project_task_plan | — |
| Activity Types | mail_activity_type_action_config_project_types | — |
| All Tasks | action_view_all_task | — |
| Configuration | — | project.group_project_manager |
| Customer Ratings | rating_rating_action_project_report | — |
| My Tasks | action_view_my_task | — |
| Project | — | group_project_manager,group_project_user |
| Project Roles | project_roles_action | — |
| Project Stages | project_project_stage_configure | project.group_project_stages |
| Projects | open_view_project_all | — |
| Projects | open_view_project_all_group_stage | project.group_project_stages |
| Projects | open_view_project_all_config_group_stage | project.group_project_stages |
| Projects | open_view_project_all_config | — |
| Reporting | — | — |
| Settings | project_config_settings_action | base.group_system |
| Tags | project_tags_action | — |
| Task Stages | open_task_type_form | base.group_no_one |
| Tasks | — | — |
| Tasks Analysis | action_project_task_user_tree | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Tasks Analysis | report.project.task.user | graph,pivot |
| Burndown Chart | project.task.burndown.chart.report | graph |
| Activity Plans | mail.activity.plan | list,kanban,form |
| Activity Types | mail.activity.type | list,kanban,form |
| Milestones | project.milestone | list,kanban,form |
| Project Stages | project.project.stage | list,kanban,form |
| Send Email | mail.compose.message | form |
| Create a Project | project.project | form |
| Projects | project.project | kanban,list,form |
| Projects | project.project | kanban,list,form,calendar,activity |
| Projects | project.project | list,kanban,form |
| Projects | project.project | list,kanban,form,calendar,activity |
| Project Roles | project.role | list,kanban,form |
| Project Sharing | project.task | kanban,list,form |
| Blocking | project.task | list,kanban,form |
| Sub-tasks | project.task | list,kanban,form |
| Project Sharing Recurrence | project.task | list,kanban,form |
| Tags | project.tags | — |
| Task Stages | project.task.type | list,kanban,form |
| Task Stages | project.task.type | list,kanban,form |
| Tasks | project.task | kanban,list,form,calendar,pivot,graph,activity |
| Sub-tasks | project.task | list,kanban,form,calendar,pivot,graph,activity |
| Send Email | mail.compose.message | form |
| Share Task | task.share.wizard | form |
| Tasks | project.task | kanban,list,form,calendar,pivot,graph,activity |
| My Tasks | project.task | kanban,list,form,calendar,activity,pivot,graph |
| All Tasks | project.task | list,kanban,form,calendar,activity,pivot,graph |
| Partner's Tasks | project.task | list,kanban,form,calendar,pivot,graph,activity |
| Overpassed Tasks | project.task | list,form,calendar,graph,kanban |
| Project's tasks | project.task | list,form,calendar,graph,kanban |
| Tasks | project.task | kanban,list,calendar,pivot,graph,activity,form |
| Add/Remove Followers | mail.followers.edit | form |
| Tasks.test | project.task | kanban,list,form,calendar,pivot,graph,activity |
| Dashboard | project.update | kanban,list,form |
| Ratings | rating.rating | kanban,list,graph,pivot,form |
| Ratings | rating.rating | kanban,list,pivot,graph,form |
| Customer Ratings | rating.rating | kanban,list,pivot,graph,form |
| Settings | res.config.settings | form |
| Share Project | project.share.wizard | form |

## View inventory

- Primary views defined: 57 (form: 23, kanban: 9, search: 8, list: 8, graph: 3, pivot: 2, activity: 2, calendar: 2)
- Inheriting views (UI extensions of other modules): 55
- Richest UI objects: `project.task` (activity, calendar, form, graph, kanban, list, pivot, search); `project.project` (activity, calendar, form, kanban, list, search); `project.project.stage` (form, kanban, list, search); `project.role` (form, kanban, list, search); `project.task.type` (form, kanban, list, search); `project.update` (form, kanban, list, search); `project.milestone` (form, kanban, list); `project.tags` (form, list, search); `report.project.task.user` (graph, pivot); `project.task.burndown.chart.report` (graph, search); `project.project.stage.delete.wizard` (form); `project.share.wizard` (form)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
