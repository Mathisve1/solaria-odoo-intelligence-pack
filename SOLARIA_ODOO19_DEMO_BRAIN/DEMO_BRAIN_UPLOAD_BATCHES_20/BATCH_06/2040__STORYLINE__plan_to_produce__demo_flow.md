# Demo Storyline: Plan-to-Produce

| Attribute | Value |
|---|---|
| Category | STORYLINE (instantiates the 12-beat framework, foundation 0009) |
| Rules | Timing limits per format apply (0014); every beat needs data (0016) and rehearsal (0017); editions and claim labels always (0011, 0018) |

## Client problem
Orders released blind, shortages discovered at the machine, paper travelers hiding the truth.

## Audience
Manufacturing manager, COO, CFO (costing); 60 minutes

## Prerequisites
- mrp + stock rehearsed
- hero BoM 2 levels
- engineered shortage
- Shop Floor device if Enterprise (labelled)

## Modules (edition)
- mrp (C)
- stock (C)
- mrp_workorder Shop Floor + quality labelled (E)

## Start state
MTO order confirmed for the hero product

## End state
Produced, quality-checked (E), delivered; cost review on the MO

## Step-by-step demo flow
1. Order creates the MO
2. availability check exposes the component shortage
3. resolve via purchase suggestion
4. release to the floor
5. operator tablet: start, instructions, inline quality check (E, labelled)
6. register production with lot
7. deliver and trace
8. cost rollup review

## Wow moments
- Shortage caught at planning
- the tablet moment with inline quality
- the two-way lot trace

## Challenger insight
Late orders are usually late at release, not at the machine: availability visibility beats expediting heroics.

## Likely questions
- Finite scheduling? (honest boundary)
- subcontracting?
- scrap handling?

## Risks
Tablet demo unrehearsed on the actual device (the classic FSM/MRP demo killer)

## Validation points
- Their deepest BoM rebuilt
- costing method with finance
- scheduling expectations workshop

## Short version (15 min)
MO with shortage caught, produce, trace

## Executive version (30 min)
OTD framing, compress execution, expand the planning-visibility insight
