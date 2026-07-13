# Module Demo Pack: Manufacturing (`mrp`)

| Attribute | Value |
|---|---|
| Edition | Community core; execution layers Enterprise |
| Category | MODULE_DEMO (demo guidance only; product truth lives in the Intelligence Pack module docs, routed via foundation 0012) |
| Rule | Every claim keeps its edition tag and claim label (foundation 0018); nothing here is demo-ready until rehearsed (foundation 0017) |

## Demo purpose
From plan to produced: BoM truth, orders with availability visibility, honest execution story (paper-free is Enterprise).

## Best personas
Manufacturing manager, COO, CFO for costing

## Prerequisites
- Multi-level BoM for a hero product
- routing with work centers
- component stock staged incl. one shortage

## Minimum demo data
- Hero product 2-level BoM
- 3 MOs in different states
- shortage on one component
- cost data for the costing beat

## Recommended flow
- Demand creates MO
- availability check exposes the shortage
- resolve (purchase or transfer)
- produce (Shop Floor tablet if Enterprise, labelled)
- trace and cost review

## Wow moments
- Shortage caught at planning, not at the machine
- Shop Floor tablet with inline quality (E, labelled)
- BoM cost rollup live

## Common mistakes
- Promising finite scheduling
- demoing single-level toy BoMs
- ignoring the operator experience question

## Standard vs custom notes
- BoMs, routes, availability: standard/configuration
- Shop Floor, MPS, PLM, quality: Enterprise
- APS: integration boundary, never promised

## Community vs Enterprise notes
Organized factory Community; instrumented factory Enterprise: a one-sentence framing that lands well

## Likely objections
- Scheduling depth (honest boundary)
- our BoM data is bad (name it as the real workstream)
- machine integration (IoT/MES boundary validated)

## Validation checklist
- Their deepest BoM rebuilt in demo DB
- costing method with finance
- scheduling expectations workshop

## Backup flow
MO staged at every state; shop floor moment has a recorded fallback
