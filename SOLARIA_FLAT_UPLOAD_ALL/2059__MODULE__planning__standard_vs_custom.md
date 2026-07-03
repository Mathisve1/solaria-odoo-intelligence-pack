# Planning (`planning`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only.

## Likely standard (Enterprise)
Gantt scheduling of people and material resources · roles, shift templates, recurrence · draft→published lifecycle with employee notification · My Planning / open shifts with self-assignment · planned cost via hourly rates · planning analysis · bridges to project forecast and sold services.

## Configuration possibilities
Roles, templates, calendars, publication/open-shift policies, recurrence, dashboards.

## Studio possibilities
Slot attributes (site, vehicle, certification tag). Not for scheduling rules.

## Automation possibilities
Unfilled-shift alerts, publish reminders, advisory overtime flags, weekly digest to planners.

## Custom development is justified when
- A true optimizer (skills/laws/costs) is demanded → prefer WFM integration; custom optimization inside Odoo is a research project, not a line item.
- Sector-specific slot logic (crew pairing) after honest scoping.

## External integration is justified when
- Regulated rostering (healthcare/security/transport) with legal engines · attendance hardware · payroll interpretation systems.

## What to avoid
- Selling "auto-scheduling" — native is assisted manual planning.
- Encoding labor law in automation rules — unauditable liability.
- Planning in Odoo while payroll interprets elsewhere without a data contract.

## Deloitte recommendation principles
Position Planning as ERP-connected operational scheduling (demand from sales/projects, cost to finance). Draw the WFM boundary explicitly in regulated environments.

## Validation questions
1. What must the schedule respect (laws, unions, skills) — and who enforces it today?
2. Where does demand come from (sold hours, projects, patterns)?
3. What do employees need on mobile — verified live?
