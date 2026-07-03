# Security & Access Summary — `purchase` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `purchase` — Purchase |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Approval beyond User/Manager (amount matrices, N-level) is not in Community defaults — that conversation leads to Approvals app (E) or automation.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| User | group_purchase_user | group_user |
| Administrator | group_purchase_manager | — |
| A warning can be set on a product or a customer (Purchase) | group_warning_purchase | — |
| Send an automatic reminder email to confirm delivery | group_send_reminder | — |

## Existing groups this module modifies

These records extend groups owned by other modules (typically adding implied rights) — they do not create new roles:

| Existing group (reference) | Rights/groups implied by this module |
|---|---|
| base.group_user | group_send_reminder |

## Access rights (ir.model.access) — 35 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_purchase_user | `account.account_move`, `purchase_order`, `purchase_order_line` | `account.account_move_line`, `bill_to_po_wizard` | `account.account_account_tag`, `account.account_analytic_line`, `account.account_fiscal_position`, `account.account_journal`, `account.account_partial_reconcile`, `account.account_tax` +6 more |
| group_purchase_manager | `account.account_move_line`, `product.product_pricelist_item`, `product.product_supplierinfo`, `purchase_order`, `purchase_order_line` | `base.res_partner` | `account.account_account`, `account.account_journal`, `account.account_tax`, `purchase_report` |
| group_account_readonly | — | — | `purchase_bill_line_match`, `purchase_order`, `purchase_order_line` |
| group_account_invoice | — | `purchase_bill_line_match`, `purchase_order`, `purchase_order_line` | — |
| group_portal | — | — | `purchase.purchase_order`, `purchase.purchase_order_line` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Purchase Order multi-company | purchase.order | `[('company_id', 'in', company_ids)]` |
| Purchase Order Line multi-company | purchase.order.line | `[('company_id', 'in', company_ids)]` |
| Portal Purchase Orders | purchase.order | `[('partner_id', 'child_of', [user.commercial_partner_id.id])]` |
| Purchase User Account Move Line | account.move.line | `[('move_id.move_type', 'in', ('in_invoice', 'in_refund', 'in_receipt'))]` |
| Purchase User Account Move | account.move | `[('move_type', 'in', ('in_invoice', 'in_refund', 'in_receipt'))]` |
| Portal Purchase Order Lines | purchase.order.line | `[('order_id.partner_id','child_of',[user.commercial_partner_id.id])]` |
| Purchases & Bills Union multi-company | purchase.bill.union | `[('company_id', 'in', company_ids + [False])]` |
| Purchase Order Report multi-company | purchase.report | `[('company_id', 'in', company_ids)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
