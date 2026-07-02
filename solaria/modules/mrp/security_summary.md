# Security & Access Summary — `mrp` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `mrp` — Manufacturing |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- User vs Manager plus feature groups (work orders, subcontracting via settings) — shop-floor operator roles typically need tailored, narrower access.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| User | group_mrp_user | group_stock_user |
| Administrator | group_mrp_manager | — |
| Manage Work Order Operations | group_mrp_routings | — |
| Produce residual products | group_mrp_byproducts | — |
| Unlocked by default | group_unlocked_by_default | — |
| Use Reception Report with Manufacturing Orders | group_mrp_reception_report | — |
| Use Operation Dependencies | group_mrp_workorder_dependencies | — |

## Access rights (ir.model.access) — 54 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_mrp_user | `mrp_production`, `mrp_production_split_line`, `mrp_unbuild`, `mrp_workcenter_productivity`, `mrp_workorder`, `resource.resource_calendar_attendance` +2 more | `change_production_qty`, `mrp.mrp_production_group`, `mrp_consumption_warning`, `mrp_consumption_warning_line`, `mrp_production_backorder`, `mrp_production_backorder_line` +4 more | `base.res_partner`, `mrp_bom`, `mrp_bom_byproduct`, `mrp_bom_line`, `mrp_routing_workcenter`, `mrp_workcenter` +9 more |
| group_mrp_manager | `mrp_bom`, `mrp_bom_byproduct`, `mrp_bom_line`, `mrp_routing_workcenter`, `mrp_unbuild`, `mrp_workcenter` +8 more | `base.res_partner` | `mrp_production`, `product.product_supplierinfo`, `resource.resource_calendar_leaves` |
| group_stock_user | — | — | `mrp_bom`, `mrp_bom_line`, `mrp_production` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| mrp_production multi-company | — | `[('company_id', 'in', company_ids)]` |
| mrp_unbuild multi-company | — | `[('company_id', 'in', company_ids)]` |
| mrp_workcenter multi-company | — | `[('company_id', 'in', company_ids + [False])]` |
| mrp_workorder multi-company | — | `[('company_id', 'in', company_ids)]` |
| mrp_bom multi-company | — | `[('company_id', 'in', company_ids + [False])]` |
| mrp_bom_line multi-company | — | `[('company_id', 'in', company_ids + [False])]` |
| mrp_bom_byproduct multi-company | — | `[('company_id', 'in', company_ids + [False])]` |
| mrp_routing_workcenter multi-company | — | `[('company_id', 'in', company_ids + [False])]` |
| mrp_workcenter_productivity multi-company | — | `[('company_id', 'in', company_ids)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
