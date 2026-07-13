# Demo Storyline: Subscription-to-Renewal

| Attribute | Value |
|---|---|
| Category | STORYLINE (instantiates the 12-beat framework, foundation 0009) |
| Rules | Timing limits per format apply (0014); every beat needs data (0016) and rehearsal (0017); editions and claim labels always (0011, 0018) |

## Client problem
Recurring billing on spreadsheets; renewals by memory; MRR debated in every meeting.

## Audience
CFO, CRO, CEO; 45 minutes

## Prerequisites
- sale_subscription (E) with history
- plans configured
- dunning case staged
- cohort view populated

## Modules (edition)
- sale_subscription (E; depends on Enterprise accounting: state it)
- payment tokens per provider (validated)

## Start state
Quote with a recurring plan for the spine customer

## End state
Running subscription upgraded once, renewal secured, MRR movements accounted

## Step-by-step demo flow
1. Quote with plan, activation
2. the invoicing engine's overnight work shown
3. mid-term upgrade with its MRR expansion log
4. failed-payment dunning beat
5. renewal handled as a process with a date
6. cohort/MRR view for the board

## Wow moments
- The MRR movement log
- cohorts telling the retention truth
- dunning path shown honestly

## Challenger insight
MRR without agreed definitions is a fight, not a metric: the definitions workshop is the first deliverable, the software enforces it afterwards.

## Likely questions
- Usage billing? (validate scope)
- proration? (sandbox)
- our churn definition?

## Risks
Metric questions without the definitions-workshop honesty

## Validation points
- Billing edge cases in sandbox
- PSP token support
- contract migration rehearsal

## Short version (15 min)
Plan to invoice-run to MRR view

## Executive version (30 min)
Predictable-revenue framing, engine run, board-metrics close
