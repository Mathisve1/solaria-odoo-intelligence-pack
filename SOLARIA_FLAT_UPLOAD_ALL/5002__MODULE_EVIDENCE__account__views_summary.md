# Views & Navigation Summary — `account` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `account` — Invoicing |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Menu structure mirrors finance org: Customers (AR), Vendors (AP), Accounting (journals), Reporting, Configuration.
- Invoice form doubles as vendor bill form (move types on account.move) — one model, many faces; explains UI consistency.
- Community reporting here is operational (ledgers, aged balances via views); statutory reports live in Enterprise account_reports.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Accounting | — | account.group_account_readonly |
| Accounting | — | account.group_account_manager |
| Analytic Accounting | — | analytic.group_analytic_accounting |
| Analytic Distribution Models | action_analytic_distribution_model | analytic.group_analytic_accounting |
| Analytic Items | account_analytic_line_action_entries | analytic.group_analytic_accounting |
| Analytic Plans | account_analytic_plan_action | analytic.group_analytic_accounting |
| Analytic Report | action_analytic_reporting | account.group_account_readonly |
| Closing | — | account.group_account_readonly |
| Closing / Secure Entries | action_view_account_secure_entries_wizard | base.group_no_one,account.group_account_secured |
| Configuration | — | account.group_account_manager |
| Control | — | account.group_account_readonly |
| Currencies | action_currency_form | — |
| Customers | — | — |
| Customers | res_partner_action_customer | — |
| Dashboard | open_account_journal_dashboard_kanban | account.group_account_basic |
| Invoice Analysis | action_account_invoice_report_all | — |
| Invoicing | — | account.group_account_readonly,account.group_account_invoice |
| Invoicing | — | account.group_account_invoice,account.group_account_readonly |
| Logs | — | — |
| Logs / Audit Trail | action_account_audit_trail_report | — |
| Management | — | — |
| Multi-Ledger | action_account_journal_group_list | account.group_account_readonly |
| Online Payments | — | account.group_account_manager |
| Partner Reports | — | — |
| Payments | action_account_payments | — |
| Payments | action_account_payments_payable | — |
| Product Categories | product_category_action_form | — |
| Products | product_product_action_sellable | — |
| Products | product_product_action_purchasable | — |
| Reporting | — | account.group_account_readonly,account.group_account_invoice |
| Reporting | — | account.group_account_readonly |
| Review | — | account.group_account_readonly |
| Settings | action_account_config | base.group_system |
| Statement Reports | — | account.group_account_readonly,account.group_account_basic |
| Taxes & Fiscal | — | — |
| Transactions | — | account.group_account_readonly |
| Vendors | — | — |
| Vendors | res_partner_action_supplier | — |
| account_analytic_def_account | action_account_analytic_account_form | analytic.group_analytic_accounting |
| menu_action_account_fiscal_position_form | action_account_fiscal_position_form | — |
| menu_action_account_form | action_account_form | account.group_account_readonly |
| menu_action_account_journal_form | action_account_journal_form | account.group_account_manager |
| menu_action_account_moves_all | action_account_moves_all | account.group_account_readonly |
| menu_action_incoterm_open | action_incoterms_tree | base.group_no_one |
| menu_action_move_in_invoice_type | action_move_in_invoice | — |

*…8 further menus omitted; full detail available on request from source.*

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Settings | res.config.settings | form |
| Bills Analysis | account.invoice.report | graph,pivot |
| Invoices Analysis | account.invoice.report | graph,pivot |
| Chart of Accounts | account.account | list,kanban,form |
| analytic.account_analytic_line_action_entries | — | — |
| Analytic Reporting | account.analytic.line | — |
| Bank Statements | account.bank.statement | list,pivot,graph,form |
| Credit Statements | account.bank.statement | list,pivot,graph |
| Cash Registers | account.bank.statement | list,pivot,graph |
| Cash Roundings | account.cash.rounding | list,form |
| Incoterms | account.incoterms | list,form |
| Dashboard | account.journal | kanban,form |
| Journals | account.journal | list,kanban,form |
| Multi-ledger | account.journal.group | — |
| Journal Items | account.move.line | — |
| Journal Items | account.move.line | list,pivot,graph,kanban |
| Journal Items | account.move.line | list,pivot,graph,kanban |
| Sales | account.move.line | list,pivot,graph,kanban |
| Purchases | account.move.line | list,pivot,graph,kanban |
| Bank and Cash | account.move.line | list,pivot,graph,kanban |
| Miscellaneous | account.move.line | list,pivot,graph,kanban |
| Partner Ledger | account.move.line | list,pivot,graph |
| Journal Items | account.move.line | — |
| Journal Items | account.move.line | list,pivot,graph,kanban |
| Journal Entries | account.move | list,kanban,form,activity |
| Journal Entries | account.move | list,kanban,form,activity |
| Invoices | account.move | list,kanban,form,activity |
| Invoices | account.move | list,kanban,form,activity |
| Credit Notes | account.move | list,kanban,form,activity |
| Bills | account.move | list,kanban,form,activity |
| Bills | account.move | list,kanban,form,activity |
| Refunds | account.move | list,kanban,form,activity |
| Amounts to Settle | account.move.line | list |
| Entries | account.move | — |
| Credit Notes | account.move | list,kanban,form,activity |
| Payment Terms | account.payment.term | list,kanban,form |
| Payments | account.payment | list,kanban,form,graph,activity |
| Customer Payments | account.payment | list,kanban,form,graph,activity |
| Vendor Payments | account.payment | list,kanban,form,graph,activity |
| Internal Transfers | account.payment | list,kanban,form,graph |
| Send receipt by email | mail.compose.message | form |
| Send receipts by email | mail.compose.message | form |
| Reconciliation Models | account.reconcile.model | list,form |
| Taxes | account.tax | list,kanban,form |
| Tax Groups | account.tax.group | list,form |

*…16 more actions omitted.*

## View inventory

- Primary views defined: 96 (form: 34, list: 25, search: 20, kanban: 9, graph: 4, pivot: 3, activity: 1)
- Inheriting views (UI extensions of other modules): 51
- Richest UI objects: `account.move.line` (form, graph, kanban, list, pivot, search); `account.move` (activity, form, kanban, list, search); `account.payment` (form, graph, kanban, list, search); `account.invoice.report` (graph, list, pivot, search); `account.account` (form, kanban, list, search); `account.bank.statement` (graph, list, pivot, search); `account.journal` (form, kanban, list, search); `account.payment.term` (form, kanban, list, search); `account.tax` (form, kanban, list, search); `account.account.tag` (form, list, search); `account.cash.rounding` (form, list, search); `account.group` (form, list, search)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Invoice PDF | account.move | qweb-pdf |
| Original Bills | account.move | qweb-pdf |
| PDF without Payment | account.move | qweb-pdf |
| Payment Receipt | account.payment | qweb-pdf |
| Statement | account.bank.statement | qweb-pdf |
| Hash integrity result PDF | res.company | qweb-pdf |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
