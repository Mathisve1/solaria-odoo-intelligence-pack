# Security & Access Summary — `point_of_sale` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `point_of_sale` — Point of Sale |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Cashier vs Administrator; session controls (cash control, price edits, discounts) are settings+groups — align with retail loss-prevention policy.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| User | group_pos_user | — |
| Administrator | group_pos_manager | group_stock_user |
| Preset Menu | group_pos_preset | — |

## Existing groups this module modifies

These records extend groups owned by other modules (typically adding implied rights) — they do not create new roles:

| Existing group (reference) | Rights/groups implied by this module |
|---|---|
| base.group_user | group_product_variant |

## Access rights (ir.model.access) — 54 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_pos_user | `pos_bill`, `pos_confirmation_wizard`, `pos_order`, `pos_order_line`, `pos_pack_operation_lot`, `pos_payment` +2 more | `account.account_bank_statement_line`, `pos_close_session_wizard`, `pos_config`, `pos_make_invoice`, `pos_session` | `account.account_cash_rounding`, `account.account_journal`, `account_move`, `account_move_line`, `barcodes.barcode_nomenclature`, `barcodes.barcode_rule` +13 more |
| group_pos_manager | `account.account_bank_statement_line`, `barcodes.barcode_nomenclature`, `barcodes.barcode_rule`, `pos_category`, `pos_config`, `pos_confirmation_wizard` +6 more | `pos_daily_sales_reports_wizard`, `pos_details_wizard`, `pos_make_payment` | `account.account_payment_method`, `account.account_payment_method_line`, `stock.stock_location`, `stock.stock_warehouse` |
| group_stock_user | — | — | `pos_order` |
| group_system | — | `pos_config` | — |
| group_user | — | — | `pos_category` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Point Of Sale Bank Statement Accountant | account.bank.statement | `[(1, '=', 1)]` |
| Point Of Sale Bank Statement Line POS User | account.bank.statement.line | `[('pos_session_id', '!=', False)]` |
| Point Of Sale Bank Statement Line Accountant | account.bank.statement.line | `[(1, '=', 1)]` |
| Point Of Sale Order | pos.order | `[('company_id', 'in', company_ids)]` |
| Point Of Sale Order Line | pos.order.line | `[('company_id', 'in', company_ids)]` |
| Point Of Sale Session | pos.session | `[('config_id.company_id', 'in', company_ids)]` |
| Point Of Sale Config | pos.config | `[('company_id', 'in', company_ids)]` |
| Point Of Sale Order Analysis multi-company | report.pos.order | `[('company_id', 'in', company_ids)]` |
| PoS Payment Method | pos.payment.method | `[('company_id', 'in', company_ids)]` |
| PoS Payment | pos.payment | `[('company_id', 'in', company_ids)]` |
| Invoice POS User | account.move | `[('pos_order_ids', '!=', False)]` |
| Invoice Line POS User | account.move.line | `[('move_id.pos_order_ids', '!=', False)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
