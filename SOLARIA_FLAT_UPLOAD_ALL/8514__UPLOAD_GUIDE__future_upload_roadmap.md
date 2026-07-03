# Future Upload Roadmap — What Goes Up, When

| Attribute | Value |
|---|---|
| Companion | `batch_4_later_evidence_manifest.json` (file-level detail per use case), `context_overload_strategy.md` (the rules) |
| Rule | Nothing moves to a later stage early "because it's ready". Triggers, not readiness, schedule uploads. |

## Stage 0 — Immediate (now)
Paste `global_context_FINAL.txt` → upload **Batch 1** (6 governance docs) with descriptions. Nothing else.

## Stage 1 — After Batch 1 tests pass (≥7/8, no critical)
Upload **Batch 2** (5 navigation/evidence docs; catalog last). Run its suite (≥8/10).

## Stage 2 — After Batch 2 tests pass
Upload **Batch 3** (18 functional summaries incl. platform rungs + AI unit — AI items only with the risk/legal checkbox). Run the 12-test suite + 15 red-team probes. **Then stop for at least one working week** and log real usage.

## Stage 3 — After first business demo use case
When a real demo build starts (e.g., retail inventory demo):
- that module's `views_summary.md` (exact menu paths)
- `playbooks/odoo_demo_storyline_playbook.md`
- the module's `standard_vs_custom.md` if scope debates accompany the demo
Cap: ≤10 files; run the retrieval-quality checklist after.

## Stage 4 — Only for technical deep-dives
Trigger: migration mapping, integration design, or recurring field-level questions on a module.
- that module's `models.json` (never in bulk; per module)
- its `workflow_summary.md` for state-mapping work
First candidates historically: sale, account, stock, crm.

## Stage 5 — Only for security/role design
Trigger: authorization-concept workstream starts.
- `security_summary.md` for the modules in scope (start: account, stock, hr, documents)
- pair with the reminder that shipped defaults ≠ client security model.

## Stage 6 — Only for AI/Odoo strategy conversations
Trigger: AI existence disputes, build-vs-buy scoping, governance workshops.
- `modules/ai_native_odoo_19/ai_module_inventory.json` (existence precision)
- `modules/ai_native_odoo_19/standard_vs_custom.md`
- `playbooks/odoo_ai_inside_erp_strategy.md`
- `06` is already up from Batch 2; keep the four-way separation intact.

## Stage 7 — Methodology maturity (when recurring)
- `playbooks/odoo_fit_gap_methodology.md` + `odoo_requirement_to_solution_mapping_guide.md` (fit-gap runs)
- `odoo_client_discovery_question_bank.md` (workshop prep)
- `odoo_implementation_roadmap_template.md` (roadmap requests)
- `deloitte_odoo_partner_positioning.md` — internal framing; restrict audience if the platform allows.

## Stage 8 — Remaining functional summaries (demand-ranked)
Expected order by demand: `account_accountant`+`account_reports` (as a pair) → `quality`/`mrp_workorder`/`stock_barcode` (manufacturing deals) → `hr`, `hr_timesheet`, `planning`, `approvals`, `knowledge`, `point_of_sale`, `spreadsheet_edition`, `marketing_automation`, `website` → foundations (`base`, `mail`, `product`, `contacts`) usually last (architect audiences only).

## Never (see `do_not_upload_manifest.md`)
`.usage.md` companions · index.html · audit/QC/compliance reports · operator folders (upload_ready, final_upload_package) · test suites · superseded prompt copies · source folders.

## Governance of this roadmap
Review monthly against the question log; every stage change is logged (file, date, trigger, test result). When the pack versions (V4+), rebase this roadmap on the release notes before further expansion.
