# Copy-Paste Document Descriptions for Solaria Upload

| Attribute | Value |
|---|---|
| Document type | Context Manifest / Knowledge Base Rules (upload aid) |
| Usage | When uploading a file to Solaria, paste its description below into the document description / usage-instruction field. Priorities: 1 = upload first. Authority: how strongly Solaria should trust it. |

For module evidence files not individually listed (Batch 4), use the generic templates at the end. Full registry (machine-readable, every file): `00_document_usage_registry.json`.
**V2 note:** exact per-batch upload checklists with these descriptions pre-inserted live in `upload_ready/` — prefer them for execution. V2 additions covered below: the `ai_native_odoo_19` consolidated pack and eight new module packs (account_accountant, account_reports, web_studio, base_automation, spreadsheet_edition, quality, mrp_workorder, stock_barcode) — use the Batch 3/4 templates for their standard files.

## V2 — AI evidence pack (`modules/ai_native_odoo_19/`, upload as one unit when AI questions appear)

**`modules/ai_native_odoo_19/ai_module_inventory.json`**
> Source-verified inventory of all 28 native AI and OCR-digitization modules in Odoo 19.0 (all Enterprise; pgvector and IAP gates noted). THE authority on whether a native AI module exists. Existence only — output quality requires a pilot on client data.

**`modules/ai_native_odoo_19/functional_summary.md`**
> Business-level explanation of the native AI layer of Odoo 19.0 Enterprise, grouped by capability (platform, front-office assists, drafting, document intelligence/OCR, specialized assists), with edition/infrastructure/commercial gates and what does NOT exist natively. Use for any "what can Odoo's AI do" question; always give the two-part verdict (exists / quality-piloted).

**`modules/ai_native_odoo_19/standard_vs_custom.md`**
> Places AI requests on the Deloitte solution ladder for Odoo 19.0: what is native (Enterprise), what is configuration (agents, AI fields, AI steps), when custom AI or external AI platforms are justified, and what to avoid. Use for scoping any AI build/buy question.

**`modules/ai_native_odoo_19/governance_and_validation.md`**
> Governance and phrasing rules for AI in Odoo engagements: risk table, AI register, validation protocol (pilot, leakage test), EU AI Act mapping, demo-safe rules and client-safe wording patterns with examples of what never to promise. High authority for how to talk about and govern AI.

---

## Batch 1 — Behaviour (priority 1, authority: highest)

**`00_solaria_role_and_answering_rules.md`**
> Highest-authority behaviour rules for acting as Deloitte's senior Odoo 19.0 Strategic Partner advisor. Follow in every answer: business-first 11-step structure, standard-before-custom ladder, explicit Community/Enterprise tags, explicit confidence marking, no overclaiming, no code-first answers. Overrides any conflicting document.

**`00_context_manifest_and_usage_rules.md`**
> Master guide to the Deloitte Odoo Intelligence Pack: document hierarchy, source hierarchy, routing logic, conflict and uncertainty rules, client-facing vs internal answering. Consult to decide which document to trust for which question. Highest authority together with the role rules.

**`00_document_type_usage_templates.md`**
> Defines the 11 document types in this pack (behaviour, manifest, playbook, index, domain map, functional summary, source evidence, security evidence, decision framework, demo, visual) with authority levels and combination rules. Use when deciding how much weight a retrieved document carries.

**`03_community_vs_enterprise_map.md`**
> High-authority map of the Odoo 19.0 Community vs Enterprise boundary per business domain, from manifest-level source analysis (Enterprise = add-ons-only layer). Use for every edition question. Licensing/subscription contents remain commercial questions — always flag validation.

**`05_standard_vs_configuration_vs_custom_framework.md`**
> Deloitte decision framework for every customization question: Standard → Configuration → Studio (Enterprise) → Automation → Custom → External integration, with tests, red flags and a decision tree. Apply whenever asked "can/should we customize/build/integrate". Pair with module evidence for feature claims.

**`00_document_usage_registry.json`**
> Machine-readable registry of every document in the pack: type, authority, when to use / not use, combinations, limitations, confidence. Use to route questions and to answer "which documents did you use".

## Batch 2 — Navigation (priority 2)

**`04_functional_domain_map.md`** (authority: medium-high)
> Domain-level map of Odoo 19.0 (CRM, Sales, Finance, Supply Chain, Manufacturing, HR, Services, Website/eCommerce, POS, Marketing, AI, Localization…): purpose, key modules with edition, client questions, demo potential, watch-outs per domain. Use to scope which domains/modules a business problem touches; go to module documents for depth.

**`07_priority_module_recommendation.md`** (authority: medium)
> Lists the 26 modules with deep intelligence packs (tiers and rationale) and next-iteration candidates. Use to know whether a deep pack exists for a module; if not, answer from the catalog + domain map at reduced confidence and say so.

**`01_global_module_catalog.json`** (authority: high for existence)
> Source-derived catalog of ALL 1,422 Odoo 19.0 modules (650 Community + 772 Enterprise): edition, dependencies, category, functional domain, per-entry confidence. THE authority on whether a module exists and which edition ships it. Never cite a module absent from this catalog. Not proof of runtime behaviour.

**`02_global_dependency_map.yaml`** (authority: high for dependencies)
> Manifest-level dependency map of all 1,422 modules incl. dependency hubs and which Enterprise modules extend each core Community app. Use for architecture questions ("what does X depend on / what extends Y"). Direct dependencies only; not behaviour.

**`00_inventory_and_extraction_plan.md`** (authority: high for coverage questions)
> Documents what sources this pack was built from (Community 19.0 final incl. server; Enterprise 19.0 add-ons snapshot 2026-07-02), counts, method, and coverage limits. Use for "how was this pack built / what are its limits" questions.

**`06_odoo_ai_opportunity_map.md`** (authority: high for §1 inventory; medium for concepts)
> Two-layer AI document: §1 = source-verified inventory of native AI modules in Odoo 19.0 Enterprise (agents, AI fields, AI server actions, domain assists, OCR family, pgvector prerequisite); §3–4 = Deloitte opportunity concepts (Company Brain, Copilots, Alerts Center) that are NOT product features. Never blur the two layers.

## Batch 3 — Module narratives (priority 3, authority: high for that module)

**`modules/<name>/functional_summary.md`** — use this template, replacing the module:
> Primary business-level reference for the Odoo 19.0 `<name>` module (<edition>). Capabilities, processes, personas, edition split, configuration/Studio/custom triggers, fit-gap notes, demo angles, watch-outs, validation checklist. High authority for functional questions on this module; behaviour details still require live validation.

**`modules/<name>/standard_vs_custom.md`**
> Module-specific application of the Deloitte standard-vs-custom framework for `<name>` (Odoo 19.0): what is likely standard, what configuration/Studio/automation can do, when custom or integration is justified, what to avoid. High authority for customization advice on this module.

**`modules/<name>/README.md`**
> Guide to the `<name>` intelligence pack: what each file covers and reading order (narrative for meaning, evidence files for existence). Use for routing within the module pack.

## Batch 4 — Module evidence (priority 4, authority: high for existence)

**`modules/<name>/models.json`**
> Source-derived data model of `<name>` in Odoo 19.0: models defined/extended, curated key fields with relations and status values, mixin-based capabilities. High authority that these structures exist; contains no code and does not prove runtime behaviour.

**`modules/<name>/views_summary.md`**
> Source-derived UI surface of `<name>`: real menu paths, window actions, view types, printable reports. Use for demo navigation and "where do users do X" questions.

**`modules/<name>/security_summary.md`**
> Shipped security baseline of `<name>` in 19.0: groups, access rights, record rules, advisory notes. Baseline for role design — the client's target security model is a project design task.

**`modules/<name>/workflow_summary.md`**
> Source-verified lifecycle fields/status flows, scheduled automations, server actions and mail templates of `<name>`. Use for process design, migration state mapping and automation questions.

## Batch 5 — Playbooks (priority 5, authority: high for method, medium for product claims)

**`playbooks/odoo_fit_gap_methodology.md`**
> Deloitte method for Odoo 19.0 fit-gap: verdict classes (FIT-STD…UNKNOWN-VALIDATE), evidence discipline, anti-overcustomization tactics, register structure. Use to run/structure fit-gap work. Feature claims still need catalog/module evidence.

**`playbooks/odoo_requirement_to_solution_mapping_guide.md`**
> Recipe for turning a client requirement into an Odoo-native recommendation: normalize → classify → map via catalog/domain map → decide level via the ladder → write verdict with evidence and assumptions. Use for "how do we solve X in Odoo" questions.

**`playbooks/odoo_demo_storyline_playbook.md`**
> Demo craft: executive/functional/technical structures, storytelling patterns, domain demo seeds, responsible AI demo rules. Medium authority — every demo step must be rehearsed in a live 19.0 database.

**`playbooks/odoo_implementation_roadmap_template.md`**
> Phase/gate template for Odoo programs (discovery → fit-gap → prototype → configuration → custom (gated) → integrations → migration → security → testing → training → go-live → hypercare → continuous improvement). Use for roadmap and governance questions.

**`playbooks/odoo_ai_inside_erp_strategy.md`**
> Deloitte AI-in-ERP strategy: inside-vs-outside rationale, the four concepts (labeled concepts!), governance framework (register, human-in-the-loop, AI Act, data boundaries), phased path, honest risks. Capability claims defer to the AI opportunity map.

**`playbooks/odoo_client_discovery_question_bank.md`**
> Structured discovery questions per domain (executive, sales, finance, supply chain, manufacturing, HR, services, web, BI, security, AI, customization-risk). Use to prepare workshops; answers feed the fit-gap register.

**`playbooks/deloitte_odoo_partner_positioning.md`**
> INTERNAL Deloitte positioning: why Odoo matters, the Deloitte difference, audience-specific narratives, engagement patterns. Use for internal pursuit framing; strip internal competitive framing from client-facing outputs.

## Do not upload
`.usage.md` companions (their text = these descriptions), `index.html` (human navigation), `99_*` reports (maintainer governance; optional late upload if Solaria should self-describe pack limits).
