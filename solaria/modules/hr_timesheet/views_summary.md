# Views & Navigation Summary — `hr_timesheet` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `hr_timesheet` — Task Logs |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- The My Timesheet list/grid is the adoption battleground — show speed of entry; grid view is Enterprise (timesheet_grid).

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| All Timesheets | timesheet_action_all | hr_timesheet.group_hr_timesheet_approver |
| By Employee | act_hr_timesheet_report | hr_timesheet.group_hr_timesheet_approver |
| By Project | timesheet_action_report_by_project | — |
| By Task | timesheet_action_report_by_task | — |
| Configuration | hr_timesheet_config_settings_action | base.group_system |
| My Timesheets | act_hr_timesheet_line | group_hr_timesheet_user |
| My Timesheets | act_hr_timesheet_line | group_hr_timesheet_approver |
| Reporting | — | group_hr_timesheet_approver |
| Timesheets | — | group_hr_timesheet_user |
| Timesheets | — | group_hr_timesheet_approver |
| Timesheets | — | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Timesheets by Employee | timesheets.analysis.report | pivot,graph |
| Timesheets by Project | timesheets.analysis.report | pivot,graph |
| Timesheets by Task | timesheets.analysis.report | pivot,graph |
| My Timesheets | account.analytic.line | list,form,kanban,pivot,graph |
| Task's Timesheets | account.analytic.line | list |
| Project's Timesheets | account.analytic.line | list |
| All Timesheets | account.analytic.line | list,form,kanban,pivot,graph |
| Timesheets | account.analytic.line | — |
| Timesheets | account.analytic.line | list,kanban,pivot,graph,form |
| project.open_view_project_all | — | — |
| project.open_view_project_all_group_stage | — | — |
| Settings | res.config.settings | form |

## View inventory

- Primary views defined: 19 (graph: 6, pivot: 5, form: 4, list: 2, kanban: 1, calendar: 1)
- Inheriting views (UI extensions of other modules): 35
- Richest UI objects: `account.analytic.line` (calendar, form, graph, kanban, list, pivot); `timesheets.analysis.report` (form, graph, list, pivot); `hr.employee.delete.wizard` (form)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Timesheets | account.analytic.line | qweb-pdf |
| Timesheets | project.task | qweb-pdf |
| Timesheets | project.project | qweb-pdf |
| Timesheets | account.analytic.line | qweb-pdf |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
