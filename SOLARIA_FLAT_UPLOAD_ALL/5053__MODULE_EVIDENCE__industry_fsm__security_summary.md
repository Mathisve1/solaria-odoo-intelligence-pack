# Security & Access Summary — `industry_fsm` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `industry_fsm` — Field Service |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Field technicians = project users with mobile focus; consider restricting pricing/margin visibility on-site.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| User | group_fsm_user | group_hr_timesheet_user, group_project_user |
| Administrator | group_fsm_manager | group_fsm_user, group_project_manager |
| Create new quotations directly from the tasks | group_fsm_quotation_from_task | — |

## Access rights (ir.model.access) — 4 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_fsm_user | — | `project_task_stop_timers_wizard`, `project_task_stop_timers_wizard_line` | `report_project_task_user_fsm` |
| group_fsm_manager | — | — | `report_project_task_user_fsm` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Tasks Analysis: FSM project visibility | report.project.task.user.fsm | `[ '|', ('project_id.privacy_visibility', 'in', ['employees', 'portal']), '|', ('project_id` |
| Tasks Analysis: FSM project visibility for manager | report.project.task.user.fsm | `[(1, '=', 1)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
