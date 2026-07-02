# Security & Access Summary — `marketing_automation` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `marketing_automation` — Marketing Automation |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Marketing users manage campaigns; sending identity/domain is an org-level decision — govern who may launch mass journeys.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| User | group_marketing_automation_user | group_user, group_mass_mailing_user |

## Access rights (ir.model.access) — 6 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_marketing_automation_user | `marketing_activity`, `marketing_campaign`, `marketing_participant`, `marketing_trace` | `marketing_campaign_test` | `base.ir_fields` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
