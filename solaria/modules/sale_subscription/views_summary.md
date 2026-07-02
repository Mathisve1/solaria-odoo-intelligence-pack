# Views & Navigation Summary — `sale_subscription` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `sale_subscription` — Subscriptions |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Subscription = a sales order with recurrence: form shows plan, next invoice, MRR; pipeline-style kanban for renewals; cohort/analysis views are the CFO story.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Activity Plans | mail_activity_plan_action_subscription | — |
| Activity Types | mail_activity_type_action_config_subscription | — |
| Configuration | — | sales_team.group_sale_manager |
| Products | — | sales_team.group_sale_salesman |
| Recurring Plans | sale_subscription_plan_action | — |
| Settings | action_sale_config_settings | base.group_system |
| Subscriptions | — | sales_team.group_sale_salesman |
| Subscriptions | — | — |
| Subscriptions / Reporting | — | — |
| Subscriptions / Reporting / MRR Breakdown | sale_order_log_growth_action | — |
| Subscriptions / Reporting / MRR Timeline | sale_order_log_analysis_action | — |
| Subscriptions / Reporting / Retention | sale_subscription_report_cohort_action | — |
| Subscriptions / Reporting / Subscriptions | sale_subscription_report_analysis_action | — |
| menu_orders_customers | res_partner_action_customer | — |
| menu_sale_subscription_action | sale_subscription_action | — |
| menu_sale_subscription_close_reason_action | sale_subscription_close_reason_action | — |
| menu_sale_subscription_pending | sale_subscription_action_pending | — |
| menu_sale_subscription_pricelist | product_pricelist_action2 | product.group_product_pricelist |
| menu_sale_subscription_product | product_action_subscription | — |
| menu_sale_subscription_quotes | sale_subscription_action_quotes | — |
| menu_sale_subscription_upsell | sale_subscription_action_upsell | — |
| menu_template_of_subscription | sale_subscription_template_action | sale_management.group_sale_order_template |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Send an SMS Text Message | sms.composer | form |
| Send an SMS Text Message | sms.composer | form |
| MRR Breakdown | sale.order.log.report | graph,list,pivot |
| MRR Analysis | sale.order.log.report | graph,list,pivot |
| Subscriptions Analysis | sale.subscription.report | graph,list,pivot |
| Retention Analysis | sale.order | cohort |
| Sales Analysis | sale.report | — |
| Activity Plans | mail.activity.plan | list,kanban,form |
| Activity Types | mail.activity.type | list,kanban,form |
| Products | product.template | kanban,list,form,activity |
| Quotation Templates | sale.order.template | list,form |
| Recurring Plans | sale.subscription.plan | list,form |
| Sale Order Lines | sale.order.line | list,kanban,form |
| Subscriptions | sale.order | list,kanban,form,pivot,graph,cohort,activity |
| Subscriptions | sale.order | list,form,kanban,pivot,graph,activity |
| To Renew | sale.order | list,form,pivot,graph,kanban,cohort,activity |
| Upsells | sale.order | list,form,pivot,graph,kanban,cohort,activity |
| Quotations | sale.order | list,kanban,form,pivot,graph,cohort,activity |
| Close Reasons | sale.order.close.reason | list,form |
| Change Customer | sale.subscription.change.customer.wizard | form |
| Close Reason | sale.subscription.close.reason.wizard | form |

## View inventory

- Primary views defined: 26 (list: 6, search: 6, graph: 4, form: 4, pivot: 2, cohort: 2, kanban: 1, activity: 1)
- Inheriting views (UI extensions of other modules): 27
- Richest UI objects: `sale.order` (activity, cohort, graph, kanban, list, search); `sale.order.log.report` (graph, list, pivot, search); `sale.subscription.report` (graph, list, pivot, search); `sale.subscription.plan` (form, list, search); `sale.order.line` (list, search); `sale.order.close.reason` (form, list); `sale.order.template` (search); `sale.subscription.change.customer.wizard` (form); `sale.subscription.close.reason.wizard` (form)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
