# Views & Navigation Summary — `sign` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `sign` — Sign |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Template editor (drag fields on PDF) and request tracking views carry the demo; the signing itself happens in portal.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Sign | — | — |
| Sign / Configuration | — | — |
| Sign / Configuration / Fields | sign_item_type_action | — |
| Sign / Configuration / Settings | sign_settings_action | sign.group_sign_manager |
| Sign / Configuration / Tags | sign_template_tag_action | sign.group_sign_manager |
| Sign / Documents | — | — |
| Sign / Documents / All Documents | sign_all_request_action | — |
| Sign / Documents / My Documents | sign_request_action | — |
| Sign / Reports | — | — |
| Sign / Reports / Green Savings | sign_report_green_savings_action | — |
| Sign / Templates | sign_template_action | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Documents | sign.request | list,kanban,form,pivot,graph,activity |
| All Documents | sign.request | list,kanban,form,pivot,graph,activity |
| Signature Request Items | sign.request.item | list,form |
| Templates | sign.template | kanban,list,form |
| Signature Fields | sign.item.type | list,form |
| Signature Item Options | sign.item.option | list |
| Tags | sign.template.tag | — |
| Settings | res.config.settings | form |
| New Signature Request | sign.send.request | form |

## View inventory

- Primary views defined: 27 (form: 11, list: 7, kanban: 3, search: 3, pivot: 1, graph: 1, activity: 1)
- Inheriting views (UI extensions of other modules): 4
- Richest UI objects: `sign.request` (activity, form, graph, kanban, list, pivot, search); `sign.template` (form, kanban, list, search); `sign.item.type` (form, list, search); `sign.request.item` (form, list); `sign.template.tag` (form, list); `sign.item` (form, list); `res.company` (form); `sign.log` (list); `sign.item.role` (form); `sign.request.share` (form); `sign.send.request` (form); `sign.template.preview` (form)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Activity Logs | sign.request | qweb-pdf |
| Green Savings | sign.template | qweb-html |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
