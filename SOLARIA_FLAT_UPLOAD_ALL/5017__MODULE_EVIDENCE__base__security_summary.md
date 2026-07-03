# Security & Access Summary — `base` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `base` — Base |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Admin ('Settings') rights are radioactive: keep to 2-3 people; use Technical-features group sparingly in production.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| Access Rights | group_erp_manager | — |
| Bypass HTML Field Sanitize | group_sanitize_override | — |
| Role / Administrator | group_system | — |
| Role / User | group_user | — |
| Multi Companies | group_multi_company | — |
| Multi Currencies | group_multi_currency | — |
| Technical Features | group_no_one | — |
| Allowed | group_allow_export | — |
| Creation | group_partner_manager | — |
| Role / Portal | group_portal | — |
| Role / Public | group_public | — |
| Default access for new users | default_user_group | — |

## Access rights (ir.model.access) — 146 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_system | `base.properties_base_definition`, `ir_actions_act_url`, `ir_actions_act_window`, `ir_actions_act_window_close`, `ir_actions_act_window_view`, `ir_actions_actions` +27 more | `base_enable_profiling_wizard`, `base_language_import`, `base_language_install`, `base_module_uninstall`, `base_module_update`, `base_module_upgrade` +11 more | — |
| group_user | `change_password_own`, `ir_attachment`, `ir_default`, `ir_embedded_actions`, `ir_exports_line`, `ir_filters` +2 more | `base_language_export`, `ir_data`, `ir_fields`, `ir_fields_selection`, `ir_model`, `res_users_apikeys_description` +2 more | `base.res_device`, `base.res_device_log`, `ir_sequence`, `ir_sequence_date_range`, `ir_ui_menu`, `report_paperformat` +16 more |
| group_erp_manager | `ir_access`, `ir_data`, `ir_fields`, `ir_fields_selection`, `ir_filters`, `ir_logging` +8 more | `change_password_user`, `change_password_wizard`, `ir_constraint`, `reset_view_arch_wizard` | `ir_module_category` |
| group_portal | `ir_filters` | `res_users_apikeys_description`, `res_users_identitycheck` | `res_company`, `res_country`, `res_country_group`, `res_country_state`, `res_currency`, `res_currency_rate` +4 more |
| group_public | `ir_filters` | — | `res_company`, `res_country`, `res_country_group`, `res_country_state`, `res_currency`, `res_currency_rate` +3 more |
| group_partner_manager | `base_partner_merge_line`, `res_bank`, `res_country_group`, `res_country_state`, `res_partner`, `res_partner_bank` +1 more | `base_partner_merge_automatic_wizard` | `res_country` |
| (no group / global) | — | `ir_attachment`, `ir_default`, `ir_inherit`, `ir_ui_view`, `res_users_deletion`, `res_users_settings` | — |
| group_allow_export | `ir_exports` | — | — |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| res.users.log per user | res.users.log | `[('create_uid','=', user.id)]` |
| res.partner company | res.partner | `['|', '|', ('partner_share', '=', False), ('company_id', 'parent_of', company_ids), ('comp` |
| res_partner: portal/public: read access on my commercial partner | res.partner | `[('id', 'child_of', user.commercial_partner_id.id)]` |
| Defaults: alter personal defaults | ir.default | `[('user_id','=',user.id)]` |
| Defaults: alter all defaults | ir.default | `[(1,'=',1)]` |
| ir.ui.view_custom rule | ir.ui.view.custom | `[('user_id','=',user.id)]` |
| Partner bank company rule | res.partner.bank | `['|', ('company_id', 'parent_of', company_ids), ('company_id', '=', False)]` |
| multi-company currency rate rule | res.currency.rate | `['|', ('company_id', 'parent_of', company_ids), ('company_id', '=', False)]` |
| change user password rule | change.password.user | `[('create_uid', '=', user.id)]` |
| ir.filters.admin.all.rights | ir.filters | `[(1, '=', 1)]` |
| ir.filter: owner or global | ir.filters | `[('user_ids','in',[False,user.id])]` |
| ir.filter: portal/public | ir.filters | `[('user_ids', 'in', user.ids)]` |
| company rule portal | res.company | `[('id','in', company_ids)]` |
| company rule employee | res.company | `[('id','in', company_ids)]` |
| company rule public | res.company | `[('id','in', company_ids)]` |
| company rule erp manager | res.company | `[(1,'=',1)]` |
| users can only access their own id check | res.users.identitycheck | `[('create_uid', '=', user.id)]` |
| user rule | res.users | `['|', ('share', '=', False), ('company_ids', 'in', company_ids)]` |
| portal user access | res.users | `[('commercial_partner_id', '=', user.commercial_partner_id.id)]` |
| change own password | change.password.own | `[('create_uid', '=', user.id)]` |
| Administrators can access all User Settings. | res.users.settings | `[(1, '=', 1)]` |
| res.users.settings: access their own entries | res.users.settings | `[('user_id', '=', user.id)]` |
| Public users can't interact with keys at all | res.users.apikeys | `[(0, '=', 1)]` |
| Users can read and delete their own keys | res.users.apikeys | `[('user_id', '=', user.id)]` |
| Administrators can view user keys to revoke them | res.users.apikeys | `[(1, '=', 1)]` |

*…7 more rules omitted.*

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
