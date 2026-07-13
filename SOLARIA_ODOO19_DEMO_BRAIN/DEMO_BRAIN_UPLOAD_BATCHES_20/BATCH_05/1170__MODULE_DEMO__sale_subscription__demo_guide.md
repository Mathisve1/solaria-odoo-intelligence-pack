# Module Demo Pack: Subscriptions (`sale_subscription`)

| Attribute | Value |
|---|---|
| Edition | Enterprise |
| Category | MODULE_DEMO (demo guidance only; product truth lives in the Intelligence Pack module docs, routed via foundation 0012) |
| Rule | Every claim keeps its edition tag and claim label (foundation 0018); nothing here is demo-ready until rehearsed (foundation 0017) |

## Demo purpose
Recurring revenue on autopilot with metrics a board trusts: plans, invoicing crons, MRR truth.

## Best personas
CFO, CRO, CEO (metrics), finance director

## Prerequisites
- Enterprise database (pulls Enterprise accounting: state it)
- plans configured
- history for cohorts

## Minimum demo data
- Running subscriptions with months of history
- one upgrade case
- one dunning/failed-payment case
- MRR dashboard populated

## Recommended flow
- Quote with plan
- activation
- the invoicing engine's work shown
- mid-term upgrade with its MRR log
- churn-save beat
- cohort view

## Wow moments
- The MRR movement log (every expansion/contraction accounted)
- cohort retention view
- dunning path shown honestly

## Common mistakes
- Metric definitions assumed (workshop needed, say it)
- proration specifics promised blind
- edition dependency unstated

## Standard vs custom notes
- Plans, closing reasons: configuration
- usage-based billing: validate scope, often custom/integration
- rev-rec: finance design

## Community vs Enterprise notes
Enterprise-only and depends on Enterprise accounting: the double edition implication is part of the pitch honesty

## Likely objections
- Usage billing (scope validation first)
- our churn definition (definitions workshop as the real deliverable)

## Validation checklist
- Billing models incl. edge cases in sandbox
- payment provider token support
- migration of running contracts rehearsed

## Backup flow
Cron results pre-generated; upgrade case staged twice
