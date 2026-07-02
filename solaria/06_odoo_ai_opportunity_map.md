# Odoo 19.0 AI Opportunity Map — Deloitte Perspective

| Attribute | Value |
|---|---|
| Document type | Strategy / Advisory (AI) with source-verified capability layer |
| Authority level | High for the capability inventory (§1); medium for concepts (§3–4) — concepts are Deloitte ideas, not product features |
| Version scope | Odoo 19.0 (Enterprise snapshot 2026-07-02) |
| Confidence | Module existence: high (verified in source). Runtime quality/behavior: unverified — always validate live |

**Golden rule:** never present a §3/§4 concept as an existing Odoo feature. §1 lists what verifiably ships in 19.0 Enterprise at module level; even there, *how well it works* requires live validation.

## 1. What Odoo 19.0 actually ships (source-verified, ALL Enterprise)

| Capability | Modules (evidence) | Functional meaning |
|---|---|---|
| AI foundation | `ai`, `ai_app` | Base AI framework + "AI agents" suite integrated in the environment |
| AI-computed fields | `ai_fields`, `web_studio_ai_fields`, `test_ai_fields` | Fields computed by an AI model from a prompt — configurable, incl. via Studio |
| AI server actions | `ai_server_actions` | AI steps inside automation rules |
| AI agents grounded on documents | `ai_documents_source` | Documents app content as AI agent knowledge sources |
| CRM: AI lead creation | `ai_crm`, `ai_crm_livechat` | Auto-create leads (incl. from livechat conversations) |
| Livechat AI agents | `ai_livechat`, `ai_website_livechat` | AI chat agents on website/livechat |
| Document auto-sorting | `ai_documents`, `ai_documents_account` | AI classification/filing in the DMS |
| AI text drafts | `ai_account`, `ai_knowledge` | Drafting assistance in Accounting and Knowledge |
| Recruitment AI | `hr_recruitment_ai` | AI assist in recruitment flow (manifest is terse — validate scope live) |
| Sign AI | `sign_ai` | AI assist in signature flows (validate scope live) |
| Call transcription | `voip_ai` | AI features incl. transcription on VoIP calls |
| ESG/CSRD AI | `esg_csrd_ai` | AI assist for sustainability reporting |
| OCR digitization (IAP, pay-per-use) | `account_invoice_extract`, `account_bank_statement_extract`, `hr_expense_extract`, `hr_recruitment_extract`, `iap_extract` | Vendor bills, bank statements, expense receipts, CVs auto-filled from scans |
| Infrastructure gate | `ai_auto_install` | AI auto-activates only if PostgreSQL **pgvector** is available — a real deployment prerequisite |

**Community edition ships none of the `ai*` modules.** Automation rules (`base_automation`) are Community — deterministic automation is available to everyone; AI automation is Enterprise.

## 2. Deloitte framing: where AI belongs in an ERP

AI creates value inside the ERP when it sits **inside the process** (drafting, classifying, extracting, alerting at the moment of work) and **stays out of the ledger** (no probabilistic posting, reserving, or tax logic). Three governance anchors for every opportunity below: human-in-the-loop, auditability of AI-influenced records, data boundaries (what leaves the client's environment, IAP/model hosting must be validated).

## 3. Opportunity map by domain

Legend — **N**: native 19.0 Enterprise capability (validate behavior live) · **C**: configuration/automation on standard data · **X**: custom AI extension · **V**: strategic vision.

| Domain | Opportunity | Type | Business value | Odoo data/modules | Pattern & governance |
|---|---|---|---|---|---|
| Sales | Quote text drafting; product description generation | N/X | Faster, consistent proposals | `sale`, `ai` | Draft-only, human sends; brand-tone review |
| Sales | Discount/margin anomaly alerts | C/X | Margin protection | `sale`, automation rules | Deterministic thresholds first; AI ranking optional |
| CRM | AI lead creation from email/livechat | **N** | Zero-touch capture | `ai_crm`, `ai_crm_livechat` | Review queue before assignment |
| CRM | Lead scoring/next-best-action | X | Focus on winnable deals | `crm` history | Score = advice, never auto-disqualify; bias monitoring |
| Accounting | Vendor bill / bank statement / receipt OCR | **N** | Touchless AP capture | `*_extract` | Confidence thresholds; human validation queue; IAP cost model |
| Accounting | AI text drafts (customer communications) | **N** | Faster follow-ups | `ai_account`, `account_followup` | Human sends; no autonomous dunning at start |
| Accounting | Close anomaly detection (unusual entries) | X | Audit quality, fewer surprises | `account` journals | Advisory flags only — never block or post |
| Inventory | Replenishment suggestion explainers; exception alerts | C/X | Fewer stockouts/overstock | `stock`, reordering data | Deterministic MRP logic remains master |
| Purchase | Touchless vendor bills with PO matching | **N** | AP productivity | `account_invoice_extract_purchase`, `account_3way_match` | 3-way match stays deterministic |
| Manufacturing | Quality-defect pattern mining; predictive maintenance | X/V | OEE, scrap reduction | `quality`, `maintenance`, `mrp` | Needs data volume; start descriptive → predictive |
| HR/Recruitment | CV parsing (**N**), screening assist (**N**, `hr_recruitment_ai`) | N | Recruiter productivity | `hr_recruitment_*` | EU AI Act: recruitment = high-risk area → human decision, documented criteria, candidate transparency |
| Project | Status summarization from chatter/timesheets | X | PM overhead down | `project`, `mail` | Summaries labeled AI-generated |
| Helpdesk | AI livechat agents (**N**); reply drafting; auto-triage | N/X | Deflection + speed | `ai_livechat`, `helpdesk`, `knowledge` | Escalation path to human always visible |
| Documents | Auto-classification (**N**); agents grounded on docs (**N**) | N | Findability, touchless filing | `ai_documents`, `ai_documents_source` | Misfiling review loop; access rights inherited — test leakage |
| Field Service | Fault-pattern suggestions; schedule risk alerts | X/V | First-time-fix rate | `industry_fsm`, `planning` | Suggestions only; dispatcher decides |
| Mgmt reporting | Narrative commentary on dashboards/spreadsheets | X | Executive time saved | `spreadsheet_*`, `account_reports` | Numbers from queries, words from AI — never AI-computed KPIs |

## 4. Deloitte strategic concepts (vision — NOT Odoo features)

These are advisory constructs Deloitte can design **on top of** the native layer (`ai_app` agents + `ai_fields` + `ai_server_actions` + automation rules + APIs). Present them as Deloitte offerings.

1. **Company Brain** — a governed assistant grounded on the client's Odoo data (Knowledge articles, Documents, key records) answering "how do we…/what is the status of…" questions with role-based access respected. Foundation exists natively (`ai_app`, `ai_documents_source`); the governance model, scope and quality bar are the Deloitte deliverable.
2. **Operations Copilot** — role-embedded assistants at process moments (AP clerk: bill exceptions; sales rep: quote prep pack; planner: exception queue). Pattern: AI fields + server actions + curated prompts per role.
3. **Alerts Center** — one governed inbox of business-exception alerts (margin, credit, SLA, stock, close anomalies), each with owner, threshold logic (deterministic first), optional AI ranking/explanation.
4. **Role Assistants** — persona-scoped variants (CFO monthly narrative, CRO pipeline hygiene, COO backlog risks) with explicit data contracts and human sign-off.

## 5. Implementation path (advisory default)

1. **Foundations first:** clean master data, adopted standard processes — AI on chaotic data amplifies chaos.
2. **Native quick wins** (§1): OCR family, AI drafts, document sorting — measurable, low risk, validate live in a pilot.
3. **Copilot pilots** on one role with human-in-the-loop metrics (acceptance rate, correction rate).
4. **Scale with governance:** AI usage register, prompt/agent versioning, data-boundary review (IAP endpoints, model hosting), periodic quality audits.

## 6. Demo guidance

- Lead with a native moment: drop a vendor bill PDF → fields auto-filled → human validates → posted. Concrete, honest, impressive.
- Always label: "shipping capability" vs "concept we would build".
- Rehearse AI demos live beforehand — never demo AI features cold; behavior is probabilistic.
- Keep a deterministic fallback slide if the live AI misbehaves.

## 7. Risks and honesty list

- Module existence ≠ feature quality — the source proves the former only.
- IAP features are metered (cost per document) — include in run-cost discussions.
- pgvector prerequisite for AI activation — infrastructure/hosting dependent (Odoo Online vs on-prem differences must be validated).
- Regulatory: recruitment and worker-monitoring AI are high-risk categories under the EU AI Act — Deloitte must bring the compliance frame, not just the tech.
- Model/vendor specifics (which LLM, hosting region, data retention) are not derivable from source — validate contractually.
