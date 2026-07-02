# Employees (`hr`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `hr` |
| Display name | Employees |
| Source origin | **Community** (Enterprise adds payroll, appraisal, referral, salary configurator, documents/planning bridges) |
| Version scope | Odoo 19.0 |
| Dependencies | `base_setup`, `mail`, `resource` ecosystem |
| Functional domain | HR (employee master) |
| Confidence | High for structures; version/contract handling specifics need live validation |

## Business purpose
The employee system of record: people, departments, jobs, work locations, working schedules and employment data versions — the hub that time off, attendance, expenses, payroll (E), recruitment and planning all plug into.

## Main users / personas
HR officers/administrators, managers (team data), employees (self-service via linked user), IT (user↔employee linkage), payroll (E).

## Business problems solved
- Fragmented employee data → single master with public/private layering (`hr.employee` vs `hr.employee.public` — privacy by design in the data model).
- Contract/employment-change history → **`hr.version`** (19.0 models employment data as versions; contract-type via `hr.payroll.structure.type` structures — the payroll bridge is pre-wired even in Community).
- Org opacity → departments, jobs, manager chains, org-chart UX.
- Onboarding/offboarding chaos → activity plans + departure wizard (`hr.departure.wizard`, reasons taxonomy).

## Main business processes (source-verified)
1. Hire/onboard: employee record (often from recruitment), user link, activity plans ("Onboarding/Offboarding" menu exists).
2. Employment changes: versioned data (`hr.version`, `hr.version.wizard`) — department/job/schedule/salary-structure changes with history.
3. Departure: wizard with reasons, archiving, downstream cleanup (planning wizard extension confirms cross-app choreography).
4. Directory & reporting: public directory, manager/department reporting.

## Key functional capabilities
Work locations, working schedules (resource calendars), employee categories/tags, contract types, bank accounts with allocation wizard (19.0 — multiple accounts/salary split structures), skills via `hr_skills` (sibling), badges/appraisal/payroll as E siblings.

## Fit with other modules
Everything HR: `hr_holidays`, `hr_attendance`, `hr_expense`, `hr_recruitment`, `hr_skills` (all Community); `hr_payroll`, `hr_appraisal`, `hr_contract_salary`, `planning`, `documents_hr`, `frontdesk` (Enterprise). Also `project`/`planning` resources, `fleet`, and user security (employee↔user linkage).

## Standard in 19.0 (Community)
Employee master with versions, org structure, schedules, departure flows, directory, activity plans, public/private data split, multi-company employees.

## Enterprise-specific
Payroll (+country `l10n_*_hr_payroll` — all Enterprise), appraisals, referrals, salary package configurator with e-sign, HR documents workspace, front desk, HR Gantt views.

## Configuration opportunities
Departments/jobs taxonomy, work locations, schedules, contract types, departure reasons, activity plans (on/off-boarding), employee tags, approval chains in sibling apps.

## Studio / automation opportunities
Automation: probation-end reminders, document-expiry alerts (ID/permit dates), birthday/anniversary niceties, data-completeness nudges. Studio (E): extra HR fields (locker no., PPE size) — mind privacy classification for every added field.

## Custom development triggers
Country HR-legal specifics without localization coverage; deep works-council processes; interfaces to niche HR tools when data must flow both ways.

## External integration triggers
Payroll bureaus (when payroll stays external — the most common HR integration), corporate HCM (Workday etc.) as master with Odoo operational, identity systems (SSO/provisioning), time clocks (attendance devices).

## Common client questions
"Can employees self-serve their data?" — yes, scoped; validate exact editable fields live. · "Contract history?" — versions (19.0 model); demo it. · "Payroll?" — Enterprise + country module check, or bureau integration. · "GDPR?" — public/private split + access design + retention policy (project work).

## Fit-gap considerations
Solid HRIS core for mid-market. Gaps cluster in country-legal depth (payroll/works councils), talent suites (learning/succession — partial via skills/appraisal E), and hardware time-capture (integration). The master-data role means every HR gap discussion starts here but often lands in a sibling module.

## Deloitte demo angles
1. **One person, one record:** employee card → user access → time off & expenses tabs appearing (installed siblings) — the hub effect.
2. **Change with history:** version wizard changing department/schedule — auditability story.
3. **Lifecycle:** onboarding activity plan firing on hire; departure wizard on exit.

## Implementation watch-outs
- Privacy/works council involvement before data model decisions (which fields, who sees).
- Employee↔user lifecycle (joiners/leavers) needs an owner and a process.
- Version data migration from legacy contracts — define the historical depth pragmatically.
- Multi-company HR sharing rules — test manager visibility across entities.

## Risks and assumptions
Structures verified (incl. 19.0 version/bank-allocation models). Self-service field scope, version wizard behavior and public-profile contents are runtime → validate. Payroll conversations always require the E + country check.

## Validation checklist
- [ ] Data privacy classification of employee fields agreed with HR/legal
- [ ] Version/contract migration depth decided
- [ ] Payroll boundary decided (E module vs bureau) with country evidence
- [ ] Self-service scope tested with a real employee login
- [ ] Joiner/mover/leaver process owners named
