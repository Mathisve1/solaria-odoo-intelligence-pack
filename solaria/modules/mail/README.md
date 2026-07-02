# Module Intelligence Pack — `mail` (Discuss)

> The communication backbone: chatter, followers, activities, email gateway, templates. Explains why every record in Odoo has a conversation and to-do trail.

| Attribute | Value |
|---|---|
| Source origin | community (Odoo 19.0) |
| Functional domain | Communication & Activity backbone |
| Direct dependencies | `base`, `base_setup`, `bus`, `web_tour`, `html_editor` |
| Priority tier | 3 |
| Recommended upload priority | Medium (Batch 3–4; foundation context) |
| Confidence | Existence of models/menus/rules: high (source-verified). Behaviour: validate in a 19.0 demo database. |

## Contents and how Solaria should use them

| File | What it is | Use it for |
|---|---|---|
| `functional_summary.md` | Business-first module summary (primary document) | Capabilities, processes, fit-gap, demo angles |
| `standard_vs_custom.md` | Module-specific standard-vs-custom guidance | Customization questions on this module |
| `models.json` | Source-derived data model (79 models defined/extended) | Verifying objects/fields/relations exist |
| `views_summary.md` | Menus, actions, views, reports | Demo navigation, UI surface questions |
| `security_summary.md` | Groups, access rights, record rules | Role design, permission questions |
| `workflow_summary.md` | Status flows, crons, server actions, templates | Process design, automation questions |

Reading order for a business question: functional_summary → standard_vs_custom → evidence files.
Evidence files outrank narrative on *existence* questions; the functional summary outranks raw metadata on *meaning*.
