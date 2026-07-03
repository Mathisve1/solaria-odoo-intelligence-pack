# Views & Navigation Summary — `sale` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `sale` — Sales |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Quotation form is the flagship: order lines, optional products, online signature/payment settings drive the portal story.
- Menus split Orders vs To Invoice vs Reporting — mirrors the quote-to-cash handoffs in demos.
- Portal (customer-facing quote page) is controller-based; show it from a customer's browser tab in demos.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Activities | — | — |
| Activity Plans | mail_activity_plan_action_sale_order | sales_team.group_sale_manager |
| Combo Choices | product_combo_action | — |
| Configuration | — | sales_team.group_sale_manager |
| Customers | action_order_report_customers | — |
| Online Payments | — | base.group_system |
| Orders | — | — |
| Orders | action_orders | sales_team.group_sale_salesman |
| Pricelists | product_pricelist_action2 | product.group_product_pricelist |
| Products | — | sales_team.group_sale_salesman |
| Products | action_order_report_products | — |
| Products | — | — |
| Reporting | — | sales_team.group_sale_manager |
| Sales | — | — |
| Sales | action_order_report_all | — |
| Sales Orders | — | — |
| Sales Teams | crm_team_action_sales | sales_team.group_sale_manager |
| Sales Teams | crm_team_action_config | — |
| Salespersons | action_order_report_salesperson | — |
| Settings | action_sale_config_settings | base.group_system |
| Tags | sales_team_crm_tag_action | — |
| To Invoice | — | sales_team.group_sale_salesman |
| Units & Packagings | product_uom_form_action | uom.group_uom |
| menu_product_attribute_action | attribute_action | product.group_product_variant |
| menu_product_categories | product_category_action_form | — |
| menu_product_tags | product_tag_action | — |
| menu_product_template_action | product_template_action | — |
| menu_products | product_normal_action_sell | product.group_product_variant |
| menu_sale_order_invoice | action_orders_to_invoice | — |
| menu_sale_order_upselling | action_orders_upselling | — |
| menu_sale_quotations | action_quotations_with_onboarding | sales_team.group_sale_salesman |
| payment_method_menu | action_payment_method | — |
| payment_provider_menu | action_payment_provider | — |
| payment_token_menu | action_payment_token | base.group_no_one |
| payment_transaction_menu | action_payment_transaction | base.group_no_one |
| res_partner_menu | res_partner_action_customer | sales_team.group_sale_salesman |
| sale_menu_config_activity_type | mail_activity_type_action_config_sale | base.group_no_one |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Invoices Analysis | account.invoice.report | graph |
| Sales Analysis | sale.report | graph,pivot,list,form |
| Sales Analysis By Salespersons | sale.report | graph,pivot |
| Sales Analysis By Products | sale.report | graph,pivot |
| Sales Analysis By Customers | sale.report | graph,pivot |
| Sales Analysis | sale.report | list,pivot,graph,form |
| Quotations Analysis | sale.report | graph,list |
| Sales Analysis | sale.report | graph,list |
| Invoices | account.move | list,form,kanban |
| Quotations | sale.order | list,form,calendar,graph,kanban,pivot |
| New Quotation | sale.order | form |
| Sales Orders | sale.order | list,form,calendar,graph,kanban,pivot |
| Sales Orders | sale.order | list,form,calendar,graph,kanban,pivot |
| sales_team.mail_activity_type_action_config_sales | — | — |
| Sale Order Plans | mail.activity.plan | list,kanban,form |
| Activity Types | mail.activity.type | list,kanban,form |
| Products | product.template | — |
| Quotations and Sales | sale.order | list,kanban,form,graph |
| Sales Orders | sale.order | list,kanban,form,calendar,pivot,graph,activity |
| Quotations | sale.order | list,kanban,form,calendar,pivot,graph,activity |
| Quotations | sale.order | list,kanban,form,calendar,pivot,graph,activity |
| Orders to Invoice | sale.order | list,form,calendar,graph,pivot,kanban,activity |
| Orders to Upsell | sale.order | list,form,calendar,graph,pivot,kanban,activity |
| Add/Remove Followers | mail.followers.edit | form |
| Accrued Revenue Entry | account.accrued.orders.wizard | form |
| Accrued Revenue Entry | account.accrued.orders.wizard | form |
| Cancel | sale.mass.cancel.orders | form |
| Generate a Payment Link | payment.link.wizard | form |
| Settings | res.config.settings | form |
| Create invoice(s) | sale.advance.payment.inv | form |

## View inventory

- Primary views defined: 19 (form: 5, list: 3, search: 3, pivot: 2, graph: 2, kanban: 2, activity: 1, calendar: 1)
- Inheriting views (UI extensions of other modules): 38
- Richest UI objects: `sale.order` (activity, calendar, form, graph, kanban, list, pivot, search); `sale.report` (graph, list, pivot, search); `sale.order.line` (form, kanban, list, search); `sale.mass.cancel.orders` (form); `sale.advance.payment.inv` (form); `sale.order.discount` (form)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Quotation / Order | sale.order | qweb-pdf |
| PRO-FORMA Invoice | sale.order | qweb-pdf |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
