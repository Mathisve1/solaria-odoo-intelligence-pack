# V2 Initial Audit Report — Deloitte Solaria Odoo Intelligence Pack

| Attribute | Value |
|---|---|
| Document type | Context Manifest / Knowledge Base Rules (V2 audit) |
| Audit scope | Full V1 pack (417 files, 209 documents) — governance docs read in full; module packs sampled + machine-checked |
| Audit method | Manual review + scripted cross-checks against the extracted 19.0 source metadata (dependency rows vs manifests, module-name references vs catalog, security-table content vs security XML) |
| Date | 2026-07-02 (same-day V2 of the V1 build) |

## 1. What is already strong in V1 (verified — do not rewrite)

1. **Governance architecture**: role rules, context manifest, document-type templates, registry and per-file `.usage.md` companions form a coherent authority hierarchy; conflict and uncertainty rules are explicit and mutually consistent.
2. **Evidence layer**: catalog (all 1,422 modules with per-entry confidence), dependency map (zero unresolved deps), and per-module models/views/security/workflow extractions are genuinely source-derived, code-free, and correctly scoped to 19.0.
3. **Edition discipline**: the Community-vs-Enterprise map is manifest-grounded and consistently echoed in module docs; the Enterprise-as-add-ons-layer fact is used correctly throughout.
4. **AI honesty**: 06 separates the source-verified native AI inventory from Deloitte concepts; playbooks repeat the separation.
5. **Playbooks**: consulting-grade, practical, correctly defer product claims to evidence documents.
6. **File hygiene**: 100% supported extensions, no raw code, no secrets (compliance report PASS).

## 2. What is weak, generic, or wrong (findings — each with a planned/applied V2 action)

| # | Finding | Severity | Files affected | V2 action |
|---|---|---|---|---|
| F1 | **Dependency rows approximated** in ~16 functional summaries: they list "conceptual" dependencies instead of actual manifest `depends` (e.g., `sale` row omitted `account_payment`; `industry_fsm` listed `project`/`hr_timesheet` instead of the actual `project_enterprise`/`timesheet_grid`/`base_geolocalize`; `purchase` listed `product` which is transitive). This is an evidence-discipline breach in an otherwise evidence-driven pack. | High | modules/*/functional_summary.md (16 files) | Replace rows with exact manifest depends (+ clarifying parenthetical where useful) |
| F2 | **One uncataloged module referenced**: `sale_blanket_order` (an ecosystem/OCA name, absent from the 19.0 catalog) named in the sale functional summary — violates the pack's own "never cite uncataloged modules" rule. | High | modules/sale/functional_summary.md | Rewrite the sentence around `purchase_requisition` (cataloged, Community) and honest validation language |
| F3 | **Security summaries misrepresent group-modification records**: `<record model="res.groups">` entries that *extend existing groups* (e.g., adding implied rights to `base.group_system`) were rendered as unnamed "groups defined by this module" (rows with `—`). Misleading evidence. | High | 11+ modules/*/security_summary.md | Generator logic fixed; affected security summaries regenerated with an explicit "modifies existing groups" section |
| F4 | **Generated evidence docs end with identical generic sections** ("Implementation implications (generic)", "UX/demo observations (generic)"). Honest (labeled generic) but low-value repetition. | Low | all generated views/workflow docs | Keep (labeled, harmless); noted as acceptable trade-off — rewriting 26×2 closings adds words, not value |
| F5 | **`purchase` functional summary capabilities section thinner** than sibling Tier-1 docs. | Medium | modules/purchase/functional_summary.md | Strengthen capabilities + advisory content |
| F6 | **Finance depth gap**: `account_accountant`/`account_reports` only summarized inside the `account` pack; most finance fit-gap questions land exactly there. | High | (missing packs) | New deep packs (Phase 6) |
| F7 | **AI evidence exists only inside 06** (a strategy-flavored doc); no dedicated evidence pack for the native AI layer. | Medium | (missing pack) | New `modules/ai_native_odoo_19/` consolidated evidence pack |
| F8 | **Platform gap**: `web_studio` and `base_automation` carry the standard-vs-custom ladder's rungs 3–4 but have no packs of their own. | Medium | (missing packs) | New packs (Phase 6) |
| F9 | **Upload instructions assume a knowledgeable operator**: 90/93 are complete but not a step-by-step kit (no per-batch acceptance criteria, no "what if Solaria answers generically" troubleshooting). | Medium | 90, 93 | New `upload_ready/` kit (Phase 3); 90/93 updated to point at it |
| F10 | **No audience orientation documents** (executives / functional consultants) explaining what this Solaria configuration is for and how to use it well. | Medium | (missing) | New docs 10 and 11 (Phase 7) |
| F11 | Minor **UI-level phrasings without explicit caveat** in a few narratives (e.g., hr "org-chart UX", views notes describing screens). Covered by module-level confidence rows but individually uncaveated. | Low | few module docs | Claims audit (96) spot-fixes the strongest instances; module-level caveats remain the primary control |
| F12 | **Authority-level vocabulary** varies ("Highest", "High", "Medium-high", "High for X") across docs/registry. Not contradictory, but not a controlled vocabulary. | Low | registry + headers | Accepted for V2 (meaningful, human-readable); normalization deferred — full renaming pass = churn risk without retrieval benefit |

## 3. Documents that need improvement (V2 worklist)
- 16 functional summaries: dependency-row corrections (F1); sale sentence fix (F2); purchase strengthening (F5).
- All affected security summaries: regeneration with corrected group logic (F3).
- Behaviour docs (00 role rules, 00 manifest, 91 prompt): targeted sharpening only — add an evidence-phrase vocabulary, a self-description rule, and a generic-answer kill-switch; no wholesale rewrite.
- 90/93: add pointers to the new upload_ready kit; 07/06: register the new packs.

## 4. Documents that should NOT be touched
Playbooks (all 7) · 03 Community-vs-Enterprise map · 04 domain map (only additive edits if new packs demand) · 05 framework · 01 catalog / 02 dependency map (generated, correct) · 92 test questions (extended, not rewritten, by the new acceptance script) · most module narratives outside the worklist · index.html (regenerated mechanically at the end).

## 5. Inconsistencies found (naming, origin, authority, priorities, descriptions)
- Source_origin tagging: **consistent** (machine-checked catalog vs module docs on sampled modules).
- Upload priorities: consistent between registry, 90 and 93.
- F12 vocabulary variance (see above) — accepted.
- Registry vs document content: descriptions match; entry_count meta accurate (209). No orphan registry entries; no unregistered documents.

## 6. Overclaiming risks identified
- F1/F2/F3 above (fixed in V2).
- Watchlist phrasings that remain by design but rely on their caveats: POS offline envelope, portal self-service depth (subscriptions), OCR/AI output quality, SLA timer semantics. Verified each carries "validate live" language in place (spot-checked in 96).

## 7. Missing disclaimers
None systemic — the behaviour docs impose caveats globally. Individual gaps addressed via 96 fixes (F11). One addition made: the evidence-phrase vocabulary in the role rules now gives consultants the exact caveat sentences to reuse.

## 8. Formatting / readability issues
- Minor: em-dash-heavy tables render awkwardly in some viewers; acceptable.
- Generated menu tables for large modules truncate at 45 rows with an explicit omission note — correct behavior, keep.
- No broken internal references found (registry paths spot-checked).

## 9. Recommended V2 changes (executed in this iteration)
1. Evidence fixes: F1, F2, F3 (highest priority — they defend the pack's core credibility).
2. `upload_ready/` operator kit (F9).
3. New packs: finance depth (`account_accountant`, `account_reports`), platform (`web_studio`, `base_automation`, `spreadsheet_edition`), supply-chain depth (`stock_barcode`, `mrp_workorder`, `quality`), consolidated `ai_native_odoo_19` evidence pack (F6/F7/F8).
4. Behaviour-doc sharpening (targeted).
5. Orientation docs 10/11 (F10).
6. Claims audit (96), module improvement report (97), QC/compliance/release-notes/self-check updates.

## 10. Priority ranking
1. **P1 — credibility**: F1, F2, F3 fixes (evidence discipline).
2. **P2 — usability**: upload_ready kit + behaviour sharpening.
3. **P3 — coverage**: new module packs (finance first, then platform, supply chain, AI pack).
4. **P4 — audience**: orientation docs.
5. **P5 — governance**: audit/improvement/QC/release-notes/self-check reports.
