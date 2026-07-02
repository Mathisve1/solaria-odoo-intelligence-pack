# Security & Access Summary — `documents` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `documents` — Documents |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Workspace-level access (own/role-based) via record rules is the core mechanism — folder design IS the security design; test inheritance to AI features.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| User | group_documents_user | group_user |
| Administrator | group_documents_manager | — |
| System Administrator | group_documents_system | — |

## Access rights (ir.model.access) — 20 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_user | `documents_access`, `documents_document` | `documents.documents_operation`, `documents.documents_sharing`, `documents.documents_sharing_access` | `documents_tag` |
| group_documents_manager | `documents_access`, `documents_document`, `documents_tag`, `mail.mail_activity_plan`, `mail.mail_activity_plan_template` | — | — |
| group_portal | `documents_document` | `documents.documents_operation` | `documents_access`, `documents_tag` |
| group_documents_user | — | `documents_link_to_record_wizard`, `documents_request_wizard` | `documents_tag` |
| group_system | `documents_access_tracking` | `documents_redirect` | — |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Documents.document: global read rule | documents.document | `[('user_permission', '!=', 'none')]` |
| Documents.document: global create rule | documents.document | `[ '|', ('folder_id.user_permission', '=', 'edit'), ('folder_id', '=', False), ]` |
| Documents.document: global write rule | documents.document | `[('user_permission', '=', 'edit')]` |
| Documents.document: write+unlink base rule | documents.document | `[ ('user_permission', '=', 'edit'), '|', ('type', '!=', 'folder'), '|', ('owner_id', '!=',` |
| Documents.document: write+unlink manager rule | documents.document | `[('user_permission', '=', 'edit')]` |
| Documents.access: global read rule | documents.access | `[('document_id.user_permission', '!=', 'none')]` |
| Documents.access: global write rule | documents.access | `[('document_id.user_permission', '=', 'edit')]` |
| Manager can manage document plans | mail.activity.plan | `[('res_model', '=', 'documents.document')]` |
| Manager can manage document plan templates | mail.activity.plan.template | `[('plan_id.res_model', '=', 'documents.document')]` |
| Tag portal: Read access to the tags of the documents the user has access to | documents.tag | `[('document_ids.user_permission', '!=', 'none')]` |
| Documents Operation Rule | documents.operation | `[('create_uid', '=', user.id)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
