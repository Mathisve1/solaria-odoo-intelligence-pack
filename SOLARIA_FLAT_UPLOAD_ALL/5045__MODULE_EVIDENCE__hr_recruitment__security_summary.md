# Security & Access Summary — `hr_recruitment` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `hr_recruitment` — Recruitment |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Interviewers get restricted applicant access (assigned positions); recruiters/officers manage the pipeline — good default separation, validate against hiring committee practice.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| Interviewer | group_hr_recruitment_interviewer | group_user |
| Officer: Manage all applicants | group_hr_recruitment_user | — |
| Administrator | group_hr_recruitment_manager | — |
| Display CV on application form | group_applicant_cv_display | — |

## Existing groups this module modifies

These records extend groups owned by other modules (typically adding implied rights) — they do not create new roles:

| Existing group (reference) | Rights/groups implied by this module |
|---|---|
| base.group_user | group_applicant_cv_display |

## Access rights (ir.model.access) — 31 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_hr_recruitment_user | `base.res_partner`, `calendar.calendar_event`, `hr_applicant`, `hr_applicant_category`, `hr_applicant_refuse_reason`, `hr_job` +5 more | `applicant_get_refuse_reason`, `applicant_send_mail`, `calendar.calendar_event_type` | `hr_recruitment_stage` |
| group_hr_recruitment_interviewer | — | `applicant_get_refuse_reason`, `applicant_send_mail`, `hr_applicant`, `job_add_applicants`, `talent_pool_add_applicants` | `hr.hr_job`, `hr_applicant_refuse_reason`, `hr_recruitment_stage`, `hr_talent_pool` |
| group_hr_recruitment_manager | `hr_job_platform`, `hr_recruitment_stage`, `mail.mail_activity_plan`, `mail.mail_activity_plan_template` | — | — |
| group_user | — | `hr_applicant_category` | `hr_recruitment_source` |
| group_hr_user | — | — | `hr_job` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Applicant multi company rule | hr.applicant | `[('company_id', 'in', company_ids + [False])]` |
| Applicant Interviewer | hr.applicant | `[ '|', ('job_id.interviewer_ids', 'in', user.id), ('interviewer_ids', 'in', user.id), ]` |
| User: All Applicants | hr.applicant | `[(1, '=', 1)]` |
| User: All Applicants | hr.job | `[(1, '=', 1)]` |
| User: All Talent Pools | hr.talent.pool | `[(1, '=', 1)]` |
| User: All Chatter | mail.message | `[(1, '=', 1)]` |
| Manager can manage applicant plans | mail.activity.plan | `[('res_model', '=', 'hr.applicant')]` |
| Manager can manage applicant plan templates | mail.activity.plan.template | `[('plan_id.res_model', '=', 'hr.applicant')]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
