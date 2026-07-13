# Industry Demo Pack: Manufacturing

| Attribute | Value |
|---|---|
| Category | INDUSTRY (defaults to confirm; never a substitute for client intake) |
| Product truth | All module claims route via the Intelligence Pack (foundation 0012); editions labelled; statutory items always validation |

## Operating model
Convert materials through capacity into products; margin lives in throughput, scrap, procurement and schedule adherence; MTO/MTS mix defines complexity.

## Common pain points
- BoM truth in spreadsheets
- Late orders discovered late
- Paper on the shop floor
- Material shortages surprise the line
- Costing disconnected from reality

## Common process flows
- Plan-to-produce
- Procure-to-pay for direct materials
- Order-to-cash MTO with engineering touches
- Quality gates on receipt and production

## Relevant Odoo modules
- mrp, stock, purchase, sale (Community core)
- mrp_workorder Shop Floor, quality, mrp_mps, stock_barcode, plm (Enterprise, labelled)

## Relevant KPIs
OTD, scrap rate, schedule adherence, inventory turns, purchase price variance, OEE direction

## Suitable demo storyline
Plan-to-Produce spine: MTO order, MO with availability check, shop floor execution with inline quality, delivery, cost review (storyline 2040 pattern)

## Persona emphasis
COO, manufacturing manager, warehouse manager, CFO for costing, operators as end users

## Challenger insights
- Orders are late at release, not at the machine: availability visibility beats expediting heroics
- The shop floor tablet is a knowledge-capture device, not a control device

## Likely objections
- Finite scheduling expectations (honest APS boundary)
- Our BoMs are a mess (name the data workstream)
- Production cannot stop for a migration (phasing answer)

## Data required for demo
Multi-level BoM for a hero product, routing with 2-3 work centers, component stock with one engineered shortage, quality point on one operation, cost data

## Localisation and validation concerns
Costing method with finance (validation), machine integration ambitions (IoT boundary validation), country statutory as always

## What not to overclaim
- APS-grade finite scheduling
- Process-industry batch behaviours without a dedicated validation workshop
- OEE dashboards as automatic (they need capture discipline)
