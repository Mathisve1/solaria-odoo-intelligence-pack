# Security & Access Summary — `sale` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `sale` — Sales |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Own-documents-only rule for basic salespeople is the default; managers see all. Align commission/territory design with these groups before customizing.
- Portal users see their own orders via portal rules — the customer portal is security-driven, validate with real portal accounts.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| Lock Confirmed Sales | group_auto_done_setting | — |
| Discount on lines | group_discount_per_so_line | — |
| A warning can be set on a product or a customer (Sale) | group_warning_sale | — |
| Pro-forma Invoices | group_proforma_sales | — |

## Access rights (ir.model.access) — 39 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_sale_salesman | `product.product_attribute_custom_value`, `sale_order_line` | `account.account_move_send_batch_wizard`, `account.account_move_send_wizard`, `analytic.account_analytic_account`, `payment.payment_link_wizard`, `sale_advance_payment_inv`, `sale_mass_cancel_orders` +2 more | `account.account_account`, `account.account_account_tag`, `account.account_journal`, `account.account_move`, `account.account_move_line`, `account.account_partial_reconcile` +7 more |
| group_sale_manager | `mail.mail_activity_plan`, `mail.mail_activity_plan_template`, `mail.mail_activity_type`, `product.product_document`, `product.product_pricelist`, `product.product_pricelist_item` +1 more | `base.res_partner` | — |
| group_portal | — | — | `sale.sale_order`, `sale.sale_order_line` |
| group_account_readonly | — | — | `sale_order`, `sale_order_line` |
| group_account_invoice | — | `sale_order`, `sale_order_line` | — |
| group_account_user | — | `sale_order`, `sale_order_line` | — |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Sales Order multi-company | sale.order | `[('company_id', 'in', company_ids)]` |
| Sales Order Line multi-company | sale.order.line | `[('company_id', 'in', company_ids)]` |
| Sales Order Analysis multi-company | sale.report | `[('company_id', 'in', company_ids)]` |
| Portal Personal Quotations/Sales Orders | sale.order | `[('partner_id','child_of',[user.commercial_partner_id.id])]` |
| Portal Sales Orders Line | sale.order.line | `[('order_id.partner_id','child_of',[user.commercial_partner_id.id])]` |
| Personal Orders | sale.order | `['|',('user_id','=',user.id),('user_id','=',False)]` |
| All Orders | sale.order | `[(1,'=',1)]` |
| Personal Orders Analysis | sale.report | `['|',('user_id','=',user.id),('user_id','=',False)]` |
| All Orders Analysis | sale.report | `[(1,'=',1)]` |
| Personal Order Lines | sale.order.line | `['|',('salesman_id','=',user.id),('salesman_id','=',False)]` |
| All Orders Lines | sale.order.line | `[(1,'=',1)]` |
| Personal Invoices Analysis | account.invoice.report | `['|', ('invoice_user_id', '=', user.id), ('invoice_user_id', '=', False)]` |
| All Invoices Analysis | account.invoice.report | `[(1, '=', 1)]` |
| Access every payment transaction | payment.transaction | `[(1, '=', 1)]` |
| Access every payment token | payment.token | `[(1, '=', 1)]` |
| Personal Invoices | account.move | `[('move_type', 'in', ('out_invoice', 'out_refund')), '|', ('invoice_user_id', '=', user.id` |
| All Invoices | account.move | `[('move_type', 'in', ('out_invoice', 'out_refund'))]` |
| Personal Invoice Lines | account.move.line | `[('move_id.move_type', 'in', ('out_invoice', 'out_refund')), '|', ('move_id.invoice_user_i` |
| All Invoice Lines | account.move.line | `[('move_id.move_type', 'in', ('out_invoice', 'out_refund'))]` |
| Personal Invoice Send and Print (single mode) | account.move.send.wizard | `[('move_id.move_type', 'in', ('out_invoice', 'out_refund')), '|', ('move_id.invoice_user_i` |
| Personal Invoice Send and Print (batch mode) | account.move.send.batch.wizard | `[('move_ids.move_type', 'in', ('out_invoice', 'out_refund')), '|', ('move_ids.invoice_user` |
| All Invoice Send and Print (single mode) | account.move.send.wizard | `[('move_id.move_type', 'in', ('out_invoice', 'out_refund'))]` |
| All Invoice Send and Print (batch mode) | account.move.send.batch.wizard | `[('move_ids.move_type', 'in', ('out_invoice', 'out_refund'))]` |
| Sales Advance Payment Invoice Rule | sale.advance.payment.inv | `[('create_uid', '=', user.id)]` |
| Sales Mass Cancel Orders: access only your own wizard | sale.mass.cancel.orders | `[('create_uid', '=', user.id)]` |

*…2 more rules omitted.*

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
