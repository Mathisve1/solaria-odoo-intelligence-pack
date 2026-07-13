# Module Demo Pack: Helpdesk (`helpdesk`)

| Attribute | Value |
|---|---|
| Edition | Enterprise |
| Category | MODULE_DEMO (demo guidance only; product truth lives in the Intelligence Pack module docs, routed via foundation 0012) |
| Rule | Every claim keeps its edition tag and claim label (foundation 0018); nothing here is demo-ready until rehearsed (foundation 0017) |

## Demo purpose
Tickets that can act: SLA-driven service wired into the ERP (returns, credits, interventions).

## Best personas
Customer service manager, COO, CFO (credit control)

## Prerequisites
- Enterprise database
- team with email alias
- SLA policies configured
- stock/account bridges if the wow is shown

## Minimum demo data
- 20 tickets across stages with SLA states
- canned responses
- one ticket staged for the return/credit beat

## Recommended flow
- Email becomes ticket
- SLA clock visible
- agent resolves with canned answer
- escalation beat: create return and credit note from the ticket
- rating request

## Wow moments
- The ERP bridge (return + credit from the ticket: competitors need three systems)
- SLA breach surfacing on the manager view

## Common mistakes
- Demoing it as a standalone ticket tool (the bridge IS the differentiator)
- Community client without the edition gate stated

## Standard vs custom notes
- Teams, SLAs, assignment methods: configuration
- entitlement/contract-based support: design/custom, flagged

## Community vs Enterprise notes
Enterprise-only app: state the gate and the honest Community fallbacks when relevant

## Likely objections
- We have Zendesk (bridge story, honest deeper-tool concessions)
- SLA per tier (policy design shown)

## Validation checklist
- SLA matrix in policies on samples
- volumes per channel
- bridge flows demoed with ops and finance present

## Backup flow
Ticket staged at each stage; bridge beat pre-executed once
