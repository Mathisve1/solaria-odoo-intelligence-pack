# Security & Access Summary — `sale_subscription` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `sale_subscription` — Subscriptions |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Follows sales groups; recurring billing jobs run as system — finance should own plan/pricing config rights.

## Existing groups this module modifies

These records extend groups owned by other modules (typically adding implied rights) — they do not create new roles:

| Existing group (reference) | Rights/groups implied by this module |
|---|---|
| base.group_user | group_discount_per_so_line |

## Access rights (ir.model.access) — 19 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_sale_manager | `mail.mail_activity_plan`, `mail.mail_activity_plan_template`, `product_pricelist_item`, `sale_order_close_reason`, `sale_subscription_plan`, `sms.sms_template` | `sale_subscription_change_customer_wizard` | `sale_order_log_report`, `sale_subscription_report` |
| group_sale_salesman | — | `sale_subscription_close_reason_wizard` | `product_pricelist_item`, `sale_order_close_reason`, `sale_order_log`, `sale_order_log_report`, `sale_subscription_plan`, `sale_subscription_report` |
| group_public | — | — | `sale_subscription.sale_order_close_reason` |
| group_portal | — | — | `sale_subscription.sale_order_close_reason` |
| group_user | — | — | `sale_subscription.sale_order_close_reason` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Subscription log multi-company | sale.order.log | `[('company_id', 'in', company_ids)]` |
| Subscription Plan multi-company | sale.subscription.plan | `[('company_id', 'in', company_ids + [False])]` |
| Subscription Pricing multi-company | product.pricelist.item | `['&', ('company_id', 'in', [False] + company_ids), '|', ('pricelist_id', '=', False), ('pr` |
| Subscription Analysis multi-company | sale.subscription.report | `[('company_id', 'in', company_ids)]` |
| Personal Subscription Analysis | sale.subscription.report | `['|',('user_id','=',user.id),('user_id','=',False)]` |
| All Orders Analysis | sale.subscription.report | `[(1,'=',1)]` |
| Manager can manage sale order plans | mail.activity.plan | `[('res_model', '=', 'sale.order')]` |
| Manager can manage sale order plan templates | mail.activity.plan.template | `[('plan_id.res_model', '=', 'sale.order')]` |
| Subscription log report multi-company | sale.order.log.report | `[('company_id', 'in', company_ids)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
