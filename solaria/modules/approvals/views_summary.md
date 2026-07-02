# Views & Navigation Summary — `approvals` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `approvals` — Approvals |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Category kanban (New Request tiles) plus request form with approver status bar — clean, self-explanatory demo.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Approvals | approval_category_action_new_request | — |
| Approvals / Configuration | — | group_approval_manager |
| Approvals / Configuration / Approval Categories | approval_category_action | group_approval_manager |
| Approvals / Configuration / Products | — | — |
| Approvals / Configuration / Products / Product Variants | product_product_action | product.group_product_variant |
| Approvals / Configuration / Products / Products | product_template_action | — |
| Approvals / Dashboard | approval_category_action_new_request | — |
| Approvals / Manager | — | — |
| Approvals / Manager / All Approvals | approval_request_action_all | — |
| Approvals / Manager / Approvals to Review | approval_request_action_to_review | — |
| Approvals / My Approvals | — | — |
| Approvals / My Approvals / My Requests | approval_request_action | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Dashboard | approval.category | kanban |
| Approval Categories | approval.category | list,form |
| Approvals to review | approval.request | list,form,kanban |
| Products | product.template | kanban,list,form |
| Product Variants | product.product | list,form,kanban,activity |
| My Requests | approval.request | kanban,list,form |
| Approvals to Review | approval.request | list,form,kanban |
| All Approvals | approval.request | list,form,kanban |

## View inventory

- Primary views defined: 13 (list: 5, form: 3, kanban: 3, search: 2)
- Inheriting views (UI extensions of other modules): 0
- Richest UI objects: `approval.category` (form, kanban, list, search); `approval.request` (form, kanban, list, search); `approval.product.line` (form, kanban, list); `approval.category.approver` (list)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Approval Request | approval.request | qweb-pdf |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
