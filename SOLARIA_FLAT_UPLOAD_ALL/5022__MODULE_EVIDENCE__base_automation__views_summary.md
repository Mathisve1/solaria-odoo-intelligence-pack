# Views & Navigation Summary — `base_automation` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `base_automation` — Automation Rules |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- No user-facing menus beyond the technical Automation Rules editor (Settings/Technical) — demo by building a rule live (stale-lead alert) in 2 minutes.
- The rules editor is Community — a strong 'automation without Studio/custom' message.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| menu_base_automation_form | base_automation_act | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Automation Rules | base.automation | kanban,list,form |

## View inventory

- Primary views defined: 4 (form: 1, list: 1, kanban: 1, search: 1)
- Inheriting views (UI extensions of other modules): 1
- Richest UI objects: `base.automation` (form, kanban, list, search)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
