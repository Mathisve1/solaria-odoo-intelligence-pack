# Manufacturing (`mrp`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: `mrp` core is Community; shop-floor UI, MPS, PLM, quality gates, IoT are Enterprise.

## Likely standard (Community)
Multi-level BoMs, variants, kits, byproducts · MOs with reservation, backorders, consumption warnings · work centers with capacity & productivity/loss structures · subcontracting · unbuild & scrap · MTO/MTS via routes · lot/serial traceability through production · costing hooks to valuation.

## Configuration possibilities
Routes & lead times, BoM/operation design, consumption policy, backorder policy, work center calendars/capacity, operation dependencies (group), lot policies, warnings, production grouping.

## Studio possibilities (E)
Spec/compliance fields on BoM/MO (drawing no., cert flags), simplified operator views where floor UI isn't used. Never scheduling or consumption logic.

## Automation possibilities
Delay/scrap alerts, auto-activities for planners on exceptions, KPI snapshots. Enterprise quality gates replace most "check reminders" automations — prefer them.

## Custom development is justified when
- Industry costing (process/co-product economics) after standard costing validation with finance and auditors.
- Specialized production documents (batch records) beyond report tweaks — consider quality (E) first.
- Niche machine protocols where IoT box doesn't reach — usually thin adapters.

## External integration is justified when
- APS/finite scheduling is a hard requirement — integrate, don't fake it in Odoo.
- MES/SCADA remains the floor system (Odoo = orders/inventory truth).
- CAD/PDM authoring stays engineering-side (PLM ECO in E for the change workflow).
- LIMS for regulated labs.

## What to avoid
- Custom scheduling engines inside Odoo — the classic budget sink; integrate an APS instead.
- Forking consumption/reservation logic.
- Rebuilding work order execution UI as custom screens when `mrp_workorder` (E) exists.
- Promising process-manufacturing behaviors without a validation pilot.

## Deloitte recommendation principles
Set the scheduling expectation explicitly in the first workshop (availability-based, not APS). Make BoM data readiness a tracked workstream from day one. Costing decisions are finance decisions executed in manufacturing — co-sign them. Demo the floor (E) only when the hardware story is real.

## Validation questions
1. Discrete or process characteristics? Which recipes/batch behaviors are non-negotiable?
2. What does "scheduling" mean to the client — sequencing, capacity leveling, or promise dates?
3. Which quality/compliance documents are mandatory, and does E quality cover them?
4. Machine integration ambitions vs actual protocols available?
