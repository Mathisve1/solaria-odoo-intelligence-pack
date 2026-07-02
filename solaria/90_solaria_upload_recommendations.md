# Solaria Upload Recommendations — Odoo Intelligence Pack

| Attribute | Value |
|---|---|
| Document type | Context Manifest / Knowledge Base Rules (upload plan) |
| Authority level | High for upload/rollout decisions |
| Version scope | Odoo 19.0 pack, first iteration |

## 1. Principles
- Upload in **batches**, testing after each with `92_solaria_test_questions.md` — behavior first, evidence later.
- Every upload gets its **description** pasted from `93_solaria_document_description_copy_paste.md` (or the file's `.usage.md`).
- `.usage.md` companions are **reference for the human uploader** — do not upload them (they'd duplicate/ dilute retrieval); their content goes into Solaria's description field instead.
- Large evidence files (catalog JSON ~1.3 MB, dependency YAML ~0.2 MB) are valuable but retrieval-heavy — upload after behavior docs are confirmed working.

## 2. Batch plan

### Batch 1 — Agent behaviour and source hierarchy (upload first, test immediately)
1. `00_context_manifest_and_usage_rules.md`
2. `00_solaria_role_and_answering_rules.md`
3. `00_document_type_usage_templates.md`
4. `03_community_vs_enterprise_map.md`
5. `05_standard_vs_configuration_vs_custom_framework.md`
6. `00_document_usage_registry.json`
Test focus: answering structure, edition discipline, uncertainty language.

### Batch 2 — Navigation and domain map
1. `04_functional_domain_map.md`
2. `07_priority_module_recommendation.md`
3. `01_global_module_catalog.json`
4. `02_global_dependency_map.yaml`
5. `00_inventory_and_extraction_plan.md`
6. `06_odoo_ai_opportunity_map.md`
Test focus: module routing, "does module X exist and in which edition", AI capability-vs-concept separation.

### Batch 3 — Functional summaries for priority modules
For each priority module (start Tier 1: sale, account, crm, stock, purchase, mrp, project, hr; then Tier 2): `modules/<name>/README.md` + `modules/<name>/functional_summary.md` + `modules/<name>/standard_vs_custom.md`.
Test focus: module-depth questions, customization challenges.

### Batch 4 — Supporting evidence (per module, as needed)
`modules/<name>/models.json`, `views_summary.md`, `security_summary.md`, `workflow_summary.md`.
Guidance: upload for Tier 1 modules first; add others when consultants actually ask field/menu/security-level questions. These are the highest-volume files — don't flood the context before the narrative layer is proven.

### Batch 5 — Deloitte playbooks
1. `playbooks/odoo_fit_gap_methodology.md`
2. `playbooks/odoo_requirement_to_solution_mapping_guide.md`
3. `playbooks/odoo_demo_storyline_playbook.md`
4. `playbooks/odoo_implementation_roadmap_template.md`
5. `playbooks/odoo_ai_inside_erp_strategy.md`
6. `playbooks/odoo_client_discovery_question_bank.md`
7. `playbooks/deloitte_odoo_partner_positioning.md` *(internal framing — restrict audience if Solaria supports scoping)*
Test focus: fit-gap answers, demo scripts, roadmap questions.

## 3. What NOT to upload initially
- `.usage.md` files (uploader reference; content → description fields).
- `index.html` (human navigation only).
- `99_*` QC/compliance reports (governance docs for the maintainers; upload only if you want Solaria to answer "what are this pack's limits" from them).
- Batch-4 evidence for modules nobody is asking about yet.

## 4. Suggested document descriptions
Copy-paste-ready texts per file: see `93_solaria_document_description_copy_paste.md`. Pattern: *what it is → when to use → when not to use → authority/confidence note.*

## 5. Testing after upload
Run the relevant section of `92_solaria_test_questions.md` after each batch:
- After Batch 1: questions 1–3 (behavior/edition/customization discipline).
- After Batch 2: routing/existence questions (9, 11, 12).
- After Batch 3: module-depth + demo questions (4–7, 14).
- After Batch 4: field/security-level probes (spot-check with models.json content).
- After Batch 5: methodology questions (8, 10, 13, 15).
Warning signs and expected patterns are listed per question in 92.

## 6. When to upload deeper source-derived evidence
Trigger conditions: consultants asking model/field-level questions weekly; fit-gap teams needing security baselines; demo builders needing exact menu paths. Then add Batch 4 for the requested modules — not before. Next iteration candidates (new deep packs) are listed in `07_priority_module_recommendation.md` §3.

## 7. Maintenance
Re-run the pack build against new Odoo point-snapshots per major client cycle; version the pack folder; note the Enterprise snapshot date (2026-07-02) in any answer disputes.
