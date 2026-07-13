# Industry Demo Pack: Wholesale and Distribution

| Attribute | Value |
|---|---|
| Category | INDUSTRY (defaults to confirm; never a substitute for client intake) |
| Product truth | All module claims route via the Intelligence Pack (foundation 0012); editions labelled; statutory items always validation |

## Operating model
Buy smart, stock right, ship fast; margin lives in purchasing conditions, inventory turns and delivery reliability; B2B relationships with price agreements.

## Common pain points
- Stockouts next to overstock
- Customer-specific pricing chaos
- Picking errors and returns
- Margin per customer unknown
- Manual order intake

## Common process flows
- Procure-to-pay with reordering automation
- Order-to-cash B2B incl. portal and EDI-like intake
- Warehouse-to-delivery with carriers
- Returns handling

## Relevant Odoo modules
- sale, purchase, stock with reordering rules, pricelists (Community)
- stock_barcode, carrier connectors, B2B portal pricing via website_sale (Community core, connectors Enterprise, labelled)

## Relevant KPIs
OTIF, inventory turns, margin per customer/product, pick accuracy, stockout rate, purchase rebate capture

## Suitable demo storyline
Warehouse-to-Delivery spine wrapped in order-to-cash: B2B portal order at customer price, availability, pick with scanner, carrier label, invoice; replenishment fires behind the scenes (storyline 2050 pattern)

## Persona emphasis
COO, warehouse manager, purchasing lead, sales director for pricing, CFO for margin

## Challenger insights
- Service level is bought in purchasing, not in the warehouse: replenishment parameters decide most stockouts
- Customer-specific pricing in spreadsheets is margin leakage with a UI

## Likely objections
- Our pricing agreements are too complex (rebuild three real ones in pricelists)
- WMS-grade needs? (honest boundary)
- Carrier landscape? (connector check per carrier, Enterprise)

## Data required for demo
Catalog with customer-specific pricelists, reordering rules on hero SKUs, one engineered stockout, carrier setup (labelled if simulated), B2B portal user

## Localisation and validation concerns
Intrastat and e-invoicing per country (validation), carrier connector coverage (catalog check plus commercial validation)

## What not to overclaim
- Slotting/wave optimisation (WMS boundary)
- EDI coverage without checking the specific network
- Real-time accuracy as a product property (it is process discipline)
