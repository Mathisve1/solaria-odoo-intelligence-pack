# Security & Access Summary — `crm` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `crm` — CRM |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Salesperson vs 'All Documents' salesperson vs Manager is the practical role split; personal-leads record rule enforces my-pipeline-only visibility.
- Multi-company rule on leads matters for group rollouts — test cross-company lead visibility early.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| Show Lead Menu | group_use_lead | — |
| Show Recurring Revenues Menu | group_use_recurring_revenues | — |

## Access rights (ir.model.access) — 32 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_sale_salesman | — | `base.res_partner`, `base.res_partner_category`, `calendar.calendar_event`, `crm_lead`, `crm_lead2opportunity_partner`, `crm_lead2opportunity_partner_mass` +2 more | `calendar.calendar_event_type`, `crm_activity_report`, `crm_lead_scoring_frequency`, `crm_lead_scoring_frequency_field`, `crm_lost_reason`, `crm_recurring_plan` |
| group_sale_manager | `calendar.calendar_event`, `crm_lead`, `crm_lost_reason`, `crm_recurring_plan`, `crm_stage`, `mail.mail_activity_plan` +2 more | `calendar.calendar_event_type` | `base.res_partner`, `base.res_partner_category` |
| group_user | — | `crm_activity_report` | `calendar.calendar_event_type`, `crm_lost_reason`, `crm_stage` |
| group_system | — | — | `crm_lead_scoring_frequency`, `crm_lead_scoring_frequency_field` |
| group_erp_manager | `crm_lead_pls_update` | — | — |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Personal Leads | crm.lead | `['|',('user_id','=',user.id),('user_id','=',False)]` |
| CRM Lead Multi-Company | crm.lead | `[('company_id', 'in', company_ids + [False])]` |
| All Leads | crm.lead | `[(1,'=',1)]` |
| All Activities | crm.activity.report | `[(1,'=',1)]` |
| Personal Activities | crm.activity.report | `['|',('user_id','=',user.id),('user_id','=',False)]` |
| CRM Lead Multi-Company | crm.activity.report | `[('company_id', 'in', company_ids + [False])]` |
| Manager can manage lead plans | mail.activity.plan | `[('res_model', '=', 'crm.lead')]` |
| Manager can manage lead plan templates | mail.activity.plan.template | `[('plan_id.res_model', '=', 'crm.lead')]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
