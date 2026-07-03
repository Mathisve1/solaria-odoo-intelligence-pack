# Recruitment (`hr_recruitment`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: pipeline is Community; CV OCR, AI assist, referrals, salary configurator, job boards are Enterprise.

## Likely standard (Community)
Job positions + careers site applications · staged applicant pipeline with per-stage emails · interviewer restricted role · refuse reasons with templates · talent pools (19.0) · UTM source analytics · calendar/activity interview management · employee creation on hire.

## Configuration possibilities
Stages, stage templates, refuse reasons, degrees/tags, sources/mediums, job aliases, activity plans for interview loops, CV-on-form display group.

## Studio possibilities (E)
Scorecard/assessment fields (privacy-classified), requisition metadata. Avoid candidate-evaluation logic in Studio — evaluation criteria belong in a governed process.

## Automation possibilities
Auto-acknowledgements, stage-idle alerts, interview reminder chains, GDPR anonymization schedules, hiring-manager digest.

## Custom development is justified when
- Assessment/e-testing platform integrations with result mapping.
- High-volume custom application funnels (multi-step, branded) beyond website forms.
- Agency/VMS collaboration portals.

## External integration is justified when
- Background checks, assessment science platforms, corporate ATS coexistence, additional job boards.

## What to avoid
- Auto-rejection logic (AI or rules) without human review — legal exposure (EU AI Act high-risk domain) and brand damage.
- Storing evaluations in free text on the applicant without access design.
- Custom "requisition approval" modules before assessing Approvals (E) + activities.

## Deloitte recommendation principles
Lead with governance on anything AI-assisted (criteria documentation, human decision, candidate transparency). Keep candidate experience artifacts (emails, careers page) brand-reviewed. Use talent pools instead of "keep CV in a drawer" habits — with retention automation.

## Validation questions
1. Volumes/channels: which boards and sources actually matter (evidence from current funnel)?
2. Which steps legally require documentation in the client's jurisdictions?
3. Retention policy: how long, then what (anonymize/delete) — automated how?
4. If AI/OCR: which languages/CV formats — tested on a real sample?
