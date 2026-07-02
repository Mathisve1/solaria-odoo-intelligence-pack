# Views & Navigation Summary — `website` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `website` — Website |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Most of the UX is the front-end builder (controllers/static, not classic backend views) — demo in the browser, not in form views.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Website | — | base.group_user |
| Website / Configuration | — | base.group_system |
| Website / Configuration / Menus | action_website_menu | base.group_no_one |
| Website / Configuration / Redirects | action_website_rewrite_list | base.group_no_one |
| Website / Configuration / Settings | action_website_configuration | base.group_system |
| Website / Configuration / Websites | action_website_list | base.group_no_one |
| Website / Configuration / menu_website_add_features | action_website_add_features | base.group_system |
| Website / Reporting | — | — |
| Website / Reporting / Analytics | ir_actions_server_website_analytics | — |
| Website / Reporting / Page Views | website_visitor_view_action | — |
| Website / Reporting / Visitors | website_visitors_action | — |
| Website / Reporting / eCommerce | ir_actions_server_website_dashboard | base.group_system,website.group_website_designer |
| Website / Site | — | — |
| Website / Site / Content | — | — |
| Website / Site / Content / Model Pages | action_website_controller_pages_list | base.group_no_one |
| Website / Site / Content / Pages | action_website_pages_list | — |
| Website / Site / Content / Technical Pages | action_website_technical_pages | — |
| Website / Site / Homepage | website_preview | — |
| Website / Site / Menu Editor | website_preview | — |
| Website / Site / This page | — | — |
| Website / Site / This page / Edit Menu | website_preview | — |
| Website / Site / This page / HTML / CSS Editor | website_preview | — |
| Website / Site / This page / Optimize SEO | website_preview | — |
| Website / Site / This page / Properties | website_preview | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Settings | res.config.settings | form |
| Website Model Pages | website.controller.page | list,kanban,form |
| Website Pages | website.page | list,kanban |
| Rewrite | website.rewrite | — |
| Technical Pages | website.technical.page | list |
| Apps | ir.module.module | kanban,list,form |
| Websites | website | list,form |
| Website Menu | website.menu | list,form |
| base.open_module_tree | — | — |
| Pick a Theme | ir.module.module | kanban,form |
| Page Views History | website.track | list |
| Partners | res.partner | list,form |
| Visitors | website.visitor | kanban,list,form,graph |
| Page Views | website.track | list |

## View inventory

- Primary views defined: 34 (form: 11, list: 9, search: 7, kanban: 4, graph: 3)
- Inheriting views (UI extensions of other modules): 17
- Richest UI objects: `website.visitor` (form, graph, kanban, list, search); `website.controller.page` (form, kanban, list, search); `website.page` (form, kanban, list, search); `website.rewrite` (form, list, search); `website.menu` (form, list, search); `ir.module.module` (form, kanban, search); `website.track` (graph, list, search); `website` (form, list); `website.page.properties.base` (form); `website.technical.page` (list); `ir.ui.view` (form); `website.custom_blocked_third_party_domains` (form)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
