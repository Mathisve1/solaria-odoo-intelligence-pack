# Project (`project`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: `project` is Community; Gantt/map, forecasting/planning, documents bridge, timesheet grid/validation are Enterprise.

## Likely standard (Community)
Kanban pipelines per project · cross-project task states · milestones · task dependencies & recurrence · project stages & health updates · portal customer collaboration + ratings · project templates with roles · email-to-task aliases · analysis/burndown reports · analytic-based profitability plumbing.

## Configuration possibilities
Stage libraries, visibility per project, milestones/dependencies/recurrence toggles (groups), aliases, rating cadence, templates, tags/roles, activity plans for delivery rituals.

## Studio possibilities (E)
Industry fields on tasks (site, asset, deliverable type), tailored kanban/list views per team, simple portal-visible info fields. Not for billing logic or scheduling logic.

## Automation possibilities
Stage-idle nudges, auto-assignment by tag/role, escalations on changes_requested, periodic update reminders to PMs, auto-create follow-up tasks on milestone reached.

## Custom development is justified when
- Stage-gate portfolio governance with financial gates is a core process (after trying updates+milestones+spreadsheet dashboards).
- Industry WBS/progress-billing regimes (construction) — check industry modules/localizations first.
- Deep bidirectional sync with engineering tools at scale (adapter-class work).

## External integration is justified when
- Engineering keeps Jira/Azure DevOps (sync boundaries: tasks/status only).
- Corporate PPM/PSA remains for portfolio, Odoo for execution+billing.
- Specialized schedulers (construction planning) own the timeline.

## What to avoid
- Custom status fields duplicating stages/state — the classic project-reporting killer.
- Replicating Gantt in custom views for Community budgets — either Enterprise or honest kanban.
- Profitability promises without timesheet adoption plans and analytic design.
- Per-team snowflake processes: 30 projects × unique stages = unreportable portfolio.

## Deloitte recommendation principles
Design the status model once (stages = flow, state = personal/health) and enforce it. Tie every billing promise to a configured service product demo. Position planning/forecast (E) when utilization is the pain — not more custom fields.

## Validation questions
1. Which billing models exist, and does a configured demo reproduce each?
2. Portfolio reporting needs: operational (native) or governance-grade (design work)?
3. Who schedules people — PMs (planning E) or a central PMO (maybe external PPM)?
4. What exactly must customers see? (Test portal, don't assume.)
