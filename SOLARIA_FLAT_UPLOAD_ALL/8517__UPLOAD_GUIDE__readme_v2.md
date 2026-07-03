# Upload-Ready Kit — How a Human Uploads This Pack to Solaria

> **V3 SUPERSESSION NOTICE:** execution now follows **`../final_upload_package/`** (exact batch manifests, FINAL global context, per-batch acceptance suites, red-team tests, go/no-go checklist). This kit remains as background reading; where the two differ — notably Batch 3, which V3 expands from 14 to 18 files — the final_upload_package manifests win.

| Attribute | Value |
|---|---|
| Document type | Context Manifest / Knowledge Base Rules (operator kit) |
| Audience | The person physically configuring Solaria — no Odoo expertise assumed |
| Companions | Batch checklists 1–3, `do_not_upload_initially.md`, `solaria_acceptance_test_script.md` (all in this folder) |

## The whole procedure in 8 steps

1. **Paste the global context.** Open `solaria/91_solaria_global_context_prompt.txt`, copy ALL of it, paste into Solaria's global context / custom-instructions field for the Odoo workspace. Save. *(If the field has a length limit, paste from the top and keep whole sections; never cut mid-section.)*
2. **Upload Batch 1** (6 governance files) following `batch_1_exact_upload_checklist.md` — file by file, pasting the given description into Solaria's document-description field each time. Descriptions are not optional decoration: they are how Solaria decides when to use a document.
3. **Test Batch 1**: run the 3 acceptance questions at the end of the checklist. All three must pass before continuing.
4. **Upload Batch 2** (5 navigation/evidence files) per `batch_2_exact_upload_checklist.md`, test again.
5. **Upload Batch 3** (14 module functional summaries) per `batch_3_functional_summary_selection.md`, test again.
6. **Run the full acceptance script** (`solaria_acceptance_test_script.md`, 12 questions). Log results.
7. **Stop there for the first week.** Let consultants use it; collect real questions.
8. **Expand on demand**: when users hit depth limits (field-level, security, menu-path questions), add that module's evidence files (models.json, views/security/workflow summaries) and its `standard_vs_custom.md`; when methodology questions appear, add the playbooks (Batch 5 in `90_solaria_upload_recommendations.md`).

## What to paste where (the three text sources)
- **Global context field** ← `91_solaria_global_context_prompt.txt` (once).
- **Per-document description field** ← the description given in the batch checklist for that file (or in `93_solaria_document_description_copy_paste.md` / the file's `.usage.md` for anything not in a checklist).
- **Nothing else** — do not paste document contents anywhere manually.

## What NOT to upload
See `do_not_upload_initially.md`. Short version: no `.usage.md` files, no `index.html`, no `9x` reports, no bulk evidence files before retrieval quality is proven.

## If Solaria gives generic answers ("Odoo is flexible…")
Work through this list in order — it fixes >90% of cases:
1. Global context actually saved? (Re-open the field and check.)
2. Batch 1 documents all present WITH their descriptions? (Missing descriptions are the #1 cause.)
3. Ask again naming the artifact: "Answer using the Community-vs-Enterprise map" — if that works, retrieval is fine and the question was too vague; coach question style (see `11_functional_consultant_orientation_for_deloitte_odoo.md`).
4. Ask "Which documents did you use?" — if it can't name any, the documents aren't being retrieved: re-upload Batch 1 with descriptions, or reduce total uploaded volume (too many low-value files dilute retrieval — see `do_not_upload_initially.md`).
5. Still failing → run only questions 1–3 of the acceptance script and record exact outputs for the pack maintainer.

## Adding more documents later (the rule of thumb)
Upload narrative before evidence, evidence per module only when its questions actually occur, playbooks when methodology questions occur. Every upload gets its description from `93` or its `.usage.md`. After each expansion, re-run the 3 spot-check questions of the nearest batch.

## Maintenance
Pack scope is Odoo 19.0 (Enterprise snapshot 2026-07-02). When a new pack version arrives, replace changed files and re-run the full acceptance script. Keep this folder's checklists in sync with any re-upload.
