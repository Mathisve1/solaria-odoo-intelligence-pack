# Views & Navigation Summary — `account_accountant` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `account_accountant` — Invoicing |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- The Reconcile view is the flagship screen: bank lines matched against invoices/payments — rehearse with realistic statement data.
- Lock Dates menu is the governance demo moment for CFOs (period control with exception workflow).

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Lock Dates… | action_view_account_change_lock_date | account.group_account_manager |
| Reconcile | action_move_line_posted_unreconciled | account.group_account_user |
| account_tag_menu | account_tag_action | base.group_no_one |
| menu_account_fiscal_year | actions_account_fiscal_year | account_accountant.group_fiscal_year |
| menu_account_group | action_account_group_tree | base.group_no_one |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Account Tags | account.account.tag | — |
| Account Groups | account.group | list,form |
| Fiscal Years | account.fiscal.year | list,form |
| Reconcile automatically | account.auto.reconcile.wizard | form |
| Journal Items to reconcile | account.move.line | list |
| account.action_account_reconcile_model | — | — |
| Create Statement | account.bank.statement | form |
| New Transaction | account.bank.statement.line | form |
| Bank Matching | account.bank.statement.line | list,kanban |
| Bank Matching | account.bank.statement.line | kanban,list |
| Lock Journal Entries | account.change.lock.date | form |

## View inventory

- Primary views defined: 21 (form: 10, list: 5, search: 4, kanban: 2)
- Inheriting views (UI extensions of other modules): 13
- Richest UI objects: `account.move.line` (form, kanban, list, search); `account.bank.statement.line` (form, kanban, list, search); `account.fiscal.year` (form, list, search); `account.bank.statement` (form); `account.move` (form); `account.account` (list); `account.auto.reconcile.wizard` (form); `account.change.lock.date` (form); `account.reconcile.wizard` (form)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
