# Views & Navigation Summary — `website_sale` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `website_sale` — eCommerce |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Backend views manage products/orders; the selling UX is the website shop — demo cart-to-payment in the storefront.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Abandoned Carts | action_view_abandoned_tree | — |
| Combo Choices | product_combo_action | — |
| Customers | action_partner_customer_form | — |
| Online Sales | sale_report_action_dashboard | sales_team.group_sale_manager |
| Orders | — | — |
| Orders | action_orders_ecommerce | — |
| Payment Methods | action_payment_method | — |
| Payment Providers | action_payment_provider | — |
| Pricelists | product_pricelist_action2 | product.group_product_pricelist |
| Product Ribbons | product_ribbon_action | — |
| Product Tags | product_tag_action | — |
| Products | — | — |
| Products | product_template_action_website | — |
| Products | action_product_pages_list | — |
| Unpaid Orders | action_view_unpaid_quotation_tree | — |
| eCommerce | — | sales_team.group_sale_salesman |
| eCommerce | — | — |
| menu_catalog_categories | product_public_category_action | — |
| menu_delivery_zip_prefix | action_delivery_zip_prefix_list | base.group_no_one |
| menu_ecommerce_delivery | action_delivery_carrier_form | — |
| menu_ecommerce_payment_tokens | action_payment_token | base.group_no_one |
| menu_ecommerce_payment_transactions | action_payment_transaction | base.group_no_one |
| menu_product_attribute_action | attribute_action | product.group_product_variant |
| menu_product_feeds | action_product_feeds | website_sale.group_product_feed |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Online Sales Analysis | sale.report | pivot,graph |
| Sales | sale.report | pivot,graph |
| Product Feeds | product.feed | list,form |
| New Product | product.product | form |
| eCommerce Categories | product.public.category | list,form |
| Product Ribbons | product.ribbon | list,form |
| Products | product.template | kanban,list,form,activity |
| Orders | sale.order | list,form,kanban,activity |
| Unpaid Orders | sale.order | list,form,kanban,activity |
| Orders To Invoice | sale.order | list,form,kanban |
| Unpaid Orders | sale.order | list,kanban,form,activity |
| Abandoned Carts | sale.order | list,kanban,form,activity |
| Base Units | website.base.unit | list,form |
| Product Pages | product.template | list,kanban |
| Product Views History | website.track | list |

## View inventory

- Primary views defined: 15 (list: 4, form: 4, search: 3, graph: 2, pivot: 1, kanban: 1)
- Inheriting views (UI extensions of other modules): 41
- Richest UI objects: `sale.report` (graph, pivot, search); `product.feed` (form, list, search); `product.image` (form, kanban); `product.public.category` (form, list); `product.ribbon` (form, list); `website.track` (graph, list); `sale.order` (search)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
