# Views & Navigation Summary — `spreadsheet_edition` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `spreadsheet_edition` — Spreadsheet |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Demo from a pivot: Insert in Spreadsheet → live-linked sheet; cell comment threads and revision history are the collaboration angles.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Spreadsheet | — | — |
| Spreadsheet / Revisions | spreadsheet_revision_action | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Revisions | spreadsheet.revision | list,form |

## View inventory

- Primary views defined: 2 (search: 1, list: 1)
- Inheriting views (UI extensions of other modules): 0
- Richest UI objects: `spreadsheet.revision` (list, search)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
