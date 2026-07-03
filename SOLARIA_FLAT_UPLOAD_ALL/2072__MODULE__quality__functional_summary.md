# Quality (`quality` + `quality_control`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `quality` (core models) + `quality_control` (app/menus) — this pack merges both, as the evidence files note |
| Display name | Quality |
| Source origin | **Enterprise** (both modules) |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `quality` ← `stock`; `quality_control` ← `quality`, `spreadsheet_edition` |
| Functional domain | Quality (supply chain & manufacturing) |
| Confidence | High for structures; check-type UX and worksheet depth need live validation |

## Business purpose
Quality management woven into operations rather than bolted on: **control points** define what to check, where (operation type/product), and how; **quality checks** are then created automatically inside receipts, transfers and manufacturing steps; failures raise **quality alerts** routed to teams through configurable stages. The result: quality is a gate in the flow, not a spreadsheet after the fact.

## Main users / personas
Quality managers (control points, alert triage), warehouse/production operators (execute checks in their operation screens), supplier quality (incoming inspection), plant leadership (alert trends), regulated-industry compliance owners.

## Business problems solved
- Paper/Excel inspections detached from operations → checks generated in-flow from control points (`quality.point` with test types incl. **spreadsheet-based worksheets** via `quality_control` — source-verified `quality.check.spreadsheet`, `quality.spreadsheet.template`).
- Failure handling by email → `quality.alert` with teams (`quality.alert.team`), kanban stages (`quality.alert.stage`), reasons/tags taxonomy — helpdesk-style triage for defects.
- Skipped inspections → checks block/gate operations per configuration (validate exact blocking semantics live).
- Audit evidence → worksheet reports (source-verified report actions) and check history per product/lot.

## Main business processes (source-verified structures)
1. Define control points: product/category × operation type × frequency-ish parameters (validate frequency options live) × test type (`quality.point.test_type` — pass/fail, measure, worksheet…; enumerate live).
2. Operate: check appears in the receipt/MO/work order → operator executes → pass/fail (+measures/worksheet).
3. React: fail → alert → team queue → stages to resolution, with reasons for pareto analysis.
4. Analyze: checks/alerts reporting; spreadsheet worksheets make evidence analyzable.

## Fit with other modules
`stock` (checks on logistics operations), `quality_mrp`(+workorder bridges — checks inside production/shop floor), `mrp_workorder` (inline checks on the tablet — depends on `quality`), `spreadsheet_edition` (worksheet templates), purchase context for supplier quality (via receipts). Helpdesk/FSM adjacency for field-originated defects (process design, not shipped bridge — validate need).

## Community fallback (be honest)
None — no quality app in Community 19.0. Workarounds (checklist fields, project tasks) lose in-flow gating and alert management; position as compromises for non-critical needs only.

## Configuration opportunities
Control points (the heart — what/where/how), test types usage, teams & stages, reasons/tags, worksheet templates, alert routing.

## Studio / automation opportunities
Automation: alert SLA nudges, supplier-quality notifications (fail on receipt → buyer activity), recurring audit-check creation. Studio: extra fields on alerts (defect codes, cost estimates) under a governed taxonomy. Keep gating logic in control points — never simulate quality gates with automation rules.

## Custom development triggers
Regulated regimes (GxP/ISO with e-signature-on-record, CAPA workflows beyond alert stages) — assess honestly; may need dedicated design or specialized systems. Statistical process control (SPC) beyond basic measures → analytics/custom/integration decision.

## External integration triggers
LIMS (labs), measurement devices/IoT (via `iot` patterns where supported — validate), supplier quality portals, CAPA/compliance suites in regulated industries.

## Common client questions
"Can a failed check block the delivery/production step?" — designed for gating; validate the exact blocking behavior per operation type live before committing. · "Photos/measurements on checks?" — test types + attachments; enumerate live. · "Supplier scorecards?" — data exists (checks/alerts per vendor via receipts); scorecard = reporting/spreadsheet work — say so. · "ISO documentation?" — evidence yes; a full QMS documentation layer is process + Documents/Knowledge design, not automatic.

## Fit-gap considerations
High fit for discrete-manufacturing and distribution QC. Gap zones: regulated QMS depth (CAPA, DHF, e-sign records), SPC analytics, lab integration. Its Enterprise-only status is an edition driver for manufacturing deals alongside `mrp_workorder`.

## Deloitte demo angles
1. **In-flow gate:** receive a PO → check pops inside the receipt → fail it → alert appears in the quality team's kanban — the "quality lives in the flow" moment.
2. **Shop floor (with mrp_workorder):** check inline on the operator tablet.
3. **Manager view:** alert pareto by reason; worksheet spreadsheet evidence.

## Implementation watch-outs
- Control-point design workshop with real operations (over-checking kills throughput; start with critical points).
- Alert taxonomy (reasons/tags) designed for the pareto you'll want later.
- Operator UX buy-in — checks must be fast or they get pencil-whipped.
- Regulated clients: gap-assess against their QMS obligations before promising coverage.

## Risks and assumptions
Structures verified (models, menus, worksheet reports, groups incl. the pack-merge note in evidence files). Blocking semantics, test-type list, frequency options and device integrations are runtime → validate live. Enterprise licensing required.

## Validation checklist
- [ ] Critical control points piloted in a demo flow (receipt + MO)
- [ ] Blocking behavior verified per operation type
- [ ] Alert taxonomy + team routing designed with the quality manager
- [ ] Regulated-scope gap assessment done (if applicable)
