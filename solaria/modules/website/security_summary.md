# Security & Access Summary — `website` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `website` — Website |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Restricted editor vs designer separates content editing from structural design; publishing rights are part of brand governance.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| Multi-website | group_multi_website | — |
| Restricted Editor | group_website_restricted_editor | — |
| Editor and Designer | group_website_designer | group_sanitize_override |
| Public access to arbitrary exposed model | website_page_controller_expose | — |
| — | base.group_public | — |
| — | base.group_portal | — |

## Access rights (ir.model.access) — 44 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_website_designer | `ir_asset`, `ir_ui_view`, `website.website`, `website_configurator_feature`, `website_controller_page`, `website_menu` +7 more | `website_custom_blocked_third_party_domains`, `website_robots`, `website_visitor` | — |
| group_system | `theme_ir_asset`, `theme_ir_attachment`, `theme_ir_ui_view`, `theme_website_menu`, `theme_website_page`, `website_snippet_filter` +1 more | `website_visitor` | `website_technical_page` |
| group_public | — | `website_page_properties`, `website_page_properties_base` | `website.website`, `website_menu`, `website_seo_metadata` |
| group_portal | — | `website_page_properties`, `website_page_properties_base` | `website.website`, `website_menu`, `website_seo_metadata` |
| group_user | — | — | `website.website`, `website_menu`, `website_page_properties`, `website_page_properties_base`, `website_seo_metadata` |
| (no group / global) | — | `website_rewrite`, `website_snippet_filter` | — |
| website_page_controller_expose | — | — | `website_controller_page` |
| group_website_restricted_editor | — | — | `ir_ui_view` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Website menu: group_ids | website.menu | `['|', ('group_ids', '=', False), ('group_ids', 'in', user.all_group_ids.ids)]` |
| website_designer: Manage Website and qWeb view | ir.ui.view | `[('type', '=', 'qweb')]` |
| website_designer: global view | ir.ui.view | `[('type', '!=', 'qweb')]` |
| Administration Settings: Manage all views | ir.ui.view | `[(1, '=', 1)]` |
| website.page: portal/public: read published pages | website.page | `[('website_published', '=', True)]` |
| Website View Visibility Public | ir.ui.view | `['|', ('type', '!=', 'qweb'), ('visibility', 'in', ('public', False))]` |
| Website View Visibility Connected | ir.ui.view | `['|', ('type', '!=', 'qweb'), ('visibility', 'in', ('public', 'connected', False))]` |
| website.controller.page: portal/public: read published pages | website.controller.page | `[('website_published', '=', True)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
