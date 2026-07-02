# Views & Navigation Summary — `documents` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `documents` — Documents |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Workspace 'file manager' view with right-side panel of workflow actions is the wow-screen; actions are configuration.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Activities | — | documents.group_documents_manager |
| Activity Plans | mail_activity_plan_action_document | — |
| Activity Types | mail_activity_type_action_document | — |
| Configuration | — | documents.group_documents_manager |
| Documents | — | base.group_user |
| Documents | document_action_preference | base.group_user |
| Settings | configuration_action | base.group_system |
| Structure | — | documents.group_documents_manager |
| Tags | tag_action | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Add Url | documents.document | form |
| Documents | documents.document | kanban,list,activity |
| Documents | documents.document | kanban |
| Add Folder | documents.document | form |
| Tags | documents.tag | list,form |
| Document Plans | mail.activity.plan | list,kanban,form |
| Activity Types | mail.activity.type | list,kanban,form |
| Email links | mail.alias | list,form |
| Settings | res.config.settings | form |
| Settings | res.config.settings | form |
| Request a file | documents.request_wizard | form |

## View inventory

- Primary views defined: 16 (form: 9, list: 3, search: 2, kanban: 1, activity: 1)
- Inheriting views (UI extensions of other modules): 12
- Richest UI objects: `documents.document` (activity, form, kanban, list, search); `documents.tag` (form, list, search); `documents.access` (list); `documents.link_to_record_wizard` (form); `documents.operation` (form); `documents.request_wizard` (form); `documents.sharing` (form)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
