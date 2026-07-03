# Spreadsheet Edition (`spreadsheet_edition`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise (on the Community `spreadsheet` engine). Community = view/prebuilt dashboards; Enterprise = create/edit/collaborate.

## Likely standard (Enterprise)
Live-linked spreadsheets from any pivot/list · full editing · cell comment threads · revision history · dashboard creation (with dashboard siblings — verify exact module split in catalog) · Documents storage via `documents_spreadsheet` · Excel import/export at engine level (fidelity: validate).

## Configuration possibilities
Templates for recurring packs, curation/ownership conventions, workspace policy, distribution rituals.

## Studio possibilities
Not applicable — this is an analytics surface, not a shape-customization target.

## Automation possibilities
Review-cycle and distribution activities. Do not encode business rules as spreadsheet formulas that transactions then "must match" — the ERP is the rule engine.

## Custom development is justified when
- Custom functions/data connectors are genuinely required (rare; specialist maintenance) — challenge against the BI boundary first.

## External integration is justified when
- Cross-system analytics, data-warehouse scale, advanced modeling/ML — enterprise BI territory; Odoo feeds it.

## What to avoid
- Recreating statutory reports as sheets (compliance risk — `account_reports` owns those).
- Sheet sprawl without owners (the new export sprawl).
- Sharing before leak-testing access inheritance.
- Promising Excel-parity — validate fidelity on the client's real files.

## Deloitte recommendation principles
Position as the export-killer for Odoo-data management reporting, with governance (owners, curation, revisions) as the differentiator; keep statutory and enterprise-BI boundaries explicit in every register.

## Validation questions
1. Which recurring Excel reports exist today, on which data, for whom?
2. Which of those are statutory (→ account_reports) vs management (→ here) vs cross-system (→ BI)?
3. Who curates the sheet library after go-live?
