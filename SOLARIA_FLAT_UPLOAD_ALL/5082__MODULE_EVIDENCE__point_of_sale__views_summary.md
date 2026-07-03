# Views & Navigation Summary — `point_of_sale` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `point_of_sale` — Point of Sale |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Backend views configure sessions/payment methods; the POS UI itself is a dedicated JS app — demo the register screen.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Point of Sale | — | group_pos_manager,group_pos_user |
| Point of Sale / Configuration | — | group_pos_manager |
| Point of Sale / Configuration / Coins/Bills | action_pos_bill | group_pos_manager |
| Point of Sale / Configuration / Point of Sales | action_pos_config_tree | — |
| Point of Sale / Configuration / Products | — | — |
| Point of Sale / Configuration / Products / menu_products_pos_category | product_pos_category_action | — |
| Point of Sale / Configuration / Products / pos_menu_products_attribute_action | attribute_action | product.group_product_variant |
| Point of Sale / Configuration / Products / pos_menu_products_tag_action | product_tag_action | — |
| Point of Sale / Configuration / Settings | action_pos_configuration | base.group_system |
| Point of Sale / Configuration / menu_action_tax_form_open | action_tax_form | base.group_no_one |
| Point of Sale / Configuration / menu_pos_note_model | action_pos_note_model | — |
| Point of Sale / Configuration / menu_pos_payment_method | action_pos_payment_method_form | group_pos_manager,group_pos_user |
| Point of Sale / Configuration / menu_pos_preset | action_pos_preset_form | group_pos_preset |
| Point of Sale / Dashboard | action_pos_config_kanban | — |
| Point of Sale / Orders | — | — |
| Point of Sale / Orders / Customers | res_partner_action_customer | — |
| Point of Sale / Orders / Preparation Printers | action_pos_printer_form | — |
| Point of Sale / Orders / menu_point_ofsale | action_pos_pos_form | group_pos_manager,group_pos_user |
| Point of Sale / Orders / menu_pos_payment | action_pos_payment_form | group_pos_manager,group_pos_user |
| Point of Sale / Orders / menu_pos_session_all | action_pos_session | group_pos_user |
| Point of Sale / Products | — | — |
| Point of Sale / Products / Combo Choices | product_combo_action | — |
| Point of Sale / Products / Product Variants | product_product_action | product.group_product_variant |
| Point of Sale / Products / menu_pos_products | product_template_action_pos_product | — |
| Point of Sale / Products / pos_config_menu_action_product_pricelist | product_pricelist_action2 | product.group_product_pricelist |
| Point of Sale / Reporting | — | — |
| Point of Sale / Reporting / Orders | action_report_pos_order_all | — |
| Point of Sale / Reporting / Sales Details | action_report_pos_details | — |
| Point of Sale / Reporting / Session Report | action_report_pos_daily_sales_reports | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Sessions | pos.session | list,form |
| Orders | pos.order | list,form |
| Orders Analysis | report.pos.order | graph,pivot |
| Settings | res.config.settings | form |
| Coins/Bills | pos.bill | list,form |
| PoS Product Categories | pos.category | list,kanban,form |
| Point of Sale | pos.config | kanban,list,form |
| Point of Sale List | pos.config | list,form |
| Note Models | pos.note | list |
| Orders Analysis | report.pos.order | graph,pivot |
| Sales Details | pos.details.wizard | form |
| Orders | pos.order | list,form,kanban,pivot |
| Orders | pos.order | graph,list,form,kanban,pivot |
| Sale line | pos.order.line | list |
| Sale line | pos.order.line | form,list |
| Sale line | pos.order.line | list |
| All sales lines | pos.order.line | — |
| Payment Methods | pos.payment.method | list,kanban,form |
| Payments Methods | pos.payment.method | list,form,kanban |
| Payments | pos.payment | list,form |
| Presets | pos.preset | list,form |
| Preparation Printers | pos.printer | list,kanban,form |
| Sessions | pos.session | list,kanban,form |
| Products | product.template | kanban,list,form,activity |
| Product Variants | product.product | kanban,list,form,activity |
| Internal Categories | product.category | — |
| New Product | product.template | form |
| Edit Product | product.template | form |
| Edit Partner | res.partner | form |
| Confirm Action | pos.confirmation.wizard | form |
| Session Report | pos.daily.sales.reports.wizard | form |
| Payment | pos.make.payment | form |

## View inventory

- Primary views defined: 44 (form: 17, list: 13, search: 7, kanban: 4, pivot: 2, graph: 1)
- Inheriting views (UI extensions of other modules): 16
- Richest UI objects: `pos.order` (form, kanban, list, pivot, search); `pos.config` (form, kanban, list, search); `report.pos.order` (graph, list, pivot, search); `pos.session` (form, kanban, list, search); `pos.category` (form, kanban, list); `pos.payment.method` (form, list, search); `pos.payment` (form, list, search); `pos.bill` (form, list); `pos.order.line` (form, list); `pos.preset` (form, list); `pos.printer` (form, list); `pos.note` (list)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| User Labels | res.users | qweb-pdf |
| Sales Details | pos.session | qweb-pdf |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
