# Views & Navigation Summary — `hr` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `hr` — Employees |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Employee kanban (photo cards by department) is the classic opener; org chart and HR settings drive the master-data story.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Employees | — | group_hr_manager,group_hr_user,base.group_user |
| Employees / Configuration | — | group_hr_manager |
| Employees / Configuration / Employee | — | — |
| Employees / Configuration / Employee / Onboarding / Offboarding | mail_activity_plan_action | — |
| Employees / Configuration / Employee / Tags | open_view_categ_form | base.group_no_one |
| Employees / Configuration / Employee / Working Schedules | action_resource_calendar_form | — |
| Employees / Configuration / Employee / menu_hr_departure_reason_tree | hr_departure_reason_action | — |
| Employees / Configuration / Employee / menu_hr_work_location_tree | hr_work_location_action | — |
| Employees / Configuration / Recruitment | — | — |
| Employees / Configuration / Recruitment / Contract Templates | action_hr_contract_templates | hr.group_hr_manager |
| Employees / Configuration / Recruitment / menu_view_hr_contract_type | hr_contract_type_action | group_hr_user |
| Employees / Configuration / Recruitment / menu_view_hr_job | action_hr_job | — |
| Employees / Configuration / Settings | hr_config_settings_action | base.group_system |
| Employees / Directory | hr_employee_public_action | — |
| Employees / Employees | open_view_employee_list_my | group_hr_user |
| Employees / Human Resources | — | — |
| Employees / Reporting | — | group_hr_user |
| Employees / menu_hr_department_kanban | hr_department_kanban_action | base.group_user |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Contract Templates | hr.version | list,form |
| Employment Types | hr.contract.type | list |
| Departments | hr.department | list,form,kanban |
| Departments | hr.department | kanban,list,form |
| Departure Reasons | hr.departure.reason | list |
| Employee Tags | hr.employee.category | list,form |
| Employees | hr.employee.public | kanban,list,form |
| Employees | hr.employee | kanban,list,form,activity,graph,pivot |
| Employees | hr.employee | form,list |
| All activities | hr.employee | activity,list,kanban,form,graph,pivot |
| Create a Job Position | hr.job | form |
| Job Positions | hr.job | list,form |
| Employee Records | hr.version | list,graph,pivot |
| Work Locations | hr.work.location | list,form |
| Employee Plans | mail.activity.plan | list,kanban,form |
| Launch Plan | mail.activity.schedule | form |
| Settings | res.config.settings | form |
| Change my Preferences | res.users | form |
| Bank Account Allocations | hr.bank.account.allocation.wizard | form |
| Contract Template Load | hr.version.wizard | form |

## View inventory

- Primary views defined: 39 (list: 13, form: 12, search: 5, kanban: 4, graph: 2, pivot: 2, activity: 1)
- Inheriting views (UI extensions of other modules): 17
- Richest UI objects: `hr.employee` (activity, form, graph, kanban, list, pivot, search); `hr.version` (form, graph, list, pivot, search); `hr.department` (form, kanban, list, search); `hr.employee.public` (form, kanban, list, search); `hr.job` (form, kanban, list, search); `hr.contract.type` (form, list); `hr.departure.reason` (form, list); `hr.employee.category` (form, list); `hr.work.location` (form, list); `hr.bank.account.allocation.wizard` (form); `hr.bank.account.allocation.wizard.line` (list); `hr.version.wizard` (form)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Print Badge | hr.employee | qweb-pdf |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
