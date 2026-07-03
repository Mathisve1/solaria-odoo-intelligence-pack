# Security & Access Summary — `base_automation` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `base_automation` — Automation Rules |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Automation rules run with system-level effect — restrict rule editing to admins; every rule is an unaudited process change if ungoverned.
- Failing rules can silently break flows: monitoring/ownership per rule is an operations requirement, not a nicety.

## Access rights (ir.model.access) — 1 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_system | `base_automation` | — | — |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
