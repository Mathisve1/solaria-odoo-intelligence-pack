# Security & Access Summary — `hr` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `hr` — Employees |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- HR officer vs own-employee access: employees see limited own data; HR data is sensitive — involve privacy/works council early in role design.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| Officer: Manage all employees | group_hr_user | group_user |
| Administrator | group_hr_manager | — |

## Access rights (ir.model.access) — 26 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_hr_user | `hr_bank_account_allocation_wizard_line`, `hr_contract_type`, `hr_department`, `hr_departure_reason`, `hr_employee`, `hr_employee_category` +5 more | `hr_bank_account_allocation_wizard`, `hr_departure_wizard`, `hr_version_wizard` | — |
| group_hr_manager | `hr_payroll_structure_type`, `hr_version`, `hr_work_location`, `mail.mail_activity_plan`, `mail.mail_activity_plan_template`, `resource.resource_resource` | — | — |
| group_user | — | — | `hr_department`, `hr_employee_category`, `hr_employee_public`, `hr_job`, `hr_work_location` |
| group_system | — | — | `hr_employee` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Employee multi company rule | hr.employee | `['|', '|', '|', ('company_id', 'in', company_ids + [False]), ('parent_id.user_id', '=', us` |
| Department multi company rule | hr.department | `[('company_id', 'in', company_ids + [False])]` |
| Employee multi company rule | hr.employee.public | `['|', '|', '|', ('company_id', 'in', company_ids + [False]), ('parent_id.user_id', '=', us` |
| Job multi company rule | hr.job | `[('company_id', 'in', company_ids + [False])]` |
| HR: Prevent non HR officers from accessing employee bank accounts | res.partner.bank | `[('partner_id.employee_ids', '=', False)]` |
| HR: Allow HR officers from accessing employee bank accounts | res.partner.bank | `[(1, '=', 1)]` |
| HR Contract Type: Multi Company | hr.contract.type | `['|', ('country_id', '=', False), ('country_id', 'in', user.env.companies.country_id.ids)]` |
| Manager can edit employee plan | mail.activity.plan | `[('res_model', '=', 'hr.employee')]` |
| Manager can edit employee plan template | mail.activity.plan.template | `[('plan_id.res_model', '=', 'hr.employee')]` |
| Departure Reason: multi company | hr.departure.reason | `[('country_code', 'in', user.env.companies.mapped('country_code') + [False])]` |
| HR Contract: Contract Manager | hr.version | `[(1, '=', 1)]` |
| HR Contract: Multi Company | hr.version | `[('company_id', 'in', company_ids)]` |
| HR Payroll Structure Type: Multi Company | hr.payroll.structure.type | `['|', ('country_id', '=', False), ('country_id', 'in', user.env.companies.mapped('country_` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
