# Native AI in Odoo 19.0 — Functional Summary (Consolidated)

| Attribute | Value |
|---|---|
| Scope | All 28 source-verified native AI/OCR modules (see `ai_module_inventory.json`) |
| Source origin | **Enterprise only** — no `ai*` module exists in the Community 19.0 tree (verified) |
| Version scope | Odoo 19.0 (Enterprise snapshot 2026-07-02) |
| Confidence | Existence high; **behaviour/quality unverified — every capability below carries an implicit "validate live"** |

## Business purpose of the layer
Odoo 19.0 Enterprise embeds AI *inside* business processes rather than beside them: agents that act on records, AI-computed fields, AI steps in automations, drafting assistance where users write, classification where documents pile up, and OCR where paper enters the company. For Deloitte, this is the credible foundation under the AI-in-ERP story — a shipping product layer, not slideware.

## Capability groups (business language, with module evidence)

### 1. AI platform (the machinery)
- `ai` (base features), `ai_app` (AI agents suite — create/manage agents for business tasks, per manifest), `ai_fields` (fields computed by a model+prompt), `ai_server_actions` (AI steps inside automation rules), `web_studio_ai_fields` (create AI fields from Studio), `ai_auto_install` (activates the stack when **pgvector** is present — an infrastructure prerequisite to surface in every architecture conversation).
- **Business meaning:** the same no-code rungs consultants already use (fields, automations, Studio) gain an AI option — AI capability lands as *configuration*, which is exactly how governance wants it.

### 2. Front-office assists
- `ai_crm` + `ai_crm_livechat`: leads auto-created from conversations/email context.
- `ai_livechat`, `ai_website`, `ai_website_livechat`: AI chat agents on the website/livechat.
- **Business meaning:** zero-touch demand capture and first-line conversation handling — with a human review queue as the design default (see governance doc).

### 3. Writing & knowledge assists
- `ai_account` (AI text drafts in accounting communications), `ai_knowledge` (drafting in Knowledge), `ai_documents_source` (documents as agent knowledge sources).
- **Business meaning:** drafting acceleration where users already write; curated Knowledge/Documents become the grounding corpus — content governance becomes AI governance.

### 4. Document intelligence
- `ai_documents` + `ai_documents_account`: AI classification/filing in the DMS.
- OCR/IAP extract family: `account_invoice_extract` (vendor bills), `account_bank_statement_extract`, `hr_expense_extract` (receipts), `hr_recruitment_extract` (CVs), `account_invoice_extract_purchase` (bill↔PO auto-matching), on the common `iap_extract`/`account_extract` plumbing.
- **Business meaning:** the touchless-AP / smart-recruiting quick wins — measurable, pilotable, metered (IAP cost per document belongs in run-rate discussions).

### 5. Specialized assists
- `hr_recruitment_ai` (recruitment assist — terse manifest, **scope must be validated live before any client claim**), `sign_ai`, `voip_ai` (call transcription per manifest), `esg_csrd_ai` (sustainability reporting assist).

## What does NOT exist natively (say it plainly)
No shipped "Company Brain", no cross-module executive copilot, no alerts-center product, no autonomous posting/reservation/pricing AI — these are **Deloitte concepts** (see 06 §4) buildable *on* the platform pieces above, or deliberate non-goals (deterministic finance logic stays deterministic).

## Edition, infrastructure and commercial gates (repeat in every answer)
Enterprise-only · pgvector prerequisite (hosting-model dependent — validate for Odoo Online vs on-prem) · IAP metering for OCR · model/hosting/data-retention specifics are **not source-derivable** → contractual validation with Odoo.

## Typical client questions
"Is AI included?" — the modules ship in Enterprise; activation gates + subscription validation apply. · "How good is the invoice OCR?" — pilot with the client's real documents; never quote rates. · "Can it answer from our procedures?" — grounding pattern exists (`ai_documents_source` + Knowledge); quality and access-leakage must be piloted. · "Which LLM runs underneath / where is data processed?" — not in the source; validate with Odoo commercially.

## Fit-gap considerations
Treat each AI capability as FIT-STD *(existence)* + UNKNOWN-VALIDATE *(quality)* until piloted — a two-part verdict that keeps registers honest. AI asks that exceed this layer route to the standard ladder (custom AI = rung 5 with the governance doc's obligations).

## Deloitte demo angles
The three rehearsed-live winners: vendor-bill OCR → validation queue → posted; messy Documents inbox → AI auto-sorting → review step shown; CV → parsed applicant → human decision recorded. Concept demos (Company Brain etc.) only as labeled mockups — rules in `governance_and_validation.md` §5.

## Validation checklist
- [ ] pgvector/hosting compatibility confirmed for the client's deployment model
- [ ] IAP economics estimated at the client's document volumes
- [ ] Per-capability pilot with real client data before any commitment
- [ ] Data boundary (endpoints, retention, region) contractually validated
- [ ] `hr_recruitment_ai` scope tested live before any recruitment claim (high-risk domain)
