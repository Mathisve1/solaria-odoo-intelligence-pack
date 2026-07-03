# Workflow & Automation Summary — `hr_recruitment` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `hr_recruitment` — Recruitment |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Applicant pipeline: New -> Qualification -> Interview stages -> Contract Proposal -> Hired (stages configurable per job).
- Refuse reasons + templated emails formalize decline flows; 'create employee' closes the loop into HR.
- Interview scheduling leans on activities/calendar; assessments via surveys — configuration first.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| hr.applicant | kanban_state | normal → done → waiting → blocked |
| hr.applicant | application_status | ongoing → hired → refused → archived |
| hr.applicant | stage_id | configurable stages via `hr.recruitment.stage` |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Send Email | hr.applicant | code |
| Load demo data | hr.job | code |

## Mail templates shipped: 4

*Recruitment: Refuse*, *Recruitment: Interest*, *Recruitment: Application Acknowledgement*, *Recruitment: Not interested anymore*

## Integration surface
- Direct dependencies: `hr`, `calendar`, `utm`, `attachment_indexation`, `web_tour`, `digest`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
