# Security & Access Summary — `account_reports` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `account_reports` — Accounting Reports |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Report access follows accounting groups; the sensitive decision is WHO sees management-level reports (Executive Summary) vs operational ledgers — design read-only finance-viewer roles deliberately.
- Automated report sending (cron) means distribution lists are a governance object — review recipients as part of close controls.

## Access rights (ir.model.access) — 37 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_account_user | `account_report_annotation`, `account_return`, `account_return_check`, `account_return_check_template`, `account_return_creation_wizard`, `account_return_payment_wizard` +1 more | `account_multicurrency_revaluation_wizard`, `account_report_file_download_error_wizard`, `account_reports_export_wizard`, `account_reports_export_wizard_format` | — |
| group_account_readonly | — | — | `account_report_annotation`, `account_report_budget`, `account_report_budget_item`, `account_report_horizontal_group`, `account_report_horizontal_group_rule`, `account_return` +3 more |
| group_account_basic | — | — | `account_report_budget`, `account_report_horizontal_group`, `account_report_horizontal_group_rule`, `account_return`, `account_return_check`, `account_return_type` +1 more |
| group_account_manager | `account_report_budget`, `account_report_budget_item`, `account_report_horizontal_group`, `account_report_horizontal_group_rule`, `account_return_type`, `account_tax_unit` | — | — |
| group_account_invoice | `account_report_send` | — | `account_report_annotation` |
| group_user | — | `account_reports.account_audit_account_status` | `account_reports.qr_code_payment_wizard` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Account Returns multi-company | account.return | `[('company_ids', 'in', company_ids)]` |
| Account Returns multi-company | account.return | `['|', ('tax_unit_id.main_company_id', 'in', company_ids), ('company_id', 'in', company_ids` |
| Account Returns Check multi-company | account.return.check | `[('return_id.company_ids', 'in', company_ids)]` |
| Account Returns Check multi-company | account.return.check | `['|', ('return_id.tax_unit_id.main_company_id', 'in', company_ids), ('return_id.company_id` |
| Account Report Budget multi-company | account.report.budget | `[('company_id', 'in', company_ids)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
