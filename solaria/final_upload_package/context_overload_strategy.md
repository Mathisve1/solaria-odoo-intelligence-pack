# Context Overload Strategy — Keeping Solaria Sharp

| Attribute | Value |
|---|---|
| Principle | Retrieval quality beats corpus size. 29 well-described documents that route cleanly outperform 500 files that compete for attention. |
| Hard numbers | First upload: **29 documents max** (Batches 1–3). Expansion steps: **≤10 files**, each followed by spot re-tests. Practical ceiling until proven otherwise: **~60 documents**. |

## Why not everything at once
1. **Dilution:** similar evidence files (34 models.json, 34 security summaries…) make every retrieval a lottery between near-duplicates; the narrative layer loses existence-of-doubt cases it should win.
2. **Debuggability:** with staged uploads, a failed test points at the last batch; a bulk upload cannot be rolled back intelligently.
3. **Test integrity:** suites must stay out of the corpus (see do-not-upload manifest) — bulk habits break this.
4. **Signal capture:** demand-driven expansion turns real consultant questions into the iteration roadmap; bulk uploading destroys that measurement.

## Signs Solaria has TOO MUCH context
- Answers cite tangential documents (a workflow summary for a business-value question).
- Evidence/narrative role confusion (quoting models.json for "what is this module for").
- Slower, padded answers stitching many sources; rubric C10 (clarity) and C5 (evidence awareness) trend down after an expansion.
- Existence questions answered from prose instead of the catalog.
**Response:** remove the most recent additions (they're logged per batch), re-run the nearest suite, re-add selectively.

## Signs Solaria has TOO LITTLE context
- Honest-but-empty answers: "the functional summary for X is not uploaded" on questions that matter weekly.
- Catalog-level answers where module depth is repeatedly needed.
- Consultants routinely asking about modules/domains outside the 18 Batch-3 summaries.
**Response:** that's a trigger firing — expand per the roadmap/Batch-4 manifest, ≤10 files.

## When to add what
| Addition | Trigger |
|---|---|
| Module functional summaries (remaining 18) | Module appears in real questions ≥2 times/week; finance pair (account_accountant+reports) as a pair |
| Evidence files (models/views/security/workflow) | Named activity starts (migration mapping, role design, demo build) or field-level questions recur — per module, per file type (Batch-4 manifest) |
| Playbooks | Methodology questions recur (how to run fit-gap / structure demos / build roadmaps) |
| AI inventory JSON + AI standard_vs_custom | AI existence disputes or build-vs-buy scoping sessions |

## How to keep context maintainable
- **One inventory:** log every uploaded file + date + trigger in a simple upload log (extend the acceptance-test log).
- **Refresh discipline:** when the pack versions (V4+), replace changed files rather than adding duplicates; re-run the nearest suite.
- **Deletion courage:** files whose trigger disappeared (workstream ended) can come out again — context is a garden, not an archive.
- **Description hygiene:** never upload a file without its exact description; never edit descriptions ad hoc — they come from the manifests/93.

## Retrieval-quality checklist (run after EVERY expansion)
1. Ask one existence question (obscure module) → catalog cited? 
2. Ask one meaning question (module purpose) → functional summary cited, not evidence files?
3. Ask one customization question → framework 05 + ladder present?
4. Ask one AI question → four-way separation intact?
5. Ask "which documents did you use?" → correct, real citations?
6. Rubric-score one full answer → C5/C10 not degraded vs baseline?
All six clean → expansion accepted. Any dirty → remove the expansion, retest, retry smaller.

## Using retrieval tests to choose the NEXT batch
Keep a question log (who asked what, which document answered, what was missing). Weekly review: the most frequent "missing document" IS the next upload; anything never missed stays out. This converts context management from taste into measurement.
