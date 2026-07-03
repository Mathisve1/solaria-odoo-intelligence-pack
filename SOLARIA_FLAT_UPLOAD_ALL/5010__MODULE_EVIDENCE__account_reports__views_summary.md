# Views & Navigation Summary — `account_reports` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `account_reports` — Accounting Reports |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- The report menus (Balance Sheet, P&L, Cash Flow, Executive Summary, Trial Balance, GL, Tax Report, Aged partners) ARE the CFO demo — live drill-down from figure to journal entry.
- Report layouts/variants are configuration; country statutory variants arrive via l10n_*_reports modules — check the catalog per country.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Accounting Reports | action_account_report_tree | base.group_no_one |
| Aged Payable | action_account_report_ap | account.group_account_readonly,account.group_account_basic |
| Aged Receivable | action_account_report_ar | account.group_account_readonly,account.group_account_basic |
| Audit | — | account.group_account_readonly |
| Balance Sheet | action_account_report_bs | account.group_account_readonly,account.group_account_basic |
| Cash Flow Statement | action_account_report_cs | account.group_account_readonly,account.group_account_basic |
| Checks | action_view_account_return_check_templates | — |
| Deferred Expenses | action_account_report_deferred_expense | account.group_account_readonly |
| Deferred Revenues | action_account_report_deferred_revenue | account.group_account_readonly |
| Executive Summary | action_account_report_exec_summary | account.group_account_readonly,account.group_account_basic |
| Financial Budgets | action_account_report_budget_tree | base.group_no_one |
| General Ledger | action_account_report_general_ledger | account.group_account_readonly,account.group_account_basic |
| Horizontal Groups | action_account_report_horizontal_groups | base.group_no_one |
| Inventory | — | account.group_account_readonly |
| Journal Audit | action_account_report_ja | account.group_account_readonly |
| Ledgers | — | — |
| Partner Ledger | action_account_report_partner_ledger | account.group_account_readonly,account.group_account_basic |
| Profit and Loss | action_account_report_pl | account.group_account_readonly,account.group_account_basic |
| Regularization Entries | — | account.group_account_readonly |
| Return Types | action_view_account_return_types | account.group_account_readonly |
| Tax Report | action_account_report_gt | account.group_account_readonly,account.group_account_basic |
| Tax Returns | action_server_open_view_account_return | — |
| Trial Balance | action_account_report_coa | account.group_account_readonly,account.group_account_basic |
| Unrealized Currencies | action_account_report_multicurrency_revaluation | base.group_multi_currency |
| Working Files | action_view_account_audit | — |
| menu_action_account_report_sales | action_account_report_sales | account.group_account_readonly,account.group_account_basic |
| menu_view_tax_units | action_view_tax_units | base.group_no_one |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Accounting Reports | account.report | list,form |
| Horizontal Groups | account.report.horizontal.group | list,form |
| Financial Budgets | account.report.budget | list,form |
| Journal Items | account.move.line | list,pivot,graph,kanban |
| Start an Audit | account.return.creation.wizard | — |
| Audit | account.return | kanban,search |
| Balances | account.account | list |
| Cycle | account.return.check | kanban |
| Check Templates | account.return.check.template | list,form |
| Return Types | account.return.type | — |
| Tax Return | account.return | kanban,calendar,search |
| Generate Return | account.return.creation.wizard | — |
| Tax Units | account.tax.unit | list,form |

## View inventory

- Primary views defined: 37 (form: 15, list: 11, search: 7, kanban: 3, calendar: 1)
- Inheriting views (UI extensions of other modules): 14
- Richest UI objects: `account.return` (calendar, kanban, search); `account.report` (form, list, search); `account.return.check.template` (form, list, search); `account.return.type` (form, list, search); `account.account` (list, search); `account.report.horizontal.group` (form, list); `account.report.budget` (form, list); `account.return.check` (kanban, search); `account.tax.unit` (form, list); `account.report.line` (form); `account.report.expression` (form); `account.report.external.value` (list)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
