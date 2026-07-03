# Security & Access Summary — `spreadsheet_edition` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `spreadsheet_edition` — Spreadsheet |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Spreadsheets embed live data views — a shared sheet can expose records beyond the viewer's normal screens; test access inheritance before broad sharing.

## Access rights (ir.model.access) — 3 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_system | `spreadsheet_cell_thread`, `spreadsheet_revision` | — | — |
| group_user | — | `spreadsheet_cell_thread` | — |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
