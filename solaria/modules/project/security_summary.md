# Security & Access Summary — `project` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `project` — Project |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Project visibility is per-project (followers/internal/portal setting) plus record rules — powerful but must be designed, not assumed.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| User | group_project_user | group_user |
| Administrator | group_project_manager | group_project_user, group_mail_canned_response_admin |
| Use Stages on Project | group_project_stages | — |
| Use Recurring Tasks | group_project_recurring_tasks | — |
| Use Task Dependencies | group_project_task_dependencies | — |
| Use Milestones | group_project_milestone | — |

## Access rights (ir.model.access) — 55 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_project_manager | `analytic.account_analytic_account`, `analytic.account_analytic_line`, `mail.mail_activity_plan`, `mail.mail_activity_plan_template`, `mail.mail_activity_type`, `project.project_task_burndown_chart_report` +13 more | `project_share_wizard`, `task_share_wizard` | `report_project_task_user` |
| group_project_user | `project_milestone`, `project_task`, `project_task_recurrence`, `project_task_type`, `project_update`, `resource.resource_calendar_leaves` | `project.project_template_create_wizard`, `project.project_template_role_to_users_map` | `analytic.account_analytic_account`, `base.res_partner`, `project.project_task_burndown_chart_report`, `project_collaborator`, `project_project`, `project_role` +3 more |
| group_user | `project_task_stage_personal` | — | `project_milestone`, `project_project`, `project_project_stage`, `project_tags`, `project_task`, `project_task_type` +1 more |
| group_portal | — | `project_update` | `project.project_project`, `project.project_tags`, `project.project_task`, `project.project_task_type`, `project_collaborator`, `project_milestone` |
| group_partner_manager | — | `task_share_wizard` | — |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Project: multi-company | project.project | `[('company_id', 'in', company_ids + [False])]` |
| Project Stage: multi-company | project.project.stage | `[('company_id', 'in', company_ids + [False])]` |
| Project: project manager: see all | project.project | `[(1, '=', 1)]` |
| Project: employees: following required for follower-only projects | project.project | `['|', ('privacy_visibility', 'in', ['employees', 'portal']), ('message_partner_ids', 'in',` |
| Project/Task: multi-company | project.task | `[('company_id', 'in', company_ids + [False])]` |
| Project/Task: employees: follow required for follower-only projects | project.task | `[ '|', '&', ('project_id', '!=', False), '|', ('project_id.privacy_visibility', 'in', ['em` |
| Project/Task: project manager: see all tasks linked to a project or its own tasks | project.task | `[ '|', ('project_id', '!=', False), ('user_ids', 'in', user.id), ]` |
| Project/Task Type: manager sees all | project.task.type | `[(1, '=', 1)]` |
| Project/Task Type: see own or unowned stages | project.task.type | `[('user_id', 'in', (False, user.id))]` |
| Project/Task Type: write own stages | project.task.type | `[('user_id', '=', user.id)]` |
| Task Analysis multi-company | report.project.task.user | `[('company_id', 'in', company_ids + [False])]` |
| Project: See my own personal stage | project.task.stage.personal | `[('user_id', '=', user.id)]` |
| Project/Task: project users: follow required for follower-only projects | project.task | `[ '|', '&', ('project_id', '!=', False), '|', ('project_id.privacy_visibility', 'in', ['em` |
| Project: See private tasks | project.task | `[ ('project_id.privacy_visibility', 'in', ['employees', 'portal']), '|', '|', ('project_id` |
| Project: portal users: portal and following | project.project | `[ '&', ('privacy_visibility', 'in', ['invited_users', 'portal']), ('message_partner_ids', ` |
| Project/Collaborator: portal users: can only see his own collobaroration in shared projects | project.collaborator | `[ ('project_id.privacy_visibility', 'in', ['invited_users', 'portal']), ('partner_id', '='` |
| Project/Task: portal users: can only see a task if he's a collaborator of the project and a follower of the task | project.task | `[ ('project_id.privacy_visibility', 'in', ['invited_users', 'portal']), ('active', '=', Tr` |
| Project/Task: portal users: portal user can edit with project sharing feature | project.task | `[ ('project_id.privacy_visibility', 'in', ['invited_users', 'portal']), ('active', '=', Tr` |
| Project/Updates: multi-company | project.update | `['|', ('project_id.company_id', 'in', company_ids), ('project_id.company_id', '=', False)]` |
| Project/Update: employees: follow required for follower-only projects | project.update | `[ '|', ('project_id.privacy_visibility', 'in', ['employees', 'portal']), '|', ('project_id` |
| Tasks Analysis: project visibility User | report.project.task.user | `[ '|', ('project_id.privacy_visibility', 'in', ['employees', 'portal']), '|', ('project_id` |
| Tasks Analysis: project visibility Manager | report.project.task.user | `[(1, '=', 1)]` |
| Project updates : Project user can see all project updates | project.update | `[(1, '=', 1)]` |
| Burndown chart: project visibility User | project.task.burndown.chart.report | `[ '|', ('project_id.privacy_visibility', 'in', ['employees', 'portal']), '|', ('project_id` |
| Burndown chart: project visibility User | project.task.burndown.chart.report | `[(1, '=', 1)]` |

*…6 more rules omitted.*

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
