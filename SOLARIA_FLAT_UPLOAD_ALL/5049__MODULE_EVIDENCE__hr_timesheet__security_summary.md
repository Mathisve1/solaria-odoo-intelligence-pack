# Security & Access Summary — `hr_timesheet` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `hr_timesheet` — Task Logs |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Own timesheets vs all timesheets (officer) split; approval flows arrive with Enterprise grid — decide the validation chain explicitly.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| User: own timesheets only | group_hr_timesheet_user | group_user |
| User: all timesheets | group_hr_timesheet_approver | group_hr_timesheet_user |
| Administrator | group_timesheet_manager | group_hr_timesheet_approver, group_hr_user |

## Existing groups this module modifies

These records extend groups owned by other modules (typically adding implied rights) — they do not create new roles:

| Existing group (reference) | Rights/groups implied by this module |
|---|---|
| project.group_project_manager | group_hr_timesheet_approver |

## Access rights (ir.model.access) — 7 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_hr_timesheet_user | `account_analytic_line_calendar_employee`, `analytic.account_analytic_line` | `analytic.account_analytic_account` | `project_project`, `uom.uom_uom` |
| group_user | — | — | `timesheets_analysis_report` |
| group_hr_user | — | `hr_employee_delete_wizard` | — |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| account.analytic.line.timesheet.portal.user | account.analytic.line | `[ ('project_id', '!=', False), ('message_partner_ids', 'child_of', [user.partner_id.commer` |
| account.analytic.line.timesheet.user | account.analytic.line | `[ ('user_id', '=', user.id), ('project_id', '!=', False), '|', '|', ('project_id.privacy_v` |
| account.analytic.line.timesheet.approver | account.analytic.line | `[ ('project_id', '!=', False), '|', '|', ('project_id.privacy_visibility', 'in', ['employe` |
| account.analytic.line.timesheet.manager | account.analytic.line | `[('project_id', '!=', False)]` |
| Timesheets Analysis Report multi-company | timesheets.analysis.report | `[('company_id', 'in', company_ids)]` |
| Timesheets Analysis Report user | timesheets.analysis.report | `[ ('has_department_manager_access', '=', True), ]` |
| Timesheets Analysis Report user | timesheets.analysis.report | `[ ('user_id', '=', user.id), '|', ('project_id.privacy_visibility', 'in', ['employees', 'p` |
| Timesheets Analysis Report approver | timesheets.analysis.report | `[ '|', ('project_id.privacy_visibility', 'in', ['employees', 'portal']), ('project_id.mess` |
| Timesheets Analysis Report manager | timesheets.analysis.report | `[(1, '=', 1)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
