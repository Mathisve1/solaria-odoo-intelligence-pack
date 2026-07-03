# Batch 2 — Exact Upload Checklist (Navigation & Global Evidence)

**Goal:** after this batch, Solaria can *route and verify*: which modules exist, in which edition, what depends on what, which domain a problem belongs to, and what native AI actually ships.
**Prerequisite:** Batch 1 passed its acceptance test.

## Upload these 5 files, in this order, with these exact descriptions

### 1. `01_global_module_catalog.json`
**Capability gained:** existence/edition authority for all 1,422 modules — kills invented-module risk.
**Description to paste:**
> Source-derived catalog of ALL 1,422 Odoo 19.0 modules (650 Community + 772 Enterprise): edition, dependencies, category, functional domain, summary, per-entry confidence. THE authority on whether a module exists and which edition ships it. Never cite a module absent from this catalog. Not proof of runtime behaviour.

### 2. `04_functional_domain_map.md`
**Capability gained:** business-problem → domain → module routing; workshop/demo scoping.
**Description to paste:**
> Domain-level map of Odoo 19.0 (CRM, Sales, Finance, Supply Chain, Manufacturing, Project, HR, Services, Website/eCommerce, POS, Marketing, Subscriptions, BI, AI, Localization, Technical): purpose, key modules with edition, typical client questions, demo potential, watch-outs and validation questions per domain. Use to scope solutions; go module-level for specifics.

### 3. `02_global_dependency_map.yaml`
**Capability gained:** architecture answers (what extends what; Enterprise-on-Community layering).
**Description to paste:**
> Manifest-level dependency map of all 1,422 Odoo 19.0 modules: per-module direct dependencies with edition, top dependency hubs, and which Enterprise modules directly extend each core Community app. Use for architecture and "what extends what" questions. Direct dependencies only.

### 4. `06_odoo_ai_opportunity_map.md`
**Capability gained:** honest AI answers — native inventory vs Deloitte concepts.
**Description to paste:**
> Two-layer AI reference for Odoo 19.0: (1) source-verified inventory of the native Enterprise AI layer (AI agents, AI fields, AI server actions, domain assists, OCR family, pgvector prerequisite) and (2) Deloitte opportunity concepts per domain with governance requirements. Never blur shipping capability with concept.

### 5. `07_priority_module_recommendation.md`
**Capability gained:** Solaria knows which modules have deep packs and says so when coverage is thin.
**Description to paste:**
> Lists the Odoo 19.0 modules with deep intelligence packs (tiers and rationale, incl. V2 additions and the consolidated AI evidence pack) and next-iteration candidates. Use to know whether deep coverage exists for a module; if absent, answer from catalog + domain map at reduced confidence and say so.

## Expected capability improvement
Names real modules with correct editions · routes vague business problems to domains · answers "does module X exist?" from the catalog · states native-AI facts with the Enterprise/pgvector/IAP gates · declares coverage limits per module.

## Acceptance test (all 3 must pass)

**Q1. "Which modules are relevant for a field service company, and which edition do they need?"**
- **PASS:** `industry_fsm` (+ worksheets/sale/stock siblings) as Enterprise, foundations (`project`, timesheets, `stock`, `sale`, `helpdesk` intake, `planning`) with editions; mobile/offline validation caveat.
- **FAIL:** invents a Community FSM app, or gives a module-free answer.

**Q2. "Does Odoo 19 have AI? What exactly ships?"**
- **PASS:** Enterprise-only native layer with concrete module names (agents/fields/server actions, domain assists, OCR family), pgvector + IAP gates, two-part verdict (exists vs quality-pilot), concepts labeled as Deloitte concepts.
- **FAIL:** "yes, Odoo has AI everywhere" or concept features presented as shipped.

**Q3. "What does `sale_subscription` depend on, and what does that imply?"**
- **PASS:** depends on `account_accountant` (⇒ Enterprise accounting bundled into any subscriptions deal) + `sale_management` etc.; draws the edition implication.
- **FAIL:** no dependency facts, or missing the Enterprise-accounting implication.

**On failure:** verify descriptions were pasted, confirm the catalog JSON uploaded completely (it is the largest file, ~1.3 MB), then see kit README troubleshooting.
