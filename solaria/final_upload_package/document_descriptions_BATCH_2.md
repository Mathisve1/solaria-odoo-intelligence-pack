# Batch 2 — Exact Document Titles & Descriptions (paste sheet)

Upload order note: the module catalog (item 5) goes LAST — it is the heaviest retrieval object and has its own retrieval test (see `batch_2_manifest.json`).

---

## 1. `04_functional_domain_map.md`
- **Solaria title:** `Odoo 19.0 — Functional Domain Map (business problem → modules)`
- **Description (paste):** Domain-level map of Odoo 19.0 (CRM, Sales, Finance, Supply Chain, Manufacturing, Project, HR, Services, Website/eCommerce, POS, Marketing, Subscriptions, BI, AI, Localization, Technical): purpose, key modules with edition, client questions, demo potential and watch-outs per domain. Use to scope which domains and modules a business problem touches. Do not use for field-level or workflow-level claims — go module-level.
- **Authority:** Medium-high (domain routing).
- **Use when:** Scoping problems to domains/modules; workshop and demo planning.
- **Do not use when:** Detailed capability claims.

## 2. `07_priority_module_recommendation.md`
- **Solaria title:** `Odoo Knowledge Pack — Deep-Coverage Index (which modules have deep packs)`
- **Description (paste):** Lists the Odoo 19.0 modules with deep intelligence packs (tiers and rationale, incl. V2 additions and the consolidated AI evidence pack) plus next-iteration candidates. Use to know whether deep coverage exists for a module; if absent, answer from catalog and domain map at reduced confidence and say so. Do not use for capability details.
- **Authority:** Medium (coverage awareness).
- **Use when:** Checking coverage before answering module-depth questions.
- **Do not use when:** Capability content.

## 3. `02_global_dependency_map.yaml`
- **Solaria title:** `Odoo 19.0 — Global Module Dependency Map (manifest-level)`
- **Description (paste):** Manifest-level dependency map of all 1,422 Odoo 19.0 modules: per-module direct dependencies with edition, dependency hubs, and which Enterprise modules extend each core Community app. Use for architecture and "what depends on / extends what" questions. Direct dependencies only — not behaviour, not transitive chains.
- **Authority:** High for declared dependencies.
- **Use when:** Architecture questions; edition-implication reasoning (e.g., subscriptions ⇒ Enterprise accounting).
- **Do not use when:** Functional capability questions.

## 4. `06_odoo_ai_opportunity_map.md`
- **Solaria title:** `Odoo 19.0 — AI Capability Inventory & Deloitte Opportunity Map`
- **Description (paste):** Two-layer AI reference for Odoo 19.0: (1) source-verified inventory of the native Enterprise AI layer (AI agents, AI fields, AI server actions, domain assists, OCR family, pgvector prerequisite) and (2) Deloitte opportunity concepts per domain with governance requirements. Use for AI value and opportunity questions. Never present layer-2 concepts as product features; quality always requires a pilot.
- **Authority:** High for §1 inventory; medium for concepts.
- **Use when:** AI capability/opportunity questions.
- **Do not use when:** Presenting concepts as product; accuracy claims.

## 5. `01_global_module_catalog.json` *(upload LAST in this batch)*
- **Solaria title:** `Odoo 19.0 — Global Module Catalog (all 1,422 modules, existence authority)`
- **Description (paste):** Source-derived catalog of ALL 1,422 Odoo 19.0 modules (650 Community + 772 Enterprise): edition, dependencies, category, functional domain, summary, per-entry confidence. THE authority on whether a module exists and which edition ships it. Never cite a module absent from this catalog. Do not use for runtime behaviour or feature depth.
- **Authority:** High for existence/edition.
- **Use when:** "Does module X exist? Which edition?" and grounding any module mention.
- **Do not use when:** Behaviour/feature-depth questions.
