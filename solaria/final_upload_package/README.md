# FINAL UPLOAD PACKAGE — Operator Guide (V3, authoritative)

| Attribute | Value |
|---|---|
| Status | **This folder supersedes `upload_ready/` for execution.** The kit remains as background; when they differ, this folder wins. |
| Contents | FINAL global context, exact Batch 1/2/3 manifests (JSON), later-evidence manifest, do-not-upload manifest, per-batch description sheets, per-batch acceptance suites, red-team suite, answer rubric, simulated benchmark, overload strategy, upload roadmap, human go/no-go checklist |
| Principle | Less context first, more context later. Batch 1 teaches HOW to reason, Batch 2 WHERE to look, Batch 3 the first functional domains. Total first footprint: **29 documents**, then stop. |

## Step-by-step upload process

**Step 0 — Gate.** Work through `HUMAN_GO_NO_GO_CHECKLIST.md` section A (pre-upload). Any NO = stop.

**Step 1 — Global context.** Open `global_context_FINAL.txt`. Copy ALL of it into Solaria's global context / custom-instructions field for the Odoo workspace. Save. Never paste partial sections.

**Step 2 — Batch 1 (6 files).** Follow `batch_1_manifest.json` in `upload_order`. For each file: upload the file at its `file_path` (paths are relative to the `solaria/` folder), paste its `paste_ready_description` into Solaria's document-description field. Descriptions are functional — they drive routing; skipping them is the #1 cause of failure.

**Step 3 — Test Batch 1.** Run `acceptance_tests_AFTER_BATCH_1.md` (8 tests). Gate: **≥7/8 with no critical fail** (critical = overclaiming or missing edition discipline). Log results. Fail → troubleshoot (below), do not proceed.

**Step 4 — Batch 2 (5 files).** Per `batch_2_manifest.json`. Note: the module catalog uploads LAST within the batch and has its own retrieval test. Then run `acceptance_tests_AFTER_BATCH_2.md` (10 tests, gate ≥8/10, no critical fail).

**Step 5 — Batch 3 (18 files).** Per `batch_3_manifest.json` (functional summaries only + the AI pack's summary and governance doc as one unit — AI items require the risk/legal review checkbox from the go/no-go list). Then run `acceptance_tests_AFTER_BATCH_3.md` (12 tests, gate ≥10/12) **plus** `red_team_tests.md` (15 adversarial probes, gate: zero critical failures). Score answers with `answer_quality_rubric.md`; compare against `simulated_answer_benchmark.md`.

**Step 6 — STOP.** Do not upload anything else for at least one working week. Let consultants use it; log their questions. That log — not intuition — decides Batch 4.

**Step 7 — Later batches.** Decide per `future_upload_roadmap.md` + `batch_4_later_evidence_manifest.json` (evidence files grouped by use case, uploaded per module per demonstrated need). Re-run the nearest acceptance suite after every expansion of ≤10 files.

## How to use document descriptions
Every uploaded file gets its description pasted from the batch manifest / description sheets — exact text, no improvisation. The descriptions carry routing language ("Use for… Do not use for…") that Solaria relies on to pick documents. If a platform title field exists, use the `solaria_title` from the description sheets.

## When to stop uploading
- A batch gate fails → stop, fix, retest. Never "upload more to fix retrieval".
- Answers start citing wrong documents or mixing narrative/evidence roles → context overload signal (see `context_overload_strategy.md`) → consider removing the last additions.
- Nobody is asking questions that need the next batch → stop; measured demand only.

## How to decide on Batch 4 evidence files
Only when a concrete trigger fires (consultant asks field-level/security/menu-path/workflow questions about a specific module **more than once**). Then upload only that module's relevant evidence file(s) per the Batch-4 manifest's use-case grouping — never "all models.json".

## Troubleshooting

**Generic answers** ("Odoo is flexible…"): check global context saved → check Batch-1 descriptions present → re-ask naming a document ("answer using the standard-vs-custom framework") → ask "which documents did you use?" — if none named, re-upload Batch 1 with descriptions; if still generic, reduce volume (remove non-Batch files) and retest.

**Overconfident answers** (features asserted without edition/caveat): verify `00_solaria_role_and_answering_rules.md` and `03_community_vs_enterprise_map.md` are uploaded with descriptions; re-run red-team tests R1–R5; if failing persistently, re-paste the global context (it contains the kill-switch and evidence vocabulary) and escalate to the pack maintainer with transcripts.

**Wrong document routing** (e.g., answering existence questions from playbooks): confirm the registry JSON is uploaded; check that no `.usage.md` files were uploaded by mistake (they duplicate descriptions and poison routing) — remove them if found.

## Roles
Operator (executes this guide) · Pack maintainer (owns fixes, receives failed-test transcripts) · Risk/legal reviewer (AI documents sign-off) · Consultant testers (run acceptance suites with fresh sessions).
