# Timesheets (`hr_timesheet`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `hr_timesheet` |
| Display name | Timesheets |
| Source origin | **Community** (Enterprise adds `timesheet_grid`: grid entry, validation, reminders; billing depth via `sale_timesheet(_enterprise)`) |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `hr`, `hr_hourly_cost`, `analytic`, `project`, `uom` — timesheets ARE analytic lines (`account.analytic.line`) |
| Functional domain | Timesheets / services costing & billing |
| Confidence | High for structures; grid/validation UX is Enterprise runtime — validate live |

## Business purpose
Capture time on projects/tasks so that services companies know cost, margin and billable value — the data spine between delivery (project), payroll-ish costing (employee hourly cost) and invoicing (with sale integration).

## Main users / personas
Consultants/engineers (entry), project managers (review), services ops/finance (billing, margins), HR (cost rates via `hr_hourly_cost` patterns).

## Business problems solved
- Unbilled hours leakage → time tied to tasks and sale order items (with `sale_timesheet`).
- Cost opacity → timesheets are analytic lines (`account.analytic.line` extension) hitting project analytics natively.
- Entry friction → My Timesheets views; (E) grid + reminders + timers (timer mixin appears via FSM/timer features).

## Main business processes
1. Daily/weekly entry on tasks (My Timesheets; `timesheets.analysis.report` for analysis).
2. Review/approval: basic oversight Community; formal validation workflow in `timesheet_grid` (E).
3. Billing: with `sale_timesheet` — billable mapping to sale items (T&M, prepaid hours); invoicing from delivered time.
4. Costing: employee hourly cost → project cost lines → margin.

## Key functional capabilities (source-verified)
Role split groups: "User: own timesheets only" / "User: all timesheets" / Administrator; department-based reporting (By Employee/Project/Task menus); employee-deletion guard wizard; portal exposure of timesheets on customer docs configurable (via sale integration — validate).

## Fit with other modules
`project` (tasks), `sale_timesheet` (billing), `hr` (employees/cost), `industry_fsm` (E timers on site), `planning` (E planned vs done), `hr_payroll` (E, payable overtime patterns per country — validate), `timesheet_grid` (E).

## Standard vs Enterprise
Community: entry, analysis, costing plumbing, role split. Enterprise: grid UX, validation workflow, reminders, timer polish, billing-rate depth (`sale_timesheet_enterprise`).

## Configuration opportunities
UoM of time (days/hours), encoding granularity policy, project billable defaults, role groups, analysis dashboards.

## Studio / automation opportunities
Automation: missing-timesheet reminders (Community approximation of E reminders), lock nudges before month-end, anomaly alerts (>12h/day). Studio (E): activity-type tags on lines (mind reporting consistency).

## Custom development triggers
Industry billing engines (blended rates matrices beyond sale item mapping), interfaces to legacy time clocks for white-collar time (rare), regulated time-recording regimes.

## External integration triggers
Payroll bureaus consuming approved time; corporate PSA/staffing tools; calendar-mining tools (governance caution).

## Common client questions
"Approval workflow?" — E grid validation; Community = discipline+automation. · "Bill hours automatically?" — with sale_timesheet mapping; demo per billing model. · "Reminders?" — E native; Community via automation. · "Mobile entry?" — validate current app scope live.

## Fit-gap considerations
Fit is high for consultancies/agencies. The battleground is adoption (entry discipline) and billing-model mapping. Complex rate cards (role×client×phase) need design; check `sale_timesheet_enterprise` scope before custom.

## Deloitte demo angles
1. **Hour to invoice:** log 2h on task → invoice draft shows the line — "no hour lost".
2. **Manager week:** (E) grid validation + reminder story.
3. **Margin truth:** project P&L from cost rates vs billed value.

## Implementation watch-outs
- Decide granularity policy (0.25h? daily?) and enforce via training+automation, not fields.
- Cost rate maintenance process (HR owns? finance?) — stale rates = fake margins.
- Billable defaults per project template prevent silent non-billable leakage.

## Risks and assumptions
Structures verified; validation flow, reminder cadence and mobile UX are E runtime → validate. Payroll-time interplay is country-specific (E payroll) — never assume.

## Validation checklist
- [ ] Billing models reproduced (T&M, prepaid, milestone+time) in demo
- [ ] Approval chain decided (who validates, when) with edition implication
- [ ] Cost-rate ownership and update cadence agreed
- [ ] Adoption plan (reminders, KPIs) defined
