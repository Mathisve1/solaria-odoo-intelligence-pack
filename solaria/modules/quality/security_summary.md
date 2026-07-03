# Security & Access Summary — `quality` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `quality` — Quality Base (pack merges: `quality`, `quality_control`) |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Quality User vs Administrator plus team-based alert routing; decide whether operators may create alerts (usually yes) vs edit control points (usually no).

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| User | quality.group_quality_user | group_user |
| Administrator | quality.group_quality_manager | group_quality_user |

## Existing groups this module modifies

These records extend groups owned by other modules (typically adding implied rights) — they do not create new roles:

| Existing group (reference) | Rights/groups implied by this module |
|---|---|
| stock.group_stock_user | group_quality_user |

## Access rights (ir.model.access) — 25 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_quality_user | — | `quality.quality_alert`, `quality.quality_check`, `quality_check_wizard`, `quality_control.quality_check_spreadsheet` | `quality.quality_alert_stage`, `quality.quality_alert_team`, `quality.quality_point`, `quality.quality_point_test_type`, `quality.quality_reason`, `quality.quality_tag` +4 more |
| group_quality_manager | `quality.quality_alert`, `quality.quality_alert_stage`, `quality.quality_alert_team`, `quality.quality_check`, `quality.quality_point`, `quality.quality_reason` +3 more | — | — |
| group_stock_user | — | `quality.quality_check` | — |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Quality alert company rule | quality.alert | `[('company_id', 'in', company_ids)]` |
| Quality check company rule | quality.check | `['|', ('company_id', 'in', company_ids), ('point_id.company_id', 'in', company_ids)]` |
| Control point company rule | quality.point | `[('company_id', 'in', company_ids)]` |
| Quality Team multi-company | quality.alert.team | `[('company_id', 'in', company_ids + [False])]` |
| Quality check spreadsheet company rule | quality.check.spreadsheet | `[('company_id', 'in', company_ids)]` |
| Quality spreadsheet template company rule | quality.spreadsheet.template | `[('company_id', 'in', company_ids)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
