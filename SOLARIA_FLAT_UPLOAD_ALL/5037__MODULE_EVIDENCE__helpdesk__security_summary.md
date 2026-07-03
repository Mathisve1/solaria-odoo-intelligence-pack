# Security & Access Summary — `helpdesk` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `helpdesk` — Helpdesk |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Team member vs manager (rwcd on config); 'personal tickets' style rules keep agents on their own queue — team-based visibility is the design lever.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| User | group_helpdesk_user | group_user |
| Administrator | group_helpdesk_manager | group_mail_canned_response_admin |
| Show SLA Policies | group_use_sla | — |
| Show Customer Ratings | group_use_rating | — |
| Auto Assigment | group_auto_assignment | — |

## Existing groups this module modifies

These records extend groups owned by other modules (typically adding implied rights) — they do not create new roles:

| Existing group (reference) | Rights/groups implied by this module |
|---|---|
| base.default_user_group | group_helpdesk_manager |

## Access rights (ir.model.access) — 22 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_helpdesk_manager | `helpdesk.helpdesk_tag_assignment`, `helpdesk_sla`, `helpdesk_stage`, `helpdesk_team`, `mail.mail_activity_type` | `helpdesk_stage_delete_wizard` | `helpdesk_sla_report_analysis`, `helpdesk_ticket_report_analysis` |
| group_user | — | — | `helpdesk_sla`, `helpdesk_sla_status`, `helpdesk_stage`, `helpdesk_tag`, `helpdesk_team`, `helpdesk_ticket` |
| group_helpdesk_user | `helpdesk_tag`, `helpdesk_ticket` | — | `helpdesk_sla_report_analysis`, `helpdesk_ticket_report_analysis` |
| group_portal | — | — | `helpdesk.helpdesk_stage`, `helpdesk.helpdesk_ticket`, `helpdesk_team` |
| group_public | — | — | `helpdesk_team` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Helpdesk Administrator | helpdesk.team | `[(1,'=',1)]` |
| Helpdesk Ticket Administrator | helpdesk.ticket | `[(1,'=',1)]` |
| Helpdesk User | helpdesk.team | `['|', ('privacy_visibility', '!=', 'invited_internal'), ('message_partner_ids', 'in', [use` |
| Helpdesk Ticket User | helpdesk.ticket | `['|', '|', ('team_id.privacy_visibility', '!=', 'invited_internal'), ('team_id.message_par` |
| Ticket: multi-company | helpdesk.ticket | `[('company_id', 'in', company_ids + [False])]` |
| Team: multi-company | helpdesk.team | `[('company_id', 'in', company_ids)]` |
| SLA: multi-company | helpdesk.sla | `[('company_id', 'in', company_ids)]` |
| Tickets: portal users: following | helpdesk.ticket | `[ ('team_privacy_visibility', '=', 'portal'), '|', ('message_partner_ids', 'in', [user.par` |
| Helpdesk SLA Report: multi-company | helpdesk.sla.report.analysis | `[('company_id', 'in', company_ids + [False])]` |
| Helpdesk SLA Report: Helpdesk Ticket User | helpdesk.sla.report.analysis | `[ '|', ('team_id.privacy_visibility', '!=', 'invited_internal'), '|', ('team_id.message_pa` |
| Helpdesk Ticket Report: multi-company | helpdesk.ticket.report.analysis | `[('company_id', 'in', company_ids + [False])]` |
| Helpdesk Ticket Report: Helpdesk Ticket User | helpdesk.ticket.report.analysis | `[ '|', ('team_id.privacy_visibility', '!=', 'invited_internal'), '|', ('team_id.message_pa` |
| Helpdesk Ticket Report: Helpdesk Ticket Administrator | helpdesk.ticket.report.analysis | `[(1,'=',1)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
