# Security & Access Summary — `web_studio` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `web_studio` — Studio |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Studio grants effectively let a user reshape apps — treat Studio access like admin-light: named users, registry of changes, staging-first policy.
- Studio approval rules create approval obligations ON actions — document who may edit rules; an unmanaged rule can block operations.

## Access rights (ir.model.access) — 10 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_system | `studio_approval_rule_approver`, `web_studio.studio_approval_request`, `web_studio.studio_approval_rule`, `web_studio.studio_export_model`, `web_studio.studio_export_wizard`, `web_studio.studio_export_wizard_data` | `web_studio.studio_approval_entry` | — |
| group_user | — | `studio_approval_rule_delegate`, `web_studio.studio_approval_entry` | `web_studio.studio_approval_rule` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Studio Validation Entries: manage your own entries (user) | studio.approval.entry | `[('user_id', '=', user.id)]` |
| Studio Validation Entries: manage all entries (admin) | studio.approval.entry | `[(1, '=', 1)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
