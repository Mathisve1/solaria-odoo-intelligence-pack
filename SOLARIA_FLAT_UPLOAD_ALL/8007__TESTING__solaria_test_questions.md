# Solaria Test Questions — Validate the Odoo Intelligence Pack After Upload

| Attribute | Value |
|---|---|
| Document type | Context Manifest / Knowledge Base Rules (validation set) |
| Authority level | High for acceptance testing of the configured Solaria |
| Usage | Run per upload batch (see `90_solaria_upload_recommendations.md` §5). For each question check: expected pattern present? warning signs absent? |

## 1. "Can Odoo 19.0 handle quote-to-cash standard?"
- **Expected:** Yes for the core arc, structured answer: `crm`→`sale` (quote, portal sign/pay — Community) → delivery (`stock`) → invoice (`account`); edition notes (advanced reporting/dunning = Enterprise); validation caveat for behavior details; demo angle offered.
- **Should use:** 04 domain map, sale/account/stock functional summaries, 03 map.
- **Warning signs:** no edition distinction; claiming statutory reporting is Community; code snippets; no validation language.

## 2. "What is Community vs Enterprise in Sales?"
- **Expected:** Community: quotations, templates, pricelists, portal signature/payment, down payments. Enterprise: `sale_enterprise` reporting, subscriptions, rental, marketplaces, commissions, external tax; licensing-validation caveat.
- **Should use:** 03 map §Sales, sale functional summary.
- **Warning signs:** vague "Enterprise has more features"; inventing modules; mixing 17/18 version claims.

## 3. "Should we customize an approval flow or use standard Odoo?"
- **Expected:** Challenge first + ladder walk: native per-app steps (e.g., purchase 'to approve') → configuration → **Approvals app (Enterprise)** as designated answer → automation for advisory alerts → custom only for DoA-grade matrices; asks for the approval matrix; edition note.
- **Should use:** 05 framework, approvals pack, purchase pack.
- **Warning signs:** jumping to custom; presenting automation-rule blocking as robust; no challenge questions.

## 4. "How would you demo Inventory for a retail client?"
- **Expected:** Storyline (receipt→putaway→pick→delivery), retail flavor (POS link, barcode = Enterprise label), rehearsal rule, menu-path realism, edition labeling.
- **Should use:** demo playbook, stock functional summary + views summary, point_of_sale pack.
- **Warning signs:** feature list instead of story; demoing Enterprise scanning without label; invented UI details.

## 5. "How would you approach CV screening in Odoo Recruitment?"
- **Expected:** Native: CV OCR (`hr_recruitment_extract`, E) + `hr_recruitment_ai` (E) with "validate live"; governance front-and-center (EU AI Act high-risk, human decision, transparency); Community fallback = manual pipeline; no auto-rejection.
- **Should use:** hr_recruitment pack, 06 AI map, AI strategy playbook.
- **Warning signs:** promising ranking accuracy; ignoring compliance; presenting AI as Community.

## 6. "What should Deloitte recommend when a client wants heavy customization?"
- **Expected:** Standard-first challenge protocol: batch challenge session, upgrade-tax quantification, phase-2 parking lot, red flags list; empathy + evidence method (reproduce need in demo).
- **Should use:** 05 framework, fit-gap methodology.
- **Warning signs:** "customization is fine, Odoo is flexible"; no method.

## 7. "What is standard vs Studio vs custom for a new field and workflow?"
- **Expected:** Field = configuration/Studio (E, governed) — with the Community caveat (Studio unavailable → small module); workflow = stages/automation first; algorithms never in Studio; governance registry mention.
- **Should use:** 05 framework (§Studio governance), base/mail packs for automation vocabulary.
- **Warning signs:** recommending Studio to Community clients; no governance mention.

## 8. "How can AI live inside Odoo without breaking governance?"
- **Expected:** Native inventory (E-only, pgvector prerequisite, IAP metering) vs Deloitte concepts clearly separated; register/human-in-the-loop/access-leakage testing/AI Act; deterministic domains excluded (posting/tax).
- **Should use:** 06 AI map, AI strategy playbook.
- **Warning signs:** concept features presented as shipping; no data-boundary mention.

## 9. "Which modules are relevant for a field service company?"
- **Expected:** `industry_fsm` (+worksheets/sale/stock siblings) as Enterprise core; foundations `project`, `hr_timesheet`, `stock`, `sale`, `helpdesk` intake, `planning`; edition gate stated; validation on mobile/offline.
- **Should use:** 04 map, industry_fsm pack, catalog.
- **Warning signs:** suggesting Community-only FSM; inventing an "fsm" Community app.

## 10. "Which documents did you use and why?"
- **Expected:** Names actual pack documents with their roles (hierarchy: behaviour → maps → summaries → evidence); explains routing logic.
- **Should use:** manifest (00), registry.
- **Warning signs:** cannot cite; invents document names.

## 11. "What does Enterprise add on top of Community in Accounting?"
- **Expected:** The precise split: `account` = Invoicing (C); `account_accountant`, `account_reports` (+ ~114 country reporting packs), assets, budgets, follow-ups, SEPA/batch, OCR, AI drafts (E); "the edition line runs through finance" advisory point.
- **Should use:** 03 map §Accounting, account pack.
- **Warning signs:** claiming bank reco workbench or statutory reports are Community.

## 12. "Which Odoo modules are relevant for a manufacturing client?"
- **Expected:** Core `mrp`+`stock`+`purchase`+`product` (C); Enterprise uplift `mrp_workorder`, `mrp_mps`, `mrp_plm`, `quality`, `iot`, barcode; APS honesty (no finite scheduling promise); BoM-data watch-out.
- **Should use:** 04 map, mrp pack.
- **Warning signs:** promising APS-grade scheduling; no edition split.

## 13. "How should Deloitte structure an Odoo implementation roadmap?"
- **Expected:** Phased with gates (discovery→fit-gap→prototype→configure→custom-only-if-needed→integrations→migration→security→testing→training→go-live→hypercare→continuous improvement); customization gate G1; upgrade governance.
- **Should use:** roadmap playbook.
- **Warning signs:** generic waterfall with no gates; missing migration/security phases.

## 14. "How would you turn 'we need customer-specific prices visible online' into a solution?"
- **Expected:** Requirement-to-solution method: normalize → Sales/eCommerce domain → pricelists + `website_sale` B2B visibility (C) → FIT-CONF verdict with demo validation step; assumptions captured.
- **Should use:** mapping guide, website_sale pack.
- **Warning signs:** proposing custom portal development first.

## 15. "When should Deloitte recommend external integration instead of Odoo customization?"
- **Expected:** Product-category test (APS, WMS-grade, hyperscale commerce, enterprise BI, payroll bureaus, banking, QES); system-of-record and interface-contract principles; prefer shipped connectors first (catalog evidence).
- **Should use:** 05 framework §7, relevant module standard_vs_custom docs.
- **Warning signs:** "build everything in Odoo"; or reflexive best-of-breed without the ladder.

## General warning signs (any question)
Version drift (non-19.0 claims) · invented modules/prices · missing edition tags · missing validation caveats on behavior claims · code-first answers · concept-vs-capability blurring in AI topics.
