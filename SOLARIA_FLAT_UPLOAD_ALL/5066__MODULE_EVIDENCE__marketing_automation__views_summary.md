# Views & Navigation Summary — `marketing_automation` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `marketing_automation` — Marketing Automation |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- The campaign canvas (activity tree with timing/branches) is the visual differentiator vs plain mass mailing.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Marketing Automation | — | marketing_automation.group_marketing_automation_user |
| Marketing Automation / Campaigns | marketing_campaign_action | — |
| Marketing Automation / Configuration | — | marketing_automation.group_marketing_automation_user |
| Marketing Automation / Configuration / mailing_filter_menu_action_marketing_automaion | mailing_filter_action | marketing_automation.group_marketing_automation_user |
| Marketing Automation / Reporting | — | marketing_automation.group_marketing_automation_user |
| Marketing Automation / Reporting / Link Tracker | link_tracker_action_marketing_campaign | marketing_automation.group_marketing_automation_user |
| Marketing Automation / Reporting / marketing_participants_menu | marketing_participants_action_reporting | marketing_automation.group_marketing_automation_user |
| Marketing Automation / Reporting / marketing_trace_menu | marketing_trace_action | marketing_automation.group_marketing_automation_user |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Link Statistics | link.tracker | graph,pivot,list,form |
| mass_mailing.mailing_mailing_action_mail | — | — |
| Marketing Automation Mailings | mailing.mailing | list,form,graph |
| Marketing Automation Mailings | mailing.mailing | form |
| Campaigns | marketing.campaign | kanban,list,form |
| Participants | marketing.participant | graph,pivot,list,form |
| Participants | marketing.participant | list,form |
| Participants | marketing.participant | list,form |
| Participants | marketing.participant | list,form |
| Traces | marketing.trace | graph,pivot,list,form |
| Launch a test | marketing.campaign.test | form |

## View inventory

- Primary views defined: 17 (form: 5, list: 4, search: 3, graph: 2, pivot: 2, kanban: 1)
- Inheriting views (UI extensions of other modules): 4
- Richest UI objects: `marketing.participant` (form, graph, list, pivot, search); `marketing.trace` (form, graph, list, pivot, search); `marketing.campaign` (form, kanban, list, search); `ir.model` (list); `marketing.activity` (form); `marketing.campaign.test` (form)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
