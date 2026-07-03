# Security & Access Summary — `mrp_workorder` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `mrp_workorder` — MRP II |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Shop-floor display groups gate timer control and floor-app management — map to actual shift roles; operators typically get the app, not backend MO rights.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| Manage Work Order timer on Shop Floor | group_mrp_wo_tablet_timer | — |
| Manage your manufacturing orders from the shop floor display app | group_mrp_wo_shop_floor | — |

## Existing groups this module modifies

These records extend groups owned by other modules (typically adding implied rights) — they do not create new roles:

| Existing group (reference) | Rights/groups implied by this module |
|---|---|
| base.group_user | group_mrp_wo_shop_floor |

## Access rights (ir.model.access) — 2 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_mrp_user | — | `mrp_production_additional_workorder`, `propose_change` | — |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
