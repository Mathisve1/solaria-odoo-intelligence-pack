# Planning (`planning`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `planning` |
| Display name | Planning |
| Source origin | **Enterprise** |
| Version scope | Odoo 19.0 |
| Dependencies | `hr`, `hr_hourly_cost`, `web_gantt`, `digest` |
| Functional domain | Planning / shift & resource scheduling |
| Confidence | High for structures; Gantt UX and recurrence behavior need live validation |

## Business purpose
Operational people-and-resource scheduling: plan shifts/assignments by role on a Gantt, publish schedules to employees, handle open shifts and self-assignment, and compare planned effort with reality (timesheets/attendance via bridges).

## Main users / personas
Planners/team leads, operations managers, employees (published schedule, open shifts), HR (calendars), services PMs (with `sale_planning`/`project_forecast`).

## Business problems solved
- Excel scheduling → `planning.slot` on a Gantt with roles (`planning.role`), templates (`planning.slot.template`), recurrence (`planning.recurrency`).
- Schedule communication → **draft → published** lifecycle (source-verified) with employee notification (`planning.send`).
- Unfilled shifts → open shifts + self-assignment patterns (validate exact flow live).
- Utilization blindness → planning analysis report; hourly cost link for planned cost.

## Main business processes (source-verified)
1. Build schedule: slots per resource/role, templates, copy-previous-week gestures; material resources supported (`resource.resource` extension; "Materials" menu — plan machines/rooms too).
2. Publish → employees notified/see "My Planning"; changes tracked (republish).
3. Open shifts board → employees pick up (governance via settings).
4. Analyze: planned hours/cost by resource/role (`planning.analysis.report`).

## Fit with other modules
`hr` (employees, calendars, departure handling — planning extends the departure wizard), `project_forecast` (project-based planning), `sale_planning` (plan from sold services), `hr_timesheet` (planned vs actual patterns), `industry_fsm` (field scheduling context), `hr_attendance`.

## Community fallback
None — no scheduling app in Community 19.0. Project deadlines/kanban are not scheduling; say so.

## Configuration opportunities
Roles, templates, working calendars, publication policy, open-shift rules, recurrence patterns, analysis dashboards.

## Studio / automation opportunities
Automation: unfilled-shift alerts, overtime-threshold flags (advisory), publish reminders. Studio: slot attributes (site, equipment tags). Labor-law compliance logic ≠ Studio — see below.

## Custom development triggers
Constraint-based auto-scheduling (skills/availability/law optimization) — native is manual/templated planning, not an optimizer; sector rostering regimes (healthcare/security) with legal constraint engines.

## External integration triggers
Workforce management suites (if law-grade rostering is required), attendance hardware, payroll interpretation engines (country-specific).

## Common client questions
"Auto-schedule?" — assisted (templates/copy/open shifts), not an optimization engine; be precise. · "Employees swap shifts?" — validate current swap/unassign flows live. · "Labor-law checks?" — not a compliance engine; rules live in calendars/process + external/WFM if regulated. · "Plan machines/rooms?" — material resources exist (source-verified).

## Fit-gap considerations
Great for services, retail-ish teams, workshops needing visual scheduling tied to ERP work. Gap zone: optimization-grade rostering, compliance engines, complex union rules — position WFM integration there instead of overbuilding.

## Deloitte demo angles
1. **Week in 2 minutes:** template-fill week → drag adjustments → publish → phone view of "My Planning".
2. **Open shift:** create open slot → employee self-assigns.
3. **Planned vs sold (with sale_planning):** sold service hours appear as demand.

## Implementation watch-outs
- Calendars/roles data quality first; garbage calendars = fake capacity.
- Publication discipline (draft vs published) trained explicitly.
- Clarify legal boundaries early in regulated rostering industries.

## Risks and assumptions
Structures verified; swap/self-assign specifics, notification cadence and Gantt scalability with large teams are runtime → validate. Enterprise licensing required.

## Validation checklist
- [ ] Roles/calendars modeled for a pilot team
- [ ] Publication + change-communication policy agreed
- [ ] Regulatory rostering constraints assessed (in/out of scope explicitly)
- [ ] Planned-vs-actual reporting needs mapped (timesheets/attendance bridges)
