# Industry Demo Pack: Technology and SaaS

| Attribute | Value |
|---|---|
| Category | INDUSTRY (defaults to confirm; never a substitute for client intake) |
| Product truth | All module claims route via the Intelligence Pack (foundation 0012); editions labelled; statutory items always validation |

## Operating model
Recurring revenue engines: subscriptions, usage tiers, land-and-expand sales; margin lives in churn, CAC payback and billing accuracy.

## Common pain points
- Billing spreadsheet fragility
- MRR/churn defined differently per meeting
- Revenue recognition effort
- CRM-to-billing handoff
- Renewal blindness

## Common process flows
- Lead-to-subscription
- Recurring billing cycles
- Upgrades, downgrades, renewals
- Dunning on failed payments
- Rev-rec and MRR reporting

## Relevant Odoo modules
- crm, sale (Community)
- sale_subscription with plans, MRR logs, cohorts (Enterprise, and it pulls Enterprise accounting: state the dependency implication)
- payment tokenisation per provider

## Relevant KPIs
MRR movements, churn (defined!), net revenue retention, CAC payback, billing error rate, DSO

## Suitable demo storyline
Subscription-to-Renewal spine: quote with plan, activation, the invoicing cron doing its round, an upgrade mid-term, a churn save beat, MRR cohort view for the board (storyline 2100)

## Persona emphasis
CFO and finance director heavily, CRO as sales director pattern, CEO for the metrics story

## Challenger insights
- MRR without agreed definitions is a fight, not a metric: the definitions workshop is the real deliverable
- Renewal is a process with a date, not an account manager's memory

## Likely objections
- Usage-based billing? (validate scope live; often custom/integration; never promised blind)
- Proration specifics? (sandbox validation)
- Our metric definitions? (workshop, then configure)

## Data required for demo
Two plans, running subscriptions with history for cohorts, one upgrade case, one failed-payment dunning case, MRR dashboard populated

## Localisation and validation concerns
- Revenue recognition rules (finance validation)
- PSP token support per market (validation)

## What not to overclaim
- Metered/usage billing beyond validated scope
- Automatic rev-rec compliance
- Churn prediction (concept, not product)
