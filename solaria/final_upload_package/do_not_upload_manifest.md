# DO NOT UPLOAD Manifest — V3 Final

| Attribute | Value |
|---|---|
| Principle | Every low-value file uploaded dilutes retrieval of the high-value ones. When in doubt: don't upload; measured demand decides later. |
| Status | Authoritative (consolidates and supersedes `upload_ready/do_not_upload_initially.md` where they differ) |

## Never upload

| Category | Files | Why |
|---|---|---|
| Usage companions | all 300+ `*.usage.md` | Human uploader reference cards. Their content belongs in the **description fields**. Uploading them duplicates every document's summary and actively poisons routing. |
| Navigation helper | `index.html` | Zero knowledge content; local browsing only. |
| Quality/compliance reports | `99_quality_control_report.md`, `99_file_type_compliance_report.md` | Pack build governance, not Odoo knowledge. (Optional documented exception: QC report late, only if Solaria should self-describe its limits.) |
| Audit reports | `98_v2_initial_audit_report.md`, `96_evidence_and_claims_audit.md`, `97_v2_module_improvement_report.md`, `99_v3_preupload_readiness_audit.md`, `99_v2_self_check.md`, `99_v3_self_check.md`, release notes | Maintainer history. Solaria advising on Odoo does not need its own build diary. |
| Operator documents | everything in `upload_ready/` and `final_upload_package/` (incl. this file, the manifests, test suites, rubric, checklists) | Instructions for the human operator. Uploading test suites would also let Solaria "study for the exam" — invalidating acceptance testing. |
| Duplicated descriptions | `93_solaria_document_description_copy_paste.md`, `90_solaria_upload_recommendations.md`, `92_solaria_test_questions.md` | Their content is either operator process or duplicates the descriptions already pasted per document. |
| Superseded prompt copies | `91_solaria_global_context_prompt.md` / `.txt` | The prompt is PASTED into the global-context field from `global_context_FINAL.txt` — never uploaded as a document (it would compete with itself in retrieval). |
| Local settings / infrastructure | `.claude/`, `.gitignore`, any `settings*.json`, environment files | Not knowledge; potential information leakage. Also git-ignored. |
| Source folders | `_sources/` (Odoo source trees), any zip archives | Raw source code — explicitly out of scope for upload, licensing-sensitive, and technically outside `solaria/`. Never. |

## Not now — demand-gated (see `batch_4_later_evidence_manifest.json`)
All `models.json`, `views_summary.md`, `security_summary.md`, `workflow_summary.md`, module-level `standard_vs_custom.md`, the 18 remaining functional summaries, the AI pack's inventory/standard-vs-custom/README, and the 7 playbooks. Each has a defined trigger; none goes up "because it exists".

## Why this is strict (the three reasons)
1. **Retrieval dilution:** ~30 well-described documents route cleanly; 500 files make every lookup a lottery.
2. **Test integrity:** acceptance and red-team suites must stay out of the corpus, or the tests measure memorization instead of behaviour.
3. **Debuggability:** if behavior degrades, a small corpus lets you find the culprit; a bulk upload cannot be rolled back intelligently.

## Enforcement
The go/no-go checklist contains explicit checkboxes for the highest-risk mistakes (usage files, test suites, source folders). If any never-upload item is found in Solaria: remove it, then re-run the nearest acceptance suite before continuing.
