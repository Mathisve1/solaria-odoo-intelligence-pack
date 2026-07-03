# Views & Navigation Summary — `web_studio` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `web_studio` — Studio |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Studio itself is an overlay editor UI, not classic menus — demo it live inside another app (add a field to a form in 60 seconds).
- Backend menus shipped here are the governance surface: Studio Approval Rules/Entries and Studio Export — show THESE to IT stakeholders.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Studio Approval Entries | studio_approval_entry_action | base.group_system |
| Studio Approval Rules | studio_approval_rule_action | base.group_system |
| Studio Export | action_models_to_export | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Webhook Automations | base.automation | kanban,list,form |
| Studio Approval Entries | studio.approval.entry | list,form |
| Studio Approval Rules | studio.approval.rule | kanban,list,form |
| Studio Export | studio.export.model | list,form |
| Studio Export | studio.export.wizard | form |

## View inventory

- Primary views defined: 13 (form: 6, list: 3, kanban: 2, search: 2)
- Inheriting views (UI extensions of other modules): 4
- Richest UI objects: `studio.approval.rule` (form, kanban, list, search); `studio.approval.entry` (form, list, search); `studio.export.model` (form, list); `ir.actions.report` (kanban); `studio.approval.rule.delegate` (form); `studio.export.wizard` (form)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
