# Odoo Implementation Roadmap Template — Deloitte Playbook

| Attribute | Value |
|---|---|
| Document type | Strategy / Deloitte Advisory Playbook (methodology template) |
| Authority level | High for phasing/governance method; durations are engagement-specific |
| Version scope | Odoo 19.0 context pack |

Use as the skeleton for Odoo programs; scale phases to deal size (SME sprint vs multi-country program). Each phase lists purpose, key activities, deliverables and its decision gate.

## Phase 0 — Discovery & Strategy
- Purpose: understand the business, scope domains, frame the case.
- Activities: executive interviews, process walkthroughs (question-bank playbook), system/landscape inventory, data-quality sampling, edition/hosting orientation (03 map; hosting constraints validated).
- Deliverables: scope memo, domain map, business case draft, program charter.
- **Gate G0:** sponsor + scope + budget envelope confirmed.

## Phase 1 — Fit-Gap & Solution Design
- Activities: requirement workshops per domain, fit-gap register (methodology playbook), demo validations, architecture design (multi-company, integrations, security concept), customization challenge session, edition & licensing decision, data migration strategy.
- Deliverables: fit-gap register, solution design document, customization inventory (target: minimal), integration contract list, migration plan, updated business case.
- **Gate G1:** design sign-off; custom inventory approved item-by-item; edition/licensing contracted.

## Phase 2 — Prototype / Conference-Room Pilot
- Activities: configure priority flows on client master-data sample; demo-driven walkthroughs with process owners; adjust design; validate risky fits (the UNKNOWN-VALIDATE list).
- Deliverables: working prototype DB, validated design deltas, adoption risk notes.
- **Gate G2:** process owners accept the to-be flows on evidence.

## Phase 3 — Build: Configuration first
- Activities: full configuration per design (CoA/taxes, routes, stages, SLAs, templates, security groups), master-data load rehearsals, report/document branding.
- Deliverables: configured system, configuration workbook (the as-built), loaded test data.

## Phase 4 — Build: Customization (only what survived G1)
- Activities: custom modules (inheritance-only, code review, automated tests), Studio artifacts under governance registry, automation rules catalog.
- Deliverables: custom code + tests + docs, Studio/automation registry, upgrade impact notes per item.
- **Gate G3:** build complete; every custom item tested + registered.

## Phase 5 — Integrations
- Activities: interface builds per contract (system-of-record per object, idempotency, monitoring), connector configuration (payment, carriers, e-invoicing per catalog evidence), end-to-end tests.
- Deliverables: live interfaces in test, interface runbook, monitoring plan.

## Phase 6 — Data Migration
- Activities: cleansing (gate: partners/products dedup done), mapping, mock loads (≥2), reconciliation procedures (open items, stock with lots, contracts), sign-off criteria.
- Deliverables: migration runbook, mock-load reconciliation reports.
- **Gate G4:** mock migration reconciles within agreed tolerances.

## Phase 7 — Security & Roles
- Activities: role design mapped to shipped groups (module security summaries as baseline), record-rule design (multi-company!), SoD review, portal exposure review, admin governance.
- Deliverables: authorization concept, tested role matrix, admin/change-control policy.

## Phase 8 — Testing
- Activities: SIT (flows across modules), UAT scripted from real scenarios, migration+integration dress rehearsal, performance sanity, regression list for future upgrades.
- Deliverables: test evidence, defect log burn-down, UAT sign-off.
- **Gate G5:** UAT signed; cutover approved.

## Phase 9 — Training & Change
- Activities: role-based training (train-the-trainer where scale demands), day-one job aids, comms plan, floor-walker plan for go-live week.
- Deliverables: training materials tied to configured system (not generic), readiness assessment.

## Phase 10 — Go-Live (Cutover)
- Activities: cutover runbook execution (freeze, final loads, reconciliation, smoke tests, go/no-go), hypercare staffing.
- **Gate G6:** go/no-go with sponsor on reconciliation evidence.

## Phase 11 — Hypercare (2–6 weeks)
- Activities: on-site/remote support, defect triage SLA, adoption monitoring (login/timesheet/queue KPIs), quick-win configuration adjustments.
- Deliverables: stabilization report, handover to run organization.

## Phase 12 — Continuous Improvement & Governance
- Activities: phase-2 backlog (the parked customizations — most will be re-challenged), quarterly value reviews, **Odoo upgrade policy** (annual major releases: test custom inventory, plan windows), AI-in-ERP roadmap activation (see AI strategy playbook), knowledge pack refresh.
- Standing governance: change advisory (config vs custom decisions), customization registry review, license/user review, security recertification.

## Cross-cutting rules
- Nothing enters Build without a fit-gap verdict; nothing custom without G1 approval.
- Every phase ends with a named gate and evidence, not a date.
- The configuration workbook and customization registry are living deliverables — they ARE the upgrade insurance.
