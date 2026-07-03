# Security & Access Summary — `sign` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `sign` — Sign |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Signers interact via portal tokens without internal access; template management is internal — validate legal retention and access to signed PDFs.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| Manage template access | manage_template_access | — |
| User: Own Templates | group_sign_user | group_user |
| Administrator | group_sign_manager | group_sign_user |

## Access rights (ir.model.access) — 19 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_sign_user | `sign.sign_completed_document`, `sign_document`, `sign_item`, `sign_item_radio_set`, `sign_item_role`, `sign_item_type` +4 more | `sign_item_option`, `sign_request_item`, `sign_request_item_value`, `sign_request_share`, `sign_template_preview` | `sign_log`, `sign_template_tag` |
| group_sign_manager | `sign_template_tag` | `sign_item_option` | — |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| sign.template: group_sign_manager: Create and manage templates | sign.template | `[(1, '=', 1)]` |
| sign.template: group_sign_user: Create templates | sign.template | `[(1, '=', 1)]` |
| sign.template: group_sign_user: Manage templates | sign.template | `['|', ('authorized_ids', 'in', user.id), '|', ('group_ids', 'in', user.all_group_ids.ids),` |
| sign.document: group_sign_manager: Create and manage documents | sign.document | `[(1, '=', 1)]` |
| sign.document: group_sign_user: Create documents | sign.document | `[(1, '=', 1)]` |
| sign.document: group_sign_user: Manage documents | sign.document | `['|', ('template_id.authorized_ids', 'in', user.id), '|', ('template_id.group_ids', 'in', ` |
| sign.document: group_sign_user: sign request document access | sign.document | `['|', ('template_id.sign_request_ids.create_uid', '=', user.id), '|', ('template_id.sign_r` |
| sign.item: group_sign_manager: Create and manage template items | sign.item | `[('template_id.has_sign_requests', '=', False)]` |
| sign.item: group_sign_manager: Readonly access to template items | sign.item | `[(1, '=', 1)]` |
| sign.item: group_sign_user: Read template items | sign.item | `['|', ('template_id.authorized_ids', 'in', user.id), '|', ('template_id.group_ids', 'in', ` |
| sign.item: group_sign_user: Create and manage template items | sign.item | `['&', ('template_id.has_sign_requests', '=', False), '|', ('template_id.authorized_ids', '` |
| sign.item.role: group_sign_user: Write/Create/delete own item roles | sign.item.role | `[('create_uid.id', '=', user.id)]` |
| sign.item.role: group_sign_manager: Manage all item roles | sign.item.role | `[(1, '=', 1)]` |
| sign.completed.document: group_sign_manager: Create and manage completed documents | sign.completed.document | `[(1, '=', 1)]` |
| sign.completed.document: group_sign_user: sender: Create and manage sign completed documents | sign.completed.document | `[('create_uid', '=', user.id)]` |
| sign.request: group_sign_manager: Create and manage sign requests | sign.request | `[(1, '=', 1)]` |
| sign.request: group_sign_user: Create sign requests | sign.request | `[(1, '=', 1)]` |
| sign.request: group_sign_user: sender: Manage sign requests | sign.request | `[('create_uid', '=', user.id)]` |
| sign.request: group_sign_user: signer,follower: Manage sign requests | sign.request | `['|', ('message_partner_ids','in', user.partner_id.ids), ('request_item_ids.partner_id', '` |
| sign.request.item: group_sign_manager: Create and manage sign request items | sign.request.item | `[(1, '=', 1)]` |
| sign.request.item: group_sign_user: sender: Create and manage sign request items | sign.request.item | `[('sign_request_id.create_uid', '=', user.id)]` |
| sign.request.item: group_sign_user: follower: Manage sign request items | sign.request.item | `[('sign_request_id.message_partner_ids', 'in', user.partner_id.ids)]` |
| sign.request.item: group_sign_user: signer: Read sign request items | sign.request.item | `[('sign_request_id.request_item_ids.partner_id', 'in', user.partner_id.ids)]` |
| sign.log: group_sign_user: Read sign logs | sign.log | `['|', ('sign_request_id.message_partner_ids', 'in', user.partner_id.ids), '|', ('sign_requ` |
| sign.log: group_sign_manager: Read sign logs | sign.log | `[(1, '=', 1)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
