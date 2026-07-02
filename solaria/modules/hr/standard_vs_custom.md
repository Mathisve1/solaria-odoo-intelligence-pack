# Employees (`hr`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: `hr` core is Community; payroll/appraisal/referral/salary-configurator/documents are Enterprise. Payroll additionally needs a country module (`l10n_xx_hr_payroll`, Enterprise) — verify per country in the catalog.

## Likely standard (Community)
Employee master with public/private split · departments, jobs, locations, schedules · employment data versions with history (19.0 `hr.version`) · departure workflow with reasons · onboarding/offboarding activity plans · directory & org views · multi-company employees · bank accounts incl. allocation structures.

## Configuration possibilities
Org taxonomy, schedules/calendars, contract types, activity plans, tags, departure reasons, self-service scope via groups, approval settings in sibling apps (time off, expenses).

## Studio possibilities (E)
Additional HR attributes (equipment sizes, badges, custom IDs) — every field added is a privacy decision; require HR/legal sign-off in the governance flow.

## Automation possibilities
Expiry alerts (permits, certifications), probation reminders, completeness nudges, scheduled exports to payroll bureau (with integration), anniversary triggers.

## Custom development is justified when
- Country statutory HR data/processes lack localization coverage (verify catalog; consider local partner modules).
- Bidirectional integration adapters (HCM master, time clocks) with mapping logic.
- Regulated industry records (medical checks regimes) beyond fields — with compliance design.

## External integration is justified when
- Payroll stays at a bureau (most common pattern): export interfaces, summary journal import.
- Corporate HCM is the group master: Odoo consumes core data, owns operational flows.
- Physical time clocks/access systems feed attendance.
- Identity: SSO/SCIM provisioning tied to employee lifecycle.

## What to avoid
- Storing sensitive data in free-text/Studio fields without classification (GDPR exposure).
- Custom contract models next to `hr.version` — use the shipped versioning.
- Building payroll "just the simple part" custom — payroll is never simple; bureau or E+localization.
- Employee↔user drift (no process owner) — the quiet root cause of HR security incidents.

## Deloitte recommendation principles
Treat HR as a privacy-first master-data project: classification, access design, retention — then features. Decide the payroll boundary early with country evidence. Prefer sibling standard apps (time off, expenses, appraisal E) over custom HR workflows.

## Validation questions
1. Which countries and which payroll boundary (E module exists? bureau mandated?)
2. Which employee fields are needed, and what's their privacy class?
3. What does self-service need to allow — verified against a live test login?
4. Works council/consultation requirements affecting rollout order?
