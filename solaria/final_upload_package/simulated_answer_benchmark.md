# Simulated Answer Benchmark — 10 Reference Outlines for Human Testers

**Use:** after Batch 3, ask each question in a fresh session and compare Solaria's answer to the ideal outline. It need not match word-for-word — it must match in **structure, edition tags, evidence grades and caveats**. Score with the rubric.

---

## B1. "Can Odoo 19.0 handle quote-to-cash standard?"
**Ideal outline:** Yes for the core arc, with structure: business framing (one platform, no interfaces) → modules with editions (`crm`→`sale` C incl. portal sign/pay; delivery `stock` C; invoice `account` C; payment) → invoicing-policy configuration note → Enterprise uplift labeled (reporting, dunning, full accounting) → behaviour-validation caveat → demo angle (the signature moment).
**Supporting documents:** sale/account/stock summaries, 03, 04.
**Red flags:** Enterprise silently assumed; no policy mention; no caveat.

## B2. "What does Enterprise add on top of Community in Sales?"
**Ideal outline:** Community baseline first (quotations, templates, pricelists, portal sign/pay, down payments) → Enterprise additions by name (`sale_enterprise` reporting, subscriptions, rental, marketplace connectors, commissions, external tax) → licensing-validation caveat → advisory point (business model drives the edition, not feature lust).
**Supporting:** 03 §Sales, sale summary, 02 (subscription dependency).
**Red flags:** vague "more features"; uncataloged modules; missing commercial caveat.

## B3. "Should we build a custom approval flow?"
**Ideal outline:** Challenge first (which matrix, advisory or blocking?) → ladder: native per-app steps → configuration/rights → Studio approval rules (E) → Approvals app (E) → automation (advisory) → custom only for documented DoA-grade gaps → edition tags → validation step (matrix workshop + live test).
**Supporting:** 05, purchase + web_studio summaries (+ approvals pack if uploaded).
**Red flags:** custom-first; automation sold as robust blocking; no matrix questions.

## B4. "How would you demo Odoo Inventory to a retail client?"
**Ideal outline:** Storyline, not features: receive→putaway→pick→deliver with retail flavor (POS/eCommerce stock link) → configuration reveals (routes as settings) → Enterprise uplift labeled (barcode scanning, quality) → rehearsal rule + demo-DB caveat → what to validate live (their SKUs, their flows).
**Supporting:** stock summary, 04; (demo playbook if uploaded — else note it exists).
**Red flags:** unlabeled Enterprise scanning; invented UI details; feature list without narrative.

## B5. "Can we build AI CV screening in Odoo Recruitment?"
**Ideal outline:** Four-way AI separation: native (CV OCR extract + recruitment AI assist — E, IAP, verified existence) → what's NOT native (scoring/ranking engines) → custom AI = possible with rung-5 obligations → governance dominates: EU AI Act high-risk, human decision always, transparency, pilot for quality → client-safe phrasing example.
**Supporting:** hr_recruitment summary, AI functional summary + governance doc, 06.
**Red flags:** accuracy promises; autonomous screening; governance missing — critical.

## B6. "What should Deloitte recommend when a client wants heavy customization?"
**Ideal outline:** Empathy + challenge protocol: understand outcomes → reproduce needs in standard demo (evidence beats debate) → batch-challenge session → upgrade-tax quantification → phase-2 parking lot → the few justified customs get owners/SDLC → standard-first as client protection, not rigidity.
**Supporting:** 05, role rules; (fit-gap playbook if uploaded).
**Red flags:** "Odoo is flexible, sure"; moralizing without method.

## B7. "What is the role of Studio vs custom modules?"
**Ideal outline:** Studio = Enterprise rung 3: shape (fields, views, apps, report cosmetics, action-level approval rules), governed (registry, staging, export) → custom = rung 5: brains (algorithms, validations, performance paths) with SDLC → boundary tests (shape vs logic) → Community note (no Studio → small modules) → governance as the differentiator.
**Supporting:** web_studio summary, 05, 03.
**Red flags:** algorithms in Studio; Studio for Community; no governance.

## B8. "Can AI live inside Odoo safely?"
**Ideal outline:** Yes, conditionally — native layer exists (E; gates: pgvector, IAP) → safety = engineering: human-in-the-loop defaults, AI register, leakage testing, deterministic domains excluded (posting/tax/reservation), EU AI Act mapping for high-risk uses → pilot-then-scale path → two-part verdict language throughout.
**Supporting:** AI governance doc, AI functional summary, 06.
**Red flags:** unconditional yes; concepts as product; no data-boundary mention.

## B9. "Which modules matter for a field service company?"
**Ideal outline:** Core: `industry_fsm` (E — on the Enterprise project/timesheet layer) + worksheets/sale/stock siblings → intake `helpdesk` (E), scheduling `planning` (E) → foundations `project`, timesheets, `stock`, `sale` (C) → edition gate stated plainly → validation: device pilot, offline envelope, parts logistics → optimization = integration boundary.
**Supporting:** industry_fsm + helpdesk summaries, 04, 02.
**Red flags:** Community FSM implied; routing optimization promised.

## B10. "What should we validate before telling a client 'this is standard Odoo'?"
**Ideal outline:** The validation protocol itself: (1) module exists in the 19.0 catalog with the right edition, (2) capability confirmed in the module's functional summary, (3) behaviour reproduced in a live 19.0 demo DB with client-like data, (4) edition vs client subscription (commercial), (5) country/statutory dimension with experts where relevant, (6) then say it — with the evidence grade attached. Bonus: names the evidence vocabulary.
**Supporting:** role rules, manifest, 01, 05.
**Red flags:** "if it's in the docs it's standard"; skipping the live-DB step.

---

## Tester instructions
Run all 10 after the Batch-3 gate; rubric-score each; expect structural match on ≥8/10 with zero red flags on B5/B8/B10 (the reputational trio). File transcripts with scores — this becomes the regression baseline for every future upload expansion.
