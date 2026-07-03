# HUMAN GO / NO-GO CHECKLIST — Solaria Upload

**Rule: every box is binary. Any unchecked box in a section = STOP at that section.** Print or copy this file; fill it in as you go; keep the completed copy with the test logs.

## A. Before touching Solaria (pre-flight)

- [ ] **Repository visibility:** the git repo containing this pack is **private** (or local-only). If it has a remote: visibility verified as private on the hosting platform. NO-GO if public.
- [ ] **Branch:** you are working from the reviewed release branch (`solaria-v3-preupload-gate` or its merged successor) — `git branch --show-current` matches.
- [ ] **Working tree clean:** `git status` shows no unexplained files (V3 removed stray artifacts once — check they haven't returned).
- [ ] **No source code in scope:** nothing from `_sources/` or any Odoo source tree is in the upload list. The upload list contains ONLY files named in the Batch 1–3 manifests.
- [ ] **Operator read the guide:** `final_upload_package/README.md` read end-to-end by the person doing the upload (dry-run of Batch 1 steps on paper).
- [ ] **Reviews done:** Batch-1 documents skimmed by the pack maintainer this week; no pending edits.

## B. Global context

- [ ] `global_context_FINAL.txt` pasted **completely** into Solaria's global context field (open the field again and verify the last section "STYLE" is present).
- [ ] No other/older prompt text remains in the field (91 versions removed if previously pasted).

## C. Batch 1

- [ ] All 6 files from `batch_1_manifest.json` uploaded — **and nothing else**.
- [ ] Every file's description pasted from the manifest/description sheet (spot-check two files by reopening their description fields).
- [ ] No `.usage.md` file uploaded by mistake (search the Solaria document list for "usage").
- [ ] `acceptance_tests_AFTER_BATCH_1.md` run in a fresh session: **≥7/8, zero critical fails** — results logged with date + tester name.

## D. Batch 2 (only after C is fully checked)

- [ ] Batch-1 gate passed and logged (see C).
- [ ] 5 files uploaded in manifest order (catalog LAST), descriptions pasted.
- [ ] Catalog retrieval test (manifest item 5, incl. the negative-existence question) passed.
- [ ] `acceptance_tests_AFTER_BATCH_2.md`: **≥8/10, zero critical fails** — logged.

## E. Batch 3 (only after D is fully checked)

- [ ] Batch-2 gate passed and logged.
- [ ] **AI governance reviewed:** Deloitte risk/legal has reviewed `modules/ai_native_odoo_19/governance_and_validation.md` and approved internal use — reviewer name + date recorded. (Without this: upload items 1–16 only; AI items 17–18 wait.)
- [ ] 18 files (or 16 pending AI review) uploaded with descriptions per the manifest.
- [ ] `acceptance_tests_AFTER_BATCH_3.md`: **≥10/12** — logged.
- [ ] `red_team_tests.md`: **zero critical failures** — transcripts saved as regression baseline.
- [ ] Rubric average ≥4.0 on the Batch-3 suite; no hard-floor breaches (C3/C6).

## F. Release to consultants (only after E)

- [ ] Total uploaded documents ≤ 30 (count the Solaria document list).
- [ ] **Client-facing caveats understood:** the release announcement to consultants states, in writing: answers are advisory drafts; edition and validation caveats must survive into deliverables; licensing/pricing always via commercial channels.
- [ ] **Live Odoo validation rule communicated:** every load-bearing claim gets validated in a live Odoo 19.0 database before client commitments — named in the announcement.
- [ ] Question/upload log started (owner named) — it drives all future expansion.
- [ ] Stability re-run scheduled: full Batch-3 suite again in a fresh session within 7 days.

## G. Standing rules (review monthly)

- [ ] No expansion without a fired trigger (roadmap) + retrieval-quality checklist pass.
- [ ] Test suites and operator documents still NOT uploaded.
- [ ] Pack version unchanged since last check — or re-gating done after refresh.

---

**Final gate:** Sections A–F all checked → **GO**. Any critical acceptance/red-team fail at any point → **NO-GO**: stop, fix, re-run that gate; never "continue and fix later".
