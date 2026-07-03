# Recruitment (`hr_recruitment`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `hr_recruitment` |
| Display name | Recruitment |
| Source origin | **Community** (Enterprise adds CV OCR `hr_recruitment_extract`, `hr_recruitment_ai`, referrals, salary configurator+sign, job-board integrations, reporting) |
| Version scope | Odoo 19.0 |
| Dependencies | `hr`, `calendar`, `utm`, `attachment_indexation`, `digest` |
| Functional domain | Recruitment / attract-to-hire |
| Confidence | High for structures; AI/OCR behavior must be validated live |

## Business purpose
Run hiring as a pipeline: job positions, applicants per stage, interviewer collaboration, refusal handling with respectful communication, offers, and conversion to employees — plus talent pooling for future roles.

## Main users / personas
Recruiters/HR officers, hiring managers, interviewers (restricted role), candidates (website applications), leadership (time-to-hire reporting).

## Business problems solved
- CV chaos in inboxes → applicants (`hr.applicant`) with attachments, sources (UTM), stages per job.
- Slow screening → (E) CV extraction autofill; (E) recruitment AI; degrees/tags/categories for triage (Community).
- Ghosting/reputation risk → refuse reasons (`hr.applicant.refuse.reason`) with templated emails (`applicant.get.refuse.reason` wizard).
- Losing silver-medal candidates → **talent pools** (`hr.talent.pool`, 19.0) with add-applicants wizards.

## Main business processes (source-verified)
1. Job position published (with `website_hr_recruitment`) → applications flow in (email alias per job, web forms; UTM sources tracked via `hr.recruitment.source`, job platforms model `hr.job.platform`).
2. Pipeline per job: configurable stages (`hr.recruitment.stage`) — kanban like CRM; interviewers with restricted access.
3. Interviews via calendar/activities; assessments via surveys (bridge).
4. Refusal with reason+template, or hire: create employee closes the loop into `hr`.
5. Reporting: recruitment analysis (source effectiveness, funnel).

## Key functional capabilities
Stages with templates per stage, degrees, tags, sources/mediums (UTM), talent pools, mail wizards, "Display CV on application form" group (side-by-side CV view — nice demo moment), multi-company recruitment.

## Fit with other modules
`hr` (employee creation), `website_hr_recruitment` (careers site), `survey` (assessments), `calendar`, `hr_referral` (E), `hr_contract_salary` (E: offer→package→e-sign), `sign` bridge (E), job-board integrations (E family `hr_recruitment_integration_*` — verify boards per market in catalog).

## Standard in 19.0 (Community)
Full pipeline incl. talent pools, sources analytics, refuse-reason flows, interviewer role, careers-site integration.

## Enterprise-specific
CV OCR autofill, recruitment AI assist, referral program, salary package configurator with e-signature, job-board postings, extended reporting.

## Configuration opportunities
Stages+stage emails, refuse reasons+templates, degrees/tags, sources/mediums, aliases per job, interviewer assignments, activity plans (interview loops).

## Studio / automation opportunities
Automation: SLA nudges (applicant idle in stage), auto-acknowledge receipt, interviewer reminder chains. Studio (E): assessment scorecards fields (mind candidate-data privacy), requisition approval fields (or use Approvals E).

## Custom development triggers
Deep assessment/e-testing integrations, high-volume hiring portals with custom UX, agencies/vendor management systems.

## External integration triggers
Assessment platforms, background-check providers, corporate ATS coexistence, job boards beyond E integrations.

## Common client questions
"Can candidates apply online with CV?" — yes (careers site). · "Automatic CV parsing?" — Enterprise OCR; validate quality live per language. · "Approval before opening a position?" — requisition approval isn't a rich native flow: configuration+activities, Approvals (E), or custom — be precise. · "GDPR retention for candidates?" — design decision: archiving/anonymization policy + automation.

## Fit-gap considerations
Great fit for in-house mid-volume recruiting. Gaps: enterprise ATS depth (agency portals, CRM-style talent marketing), assessment science, high-compliance regimes. AI screening (E) triggers EU AI Act high-risk duties — Deloitte should lead with governance, not just features.

## Deloitte demo angles
1. **Candidate-to-colleague:** careers page application → kanban stage moves → interview activity → offer (E: package+sign) → "Create Employee".
2. **Recruiter cockpit:** CV-on-form view, refuse-with-reason email, talent pool save.
3. **Funnel analytics:** source effectiveness pivot — where do good hires come from?

## Implementation watch-outs
- Candidate data retention/GDPR policy implemented, not just documented (automation for anonymization).
- Stage emails tone/branding review before go-live (candidates see them).
- Interviewer access rules tested (they must not browse all applicants).
- AI/OCR (E): human review step mandatory; document criteria for AI-assisted decisions.

## Risks and assumptions
Structures verified (incl. 19.0 talent pools, job platforms). OCR/AI behavior, board integrations coverage and survey depth are runtime/commercial → validate. Employment-law process constraints are jurisdictional — pair with Deloitte HR legal.

## Validation checklist
- [ ] Hiring process mapped to stages with owners and stage emails
- [ ] Retention/anonymization policy configured and tested
- [ ] Interviewer restricted access verified with test user
- [ ] Edition decisions (OCR/AI/referral/salary configurator) with governance notes
- [ ] Job-board coverage for target markets checked in catalog + commercially
