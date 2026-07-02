# Views & Navigation Summary — `helpdesk` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `helpdesk` — Helpdesk |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Team-based kanban with SLA indicators is the core screen; per-team settings pages reveal how much is configurable.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| All Tickets | helpdesk_ticket_action_main_tree | — |
| Configuration | — | helpdesk.group_helpdesk_manager |
| Customer Ratings | rating_rating_action_helpdesk | helpdesk.group_use_rating |
| Helpdesk | — | helpdesk.group_helpdesk_user |
| Helpdesk Teams | helpdesk_team_action | helpdesk.group_helpdesk_manager |
| My Tickets | helpdesk_ticket_action_main_my | — |
| Overview | helpdesk_team_dashboard_action_main | helpdesk.group_helpdesk_user |
| Reporting | — | — |
| SLA Status Analysis | helpdesk_sla_report_analysis_action | group_use_sla |
| Tickets | — | — |
| Tickets Analysis | helpdesk_ticket_analysis_action | — |
| helpdesk_menu_config_activity_type | mail_activity_type_action_config_helpdesk | base.group_no_one |
| helpdesk_sla_menu_main | helpdesk_sla_action_main | helpdesk.group_use_sla |
| helpdesk_stage_menu | helpdesk_stage_action | base.group_no_one |
| helpdesk_tag_menu | helpdesk_tag_action | base.group_no_one |
| helpdesk_team_canned_response_menu | mail_canned_response_action | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| SLA Status Analysis | helpdesk.sla.report.analysis | pivot,graph,cohort |
| SLA Status Analysis | helpdesk.sla.report.analysis | pivot,graph,cohort |
| Tickets Analysis | helpdesk.ticket.report.analysis | pivot,graph |
| Ticket Analysis | helpdesk.ticket.report.analysis | pivot,graph,cohort |
| Success Rate Analysis | helpdesk.ticket.report.analysis | pivot,graph |
| Ticket Analysis | helpdesk.ticket.report.analysis | pivot,graph,cohort |
| SLA Policies | helpdesk.sla | list,form,kanban |
| Stages | helpdesk.stage | list,form,kanban |
| Team Stages | helpdesk.stage | list,form,kanban |
| Configure Tags Handled by Team Members | helpdesk.tag.assignment | list |
| Tags | helpdesk.tag | list,form |
| SLA Policies | helpdesk.sla | list,form,kanban |
| Templates | mail.template | list,form |
| Helpdesk Teams | helpdesk.team | list,form,kanban |
| Helpdesk Overview | helpdesk.team | kanban,form |
| Share Ticket | portal.share | form |
| My Tickets | helpdesk.ticket | list,kanban,form,activity,pivot,graph,cohort |
| All Tickets | helpdesk.ticket | list,kanban,form,activity,pivot,graph,cohort |
| Send Email | mail.compose.message | form |
| Tickets | helpdesk.ticket | list,kanban,form,activity,pivot,graph,cohort |
| Tickets | helpdesk.ticket | list,kanban,form,activity,pivot,graph,cohort |
| Closed Tickets Analysis | helpdesk.ticket | list,form,pivot,graph |
| Closed Tickets | helpdesk.ticket | list,kanban,form,activity,pivot,graph,cohort |
| Tickets | helpdesk.ticket | kanban,list,form,activity,pivot,graph,cohort |
| Tickets | helpdesk.ticket | kanban,list,form,activity,pivot,graph,cohort |
| Performance Analysis | helpdesk.ticket | pivot,graph |
| Success Rate Analysis | helpdesk.ticket | list,form,pivot,graph |
| Success Rate | helpdesk.ticket | list,kanban,form,activity,pivot,graph,cohort |
| Add/remove followers | mail.followers.edit | form |
| Activity Types | mail.activity.type | list,kanban,form |
| Customer Ratings | rating.rating | kanban,list,graph,pivot,form |

## View inventory

- Primary views defined: 41 (form: 9, list: 8, search: 7, kanban: 5, pivot: 4, graph: 4, cohort: 3, activity: 1)
- Inheriting views (UI extensions of other modules): 33
- Richest UI objects: `helpdesk.ticket` (activity, cohort, form, graph, kanban, list, pivot, search); `helpdesk.ticket.report.analysis` (cohort, graph, list, pivot); `helpdesk.sla` (form, kanban, list, search); `helpdesk.stage` (form, kanban, list, search); `helpdesk.team` (form, kanban, list, search); `helpdesk.sla.report.analysis` (cohort, graph, pivot); `helpdesk.tag.assignment` (list, search); `helpdesk.tag` (form, list); `helpdesk.stage.delete.wizard` (form)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
