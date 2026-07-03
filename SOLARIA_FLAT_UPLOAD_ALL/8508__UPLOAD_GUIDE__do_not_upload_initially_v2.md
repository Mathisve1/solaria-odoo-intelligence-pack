# Do NOT Upload Initially — and Why

| Attribute | Value |
|---|---|
| Document type | Context Manifest / Knowledge Base Rules (operator guardrail) |
| Principle | Retrieval quality beats corpus size. Every low-value file uploaded early dilutes the retrieval of the high-value ones. |

## Never upload
| What | Why |
|---|---|
| All `.usage.md` files (209 of them) | They are uploader reference cards; their content belongs in the **description fields**, not the corpus. Uploading them duplicates every document's summary and pollutes retrieval. |
| `index.html` | Human navigation only; zero knowledge value. |
| `98_v2_initial_audit_report.md`, `96/97` audit & improvement reports, `99_file_type_compliance_report.md`, `99_v2_self_check.md` | Maintainer governance evidence. Solaria doesn't need the pack's own build history to advise on Odoo. |

## Not initially — only on demonstrated demand
| What | Upload trigger |
|---|---|
| `models.json` files (34 modules) | Consultants ask field/data-model/migration-mapping questions about a specific module → upload that module's file only |
| `views_summary.md` files | Demo builders need exact menu paths for a module |
| `security_summary.md` files | Role-design or permissions work starts on a module |
| `workflow_summary.md` files | Process-design/migration state-mapping questions on a module |
| `standard_vs_custom.md` (module-level) | Customization debates on that module become recurring |
| Remaining 20 functional summaries (base, mail, product, contacts, hr, hr_timesheet, website, point_of_sale, planning, knowledge, approvals, marketing_automation, + V2: account_accountant, account_reports, web_studio, base_automation, spreadsheet_edition, quality, mrp_workorder, stock_barcode) | The module starts appearing in real questions — **exception: upload `modules/ai_native_odoo_19/` (inventory + functional summary + governance doc) as soon as AI questions appear; treat it as one unit** |
| Playbooks (7) | Methodology questions (fit-gap runs, demo prep, roadmaps) appear — then upload per `90_solaria_upload_recommendations.md` Batch 5 |
| `99_quality_control_report.md`, `99_v2_final_release_notes.md` | Only if you want Solaria to answer "what are your knowledge limits" from its own QC — optional, late |
| `92_solaria_test_questions.md`, `90/93`, this folder's checklists | Operator documents; upload only if Solaria itself should coach uploads — normally keep out |

## Why not everything at once (the honest reasoning)
1. **Retrieval dilution:** hundreds of similar evidence files make the retriever's job harder; the narrative layer should win existence-of-doubt cases.
2. **Testability:** batch-by-batch acceptance tells you *which* upload broke behavior; a bulk upload cannot be debugged.
3. **Signal for iteration 3:** on-demand uploads reveal which modules/evidence types consultants actually need — that is the next-iteration backlog, measured instead of guessed.

## The volume guardrail
Target ≤ ~30 uploaded documents until the acceptance script passes twice in a row (fresh sessions). Expand in steps of ≤10, re-running the nearest batch's spot-checks after each step.
