# Timesheets (`hr_timesheet`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: entry/costing is Community; grid UX, validation, reminders, billing-rate depth are Enterprise.

## Likely standard (Community)
Task-level time entry · analytic-line foundation (costing) · own/all/admin role split · analysis by employee/project/task · billing via `sale_timesheet` mapping (Community bridge) · employee cost rates.

## Configuration possibilities
Time UoM & rounding, billable defaults per project/product, groups, analysis views, service product mappings (T&M/prepaid).

## Studio possibilities (E)
Line tags/classifications (activity type) — keep the taxonomy centrally governed or reporting fragments.

## Automation possibilities
Missing-entry reminders, month-end lock nudges, anomaly alerts, auto-set billable flags by project rules.

## Custom development is justified when
- Rate-card engines (role×client×contract×phase with effective dates) exceed sale-item mapping and E scope — verify `sale_timesheet_enterprise` first.
- Regulated time-recording exports with specific formats.

## External integration is justified when
- Payroll bureau consumes approved time.
- Corporate staffing/PSA remains scheduling master.

## What to avoid
- Custom approval states on analytic lines (E grid exists; Community = process).
- Duplicate time systems "temporarily" — kills adoption permanently.
- Building reminders/validation custom on Community when the need is really Enterprise — say the edition truth.

## Deloitte recommendation principles
Treat adoption as the project: entry time under 2 minutes/day, reminders, visible fairness (validated time = paid/billed). Map every billing model to a configured demo before gap verdicts.

## Validation questions
1. Who validates time and what happens to rejected lines?
2. Which rate logic exists contractually — expressible in sale items?
3. What feeds payroll/bureau, at which approval status?
