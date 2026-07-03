# Odoo 19.0 Functional Domain Map

| Attribute | Value |
|---|---|
| Document type | Functional Domain Map |
| Authority level | Medium-high for domain-level reasoning |
| Version scope | Odoo 19.0 |
| Evidence type | Manifest analysis + functional interpretation |
| Confidence | High for module-domain placement; capabilities at behavior level need validation |

How to use: route a business problem to its domain(s), identify candidate modules, then go deeper via `modules/<name>/functional_summary.md` (26 modules covered) or `01_global_module_catalog.json` (all 1,422). Edition boundaries in detail: `03_community_vs_enterprise_map.md`.

Format per domain: **Purpose · Key modules (C=Community, E=Enterprise) · Typical client questions · Demo potential · Watch-outs · AI angles · Validation questions.**

---

## CRM
- **Purpose:** Capture demand, manage pipeline, convert leads to revenue.
- **Modules:** C: `crm`, `crm_iap_mine/enrich`, `website_crm` · E: `crm_enterprise`, `voip_crm`, `social_crm`, `appointment_crm`, `marketing_automation_crm`, `ai_crm`.
- **Client questions:** Lead routing rules? Duplicate handling? Forecasting? Activity discipline? Marketing handover?
- **Demo:** Strong — kanban pipeline, activity flow, lead→quote in minutes.
- **Watch-outs:** Pipeline stage design ≠ sales methodology redesign; garbage-in lead data; over-customizing scoring early.
- **AI:** AI lead creation from email/livechat (E, native), enrichment via IAP, scoring concepts (custom).
- **Validate:** Lead volume/channels, team structure, current CRM data quality, edition budget.

## Sales
- **Purpose:** Quote-to-order: pricing, discounts, quotations, order confirmation, handoff to fulfillment/invoicing.
- **Modules:** C: `sale_management`, `sale_crm`, `sale_stock`, `sale_project`, payment providers · E: `sale_enterprise`, `sale_renting`, marketplace connectors, `partner_commission`, external tax engines.
- **Client questions:** Complex pricing? Approval on discounts? Portal quote signing? Configurable products? Margins?
- **Demo:** Excellent — online quote acceptance + payment is a signature Odoo moment.
- **Watch-outs:** Pricelist complexity explosion; discount governance; product master readiness.
- **AI:** Quote drafting assistance (concept), next-best-product (custom), anomaly alerts on discounts (automation+custom).
- **Validate:** Pricing model, order volumes, channel mix, invoicing policy (ordered vs delivered).

## Accounting / Finance
- **Purpose:** Invoicing through statutory close: AR/AP, payments, taxes, bank, reporting.
- **Modules:** C: `account` (Invoicing) · E: `account_accountant`, `account_reports`, `account_asset`, `account_budget`, `account_followup`, `account_batch_payment`, SEPA, OCR extract modules, `ai_account`, ~114 `l10n_*_reports`.
- **Client questions:** Local statutory compliance? Bank integration? Multi-company/multi-currency? Month-end close speed? Audit trail?
- **Demo:** Strong for finance leadership — bank reco, follow-ups, real-time reports (E).
- **Watch-outs:** The Community-vs-Enterprise line runs through this domain (see 03 §Accounting); chart-of-accounts and tax setup quality decides everything; migration of open items.
- **AI:** Native: vendor bill OCR, bank statement extract, AI text drafts (all E). Concept: anomaly detection, close assistant.
- **Validate:** Country list, statutory needs, bank formats, fiscal localization completeness with local experts.

## Inventory / Warehouse
- **Purpose:** Stock accuracy and flow: receipts, putaway, picking, delivery, replenishment, valuation, traceability.
- **Modules:** C: `stock`, `stock_account`, `delivery`, `product_expiry` · E: `stock_barcode`, `quality_control`, carrier connectors, `stock_enterprise`.
- **Client questions:** Multi-warehouse? Lot/serial traceability? Barcode operations? Replenishment logic? Valuation method?
- **Demo:** Very strong with a concrete scenario (receive → putaway → pick → ship with barcodes, E).
- **Watch-outs:** Route/rule complexity is powerful but easy to over-engineer; opening stock migration; valuation alignment with finance.
- **AI:** Concept: demand-driven replenishment suggestions, exception alerts. Native AI here is limited — be honest.
- **Validate:** Warehouse topology, volumes, WMS expectations vs Odoo scope, hardware (scanners).

## Purchase
- **Purpose:** Procure-to-pay: RFQs, vendor management, agreements, receipt/bill control.
- **Modules:** C: `purchase`, `purchase_stock`, `purchase_requisition` · E: `account_3way_match`, `approvals_purchase`, bill OCR with PO matching.
- **Client questions:** Approval matrix? Vendor price management? Blanket orders? Touchless invoicing?
- **Demo:** Good — reordering rule → RFQ → order → receipt → bill matching arc.
- **Watch-outs:** Approval requirements often exceed standard thresholds model → assess Approvals app (E) before custom.
- **AI:** Native: vendor bill digitization (E). Concept: supplier risk signals, price anomaly alerts.
- **Validate:** Approval matrix complexity, vendor count, direct vs indirect procurement split.

## Manufacturing
- **Purpose:** Plan-to-produce: BoMs, MOs, capacity, shop floor execution, quality, engineering change.
- **Modules:** C: `mrp`, `mrp_subcontracting`, `maintenance`, `repair` · E: `mrp_workorder`, `mrp_mps`, `mrp_plm`, `quality_mrp`, `iot`.
- **Client questions:** Routing/work centers? Scheduling? Shop-floor terminals? Traceability? Subcontracting? Costing?
- **Demo:** Excellent narrative arc (E): forecast → MPS → MO → work order tablet → quality check → cost analysis.
- **Watch-outs:** Odoo is strong mid-market MRP; APS-grade finite scheduling expectations need careful validation; BoM data quality is the real project.
- **AI:** Concept: predictive maintenance, quality-defect patterns, schedule risk alerts (custom on Odoo data).
- **Validate:** Production mode (MTO/MTS/ETO), routing depth, scheduling expectations, machine connectivity.

## Project
- **Purpose:** Deliver work: tasks, milestones, profitability, service quote→delivery.
- **Modules:** C: `project`, `sale_project`, `project_todo` · E: `project_enterprise` (Gantt/map), `project_forecast`, `documents_project`.
- **Client questions:** Billing models (fixed/T&M/milestone)? Profitability per project? Resource load? Customer visibility (portal)?
- **Demo:** Strong for services firms — sale order line → auto-created project/tasks → timesheets → invoice.
- **Watch-outs:** Stage/process proliferation across teams; analytic accounting design underpins profitability — get it right early.
- **AI:** Concept: status summarization, risk flags from activity patterns.
- **Validate:** Billing models, project types, PM maturity, reporting needs.

## HR (core)
- **Purpose:** Hire-to-retire employee administration: records, org, time off, attendance, expenses, skills.
- **Modules:** C: `hr`, `hr_holidays`, `hr_attendance`, `hr_expense`, `hr_skills`, `fleet` · E: `hr_appraisal`, `hr_contract_salary`, `documents_hr`, `frontdesk`, `hr_expense_extract`.
- **Client questions:** Country payroll? Leave rules? Expense flow? Self-service? Document compliance?
- **Demo:** Good — employee self-service, leave approval on mobile, expense photo→report (OCR is E).
- **Watch-outs:** Payroll is Enterprise + country localization — verify the client's countries exist in the catalog (`l10n_xx_hr_payroll`) before promising; works councils/GDPR on HR data.
- **AI:** Native: expense receipt OCR (E). Concept: HR policy assistant on Knowledge.
- **Validate:** Countries, headcount, collective agreements, current payroll vendor boundary.

## Recruitment
- **Purpose:** Attract-to-hire: jobs, pipeline, interviews, offers.
- **Modules:** C: `hr_recruitment`, `website_hr_recruitment` · E: `hr_recruitment_extract` (CV OCR), `hr_recruitment_ai`, `hr_referral`, `hr_contract_salary`, job-board integrations.
- **Client questions:** CV screening effort? Careers site? Offer-to-contract flow? Referrals? Time-to-hire reporting?
- **Demo:** Strong end-to-end story: careers page → application → CV auto-parse (E) → interview activities → e-signed offer (E).
- **Watch-outs:** AI screening raises fairness/compliance duties (EU AI Act awareness) — human-in-the-loop always; job-board coverage varies by market.
- **AI:** Native: CV extraction, recruitment AI module (E) — validate actual behavior live before client claims.
- **Validate:** Hiring volume, sourcing channels, assessment process, works-council constraints.

## Helpdesk (E)
- **Purpose:** Ticket intake → SLA-driven resolution → satisfaction.
- **Modules:** E: `helpdesk` (+`helpdesk_stock` returns, `helpdesk_account` credit notes, `helpdesk_timesheet`, `website_helpdesk` portal/forms, `crm_helpdesk`).
- **Client questions:** Channels (email/portal/chat)? SLAs? Knowledge integration? Field escalation? CSAT?
- **Demo:** Very strong: email→ticket→SLA timer→canned response→rating; escalate to FSM task.
- **Watch-outs:** No Community equivalent — edition gate; team/stage design; avoid recreating a full ITSM if the need is customer service.
- **AI:** Native: AI livechat agents (E), knowledge-grounded answers (validate). Concept: auto-triage, response drafting.
- **Validate:** Volumes, channels, SLA matrix, integration with product/warranty data.

## Field Service (E)
- **Purpose:** Plan and execute on-site interventions: work orders, worksheets, parts, billing.
- **Modules:** E: `industry_fsm` (+`industry_fsm_report` worksheets, `industry_fsm_sale`, `industry_fsm_stock`).
- **Client questions:** Scheduling/dispatch? Mobile offline? Worksheets/signatures? Parts van stock? Invoice on-site?
- **Demo:** Excellent mobile story: task → travel → timer → worksheet → customer signature → invoice.
- **Watch-outs:** Built on project+planning+timesheet foundations — data model spans several apps; complex routing/optimization is not an APS.
- **AI:** Concept: schedule optimization, fault-pattern suggestions from history.
- **Validate:** Technician count, job types, offline needs, spare-parts logistics.

## Planning (E)
- **Purpose:** Shift/resource scheduling: Gantt planning, open shifts, employee self-assignment.
- **Modules:** E: `planning` (+bridges `sale_planning`, `project_forecast`).
- **Demo:** Strong visual (Gantt, copy-week, publish→employee notification).
- **Watch-outs:** It is operational scheduling, not workforce management with labor-law engines; country time rules live elsewhere.
- **Validate:** Scheduling rules, union constraints, integration with attendance/payroll.

## Timesheets
- **Purpose:** Time capture → project costing → billing → (payroll input).
- **Modules:** C: `hr_timesheet`, `sale_timesheet` · E: `timesheet_grid` (grid entry, validation, reminders).
- **Watch-outs:** Adoption is behavioral — reminders/validation (E) materially help; billing rate design with sales items.
- **Validate:** Billing models, approval chain, granularity policy.

## Documents (E)
- **Purpose:** Structured DMS inside the ERP: workspaces, tags, workflow actions, spreadsheets store.
- **Modules:** E: `documents` + bridges (`documents_hr`, `documents_project`, `documents_account`…), `ai_documents` (auto-sorting).
- **Demo:** Strong: drag PDF → workflow action creates vendor bill (with OCR) — "the inbox that runs itself".
- **Watch-outs:** Not a SharePoint replacement for heavy collaboration; retention/GDPR design is a project decision.
- **AI:** Native: auto-classification (E), docs as AI-agent sources (`ai_documents_source`).

## Sign (E)
- **Purpose:** e-Signature flows on templates with roles, inside processes (offers, contracts, HR docs).
- **Modules:** E: `sign`, `sign_ai`, bridges (`hr_recruitment_sign`, `hr_sign`, `sale_renting_sign`…).
- **Watch-outs:** Legal validity levels (SES/AES/QES, eIDAS) are jurisdiction questions — validate for regulated use; certificate handling via `certificate` module.
- **Demo:** Quick win inside any flow (send offer → sign on phone → status back in record).

## Knowledge (E)
- **Purpose:** Internal knowledge base: hierarchical articles, embedded views, templates, sharing.
- **Modules:** E: `knowledge`, `ai_knowledge` (AI text drafts), `website_knowledge`.
- **AI:** Natural grounding source for AI assistants — governance of article quality becomes an AI governance topic.

## Approvals (E)
- **Purpose:** Generic approval requests (procurement, travel, contracts…) with configurable approvers.
- **Modules:** E: `approvals`, `approvals_purchase`.
- **Watch-outs:** First stop before *any* custom approval workflow — challenge custom builds against it; complex conditional matrices may still need automation rules or Studio.

## Website
- **Purpose:** Public web presence with builder, blogs, events, forms — same data platform as the ERP.
- **Modules:** C: `website`, `website_blog`, `website_event`, `im_livechat` · E: `website_studio`, `website_generator`, `ai_website`, push notifications.
- **Watch-outs:** Brand-heavy design expectations vs builder reality; multi-site/multi-lang scoping; SEO migration.

## eCommerce
- **Purpose:** Sell online with native stock/pricing/payment coherence — B2C and strong B2B portal story.
- **Modules:** C: `website_sale`, payment providers, `website_sale_stock` · E: checkout carrier/tax connectors, `website_sale_subscription/_renting`, dashboards.
- **Demo:** Excellent: cart → payment → automatic delivery order + invoice — one platform, zero interfaces.
- **Watch-outs:** Not a hyperscale commerce engine — validate traffic/catalog ambitions; PSP fees/flows; B2B pricing logic.
- **AI:** Concept: product content generation; native website AI (E) for site/livechat.

## Point of Sale
- **Purpose:** In-store selling, offline-capable, tied to stock and accounting; restaurant mode.
- **Modules:** C: `point_of_sale`, `pos_restaurant`, terminal integrations · E: `pos_enterprise`, `pos_iot`, fiscal certifications (`l10n_*_pos`).
- **Watch-outs:** Country fiscal certification is decisive for retail deals — check the specific `l10n_*_pos` module exists; hardware matrix (printers/drawers/scales) via IoT (E).

## Marketing
- **Purpose:** Campaigns and audience engagement: email, SMS, social, WhatsApp, journeys, events, surveys.
- **Modules:** C: `mass_mailing`, `mass_mailing_sms`, `survey`, `website_event` · E: `marketing_automation`, `social`, `whatsapp`.
- **Demo:** Journey builder (E) on real CRM segments is visually compelling.
- **Watch-outs:** Deliverability/domain setup; consent/GDPR lists; don't oversell as a full-blown marketing cloud.

## Subscriptions / Recurring Revenue (E)
- **Purpose:** Recurring plans, automated invoicing, renewals, churn/MRR analytics.
- **Modules:** E: `sale_subscription`, `website_sale_subscription`.
- **Watch-outs:** Depends on Enterprise Accounting (`account_accountant`) — pulls the finance edition decision with it; revenue recognition rules need finance validation.

## Spreadsheet / BI / Reporting
- **Purpose:** Operational analysis: pivot/graph everywhere, spreadsheets on live data, dashboards.
- **Modules:** C: `spreadsheet`, `spreadsheet_dashboard`, per-app pivots · E: `spreadsheet_edition`, `documents_spreadsheet`, app dashboards, cohort/map/gantt views.
- **Watch-outs:** For enterprise BI/warehousing needs, position external BI as *integration*, not as an Odoo gap failure; data extraction strategy matters.

## AI & Automation (E for AI; automation partly C)
- **Purpose:** Native AI layer (agents, AI fields, AI server actions, domain assists, OCR) + rule automation.
- **Modules:** C: `base_automation` (automation rules — deep pack exists) · E: whole `ai*` family, `iap_extract` OCR family, `web_studio_ai_fields`.
- **Watch-outs:** pgvector prerequisite (`ai_auto_install`); IAP = pay-per-use; treat performance claims cautiously — module existence is verified, quality is not. Deep coverage: `modules/ai_native_odoo_19/` (consolidated evidence + governance) and `modules/base_automation/`; strategy: `06_odoo_ai_opportunity_map.md`.

## Localization & Fiscal Compliance
- **Purpose:** Country charts of accounts, taxes, EDI (e-invoicing), statutory reports, payroll rules.
- **Modules:** ~221 C + ~317 E `l10n_*` modules. Pattern: base chart/taxes often C; statutory reporting, EDI depth and payroll E.
- **Watch-outs:** THE compliance topic per deal. Always: (1) find the country modules in the catalog, (2) validate completeness with local Deloitte tax/payroll experts, (3) check e-invoicing mandates (Peppol etc.).

## Technical / Framework
- **Purpose:** Platform: ORM, web client, mail/chatter engine, automation, import/export, APIs, Studio.
- **Modules:** C: `base`, `web`, `mail`, `base_automation`, `iap` · E: `web_studio`, `web_enterprise`, advanced view widgets, `iot`, `voip`, data cleaning.
- **Watch-outs:** For architects: everything is a module on one ORM — integration boundaries, upgrade policy and customization governance live here.

## Industry-specific
- **Purpose:** Odoo 19.0 ships limited vertical modules; verticalization mostly = configuration + app combinations.
- **Watch-outs:** Check the catalog before assuming a vertical module exists; Deloitte industry blueprints are the differentiator.
