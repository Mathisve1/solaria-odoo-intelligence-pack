# Views & Navigation Summary — `hr_recruitment` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `hr_recruitment` — Recruitment |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Kanban by recruitment stage per job position is the pipeline view; activities and interviewer widgets support process discipline.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Recruitment | — | hr_recruitment.group_hr_recruitment_user,hr_recruitment.group_hr_recruitment_interviewer |
| Recruitment / Applications | — | — |
| Recruitment / Applications / All Applications | crm_case_categ0_act_job | — |
| Recruitment / Applications / By Job Positions | action_hr_job | hr_recruitment.group_hr_recruitment_user |
| Recruitment / Applications / By Job Positions | action_hr_job_interviewer | hr_recruitment.group_hr_recruitment_interviewer |
| Recruitment / Applications / By Talent Pools | action_hr_talent_pool | hr_recruitment.group_hr_recruitment_user |
| Recruitment / Configuration | — | group_hr_recruitment_user |
| Recruitment / Configuration / Activities | — | — |
| Recruitment / Configuration / Activities / Activity Plans | mail_activity_plan_action_config_hr_applicant | hr_recruitment.group_hr_recruitment_manager |
| Recruitment / Configuration / Activities / hr_recruitment_menu_config_activity_type | mail_activity_type_action_config_hr_applicant | — |
| Recruitment / Configuration / Applications | — | — |
| Recruitment / Configuration / Applications / Degrees | hr_recruitment_degree_action | — |
| Recruitment / Configuration / Applications / hr_applicant_category_menu | hr_applicant_category_action | — |
| Recruitment / Configuration / Applications / menu_hr_applicant_refuse_reason | hr_applicant_refuse_reason_action | — |
| Recruitment / Configuration / Employees | — | — |
| Recruitment / Configuration / Employees / Departments | action_hr_department | — |
| Recruitment / Configuration / Job Boards | — | — |
| Recruitment / Configuration / Job Boards / Emails | action_hr_job_platforms | — |
| Recruitment / Configuration / Job Positions | — | — |
| Recruitment / Configuration / Job Positions / Stages | hr_recruitment_stage_act | base.group_no_one |
| Recruitment / Configuration / Job Positions / menu_hr_recruitment_contract_type | hr_contract_type_action | hr.group_hr_user |
| Recruitment / Configuration / Settings | action_hr_recruitment_configuration | base.group_system |
| Recruitment / Configuration / UTMs | — | base.group_no_one |
| Recruitment / Configuration / UTMs / Mediums | utm_medium_action | base.group_no_one |
| Recruitment / Configuration / UTMs / Sources | utm_source_action | base.group_no_one |
| Recruitment / Reporting | — | group_hr_recruitment_user |
| Recruitment / Reporting / Recruitment Analysis | hr_applicant_action_analysis | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Tags | hr.applicant.category | — |
| Refuse Reasons | hr.applicant.refuse.reason | list,form |
| Applications | hr.applicant | kanban,list,form,graph,calendar,pivot,activity |
| Talents | hr.applicant | list,kanban,form,graph,calendar,pivot,activity |
| action_hr_applicant_new | hr.applicant | form |
| Applications | hr.applicant | kanban,list,form,pivot,graph,calendar,activity |
| New Applications | hr.applicant | list,kanban,form,graph,calendar,pivot |
| Recruitment Analysis | hr.applicant | graph,pivot |
| Recruitment Analysis | hr.applicant | graph,pivot |
| Recruitment Analysis | hr.applicant | graph,pivot |
| Add/Remove Followers | mail.followers.edit | form |
| Departments | hr.department | list,form |
| New Application | hr.applicant | form |
| Create a Job Position | hr.job | form |
| Job Positions | hr.job | list,kanban,form |
| Job Positions | hr.job | kanban,list,form |
| Job Positions | hr.job | kanban,form |
| Emails | hr.job.platform | list,form |
| Degrees | hr.recruitment.degree | — |
| Trackers | hr.recruitment.source | list |
| Recruitment / Applicants Stages | hr.recruitment.stage | — |
| Stages | hr.recruitment.stage | list,kanban,form |
| Talent Pool | hr.talent.pool | kanban,list,form |
| Recruitment Plans | mail.activity.plan | list,kanban,form |
| Activity Types | mail.activity.type | list,kanban,form |
| Settings | res.config.settings | form |
| Refuse Reason | applicant.get.refuse.reason | form |

## View inventory

- Primary views defined: 36 (form: 13, list: 10, kanban: 4, search: 3, pivot: 2, graph: 2, calendar: 1, activity: 1)
- Inheriting views (UI extensions of other modules): 10
- Richest UI objects: `hr.applicant` (activity, calendar, form, graph, kanban, list, pivot, search); `hr.recruitment.stage` (form, kanban, list); `hr.talent.pool` (form, kanban, list); `hr.applicant.category` (form, list); `hr.applicant.refuse.reason` (form, list); `hr.job` (form, kanban); `hr.job.platform` (form, list); `hr.recruitment.degree` (form, list); `hr.recruitment.source` (list, search); `ir.attachment` (list); `applicant.get.refuse.reason` (form); `applicant.send.mail` (form)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
