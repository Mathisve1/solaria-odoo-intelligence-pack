# Module Intelligence Pack — `mrp_workorder` (MRP II)

> Enterprise shop-floor execution: the Shop Floor app, work-order planning Gantt by production/work center, operator flows incl. change proposals — the digital factory front end on mrp.

| Attribute | Value |
|---|---|
| Source origin | enterprise (Odoo 19.0) |
| Functional domain | Manufacturing (Shop Floor) |
| Direct dependencies | `quality`, `mrp`, `barcodes`, `web_gantt`, `web_tour`, `hr_hourly_cost` |
| Priority tier | 2 |
| Recommended upload priority | High-medium (Batch 3) |
| Confidence | Existence of models/menus/rules: high (source-verified). Behaviour: validate in a 19.0 demo database. |

## Contents and how Solaria should use them

| File | What it is | Use it for |
|---|---|---|
| `functional_summary.md` | Business-first module summary (primary document) | Capabilities, processes, fit-gap, demo angles |
| `standard_vs_custom.md` | Module-specific standard-vs-custom guidance | Customization questions on this module |
| `models.json` | Source-derived data model (21 models defined/extended) | Verifying objects/fields/relations exist |
| `views_summary.md` | Menus, actions, views, reports | Demo navigation, UI surface questions |
| `security_summary.md` | Groups, access rights, record rules | Role design, permission questions |
| `workflow_summary.md` | Status flows, crons, server actions, templates | Process design, automation questions |

Reading order for a business question: functional_summary → standard_vs_custom → evidence files.
Evidence files outrank narrative on *existence* questions; the functional summary outranks raw metadata on *meaning*.
