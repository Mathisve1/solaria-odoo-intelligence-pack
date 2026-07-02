# Workflow & Automation Summary — `product` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `product` — Products & Pricelists |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Master-data lifecycle (active/archived, variants generation from attributes); price computation via pricelists is rule evaluation, not workflow.

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Print Labels | product.template | code |
| Pricelist Report | product.template | code |
| Print Labels | product.product | code |
| Pricelist Report | product.product | code |

## Integration surface
- Direct dependencies: `base`, `mail`, `uom`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
