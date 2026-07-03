# V3 Pre-Upload Readiness Audit

| Attribute | Value |
|---|---|
| Document type | Context Manifest / Knowledge Base Rules (V3 gate audit) |
| Question | Is the V2 pack safe and effective to upload to Solaria — and what exactly goes first? |
| Method | Review of all upload-relevant V2 documents + repo hygiene check + consistency cross-checks (upload_ready ↔ 90 ↔ 91 ↔ 93) |
| Date | 2026-07-03 (V3, branch `solaria-v3-preupload-gate`) |

## 1. Is V2 ready for Solaria upload?
**Yes — conditional go.** Content quality, evidence discipline, descriptions and per-batch testing all exist and are consistent. The conditions (unchanged from QC V2.4, now enforced via the go/no-go checklist): risk/legal review of the AI governance doc, operator dry-run of the kit, and live-retrieval confirmation via the Batch-1 acceptance gate before any further upload.

## 2. What should be uploaded first?
Global context (`final_upload_package/global_context_FINAL.txt`) + **Batch 1 = exactly 6 governance documents** (manifest: `final_upload_package/batch_1_manifest.json`). Nothing else until the Batch-1 acceptance tests pass.

## 3. What should NOT be uploaded initially?
Unchanged from V2, now consolidated in `final_upload_package/do_not_upload_manifest.md`: all 283 `.usage.md` companions, `index.html`, quality/compliance/audit reports (96/97/98/99), operator documents (upload_ready + final_upload_package themselves), all evidence files (models.json, views/security/workflow summaries) and module standard_vs_custom files until demand triggers, source folders/local settings (never — also git-ignored).

## 4. Contradictions found between upload_ready, 90, 91 and 93 — and resolutions

| # | Inconsistency | Resolution applied in V3 |
|---|---|---|
| C1 | V2 `upload_ready/batch_3_functional_summary_selection.md` lists **14** summaries; V3's better selection is **18 files** (adds `web_studio`, `base_automation` — the ladder's rungs 3–4 — and the AI pack's functional summary + governance doc) | `final_upload_package/batch_3_manifest.json` is now authoritative; supersession notes added to the V2 kit files |
| C2 | `90_solaria_upload_recommendations.md` still frames a 5-batch plan with README+standard_vs_custom in Batch 3 | Kept as the long-range overview; supersession note added: execution follows `final_upload_package/` |
| C3 | `91_solaria_global_context_prompt.txt` vs the refined V3 prompt | `global_context_FINAL.txt` is the paste source; 91 retained as the documented long-form basis; registry descriptions updated to say so |
| C4 | `upload_ready/solaria_acceptance_test_script.md` (12 mixed questions) vs V3's deeper per-batch suites (8+10+12 + 15 red-team) | Script retained as the operator's fast subset; the V3 suites are the formal gate — relationship stated in both |
| No other contradictions found | Descriptions in 93, kit checklists and registry are mutually consistent | — |

## 5. Batch 1 size verdict: **just right (6 documents).**
It teaches HOW to reason: behaviour rules + manifest + type templates + edition map + ladder + registry. Removing any one breaks a tested behaviour (edition discipline needs 03; customization discipline needs 05; self-description needs the registry). Adding more would mix "how to reason" with "what to know" and muddy the gate.

## 6. Batch 2 size verdict: **just right in composition (5 files), with one managed risk.**
It teaches WHERE to look. Risk: `01_global_module_catalog.json` (~1.3 MB) is the single heaviest retrieval object. Mitigation now encoded in the manifest: it uploads **last within Batch 2**, has a dedicated retrieval test (obscure-module lookup), and a documented fallback (rely on domain map + module packs; defer the catalog) if it degrades retrieval.

## 7. Batch 3 verdict: **expand from 14 to 18 files — and no further.**
The V3 additions close the two most consequential gaps in first-week conversations: the customization ladder's practical rungs (`web_studio`, `base_automation` summaries) and AI credibility (`ai_native_odoo_19` functional summary + governance doc as one unit — governance must never lag capability). Total first-upload footprint: 6+5+18 = **29 documents — inside the ≤~30 volume guardrail**. Anything more belongs to demand-driven expansion (roadmap).

## 8. Are the AI documents safe enough for internal use?
**Yes for internal use**, with the pending risk/legal review as a go/no-go item. Verified: the AI pack enforces the four-way separation — (1) source-verified native modules (inventory JSON), (2) Deloitte strategic concepts (labeled, never product), (3) custom AI implementation opportunities (ladder-scoped), (4) runtime/quality validation always required — plus safe-phrasing patterns with explicit ✅/❌ examples and EU-AI-Act flags for the high-risk recruitment domain.

## 9. Global context prompt verdict: **good but improvable — refined in V3.**
The V2 prompt (91) is accurate and complete but long-form. `global_context_FINAL.txt` tightens it: more imperative/agent-like, explicit instruction to **route via document descriptions and hierarchy**, the four-way AI separation stated compactly, unchanged strictness (19.0-only, standard-before-custom, edition discipline, existence-vs-behaviour, no code-assistant mode). 91 remains as the documented basis.

## 10. Specific fixes applied in V3
1. **Repo hygiene:** removed five zero-byte junk files from the repo root (`50k€`, `External`, `Governance`, `N`, `threshold` — accidental shell-redirect artifacts that were staged for commit); verified `.gitignore` covers sources/secrets/archives.
2. `final_upload_package/` created: operator README, FINAL global context, exact Batch 1/2/3 manifests (JSON, with per-file descriptions, tests, pass/fail), Batch-4 later-evidence manifest grouped by use case, do-not-upload manifest, per-batch description sheets, per-batch acceptance suites (8/10/12), 15-question red-team suite, 0–5 answer rubric, 10-question simulated benchmark, context-overload strategy, future-upload roadmap, human go/no-go checklist.
3. Supersession pointers added to `upload_ready/` kit files, 90 and 93.
4. Registry, usage companions, index and compliance report regenerated to include all V3 documents.

## 11. Remaining go/no-go concerns (tracked in the checklist)
1. **Live retrieval behavior is unknowable pre-upload** — the Batch-1 gate is the control; do not proceed past a failed gate.
2. **Catalog JSON size** — managed per §6; watch the dedicated retrieval test.
3. **AI risk/legal review** still pending — required before AI documents (Batch 3 items 17–18) go up; Batches 1–2 are not blocked by it.
4. **Operator dry-run** — the checklist's first section forces it.
5. Repo is local-only; if pushed to a remote, the private-repository check in the go/no-go list must pass first.
