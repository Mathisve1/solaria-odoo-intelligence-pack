# Batch 3 — First Functional-Summary Selection (14 modules, summaries only)

**Goal:** module depth where client conversations actually happen — **functional summaries only**. Do NOT upload models.json / views / security / workflow / standard_vs_custom files yet (see `do_not_upload_initially.md`); they follow on demand once retrieval quality is proven.
**Prerequisite:** Batch 2 passed.

**Description template** (paste per file, replacing `<module>` and `<edition>`):
> Primary business-level reference for the Odoo 19.0 `<module>` module (<edition>). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.

| # | File | Edition | Why it matters | Spot-test question (ask after upload) |
|---|---|---|---|---|
| 1 | `modules/sale/functional_summary.md` | Community | Quote-to-cash backbone; most-demoed app | "Can customers sign and pay quotes online in Community?" → yes, configuration, portal flow named |
| 2 | `modules/account/functional_summary.md` | Community | Finance spine; anchors the edition decision | "Is Odoo Invoicing enough for our finance team?" → close/compliance checklist logic, three-layer story |
| 3 | `modules/crm/functional_summary.md` | Community | Front of funnel; first app in journeys | "Can leads be scored and auto-assigned?" → native scoring + assignment cron, configuration |
| 4 | `modules/stock/functional_summary.md` | Community | Fulfillment backbone; logistics deals | "Multi-warehouse with lot traceability — standard?" → yes with groups/routes, demo angle |
| 5 | `modules/purchase/functional_summary.md` | Community | Procure-to-pay; approval conversations | "Multi-level PO approvals?" → native single step vs Approvals (E) vs custom, precisely |
| 6 | `modules/mrp/functional_summary.md` | Community | Manufacturing deals; digital-factory story | "Do we get finite scheduling?" → honest availability-based answer, APS boundary |
| 7 | `modules/project/functional_summary.md` | Community | Services backbone | "Milestone billing possible?" → with sale integration, stages/state design note |
| 8 | `modules/hr_recruitment/functional_summary.md` | Community | Hiring pipeline + AI-adjacent questions | "Can CVs be parsed automatically?" → Enterprise OCR + AI assist with governance caveats |
| 9 | `modules/helpdesk/functional_summary.md` | Enterprise | Ticketing; frequent SaaS-replacement deal | "SLA per customer tier?" → SLA policies + edition gate + ERP-bridge story |
| 10 | `modules/documents/functional_summary.md` | Enterprise | DMS + AP-inbox differentiator | "Replace SharePoint?" → honest boundary, workflow-action story |
| 11 | `modules/sign/functional_summary.md` | Enterprise | Quick-win e-signature story | "Is Odoo Sign legally valid?" → signature-level nuance, legal validation required |
| 12 | `modules/sale_subscription/functional_summary.md` | Enterprise | Recurring revenue; pulls Enterprise finance | "MRR and churn out of the box?" → structures yes, finance-definition workshop caveat |
| 13 | `modules/industry_fsm/functional_summary.md` | Enterprise | Field service; strong mobile demo | "Invoice on site after a job?" → native flagship flow, device pilot caveat |
| 14 | `modules/website_sale/functional_summary.md` | Community | eCommerce; the no-integration story | "B2B customer-specific prices online?" → pricelists + login visibility, FIT-CONF |

## Upload order
As numbered (Tier-1 Community core first, Enterprise apps after) — if interrupted, the most-asked modules are already in.

## Expected capability improvement
Module-specific fit-gap reasoning, demo angles and watch-outs; correct handling of "can Odoo do X in module Y" with edition + validation language; honest deferral on the 20 deep modules not yet uploaded (it should offer catalog-level answers and say the summary isn't loaded).

## Pass/fail
Run the spot-test question per file at upload time (10 seconds each), then the full 12-question script (`solaria_acceptance_test_script.md`). PASS bar: named modules with editions, named configuration objects, validation caveats present, no invented features. Any module failing its spot-test: check description, re-ask naming the document; persistent failure → log for the maintainer.
