# Workflow & Automation Summary — `stock_barcode` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `stock_barcode` — Barcode |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Execution flow mirrors stock pickings: scan location → product/lot → quantity → validate; the app is stateless sugar over stock.picking/stock.move — migration/cutover logic stays in stock.
- GS1 nomenclature drives scan parsing (from stock's GS1 groups) — barcode data quality is the real implementation workstream.

## Integration surface
- Direct dependencies: `stock`, `web_tour`, `web_mobile`
- Sequences configured: 1 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
