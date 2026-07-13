# Persona Demo Pack: COO

| Attribute | Value |
|---|---|
| Category | PERSONA (extends foundation file 0008) |
| Rule | Refine with intake section D; this pack gives defaults, the intake gives truth. Foundation rules override. |

## Priorities
- Throughput and reliability
- Exceptions surfaced early, not discovered late
- One operational truth across sites

## Likely frustrations
- Firefighting as the default operating mode
- Handoffs between departments losing information
- Reports that describe last month instead of today

## Business KPIs
OTIF, first-time-right, cycle times, backlog age, inventory accuracy, utilisation

## Demo emphasis
- The exception beat (storyline beat 8): break something and watch it surface
- The daily worklists of their teams
- The chain: order to warehouse to delivery to invoice without a swivel chair

## Relevant Odoo modules
stock, purchase, mrp (Community core), quality and stock_barcode and mrp_workorder (Enterprise, labelled), automation rules for escalations (Community)

## Suitable Challenger insights
- Most operational firefighting is late information, not bad people; surfacing exceptions at creation time removes the fire
- Handoffs are where margin leaks; every re-typing step is an error factory

## Likely objections
- Will this disrupt operations during migration? (implementation risk)
- Our volumes? (scalability, honest validation answer)

## Unsuitable demo content
- Slide-heavy strategy sections
- Happy-path-only flows
- Marketing language

## Opening questions
- What was your last operational surprise, and when did you learn about it versus when did it happen?
- Which handoff between departments hurts most?

## Recommended closing
Pick your ugliest real order of last month; in the POC we replay it in Odoo and show where it would have been caught.
