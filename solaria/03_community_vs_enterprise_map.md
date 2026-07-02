# Odoo 19.0 — Community vs Enterprise Map

| Attribute | Value |
|---|---|
| Document type | Functional Domain Map (edition boundaries) |
| Authority level | High for edition questions |
| Version scope | Odoo 19.0 (Enterprise snapshot 2026-07-02) |
| Evidence type | Manifest + dependency analysis of both source trees |
| Confidence | High for module placement; behavior-level details need demo validation |

## 0. The structural truth (verified in source)

- **Enterprise 19.0 is an add-ons-only layer**: 772 modules with no server code. It runs on top of the Community code base (650 modules incl. the framework). Enterprise never replaces a Community module — it extends via new modules.
- Therefore every Enterprise capability = Community foundation + Enterprise extension. Phrase it that way with clients.
- **Licensing caveat (always repeat):** the source proves *which code ships in which tree*, not what a specific client subscription includes. Commercial packaging must be validated with Odoo.
- **Odoo Studio, the native AI suite, Payroll, statutory reporting, and most "Services" apps are Enterprise-only in 19.0** — this drives many advisory conclusions below.

## 1. Domain-by-domain split

For each domain: Community base → what Enterprise adds (module evidence) → advisory/demo implications.

### CRM
- **Community:** `crm` (pipeline, leads/opportunities, teams, activities, lead scoring basics), `crm_iap_mine`/enrichment via IAP credits.
- **Enterprise adds:** `crm_enterprise` (extended reporting/views), `voip` + `voip_crm` (integrated calling), `social_crm` (leads from social), `marketing_automation_crm`, `appointment_crm` (booking → lead), `ai_crm` + `ai_crm_livechat` (AI-created leads from emails/livechat).
- **Implication:** Core pipeline demos work on Community; "intelligent front office" stories (AI lead capture, VoIP, automation journeys) are Enterprise.

### Sales
- **Community:** `sale`/`sale_management` (quotations, orders, pricelists, discounts, portal quotes, invoicing policies), `sale_crm`, online quote confirmation & payment via `payment_*` providers (Community).
- **Enterprise adds:** `sale_enterprise` (reporting), `sale_subscription` (recurring revenue — see Subscriptions), `sale_renting` (rental), marketplace connectors (`sale_amazon`, `sale_shopee`, `sale_lazada`), `partner_commission`, external tax engines (`sale_external_tax`, Avatax), `sale_intrastat`, WhatsApp quote sending.
- **Implication:** Quote-to-cash is fundamentally Community-capable; subscription/rental/marketplace business models push to Enterprise.

### Accounting / Finance — the most important split to explain correctly
- **Community:** `account` = **Invoicing**: customer invoices, vendor bills, payments, taxes, basic bank statement import, partner ledgers. Community app name is literally "Invoicing".
- **Enterprise adds:** `account_accountant` (the full **Accounting** app: advanced bank reconciliation, lock dates workflows, fiduciary features), `account_reports` (financial + statutory reports: P&L, balance sheet, tax reports, audit reports), `account_asset` (depreciation), `account_budget`, `account_consolidation`, `account_batch_payment`, `account_sepa_direct_debit`, `account_followup` (dunning automation), `currency_rate_live`, `account_inter_company_rules`, OCR digitization (`account_invoice_extract`, `account_bank_statement_extract`), `ai_account` (AI text drafts), plus ~114 Enterprise `l10n_*_reports` statutory localization reporting modules.
- **Implication:** A company that "just invoices" can live on Community; a finance department that closes books, files statutory returns and automates collections effectively needs Enterprise. This is often *the* deciding edition factor.

### Inventory / Warehouse
- **Community:** `stock` (locations, routes, pickings, lots/serials, putaway, reordering rules, basic valuation), `delivery` (carrier concept), `stock_account`.
- **Enterprise adds:** `stock_barcode` (barcode scanner app), `quality`/`quality_control` (quality checks/alerts), `stock_enterprise` (reporting), integrated carrier connectors (`delivery_fedex_rest`, `delivery_ups_rest`, `delivery_dhl_rest`, `delivery_sendcloud`, `delivery_usps_rest`, `delivery_bpost`, `delivery_easypost`, `delivery_shiprocket`, `delivery_starshipit`).
- **Implication:** Warehouse structure and flows demo well on Community; paperless scanning operations and live carrier labels are Enterprise stories.

### Purchase
- **Community:** `purchase` (RFQs, orders, vendor pricelists, agreements via `purchase_requisition`), receipt/billing control.
- **Enterprise adds:** `account_3way_match` (bill vs order vs receipt), `approvals_purchase` (approval workflows on POs), vendor bill OCR with PO matching (`account_invoice_extract_purchase`), `purchase_intrastat`.
- **Implication:** Procure-to-pay runs on Community; compliance-grade control (3-way match, formal approvals, touchless vendor bills) is Enterprise.

### Manufacturing
- **Community:** `mrp` (BoMs, manufacturing orders, work centers basics), `maintenance`, `repair`, `mrp_subcontracting`.
- **Enterprise adds:** `mrp_workorder` (shop-floor tablet/work order execution), `mrp_mps` (master production schedule), `mrp_plm` (engineering change management), `quality_mrp`, IoT integration (`iot`).
- **Implication:** BoM/MO planning is Community; the "digital factory" demo (shop floor terminals, quality gates, PLM, IoT) is Enterprise.

### Project & Timesheets
- **Community:** `project` (tasks, stages, kanban), `project_todo`, `hr_timesheet` (task timesheets), `sale_project` (service quote→task).
- **Enterprise adds:** `project_enterprise` (Gantt/map views), `project_forecast` + `planning` (resource scheduling), `timesheet_grid` (grid entry, validation, billing workflows), `documents_project`, `sale_timesheet_enterprise`.
- **Implication:** Task management is Community; professional-services operations (utilization planning, timesheet validation and billing) are Enterprise.

### HR suite
- **Community:** `hr`, `hr_holidays` (time off), `hr_attendance`, `hr_expense`, `hr_skills`, `fleet`, `lunch`.
- **Enterprise adds:** `hr_payroll` (+ country payroll `l10n_*_hr_payroll` — all Enterprise), `hr_appraisal`, `hr_referral`, `hr_contract_salary` (salary package configurator with e-sign), `hr_expense_extract` (receipt OCR), `planning`, `frontdesk`, `documents_hr`, `hr_gantt`.
- **Implication:** Core HR administration is Community; payroll, appraisals and the full employee-lifecycle story are Enterprise. Payroll is a hard Enterprise dependency — flag early in any HR deal.

### Recruitment
- **Community:** `hr_recruitment` (pipeline, stages, jobs), `website_hr_recruitment` (careers page).
- **Enterprise adds:** `hr_recruitment_extract` (CV OCR autofill), `hr_recruitment_ai`, `hr_referral`, `hr_contract_salary` (offer→contract with e-signature), job-board integrations (`hr_recruitment_integration_*`), recruitment reporting.
- **Implication:** Hiring pipeline works on Community; "smart recruiting" (CV parsing, AI screening support, offer automation) is Enterprise.

### Helpdesk, Field Service, Planning, Appointments — Enterprise-native domains
- `helpdesk` (tickets, SLA, rating), `industry_fsm` (field service work orders on project foundation), `planning` (shifts/Gantt), `appointment` (online booking) have **no Community equivalent app** in 19.0. Community fallbacks are workarounds (e.g., using `project` as a ticket board).
- **Implication:** If these processes are core to the client, Enterprise is effectively required; position Community workarounds honestly as compromises.

### Documents, Sign, Knowledge, Approvals — Enterprise productivity layer
- `documents` (DMS with workspaces/tags/workflow actions + `ai_documents` auto-sorting), `sign` (e-signature + `sign_ai`), `knowledge` (structured articles), `approvals` (generic approval requests) are all Enterprise-only apps.
- **Implication:** These are high-visibility, low-effort demo wins and frequent fit-gap differentiators vs. SharePoint/DocuSign-style point tools.

### Website & eCommerce
- **Community:** `website` (site builder), `website_sale` (eCommerce), `website_slides` (eLearning), `website_event`, `im_livechat`, portal, payment providers.
- **Enterprise adds:** `website_studio`, `website_generator` (AI-assisted site generation), `social_push_notifications`, `website_appointment`, carrier/tax connectors for checkout, `website_sale_subscription`/`_renting`, `ai_website` (+ AI livechat on the site).
- **Implication:** A serious webshop is possible on Community — a differentiator vs. most ERP suites. Enterprise adds growth/automation tooling.

### Point of Sale
- **Community:** `point_of_sale` (offline-capable POS), `pos_restaurant`, several payment terminal integrations.
- **Enterprise adds:** `pos_enterprise` (advanced ops/preparation display), `pos_iot` (hardware via IoT box), `pos_settle_due`, extra terminals (e.g., `pos_tyro`), many fiscal certification modules (`l10n_*_pos`).
- **Implication:** Retail demos run on Community; fiscal-country compliance and hardware ecosystems often pull Enterprise.

### Marketing
- **Community:** `mass_mailing` (email marketing), `mass_mailing_sms`, `survey`, `website_event`, `marketing_card`.
- **Enterprise adds:** `marketing_automation` (multi-step journeys), `social` (social media management), `whatsapp` (WhatsApp business messaging).
- **Implication:** Newsletters are Community; orchestrated journeys and omnichannel are Enterprise.

### Subscriptions & Recurring Revenue — Enterprise
- `sale_subscription` (recurring invoicing, renewals, MRR/churn analytics; depends on `account_accountant`) and `website_sale_subscription`. No Community subscription app in 19.0.

### Spreadsheet / BI / Dashboards
- **Community:** `spreadsheet`, `spreadsheet_dashboard` (pre-built dashboards, read/light use).
- **Enterprise adds:** `spreadsheet_edition` (full editing/insert-from-anywhere), `documents_spreadsheet` (store/manage spreadsheets), `spreadsheet_sale_management`, dashboards across apps (`*_dashboard`, `web_cohort`, `web_map`, `web_gantt` views).
- **Implication:** "Live BI on your own numbers without leaving the suite" is essentially an Enterprise story; Community gives static-ish basics.

### AI — entirely Enterprise in 19.0 (verified: no `ai*` modules in the Community tree)
- Foundation: `ai` (base), `ai_app` (AI agents suite), `ai_fields` (AI-computed fields), `ai_server_actions`, `web_studio_ai_fields`, `ai_auto_install` (activates when PostgreSQL `pgvector` is available — an infrastructure prerequisite worth flagging).
- Domain AI: `ai_crm`, `ai_crm_livechat`, `ai_documents`(+`_account`, `_source`), `ai_account`, `ai_knowledge`, `ai_livechat`, `ai_website`(+`_livechat`), `hr_recruitment_ai`, `sign_ai`, `voip_ai` (call transcription), `esg_csrd_ai`.
- OCR digitization via IAP (pay-per-use credits): invoices, bank statements, expenses, CVs.
- **Implication:** "AI inside the ERP" is a native 19.0 Enterprise capability, not vaporware — but runtime behavior, model configuration and data governance must be validated live (source shows the modules exist, not how well they perform).

### Technical / customization layer
- **Community:** `web` client, `base_automation` (automation rules — Community!), `base_import`, REST-ish external API (XML-RPC/JSON-RPC) — all Community.
- **Enterprise adds:** `web_studio` (no-code app/field/view customization), `web_enterprise` (mobile-adaptive UI), advanced view widgets (`web_gantt`, `web_grid`, `web_cohort`, `web_map`), `iot`, `voip`, `data_cleaning`/`data_merge`, `databases`(multi-db ops).
- **Implication:** Automation rules do **not** require Studio — a frequent misconception. Studio's value is governed no-code customization; it is Enterprise-only.

## 2. Areas requiring validation (do not overclaim)

1. Exact feature depth inside a module (e.g., which reconciliation models ship) — needs demo database.
2. Odoo Online (SaaS) vs on-premise Enterprise feature availability — hosting-dependent, not source-derivable.
3. IAP-based features (OCR, enrichment, some AI) consume paid credits — commercial validation needed.
4. Anything about client-specific licensing, user pricing, or app-based pricing tiers.
5. Country scope of payroll/statutory modules for a specific client country — check the catalog for the `l10n_*` module, then validate completeness with local experts.

## 3. How Solaria should phrase edition uncertainty (patterns)

- *"Pipeline management is Community (`crm`); AI lead creation comes from the Enterprise `ai_crm` module — confirmed at module level in the 19.0 source. Exact behavior should be validated in a demo environment."*
- *"I can confirm the module ships in Enterprise 19.0; whether it is included in the client's current subscription is a licensing question to validate with Odoo."*
- *"I find no Community module for this in the 19.0 catalog; the capability appears Enterprise-only. If Community is a hard constraint, the options are configuration workarounds, custom development, or an external tool — in that order of preference."*
- *"This split is based on the 2026-07-02 Enterprise snapshot; point releases may have moved details."*

## 4. Deloitte advisory, client-facing and demo implications

- **Advisory:** Establish the edition decision early — it changes fit-gap outcomes (Payroll, statutory reporting, Helpdesk/FSM/Planning, Studio, AI are Enterprise). Never let a proposal silently assume Enterprise features on a Community budget.
- **Client-facing:** Frame Enterprise as "Community core + operational depth + compliance + AI", not as "the paid version". Quantify the value of the specific Enterprise modules the client would actually use.
- **Demos:** Decide the demo edition deliberately. Demoing Enterprise to a Community-budget client creates expectation debt. A strong pattern: show the Community core flow, then show the Enterprise uplift explicitly labeled as such.
