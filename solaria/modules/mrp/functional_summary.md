# Manufacturing (`mrp`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `mrp` |
| Display name | Manufacturing |
| Source origin | **Community** (Enterprise adds `mrp_workorder` shop floor, `mrp_mps` master schedule, `mrp_plm`, `quality_mrp`, IoT) |
| Version scope | Odoo 19.0 |
| Dependencies | `stock`, `product` |
| Functional domain | Manufacturing / plan-to-produce |
| Confidence | High for structures; scheduling/costing behavior needs live validation |

## Business purpose
Run plan-to-produce: define what products are made of (BoMs) and how (operations/work centers), launch and execute manufacturing orders with component reservation and traceability, and understand capacity and productivity — integrated natively with stock and costing.

## Main users / personas
Production planners, shop-floor operators (E work orders), production managers, engineering (BoMs; PLM in E), cost accountants.

## Business problems solved
- BoM truth scattered in Excel/legacy → structured multi-level BoMs with variants, byproducts (`mrp.bom.byproduct`), kits.
- Opaque WIP → MO lifecycle with component availability like pickings.
- Capacity blindness → work centers with capacity (`mrp.workcenter.capacity`), productivity/loss tracking (`mrp.workcenter.productivity[.loss]`) — OEE-grade data structures are standard.
- Rework/teardown chaos → unbuild (`mrp.unbuild`), scrap flows.

## Main business processes (source-verified lifecycle)
- `mrp.production` (MO): **draft → confirmed → progress → to_close → done / cancel**, with component reservation, consumption warnings (`mrp.consumption.warning`), backorders (`mrp.production.backorder`).
- `mrp.workorder` (structure in Community; execution UX in E): **blocked → ready → progress → done / cancel** per operation/work center.
- Make-to-stock via orderpoints (manufacture route) or make-to-order from sales; multi-level: MO explosion to child MOs (validate exact behavior live).
- Unbuild and scrap; production grouping (`mrp.production.group`, 19.0).

## Key functional capabilities
BoM versions per variant, operations with routing work centers (`mrp.routing.workcenter`), kits (phantom BoMs), byproducts group-gated ("Produce residual products"), subcontracting (`mrp_subcontracting`, Community), lot/serial production traceability, planning by availability, capacity & productivity loss taxonomy, "Use Operation Dependencies" group (sequenced operations), reception report with MOs.

## Fit with other modules
`stock` (components, finished goods, routes), `purchase` (buy components, subcontractor supply), `sale` (MTO), `account`/`stock_account` (WIP-ish costing via valuation — validate method), `maintenance` (Community, work center link), Enterprise: `mrp_workorder` (tablet execution), `quality_mrp` (gates), `mrp_mps` (S&OP-light), `mrp_plm` (ECO management), `iot`.

## Standard in 19.0 (Community)
Multi-level BoMs/kits/byproducts, MOs with reservation & backorders, work centers incl. capacity/productivity structures, subcontracting, unbuild/scrap, availability-based planning, costing hooks, traceability.

## Enterprise-specific additions
Shop-floor work order UI (tablet), master production schedule, PLM/engineering change orders, quality checks in production, IoT devices, Gantt-grade planning views. The "digital factory" is Enterprise; the "organized factory" is Community.

## Configuration opportunities
BoM structures/kits, routing operations & work centers, manufacture routes & lead times, consumption policies (flexible/strict — validate options), lot policies, backorder policy, operation dependencies group, subcontracting flows.

## Studio / automation opportunities
Automation: MO delay alerts, scrap-rate notifications, auto-tag orders by product family. Studio (E): extra spec fields on MOs/BoMs (compliance flags, drawing refs). Scheduling logic and consumption logic stay native.

## Custom development triggers
Finite-capacity/APS-grade scheduling (native is availability/lead-time based — set expectations); industry costing schemes (process industries) after validating standard costing with finance; complex co/by-product economics; MES-depth machine integration beyond IoT scope.

## External integration triggers
APS systems (scheduling stays there), MES/SCADA/historians, CAD/PDM (PLM in E covers ECO workflow, not CAD authoring), quality LIMS.

## Common client questions
"Multi-level BoM with variants?" — native. · "Shop floor terminals?" — Enterprise `mrp_workorder`. · "Finite scheduling?" — not APS-grade natively; be straight, propose MPS (E) + pragmatic rules or APS integration. · "Subcontracting?" — native Community. · "OEE?" — productivity/loss structures exist; dashboarding via spreadsheet/BI; validate depth.

## Fit-gap considerations
Excellent fit for discrete mid-market manufacturing. Watch: process manufacturing (batches/recipes — validate carefully), APS expectations, regulated QA (E quality + validation), deep machine integration. BoM data readiness is usually the critical path.

## Deloitte demo angles
1. **Order-to-build:** sale (MTO) → MO auto-created → components reserved → produce → serial trace back from delivery.
2. **Planner story:** availability-based MO list, backorder handling, capacity view; (E) MPS for the S&OP conversation.
3. **Factory floor (E):** tablet work order → quality check → productivity/loss capture → OEE talk track.

## Implementation watch-outs
- BoM cleansing/migration is the project inside the project — start immediately.
- Costing method alignment (standard vs AVCO/FIFO, overhead treatment) with finance early.
- Don't promise APS behavior; pilot scheduling expectations against real orders.
- Operator adoption (E floor UI) needs hardware + shift training plans.

## Risks and assumptions
Structures verified in source; scheduling heuristics, consumption tolerance options and costing postings are runtime → validate with a pilot dataset. Process-industry fit requires a dedicated validation workshop.

## Validation checklist
- [ ] Representative BoMs (deepest/most variant-heavy) rebuilt in a demo DB
- [ ] Scheduling expectations tested against availability-based logic
- [ ] Costing flows validated with finance on sample MOs
- [ ] Edition decisions for floor UI/quality/PLM/MPS confirmed
- [ ] Machine/IoT integration scope defined with plant engineering
