# Security & Access Summary — `account` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `account` — Invoicing |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Groups distinguish billing users from accountants/advisers; day-to-day AR clerks usually need less than full accountant rights.
- Record rules enforce multi-company separation on journals/moves — critical in group structures; validate consolidated vs entity access.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| Delivery Address | group_delivery_invoice_address | — |
| Show Accounting Features - Readonly | group_account_readonly | group_user |
| Invoicing | group_account_invoice | group_user |
| Basic | group_account_basic | — |
| Show Full Accounting Features | group_account_user | — |
| Administrator | group_account_manager | — |
| Show Inalterability Features | group_account_secured | — |
| Allow the cash rounding management | group_cash_rounding | — |
| Partial Purchase Deductibility | group_partial_purchase_deductibility | — |
| Validate bank account | group_validate_bank_account | — |

## Access rights (ir.model.access) — 125 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_account_manager | `account_account`, `account_fiscal_position`, `account_fiscal_position_account`, `account_group`, `account_incoterms`, `account_journal` +15 more | `account_code_mapping`, `account_financial_year_op`, `account_lock_exception`, `account_resequence_wizard`, `account_secure_entries_wizard`, `account_setup_bank_manual_config` | `account_analytic_line`, `account_invoice_report`, `account_move`, `account_move_line`, `account_root`, `res_partner` |
| group_account_readonly | — | — | `account_account`, `account_account_tag`, `account_analytic_line`, `account_bank_statement`, `account_bank_statement_line`, `account_cash_rounding` +23 more |
| group_account_invoice | `account_analytic_line`, `account_cash_rounding`, `account_full_reconcile`, `account_move`, `account_move_line`, `account_move_send_batch_wizard` +5 more | `account_autopost_bills_wizard`, `account_move_reversal`, `account_payment_method`, `account_payment_register`, `account_reconcile_line`, `account_reconcile_model` +1 more | `account_account`, `account_account_tag`, `account_bank_statement`, `account_bank_statement_line`, `account_invoice_report`, `account_journal` +4 more |
| group_user | — | — | `account_account`, `account_account_tag`, `account_fiscal_position`, `account_fiscal_position_account`, `account_incoterms`, `account_lock_exception` +8 more |
| group_account_basic | `account_bank_statement`, `account_bank_statement_line`, `account_reconcile_line`, `account_reconcile_model` | — | `account_group`, `account_report`, `account_report_column`, `account_report_expression`, `account_report_line` |
| group_account_user | `account_account_tag`, `account_full_reconcile`, `account_partial_reconcile`, `analytic.account_analytic_account`, `analytic.account_analytic_applicability`, `analytic.account_analytic_plan` | `account.account_accrued_orders_wizard`, `account_automatic_entry_wizard` | — |
| group_portal | — | — | `account.account_move`, `account.account_move_line`, `account_payment_term` |
| group_partner_manager | — | — | `account_account` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| account.analytic.line.billing.user | account.analytic.line | `[(1, '=', 1)]` |
| account.analytic.line.readonly.user | account.analytic.line | `[(1, '=', 1)]` |
| Account Entry | account.move | `[('company_id', 'in', company_ids)]` |
| Entry lines | account.move.line | `[('company_id', 'in', company_ids)]` |
| Multi-ledger multi-company | account.journal.group | `['|', ('company_id', '=', False), ('company_id', 'parent_of', company_ids)]` |
| Journal multi-company | account.journal | `[('company_id', 'parent_of', company_ids)]` |
| Account multi-company | account.account | `[('company_ids', 'parent_of', company_ids)]` |
| Account Group multi-company | account.group | `[('company_id', 'parent_of', company_ids)]` |
| Tax group multi-company | account.tax.group | `[('company_id', 'parent_of', company_ids)]` |
| Tax multi-company | account.tax | `[('company_id', 'parent_of', company_ids)]` |
| Tax Repartition multi-company | account.tax.repartition.line | `['|',('company_id','=',False), ('company_id', 'parent_of', company_ids)]` |
| Invoice Analysis multi-company | account.invoice.report | `[('company_id', 'in', company_ids)]` |
| Account fiscal Mapping company rule | account.fiscal.position | `[('company_id', 'parent_of', company_ids)]` |
| Account bank statement company rule | account.bank.statement | `[('company_id', 'in', company_ids + [False])]` |
| Account bank statement line company rule | account.bank.statement.line | `[('company_id', 'in', company_ids)]` |
| Account reconcile model template company rule | account.reconcile.model | `[('company_id', 'parent_of', company_ids)]` |
| Account reconcile model_line template company rule | account.reconcile.line | `[('company_id', 'parent_of', company_ids)]` |
| Account payment company rule | account.payment | `[('company_id', 'in', company_ids)]` |
| Account payment term company rule | account.payment.term | `['|', ('company_id', '=', False), ('company_id', 'parent_of', company_ids)]` |
| All Journal Entries | account.move | `[(1, '=', 1)]` |
| All Journal Items | account.move.line | `[(1, '=', 1)]` |
| Portal Personal Account Invoices | account.move | `[('state', 'not in', ('cancel', 'draft')), ('move_type', 'in', ('out_invoice', 'out_refund` |
| Portal Invoice Lines | account.move.line | `[('parent_state', 'not in', ('cancel', 'draft')), ('move_id.move_type', 'in', ('out_invoic` |
| Readonly Move | account.move | `[(1, '=', 1)]` |
| Readonly Move Line | account.move.line | `[(1, '=', 1)]` |

*…6 more rules omitted.*

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
