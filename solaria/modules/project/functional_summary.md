# Project (`project`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `project` |
| Display name | Project |
| Source origin | **Community** (Enterprise adds `project_enterprise` Gantt/map, `project_forecast`/`planning`, `documents_project`; billing depth via `sale_timesheet`/`timesheet_grid`) |
| Version scope | Odoo 19.0 |
| Dependencies | `base`, `mail`, `portal`, `rating`, `analytic` (profitability), `hr_timesheet` bridge |
| Functional domain | Project / services delivery |
| Confidence | High for structures; profitability computation details need live validation |

## Business purpose
Organize and deliver work: projects with configurable task pipelines, milestones, collaborators (internal + portal customers), recurring tasks, project health updates — and, with sales/timesheets, the commercial arc from sold service to billed hours.

## Main users / personas
Project managers, delivery teams, PMO (updates/portfolio), customers (portal collaboration), services ops/finance (profitability).

## Business problems solved
- Work tracked in tools disconnected from revenue → tasks linked to sale order items and analytic accounts.
- Status opacity → project updates (`project.update`), milestones, burndown reporting structures.
- Customer collaboration by email chaos → portal sharing with collaborators (`project.collaborator`).
- Repetitive work → task recurrence (`project.task.recurrence`).

## Main business processes (source-verified)
- Task flow: per-project stages (`project.task.type`, configurable) + a cross-project **state** field (`01_in_progress → 02_changes_requested → 03_approved → 04_waiting…/done/canceled` — 19.0's personal-status layer) — two complementary mechanisms; train teams on the difference.
- Project lifecycle: project stages (`project.project.stage` — group-gated "Use Stages on Project"), health updates, milestones (group-gated) that can gate invoicing with sales integration.
- Collaboration: chatter, activities, ratings (customer satisfaction on tasks — with config), portal shares (`project.share.wizard`).
- Templates: project templates incl. role-to-user mapping wizards (`project.template.*`, 19.0) — repeatable delivery setups.
- Profitability: analytic account per project; with `sale_project`/`sale_timesheet`: sold vs delivered vs billed.

## Key functional capabilities
Configurable kanban pipelines per project, task dependencies (group-gated), recurring tasks, multi-assignees model (validate exact semantics), tags, priorities, personal stages (`project.task.stage.personal` — my-work organization), project roles (`project.role`, 19.0), embedded per-project task actions (each project can feel like its own app), burndown/task analysis reports.

## Fit with other modules
`sale_project`: service products create projects/tasks; milestone invoicing. `hr_timesheet`: hours on tasks → costs (and revenue with sale_timesheet). `helpdesk` (E): ticket→task escalation. `industry_fsm` (E): field ops are project tasks. `planning`/`project_forecast` (E): resource scheduling. `documents_project` (E). Analytic accounting underpins profitability.

## Standard in 19.0 (Community)
Everything above without Gantt/map views and resource forecasting: pipelines, states, milestones, recurrence, dependencies, updates, portal collaboration, ratings, templates, analysis reports.

## Enterprise-specific additions
Gantt & map views, resource forecast/planning, documents integration, timesheet grid/validation & billing rate depth. Portfolio-grade dashboards via spreadsheet (E).

## Configuration opportunities
Stages per project + shared stage libraries, project visibility (private/internal/portal per project), milestones on/off, dependencies on/off, recurrence, rating frequency, email aliases per project, templates with roles.

## Studio / automation opportunities
Automation: SLA-ish nudges (task idle in stage), auto-assign by tag/role, escalation to PM on changes_requested, status-report reminders. Studio (E): client-industry fields (site refs, deliverable types), tailored kanban cards. Keep billing logic in sales items, not Studio.

## Custom development triggers
True portfolio management (stage-gate governance, capacity-financial planning) beyond updates+spreadsheets; construction-grade WBS/progress billing (check industry modules first); external scheduling algorithms.

## External integration triggers
Jira-style engineering stacks kept by IT (sync tasks), PSA suites being replaced gradually, BIM/construction platforms, corporate PPM tools.

## Common client questions
"Can customers see/comment tasks?" — portal collaboration, per-project visibility; validate exact rights live. · "Milestone billing?" — with sale integration; native pattern. · "Gantt?" — Enterprise. · "Cross-project my-work view?" — personal stages + My Tasks. · "Profitability per project?" — analytic-based; needs timesheets+sale links configured.

## Fit-gap considerations
High fit for services delivery and internal work management. Gap hotspots: portfolio/stage-gate governance, resource-financial planning (E planning helps operationally), heavy WBS industries. The two-mechanism status model (stages vs state) must be designed deliberately or reporting becomes mush.

## Deloitte demo angles
1. **Sell-to-deliver:** service quote → project + tasks appear → log time → invoice from delivered hours (E grid adds validation) — the PSA story.
2. **Customer collaboration:** portal task view + rating email — services differentiation.
3. **PMO story:** project updates + milestone board + task analysis pivot.

## Implementation watch-outs
- Stage taxonomy governance across teams (shared vs per-project stages) — decide once.
- Analytic design (plans, distribution) before profitability promises.
- Visibility defaults: avoid accidental portal exposure; test with a portal user.
- Recurrence/dependencies are group-gated — demo with groups enabled deliberately.

## Risks and assumptions
Structures verified. Multi-assignee semantics, burndown exactness and rating flows are runtime → validate. Profitability quality depends on timesheet discipline — an adoption risk, not a product risk.

## Validation checklist
- [ ] Stage library + state usage agreed and documented per team
- [ ] Billing models mapped to service product configs (prepaid/T&M/milestone)
- [ ] Portal visibility tested with a real customer account
- [ ] Analytic plan design signed by finance
- [ ] Edition needs (Gantt, forecast, grid validation) confirmed
