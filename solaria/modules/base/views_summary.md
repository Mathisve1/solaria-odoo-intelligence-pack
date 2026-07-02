# Views & Navigation Summary — `base` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `base` — Base |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Backend admin surfaces: Settings, Users & Companies, Technical menus — architect/admin territory, not client demos.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Application Terms | — | base.group_no_one |
| Apps | — | base.group_system |
| Apps / Apply Scheduled Upgrades | action_view_base_module_upgrade | base.group_no_one |
| Apps / Apps | — | — |
| Apps / Apps / Main Apps | open_module_tree | — |
| Apps / Apps / Theme Store | — | — |
| Apps / Apps / Theme Store | action_theme_store | — |
| Apps / Apps / Third-Party Apps | action_third_party | — |
| Apps / Update Apps List | action_view_base_module_update | base.group_no_one |
| Automation | — | — |
| Automation / ir_cron_trigger_menu | ir_cron_trigger_action | — |
| Automation / menu_ir_cron_act | ir_cron_act | — |
| Custom Shortcuts | — | — |
| Database Structure | — | — |
| Database Structure / Profiling | action_menu_ir_profile | — |
| Database Structure / ir_logging_all_menu | ir_logging_all_act | — |
| Database Structure / ir_model_constraint_menu | action_model_constraint | base.group_no_one |
| Database Structure / ir_model_model_fields | action_model_fields | — |
| Database Structure / ir_model_model_fields_selection | action_model_fields_selection | — |
| Database Structure / ir_model_model_menu | action_model_model | — |
| Database Structure / ir_model_relation_menu | action_model_relation | base.group_no_one |
| Database Structure / menu_action_asset | action_asset | — |
| Database Structure / menu_action_attachment | action_attachment | — |
| Database Structure / menu_decimal_precision_form | action_decimal_precision_form | — |
| Email | — | — |
| Email / menu_mail_servers | action_ir_mail_server_list | base.group_no_one |
| General Settings | — | — |
| Import / Export | — | base.group_no_one |
| Import / Export / menu_view_base_import_language | action_view_base_import_language | — |
| Import / Export / menu_wizard_lang_export | action_wizard_lang_export | — |
| Parameters | — | — |
| Parameters / System Parameters | ir_config_list_action | — |
| Security | — | — |
| Security / menu_action_rule | action_rule | — |
| Security / menu_action_user_device | action_user_device | — |
| Security / menu_ir_access_act | ir_access_act | — |
| Settings | — | base.group_erp_manager |
| Technical | — | base.group_no_one |
| Technical / Actions | — | — |
| Technical / Actions / ir_default_menu | ir_default_menu_action | — |
| Technical / Actions / menu_ir_action_report | ir_action_report | — |
| Technical / Actions / menu_ir_action_window | ir_action_window | — |
| Technical / Actions / menu_ir_actions_todo_form | act_ir_actions_todo_form | — |
| Technical / Actions / menu_ir_client_actions_report | ir_client_actions_report | — |
| Technical / Actions / menu_ir_embedded_action | ir_embedded_action | — |

*…21 further menus omitted; full detail available on request from source.*

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Decimal Accuracy | decimal.precision | — |
| Actions | ir.actions.actions | — |
| Reports | ir.actions.report | — |
| Window Actions | ir.actions.act_window | — |
| Client Actions | ir.actions.client | — |
| Server Actions | ir.actions.server | list,form |
| Embedded Actions | ir.embedded.actions | — |
| Configuration Wizards | ir.actions.todo | — |
| Assets | ir.asset | — |
| Attachments | ir.attachment | — |
| System Parameters | ir.config_parameter | — |
| Scheduled Actions Triggers | ir.cron.trigger | list,form |
| Scheduled Actions | ir.cron | list,form,calendar |
| User-defined Defaults | ir.default | list,form |
| User-defined Filters | ir.filters | — |
| Logging | ir.logging | list,form |
| Outgoing Mail Servers | ir.mail_server | list,form |
| Models | ir.model | — |
| Fields | ir.model.fields | — |
| Fields Selection | ir.model.fields.selection | — |
| External Identifiers | ir.model.data | — |
| Model Constraints | ir.model.constraint | — |
| ManyToMany Relations | ir.model.relation | — |
| Access Rights | ir.model.access | — |
| Apps | ir.module.module | kanban,list,form |
| Ir profile | ir.profile | list,form |
| Record Rules | ir.rule | — |
| Sequences | ir.sequence | — |
| Menu Items | ir.ui.menu | — |
| Views | ir.ui.view | — |
| Compare/Reset | reset.view.arch.wizard | form |
| Customized Views | ir.ui.view.custom | — |
| Paper Format General Configuration | report.paperformat | list,form |
| Reports | ir.actions.report | list,form |
| Banks | res.bank | list,form |
| Bank Accounts | res.partner.bank | list,form |
| Companies | res.company | list,kanban,form |
| Settings | res.config.settings | form |
| Countries | res.country | — |
| Country Group | res.country.group | — |
| Fed. States | res.country.state | — |
| Show Currency Rates | res.currency.rate | list,form |
| Currencies | res.currency | list,kanban,form |
| User Devices | res.device | list,kanban,form |
| Privileges | res.groups.privilege | — |

*…21 more actions omitted.*

## View inventory

- Primary views defined: 172 (form: 73, list: 51, search: 39, kanban: 8, calendar: 1)
- Inheriting views (UI extensions of other modules): 2
- Richest UI objects: `ir.actions.server` (form, kanban, list, search); `ir.module.module` (form, kanban, list, search); `res.currency` (form, kanban, list, search); `res.partner` (form, kanban, list, search); `res.users` (form, kanban, list, search); `ir.actions.actions` (form, list, search); `ir.actions.report` (form, list, search); `ir.actions.act_window` (form, list, search); `ir.actions.todo` (form, list, search); `ir.asset` (form, list, search); `ir.attachment` (form, list, search); `ir.config_parameter` (form, list, search)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Model Overview | ir.model | qweb-pdf |
| Technical guide | ir.module.module | qweb-pdf |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
