# Shop Floor (`mrp_workorder`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only; hard-depends on `quality` (inline checks are part of the product).

## Likely standard (Enterprise)
Shop Floor operator app (queue, timers, instructions, output/scrap registration) · inline quality checks · barcode scanning of components/lots · Gantt planning by production/work center · operator change proposals to engineering · additional work orders · labor-time capture feeding costing.

## Configuration possibilities
Work centers/capacity/calendars (core), operation steps + instruction content, quality points per operation, floor-display groups (timer control), barcode policy.

## Studio possibilities
Backend MO metadata only. The operator app is a dedicated UI — not a Studio surface.

## Automation possibilities
Delay/scrap alerts, proposal routing, shift-handover digests. Sequencing stays with planners + Gantt; don't script dispatching in rules.

## Custom development is justified when
- Machine adapters beyond IoT patterns (thin, owned adapters).
- Regulated execution records (batch records) after assessing quality/PLM coverage — sometimes specialized systems win.

## External integration is justified when
- MES/SCADA remains the machine layer · APS owns optimization · historians/monitoring platforms.

## What to avoid
- Custom operator screens before piloting the native app on real devices.
- Selling Gantt as APS.
- Time capture framed as surveillance (adoption killer; involve works councils early where applicable).
- Factory-wide big-bang rollout — one line first.

## Deloitte recommendation principles
Sell the bundle honestly (Shop Floor ⇒ quality included), pilot-first with devices, make instruction authoring a named workstream, and route optimization ambitions to the APS boundary rather than overpromising.

## Validation questions
1. Which line pilots first, with which devices and network reality?
2. Who authors and maintains operation instructions?
3. Which times/costs must be captured, and who consumes them (costing? improvement? both)?
