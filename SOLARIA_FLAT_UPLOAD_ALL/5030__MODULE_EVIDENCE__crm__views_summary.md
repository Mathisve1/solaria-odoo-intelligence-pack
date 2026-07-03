# Views & Navigation Summary — `crm` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `crm` — CRM |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- The 'My Pipeline' kanban (stage_id) is the demo centerpiece; forecast and pivot views carry the manager story.
- Lead menu only appears when the 'Show Lead Menu' group/setting is active — a configuration, not a build.
- Reporting menus (Pipeline Analysis, Activities) are pivot/graph on live data — no BI tool needed for team-level insight.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| CRM | — | sales_team.group_sale_salesman,sales_team.group_sale_manager |
| CRM / Configuration | action_your_pipeline | sales_team.group_sale_manager |
| CRM / Configuration / Activities | — | — |
| CRM / Configuration / Activities / Activity Plans | mail_activity_plan_action_lead | sales_team.group_sale_manager |
| CRM / Configuration / Activities / Activity Types | mail_activity_type_action_config_sales | — |
| CRM / Configuration / Opportunities | — | sales_team.group_sale_manager |
| CRM / Configuration / Pipeline | — | sales_team.group_sale_manager |
| CRM / Configuration / Pipeline / Lost Reasons | crm_lost_reason_action | — |
| CRM / Configuration / Pipeline / Stages | crm_stage_action | base.group_no_one |
| CRM / Configuration / Pipeline / Tags | sales_team_crm_tag_action | — |
| CRM / Configuration / Recurring Plans | crm_recurring_plan_action | crm.group_use_recurring_revenues |
| CRM / Configuration / Sales Teams | crm_team_action_config | — |
| CRM / Configuration / Settings | crm_config_settings_action | base.group_system |
| CRM / Configuration / Teams Members | crm_team_member_action | base.group_no_one |
| CRM / Import & Synchronize | — | — |
| CRM / Leads | crm_lead_all_leads | crm.group_use_lead |
| CRM / Reporting | — | sales_team.group_sale_salesman |
| CRM / Reporting / Activities | crm_activity_report_action | — |
| CRM / Reporting / Forecast | action_opportunity_forecast | — |
| CRM / Reporting / Leads | crm_opportunity_report_action_lead | — |
| CRM / Reporting / Pipeline | crm_opportunity_report_action | — |
| CRM / Sales | — | — |
| CRM / Sales / Customers | action_partner_form | — |
| CRM / Sales / My Activities | crm_lead_action_my_activities | sales_team.group_sale_salesman |
| CRM / Sales / My Pipeline | action_your_pipeline | — |
| CRM / Sales / Teams | crm_team_action_pipeline | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Activities | crm.activity.report | graph,pivot,list |
| Pipeline Activities | crm.activity.report | graph,pivot,list |
| Pipeline Analysis | crm.lead | graph,pivot,list,form |
| Leads Analysis | crm.lead | graph,pivot,list |
| Meetings | calendar.event | list,form,calendar |
| Send email | mail.compose.message | form |
| Send email | mail.compose.message | form |
| Leads | crm.lead | list,kanban,graph,pivot,calendar,form,activity |
| My Activities | crm.lead | list,kanban,graph,pivot,calendar,form,activity |
| Opportunities | crm.lead | kanban,list,graph,pivot,form,calendar,activity |
| Pipeline | crm.lead | kanban,list,graph,pivot,form,calendar,activity |
| Forecast | crm.lead | kanban,graph,pivot,list,form |
| New Lead | crm.lead | form |
| Add/Remove Followers | mail.followers.edit | form |
| Lost Reasons | crm.lost.reason | list,form |
| Recurring Plans | crm.recurring.plan | list |
| Stages | crm.stage | — |
| sales_team.crm_team_member_action | — | — |
| Leads | crm.lead | list,kanban,form |
| Opportunities | crm.lead | kanban,list,graph,form,calendar,pivot |
| Overdue Opportunities | crm.lead | kanban,list,graph,form,calendar,pivot |
| Leads Analysis | crm.lead | graph,pivot,list,form |
| Pipeline Analysis | crm.lead | graph,pivot,list,form |
| New Opportunity | crm.lead | form |
| sales_team.crm_team_action_pipeline | — | — |
| Lead Activity Plans | mail.activity.plan | list,kanban,form |
| sales_team.mail_activity_type_action_config_sales | — | — |
| Settings | res.config.settings | form |
| Mark Lost | crm.lead.lost | form |
| Update Probabilities | crm.lead.pls.update | form |
| Convert to opportunities | crm.lead2opportunity.partner.mass | form |
| Convert to opportunity | crm.lead2opportunity.partner | form |
| Merge | crm.merge.opportunity | form |

## View inventory

- Primary views defined: 36 (form: 9, search: 7, list: 6, graph: 5, pivot: 5, kanban: 2, calendar: 1, activity: 1)
- Inheriting views (UI extensions of other modules): 19
- Richest UI objects: `crm.lead` (activity, calendar, form, graph, kanban, list, pivot, search); `crm.activity.report` (graph, list, pivot, search); `crm.lost.reason` (form, list, search); `crm.stage` (form, list, search); `crm.recurring.plan` (list, search); `crm.lead.lost` (form); `crm.lead.pls.update` (form); `crm.lead2opportunity.partner.mass` (form); `crm.lead2opportunity.partner` (form); `crm.merge.opportunity` (form)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
