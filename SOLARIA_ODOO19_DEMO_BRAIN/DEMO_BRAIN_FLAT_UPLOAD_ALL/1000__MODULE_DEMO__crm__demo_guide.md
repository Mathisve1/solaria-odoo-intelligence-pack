# Module Demo Pack: CRM (`crm`)

| Attribute | Value |
|---|---|
| Edition | Community |
| Category | MODULE_DEMO (demo guidance only; product truth lives in the Intelligence Pack module docs, routed via foundation 0012) |
| Rule | Every claim keeps its edition tag and claim label (foundation 0018); nothing here is demo-ready until rehearsed (foundation 0017) |

## Demo purpose
Show demand capture and pipeline discipline: from raw lead to qualified opportunity to quotation handoff, in the client's sales vocabulary.

## Best personas
Sales director, CEO (funnel truth), CRM/end users

## Prerequisites
- sale installed for the quote handoff
- client's pipeline stages configured
- email alias or web form wired

## Minimum demo data
- 12+ leads across stages with realistic names
- 2 sales teams if relevant
- activity history on hero opportunity
- one lost opportunity with reason

## Recommended flow
- Email arrives, lead exists
- qualify to opportunity
- kanban drag through stage
- activity scheduled and done
- quotation created from the opportunity

## Wow moments
- Email-to-lead with zero typing
- pipeline analysis pivot built live in 20 seconds
- assignment rule firing (configuration, not code)
- scoring shown as a setting

## Common mistakes
- Demoing empty pipeline
- explaining fields instead of following the deal
- showing admin config mid-story

## Standard vs custom notes
- Stages, scoring, assignment: configuration
- AI lead creation: Enterprise ai_crm, labelled
- exotic scoring engines: custom, never implied standard

## Community vs Enterprise notes
- Core pipeline fully Community
- AI leads, VoIP, journeys are Enterprise extensions, label each

## Likely objections
- Sellers will not use it (show the two-minute deal update)
- our pipeline is special (change a stage live)

## Validation checklist
- Assignment rule expressiveness on the client's routing matrix
- dedup behaviour on their real lead lists
- scoring behaviour live

## Backup flow
Pre-created lead ready if the email gateway hiccups; screenshots of pipeline pivot
