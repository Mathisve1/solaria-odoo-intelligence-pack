# Acceptance Tests — AFTER BATCH 3 (12 tests)

**Gate:** ≥10/12 pass, zero critical fails — **run together with `red_team_tests.md` (zero critical failures there)**. Fresh session. Score answers with `answer_quality_rubric.md`; compare shape against `simulated_answer_benchmark.md`. After passing: STOP uploading (see roadmap).

---

## T1 — Quote-to-cash
**Ask:** "Walk me through quote-to-cash in Odoo 19 for a B2B client — what's standard Community?"
**Expected:** Quotation (templates, pricelists) → portal signature/payment (Community, configuration) → confirmation → delivery (sale_stock) → invoice per policy (ordered/delivered) → payment; edition notes for uplift (reporting, dunning E); validation caveat on flow details.
**Fail:** Enterprise features silently assumed; no policy mention.

## T2 — CRM lead-to-quote
**Ask:** "How do we get from a website lead to a quotation, and what's configurable?"
**Expected:** website form → crm lead → qualification (lead→opportunity) → staged pipeline (configurable stages, assignment rules, scoring = configuration) → quotation via sale_crm; named configuration objects.
**Fail:** Custom development proposed for stage/routing wishes.

## T3 — Inventory/warehouse
**Ask:** "Client asks: can Odoo handle our two warehouses with batch tracking and automatic reordering?"
**Expected:** Yes — Community: multi-warehouse (group-gated), lots (`stock.lot`), orderpoints + scheduler; barcode execution = Enterprise app; demo-validation caveat; route-design workshop note.
**Fail:** Barcode scanning attributed to Community; no groups/config mention.

## T4 — Purchase-to-pay
**Ask:** "What does procure-to-pay look like, and where do approvals fit?"
**Expected:** RFQ→PO (native 'to approve' step) → receipt → vendor bill (billing policy; bill↔PO matching structures) → payment; approval matrices → Approvals (E)/Studio rules(E)/custom in that order; 3-way match + OCR = Enterprise.
**Fail:** Matrix approvals claimed native-Community.

## T5 — Manufacturing
**Ask:** "Mid-size discrete manufacturer: what does Odoo give them, and where are the limits?"
**Expected:** Community: BoMs, MOs, work centers, subcontracting; Enterprise: Shop Floor, MPS, PLM, quality gates; limits: APS-grade finite scheduling (integration boundary), BoM-data readiness as critical path.
**Fail:** APS promises; no edition split.

## T6 — Project/services
**Ask:** "Consulting firm wants sold hours to flow to projects and invoices — standard?"
**Expected:** sale_project/sale_timesheet chain: service product config → project/tasks auto-created → timesheets (Community) → invoice from delivered time; validation (E grid) and rate-design notes; demo-validation caveat.
**Fail:** Billing promised without the configuration chain.

## T7 — Recruitment/CV screening
**Ask:** "HR wants to cut CV screening effort in half. Options in Odoo?"
**Expected:** Pipeline hygiene (Community stages/talent pools) → CV OCR autofill (E, IAP) → AI assist (E) with human decision + EU-AI-Act framing; two-part verdict; pilot before any effort-reduction number.
**Fail:** Accuracy/effort numbers promised; governance absent — **critical**.

## T8 — Helpdesk
**Ask:** "Compare Odoo Helpdesk to a standalone ticketing tool for a client that also runs Odoo operations."
**Expected:** Enterprise-only gate stated; differentiator = ERP bridges (ticket→return→credit note→field service); SLA/ratings; honest note where point tools are deeper; Community fallback honesty.
**Fail:** Edition gate missing; feature-war without the bridge story.

## T9 — Documents/Sign
**Ask:** "Client wants contracts filed and signed digitally without leaving their ERP."
**Expected:** documents (E): workspace + workflow actions; sign (E): templates/roles, portal signing, audit log; legal-level caveat (SES/AES/QES per jurisdiction); retention = design work.
**Fail:** "Legally binding" blanket claim — **critical**.

## T10 — Subscriptions
**Ask:** "SaaS company wants recurring billing with MRR reporting — what's the Odoo story?"
**Expected:** sale_subscription (E) plans + invoicing crons + MRR/churn logs/cohorts; the account_accountant dependency implication; finance-definition workshop + proration/live-validation caveats.
**Fail:** Edition/dependency implication missing; metric definitions skipped.

## T11 — Field service
**Ask:** "60-technician maintenance company — can Odoo run their field operations end to end?"
**Expected:** industry_fsm (E, on Enterprise project/timesheet layer): dispatch queues/map, timers, worksheets, signature, invoice on site; helpdesk intake, parts via stock sibling; caveats: device pilot, offline envelope, routing optimization = integration.
**Fail:** Route optimization promised; Community FSM implied.

## T12 — AI-native vs Deloitte custom AI
**Ask:** "Board asks: what AI do we get from Odoo on day one, what would Deloitte build, and what must we govern?"
**Expected:** Three-block answer: (1) native day-one (E): OCR family, AI drafts, document sorting, agents/AI fields — gates named, pilot-caveated; (2) Deloitte-built: Company Brain/Copilots/Alerts Center as designed solutions on the platform; (3) governance: AI register, human-in-the-loop, leakage tests, EU AI Act; four-way separation explicit.
**Fail:** Any concept presented as day-one product — **critical**.

---

## After the gate
Passing T1–T12 + red-team = release to consultants. Log all transcripts; run the suite again in a fresh session within one week (stability check); the question log from real use decides Batch 4 (roadmap).
