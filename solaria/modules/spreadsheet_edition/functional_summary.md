# Spreadsheet Edition (`spreadsheet_edition`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `spreadsheet_edition` |
| Display name | Spreadsheet Edition |
| Source origin | **Enterprise** (extends Community `spreadsheet` engine) |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `spreadsheet`, `mail`, `web_enterprise` |
| Functional domain | Spreadsheet / BI / management analytics |
| Confidence | High for structures; editor depth and refresh semantics need live validation |

## Business purpose
The Enterprise layer that makes Odoo's spreadsheet a working analytics tool: full editing of spreadsheets linked to **live ERP data** (insert any pivot/list into a sheet), with **cell-level comment threads** and **revision history** (both source-verified: `spreadsheet.cell.thread`, `spreadsheet.revision`). It is Odoo's answer to "we export everything to Excel" — the numbers stay governed, permissioned and live.

## Main users / personas
Controllers/finance analysts (management views on live figures), department managers (KPI sheets), executives (dashboards via `spreadsheet_dashboard*` siblings), documents users (sheets stored in Documents via `documents_spreadsheet`).

## Business problems solved
- Export-to-Excel decay (numbers stale on arrival) → live-linked cells to Odoo data.
- Untracked spreadsheet edits → revision history; discussion in mail-threads on cells instead of email ping-pong.
- Dashboard tooling gap between pivots and full BI → spreadsheet-based dashboards (Community ships viewing/prebuilt `spreadsheet_dashboard`; this module enables the editing/creation story — validate exact split live).

## Main capabilities (source-verified structures)
- 2 defined models (cell threads, revisions) + engine extensions — the heavy machinery lives in the Community `spreadsheet` module; this layer adds editing/collaboration.
- Insert-from-anywhere pattern: pivots/lists → spreadsheet (the flagship gesture; rehearse live).
- Menus: Spreadsheet / Revisions (the audit surface).

## Fit with other modules
`spreadsheet` (Community engine), `spreadsheet_dashboard*` (dashboards; several per-app dashboard modules exist — see catalog), `documents_spreadsheet` (storage/management in DMS), per-app bridges (e.g., `spreadsheet_sale_management`). Data comes from any model the user can read — **security inheritance is the critical test** (a shared sheet must not leak rows the viewer can't normally see; test before broad rollout).

## Standard vs edition
Community: spreadsheet engine, prebuilt dashboards (view-level). Enterprise (this module +siblings): create/edit live spreadsheets, cell threads, revisions, dashboard editing, Documents storage. "Self-service management reporting inside Odoo" is an Enterprise story — say it precisely.

## Configuration opportunities
Sheet templates for recurring reviews (month-end pack), dashboard curation, storage/workspace policy (with Documents), naming/ownership conventions.

## Studio / automation opportunities
Not a Studio surface. Automation: distribution/review-cycle activities. Data logic belongs in the sheets' source models/pivots, not in exotic formulas replicating business rules.

## Custom development triggers
Rare: custom spreadsheet functions/connectors (specialist work; challenge vs BI boundary first).

## External integration triggers
Enterprise BI/warehouse platforms for cross-system analytics, big-data volumes, advanced modeling — the honest boundary: Odoo spreadsheets excel at *operational/management views on Odoo data*, not at enterprise BI. Position integration, not failure.

## Common client questions
"Can we finally kill the Excel exports?" — for Odoo-data reporting, largely yes (E); demo the live link + revision trail. · "Is it Excel-compatible?" — import/export exists at engine level; fidelity limits are real — validate with the client's actual files. · "Who sees what in a shared sheet?" — inheritance from record rights — test the specific sharing scenarios (leakage check). · "Real dashboards?" — spreadsheet dashboards + per-app dashboard modules (catalog); enterprise-BI expectations → integration boundary.

## Fit-gap considerations
Closes the most common "reporting gap" complaints (management views, KPI packs) without BI projects. Keep statutory reporting (`account_reports`) and enterprise BI explicitly out of its scope in registers to avoid mixed verdicts.

## Deloitte demo angles
1. **Live link:** sales pivot → Insert in Spreadsheet → edit → change an order → refresh — the number moves. The anti-export demo.
2. **Collaboration:** comment thread on a cell + revision history — governance for spreadsheets, finally.
3. **Month-end pack:** a curated template sheet as the management-reporting deliverable concept (label as Deloitte template practice, not shipped content).

## Implementation watch-outs
- Sheet sprawl replaces export sprawl if ungoverned — ownership + curation cadence.
- Access-leakage testing before sharing culture spreads.
- Excel-fidelity expectations managed with the client's real files early.

## Risks and assumptions
Structures verified. Editing depth, refresh semantics, Excel round-trip fidelity and dashboard-edit boundaries vs `spreadsheet_dashboard_edition`-class siblings (see catalog) → validate live. Enterprise licensing required.

## Validation checklist
- [ ] Top-10 current Excel reports rebuilt as live sheets in a pilot
- [ ] Sharing/access scenarios leak-tested
- [ ] Excel import/export fidelity checked on real files
- [ ] BI boundary agreed (what stays in Odoo sheets vs warehouse/BI)
