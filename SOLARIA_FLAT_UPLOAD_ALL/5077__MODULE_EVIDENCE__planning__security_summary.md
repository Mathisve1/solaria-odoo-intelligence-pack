# Security & Access Summary — `planning` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `planning` — Planning |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Planners manage, employees see published own shifts (portal-ish read paths) — publishing is the security boundary; check open-shift visibility policy.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| User | group_planning_user | group_user |
| Administrator | group_planning_manager | — |

## Access rights (ir.model.access) — 17 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_planning_manager | `planning.planning_recurrency`, `planning.planning_role`, `planning.planning_slot`, `planning.planning_slot_template`, `planning_planning` | `planning_preview`, `planning_send` | — |
| group_planning_user | `planning_calendar_resource` | — | `planning.planning_recurrency`, `planning.planning_role`, `planning.planning_slot`, `planning.planning_slot_template`, `planning_analysis_report` |
| group_user | — | — | `planning.planning_recurrency`, `planning.planning_role`, `planning.planning_slot`, `planning.planning_slot_template` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Planning: internal user can read their own shifts only and open shifts | planning.slot | `[ '|', ('user_id', '=', user.id), '|', ('resource_id', '=', False), ('request_to_switch', ` |
| Planning analysis report: user can read their own shifts | planning.analysis.report | `[('user_id', '=', user.id), ('state', '=', 'published')]` |
| Planning analysis report: manager can read all the shifts | planning.analysis.report | `[(1, '=', 1)]` |
| Planning: user can only see published shifts | planning.slot | `[('state', '=', 'published')]` |
| Planning: manager can create/update/delete all planning entries | planning.slot | `[(1, '=', 1)]` |
| Planning Shift multi-company | planning.slot | `[('company_id', 'in', company_ids)]` |
| Planning Recurrence multi-company | planning.recurrency | `[('company_id', 'in', company_ids)]` |
| Planning Planning multi-company | planning.planning | `[('company_id', 'in', company_ids)]` |
| Planning Analysis Report multi-company | planning.analysis.report | `[('company_id', 'in', company_ids)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
