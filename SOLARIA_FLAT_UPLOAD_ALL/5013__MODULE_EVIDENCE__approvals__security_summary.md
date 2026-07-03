# Security & Access Summary — `approvals` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `approvals` — Approvals |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Approver assignment is data (category approvers), not just groups — the approval matrix lives in configuration; audit who can edit categories.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| Officer: Approve all requests | group_approval_user | group_user |
| Administrator | group_approval_manager | — |

## Access rights (ir.model.access) — 14 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_user | `approval_product_line`, `approval_request` | `approval_approver` | `approval_category`, `approval_category_approver` |
| group_approval_manager | `approval_approver`, `approval_category`, `approval_category_approver`, `approval_product_line`, `approval_request` | — | — |
| group_approval_user | `approval_approver`, `approval_request` | — | `approval_category`, `approval_category_approver` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Approval Request: request approver rule | approval.request | `['|', '|', ('request_owner_id', '=', user.id), ('approver_ids.user_id','=', user.id), '&',` |
| Approval Product Line: request approver rule | approval.product.line | `['|', '|', ('approval_request_id.request_owner_id', '=', user.id), ('approval_request_id.a` |
| Approval Request: unlink request owner rule | approval.request | `[('request_owner_id', '=', user.id), ('request_status', 'in', ['cancel', 'new'])]` |
| Approval Approver: read own request | approval.approver | `['|', ('request_id.request_owner_id', '=', user.id), ('user_id', '=', user.id)]` |
| Approval Approver: change own | approval.approver | `[('user_id', '=', user.id)]` |
| Approval Request: user | approval.request | `[(1, '=', 1)]` |
| Approval Request: user unlink | approval.request | `[('request_status','=','cancel')]` |
| Approval Product Line: user | approval.product.line | `[(1, '=', 1)]` |
| Approval Product Line: user unlink | approval.product.line | `[('approval_request_id.request_status','=','cancel')]` |
| Approval Approver: unlink unapproved | approval.approver | `[('request_id.request_status', 'in', ['new', 'pending', 'cancel'])]` |
| Approval Request: manager | approval.request | `[(1, '=', 1)]` |
| Approval Approver: manager | approval.approver | `[(1, '=', 1)]` |
| approval_request multi-company | — | `[('company_id', 'in', company_ids)]` |
| approval_category multi-company | — | `[('company_id', 'in', company_ids)]` |
| approval_approver multi-company | — | `[('company_id', 'in', company_ids)]` |
| approval_product_line multi-company | — | `[('company_id', 'in', company_ids)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
