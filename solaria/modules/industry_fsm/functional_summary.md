# Field Service (`industry_fsm`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `industry_fsm` |
| Display name | Field Service |
| Source origin | **Enterprise** (built on Community `project`+`hr_timesheet` foundations) |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `project_enterprise`, `timesheet_grid`, `base_geolocalize` — i.e., FSM sits on the **Enterprise** project/timesheet layer, not plain Community `project` (+siblings: `industry_fsm_report` worksheets, `industry_fsm_sale`, `industry_fsm_stock`) |
| Functional domain | Field Service |
| Confidence | High for structures; mobile/offline UX must be validated on real devices |

## Business purpose
Plan and execute on-site interventions end-to-end: field tasks with scheduling, travel/work timers, worksheets, parts consumption, customer signature and on-the-spot invoicing — the technician's whole day on a phone, wired into projects, stock and billing.

## Main users / personas
Field technicians (mobile), dispatchers/planners, service managers, customers (sign-off, portal), finance (billable interventions).

## Business problems solved
- Paper worksheets → digital worksheets (`industry_fsm_report` custom worksheet reports; source shows worksheet report models).
- Unbilled interventions → timers on tasks (timesheet integration) + "create invoice" from the task (group "Create new quotations directly from the tasks" — quote products on site with `industry_fsm_sale`).
- Dispatch chaos → My Tasks / To Schedule / Planning by user/project/location menus, map view (source-verified map/planning menus).
- Proof-of-service disputes → worksheet + customer signature + timestamps.

## Main business processes (source-verified)
1. Intake: from helpdesk escalation, sales (service products), or direct task creation; "To Schedule" queue.
2. Dispatch: planning menus by user/project; map-based grouping ("By Location").
3. Execute (mobile): start timer → do work → worksheet → add materials (with `industry_fsm_stock` van-stock flows) → customer signature.
4. Close & bill: stop timer(s) (stop-timers wizard source-verified), invoice from task; ratings for service quality.

## Key functional capabilities
FSM-flavored projects (project extension with `is_fsm` patterns), task recurrence for maintenance-ish visits, worksheets customizable per intervention type, quotations from tasks, timesheet-backed labor billing, customer ratings.

## Fit with other modules
`helpdesk` (ticket→intervention), `sale` (service products→tasks; quotes on site), `stock` (parts, van stock via sibling), `planning` (workforce view), `timesheet_grid` (validation), `maintenance` context (equipment — validate equipment linkage scope per need), `account` (invoices).

## Community fallback
`project`+timesheets can track field work minimally — no timers-on-site UX, worksheets, map dispatch or on-site invoicing. Position as a compromise only for tiny teams.

## Configuration opportunities
FSM project setup (billing type, worksheets on/off), worksheet templates, stages/tags, planning views, recurrence for periodic visits, rating cadence.

## Studio / automation opportunities
Automation: SLA-ish dispatch alerts, auto-create follow-up visits on worksheet outcomes, parts-replenishment nudges. Studio: worksheet/task fields per intervention type (safety checklists) — worksheets themselves are designed via the worksheet feature (validate the designer live).

## Custom development triggers
Route optimization (multi-stop optimization is not native — integration territory), complex warranty/contract entitlement adjudication, offline-heavy requirements beyond app scope, asset/IoT-driven auto-dispatch.

## External integration triggers
Route optimizers, IoT/telemetry platforms (alarm→intervention), subcontractor networks, legacy asset registries (or model assets in Odoo — design decision).

## Common client questions
"Offline in the field?" — validate the current mobile offline envelope honestly on devices. · "Route optimization?" — map/planning yes, optimization no (integrate). · "Custom checklists per job type?" — worksheets; demo the designer. · "Invoice on site?" — native flagship; rehearse it. · "Van stock?" — `industry_fsm_stock`; validate flows live.

## Fit-gap considerations
Excellent for installation/repair/maintenance service teams in the ERP's orbit. Gap zone: large-fleet routing optimization, entitlement-heavy warranty ops, deep asset management (pair with maintenance/custom design). The one-platform arc (ticket→visit→parts→invoice) is the winning argument vs point FSM tools.

## Deloitte demo angles
1. **Technician's hour (mobile):** my tasks → start timer → worksheet → signature → invoice — all on a phone. Rehearse ruthlessly; it's the best demo in the services portfolio.
2. **Dispatcher view:** To Schedule → map by location → assign.
3. **End-to-end:** helpdesk ticket escalates to visit; invoice references both.

## Implementation watch-outs
- Device strategy (models, MDM, connectivity) early; the phone IS the workstation.
- Worksheet design with actual technicians (usability beats completeness).
- Parts logistics design (van stock, returns) with warehouse team.
- Billing policy per intervention type decided with finance.

## Risks and assumptions
Structures verified. Mobile UX specifics, offline behavior, worksheet designer depth and van-stock flows are runtime → validate on devices. Enterprise licensing required.

## Validation checklist
- [ ] Pilot with 2-3 technicians on real devices in real coverage conditions
- [ ] Worksheet templates per top intervention types drafted with the field
- [ ] Parts/van-stock flow tested with warehouse
- [ ] Billing models per intervention type mapped and demoed
