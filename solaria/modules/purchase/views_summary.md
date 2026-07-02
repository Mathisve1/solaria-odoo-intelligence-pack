# Views & Navigation Summary — `purchase` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `purchase` — Purchase |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- RFQ form and its Send/Confirm flow is the core screen; vendor pricelists and agreements sit under Configuration/Orders.
- Three-way flow visibility (order -> receipt -> bill) appears through smart buttons — demo the audit trail.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Purchase | — | group_purchase_manager,group_purchase_user |
| Purchase / Configuration | — | group_purchase_manager |
| Purchase / Configuration / Products | — | — |
| Purchase / Configuration / Products / Attributes | attribute_action | product.group_product_variant |
| Purchase / Configuration / Products / Units & Packagings | product_uom_form_action | uom.group_uom |
| Purchase / Configuration / Products / menu_product_category_config_purchase | product_category_action_form | — |
| Purchase / Configuration / Settings | action_purchase_configuration | base.group_system |
| Purchase / Configuration / menu_product_pricelist_action2_purchase | product_supplierinfo_type_action | — |
| Purchase / Orders | — | — |
| Purchase / Orders / Vendors | res_partner_action_supplier | — |
| Purchase / Orders / menu_purchase_form_action | purchase_form_action | — |
| Purchase / Orders / menu_purchase_rfq | purchase_rfq | — |
| Purchase / Products | — | — |
| Purchase / Products / Product Variants | product_product_action | product.group_product_variant |
| Purchase / Products / Products | product_normal_action_puchased | — |
| Purchase / Reporting | — | purchase.group_purchase_manager |
| Purchase / Reporting / Purchase | action_purchase_order_report_all | purchase.group_purchase_manager |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Purchase Analysis | purchase.report | graph,pivot |
| Products | product.template | — |
| Product Variants | product.product | list,kanban,form,activity |
| Requests for Quotation | purchase.order | list,kanban,form,pivot,graph,calendar,activity |
| Purchase Orders | purchase.order | list,kanban,form,pivot,graph,calendar,activity |
| action_purchase_history | purchase.order.line | list,pivot,graph |
| Accrued Expense Entry | account.accrued.orders.wizard | form |
| Requests for Quotation | purchase.order | form |
| Add/Remove Followers | mail.followers.edit | form |
| Settings | res.config.settings | form |
| RFQs and Purchases | purchase.order | list,kanban,form,graph |
| Vendor Bills | account.move | list,form,graph |

## View inventory

- Primary views defined: 25 (list: 8, search: 5, pivot: 3, graph: 3, form: 3, calendar: 1, kanban: 1, activity: 1)
- Inheriting views (UI extensions of other modules): 15
- Richest UI objects: `purchase.order` (activity, calendar, form, graph, kanban, list, pivot, search); `purchase.order.line` (form, graph, list, pivot, search); `purchase.report` (graph, list, pivot, search); `purchase.bill.union` (list, search); `purchase.bill.line.match` (list); `bill.to.po.wizard` (form)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Purchase Order | purchase.order | qweb-pdf |
| Request for Quotation | purchase.order | qweb-pdf |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
