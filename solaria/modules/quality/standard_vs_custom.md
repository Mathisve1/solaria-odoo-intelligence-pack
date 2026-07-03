# Quality (`quality`/`quality_control`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only (no Community quality app). Pack merges `quality` (core) + `quality_control` (app), as noted in the evidence files.

## Likely standard (Enterprise)
Control points per product/operation type with test types (incl. spreadsheet worksheets) · auto-created checks inside stock/manufacturing operations · pass/fail/measure execution · quality alerts with teams, stages, reasons, tags · worksheet reports · shop-floor inline checks (with `mrp_workorder`).

## Configuration possibilities
Control points (scope, frequency, type), teams/stages, reasons/tags taxonomy, worksheet templates, routing of alerts.

## Studio possibilities
Alert metadata fields (defect codes, estimated cost) under a governed taxonomy. Never gate logic via Studio.

## Automation possibilities
Alert aging/SLA nudges, supplier-fail notifications to buyers, periodic audit-check creation, digest KPIs. Gates themselves stay in control points.

## Custom development is justified when
- Regulated QMS artifacts (CAPA workflows beyond alert stages, e-signed quality records, device-history files) are mandatory — after an honest scope assessment; sometimes the answer is a specialized QMS integration instead.
- SPC/statistical analytics beyond basic measures (or route to BI).

## External integration is justified when
- LIMS, metrology/IoT devices, supplier portals, corporate CAPA/compliance platforms.

## What to avoid
- Simulating quality gates with automation rules next to the native engine.
- Over-instrumenting (a check on everything) — throughput death; critical points first.
- Promising regulated-compliance coverage (GxP/ISO) from module existence — gap-assess formally.
- Building supplier scorecards as custom modules when reporting/spreadsheet work suffices.

## Deloitte recommendation principles
Design control points with operations in the room; make the alert taxonomy serve future pareto analysis; treat regulated QMS as a formal gap assessment with compliance experts — that assessment is Deloitte-grade work, not a module toggle.

## Validation questions
1. Which checkpoints are critical-to-quality (evidence: defect/claim history)?
2. Must failed checks hard-block operations — where exactly (verified live)?
3. Which compliance regime applies, and what records does it legally require?
