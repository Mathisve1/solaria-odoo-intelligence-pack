# Shop Floor / Work Orders (`mrp_workorder`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `mrp_workorder` |
| Display name | Work Orders / Shop Floor |
| Source origin | **Enterprise** |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `quality`, `mrp`, `barcodes`, `web_gantt`, `web_tour`, `hr_hourly_cost` — note: it **requires quality**; the shop floor ships with quality gating built in |
| Functional domain | Manufacturing (shop-floor execution) |
| Confidence | High for structures/menus; tablet UX and pacing must be validated on real devices |

## Business purpose
The digital factory front end on `mrp`: the **Shop Floor app** (source-verified menu) where operators run work orders on touchscreens — start/pause timers, follow instructions, register output and scrap, execute inline quality checks, scan components — plus planner Gantt views (**Planning by Production / by Work Center**, source-verified) for sequencing. It converts the Community "organized factory" into the Enterprise "instrumented factory".

## Main users / personas
Machine/line operators (tablet execution), team leads (queue management), production planners (Gantt sequencing), quality (inline checks), cost accountants (labor time via `hr_hourly_cost`), engineering (receiving operator change proposals).

## Business problems solved
- Paper travelers/verbal instructions → work-order screens with instructions and inline quality.
- Unknown actual labor → operator timers feeding costing (hourly-cost dependency is in the manifest — labor capture is a design intent, not an accident).
- Sequencing on whiteboards → Gantt planning by work center/production.
- Operator knowledge lost → **`propose.change`** (source-verified model): operators suggest instruction/BoM corrections from the floor — a continuous-improvement hook worth demoing to lean-minded plants.
- Skipped quality steps → checks embedded in the work-order flow (via the hard `quality` dependency).

## Main business processes (source-verified structures)
1. Planner sequences work orders (Gantt by work center; blocked/ready states from `mrp` core: `blocked → ready → progress → done`).
2. Operator opens Shop Floor → my work orders queue → start (timer) → step content (instructions/worksheets) → register production/scrap → inline quality checks → complete.
3. Exceptions: block reasons (productivity-loss taxonomy in `mrp` core), change proposals to engineering, additional work orders (`mrp_production.additional.workorder`).
4. Review: durations vs expected (workcenter productivity models in core), OEE-style analysis via reporting/spreadsheets.

## Fit with other modules
`mrp` (orders/operations backbone), `quality` (hard dependency — checks inline), `barcodes` (component/lot scanning), `hr` timing/costing (`hr_hourly_cost`), `mrp_mps` (planning upstream), `mrp_plm` (change management for the proposals it collects), IoT (`pos`-style device layer via `iot` family — validate specific device needs), `planning` (people shifts vs machine schedule — different tools, clarify in design).

## Community fallback
`mrp` alone: work orders exist as data (states verified in core) but without the Shop Floor operator app, Gantt planning views or inline quality UX. Paper or custom screens — position honestly as the edition difference.

## Configuration opportunities
Work center definitions/capacity (core), operation steps & instructions content, quality points on operations, shop-floor display groups (timer control, floor-app management — source-verified groups), barcode usage policy.

## Studio / automation opportunities
Automation: delay alerts, scrap-threshold notifications, change-proposal routing to engineering. Studio: not on the operator flow (it's a dedicated app); backend fields on MOs only. Instructions/worksheets are content design, not customization.

## Custom development triggers
Machine integration beyond available IoT patterns (adapters), MES-grade dispatching algorithms (integrate an MES instead), industry execution records beyond worksheets (assess vs quality/PLM first).

## External integration triggers
MES/SCADA/historians where they remain the machine layer (Odoo = orders/inventory truth), machine monitoring platforms, skill/certification systems gating operator assignments.

## Common client questions
"Tablets on every station?" — that's the model; device/mount/network plan is part of scope. · "Does it capture actual times?" — timers + productivity models exist (source-verified); the discipline is organizational — pilot it. · "Can operators flag wrong instructions?" — yes, change proposals (demo this; it wins plant hearts). · "Finite scheduling?" — Gantt sequencing ≠ APS optimization — same honesty as the `mrp` pack.

## Fit-gap considerations
The core of the "digital factory" Enterprise story with `quality` and `mrp_mps`. Gap zones: APS optimization, deep machine connectivity, regulated batch records. For mid-market discrete manufacturers, this module usually decides the edition.

## Deloitte demo angles
1. **Operator hour (touchscreen!):** queue → start → instruction step → inline quality check → register output → done. Rehearse on the actual demo device; mouse demos kill it.
2. **Planner beat:** drag a work order in the work-center Gantt — queue rebalanced.
3. **Lean hook:** operator proposes an instruction fix → engineering sees it — continuous improvement in the flow.

## Implementation watch-outs
- Device/ergonomics plan (mounts, gloves, network dead zones) before UX promises.
- Time-capture culture: explain why (costing/improvement), not surveillance — works councils where applicable.
- Instruction content authoring is the real backlog (who writes/maintains steps?).
- Pilot one line first; factory-wide big-bang floor rollouts fail.

## Risks and assumptions
Structures/menus verified. Tablet UX specifics, step-content capabilities, device pairing and timer semantics are runtime → validate on devices. Enterprise licensing required (and it pulls `quality`).

## Validation checklist
- [ ] One-line pilot with real devices and two shifts of operators
- [ ] Instruction/worksheet authoring ownership assigned
- [ ] Time-capture policy socialized (incl. works council where relevant)
- [ ] Machine-integration ambitions mapped to IoT/MES boundary
