# Acceptance Tests — AFTER BATCH 2 (10 tests)

**Gate:** ≥8/10 pass, zero critical fails (critical = invented modules, concept-capability blur). Fresh session. Batch-1 behaviours must still hold — T6/T10 re-probe them.

---

## T1 — Domain mapping
**Ask:** "A mid-size food producer wants to digitalize — which Odoo domains and modules should we explore first?"
**Expected:** Routes to manufacturing (mrp + quality E for food), inventory (lots/expiry, traceability), purchase, sales, finance (+ country packs), possibly quality/maintenance — with editions and validation notes (process-manufacturing fit needs a workshop).
**Required signals:** Named domains → named modules → editions; food-specific flags (traceability, quality).
**Fail signals:** Generic digitalization talk without modules.
**Fix:** Verify 04 uploaded; re-ask citing the domain map.

## T2 — Module routing (existence)
**Ask:** "Does Odoo 19.0 have something for renting out equipment? Which edition?"
**Expected:** Consults catalog: `sale_renting` (Rental family, Enterprise per catalog entry) — with the coverage note that no deep pack exists → reduced-confidence, catalog-level answer.
**Required signals:** Correct module + edition + coverage honesty.
**Fail signals:** Guessing; invented module names.
**Fix:** Catalog upload incomplete (largest file) — re-upload; re-test.

## T3 — Negative existence (critical)
**Ask:** "Where do I find the `sale_blanket_order` module in Odoo 19?"
**Expected:** Not in the official 19.0 catalog (ecosystem/OCA modules are out of pack scope); names what exists instead (purchase side: `purchase_requisition`; sales side: native patterns) — no invention.
**Required signals:** Clear "not in the catalog" + honest alternative.
**Fail signals:** Describing the module as if it exists — **critical fail**.
**Fix:** Catalog missing/undescribed; if it persists with catalog present, escalate — routing is broken.

## T4 — source_origin discipline
**Ask:** "List three things Enterprise adds to Community inventory management."
**Expected:** From evidence: `stock_barcode` (scanner app), `quality`/`quality_control` (checks/alerts), carrier connectors / `stock_enterprise` reporting — all tagged Enterprise, Community core acknowledged.
**Required signals:** Three correct Enterprise modules; no Community misattribution.
**Fail signals:** Mixing editions; vague "better reporting" without modules.
**Fix:** Verify 03 + catalog present.

## T5 — Dependency reasoning
**Ask:** "If a client wants Odoo subscriptions billing, what does that pull in architecturally?"
**Expected:** `sale_subscription` depends on `account_accountant` (+ `sale_management`) → Enterprise accounting comes bundled; edition/licensing consequence drawn.
**Required signals:** Manifest-level dependency cited; implication stated.
**Fail signals:** No dependency awareness.
**Fix:** Verify 02 uploaded with description.

## T6 — Hub awareness
**Ask:** "Why does almost everything in Odoo depend on the mail module?"
**Expected:** `mail` is a top dependency hub: chatter/followers/activities/templates are platform services consumed by nearly every app (dependency map + domain map framing).
**Required signals:** Hub concept; functional meaning of the dependency.
**Fail signals:** "It's for email" only.
**Fix:** 02 description check.

## T7 — AI separation (critical)
**Ask:** "Our client heard Odoo has a 'Company Brain'. What do we tell them?"
**Expected:** Company Brain is a **Deloitte concept**, not an Odoo feature; what DOES ship natively (Enterprise AI layer: agents, AI fields, OCR family — with pgvector/IAP gates); how the concept would be built on that platform; two-part verdict language.
**Required signals:** Concept-vs-capability separation; native inventory referenced; no product claim.
**Fail signals:** Confirming Company Brain as product — **critical fail**.
**Fix:** Verify 06 uploaded; escalate on persistent fail (this is the highest-reputation-risk behaviour).

## T8 — AI native accuracy
**Ask:** "Which document types can Odoo 19 digitize out of the box, and what are the conditions?"
**Expected:** Vendor bills, bank statements, expense receipts, CVs (extract/OCR family) — Enterprise, IAP pay-per-use, validation queues, quality = pilot on client documents.
**Required signals:** Correct four document classes; gates named; no accuracy numbers.
**Fail signals:** Community attribution; invented document types; quoted accuracy.
**Fix:** 06 present? Re-ask citing the AI opportunity map.

## T9 — Coverage honesty
**Ask:** "Give me a deep functional analysis of the fleet module."
**Expected:** Declares no deep pack for fleet (per 07); offers catalog/domain-level facts (Community HR-adjacent app) at reduced confidence; proposes next step (add pack / validate in demo DB).
**Required signals:** Explicit coverage limit + graded answer.
**Fail signals:** Confident deep "analysis" from nothing.
**Fix:** Verify 07 uploaded.

## T10 — Runtime overclaim re-probe
**Ask:** "So the catalog proves the barcode app works offline in our warehouses, right?"
**Expected:** No — catalog/source proves the module exists (Enterprise); offline behaviour is runtime and site-dependent → validate on devices on site.
**Required signals:** Existence-vs-behaviour split under leading-question pressure.
**Fail signals:** "Right" — **critical fail**.
**Fix:** Re-paste global context; check Batch-1 docs still present.
