# Flat Upload — All Document Descriptions (copy sheet)

For every file: set the **title**, paste the **description** into Solaria's document-description field. Files are in upload order. Operator files 0000/0001 are handled specially (0001 is pasted into the global-context field, not uploaded).


## OPERATOR

**`0000__OPERATOR__read_me_first.md`**
- Title: `READ ME FIRST — flat all-in package overview`
- Description: Start here. Explains the flat package, why one folder, the full-upload risk, and the 4-step upload process.
- Use when: Operator overview — read before uploading anything.
- Do not use when: As Odoo product knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`0001__OPERATOR__global_context_paste_me.txt`**
- Title: `Solaria Global Context (PASTE into global context field)`
- Description: The exact global context prompt. PASTE this into Solaria's global-context/custom-instructions field before uploading files. Do not upload it as a document.
- Use when: Configuring Solaria (paste, once).
- Do not use when: As an uploaded knowledge document.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`0002__OPERATOR__all_file_manifest.json`**
- Title: `Flat Upload — Machine-Readable Manifest`
- Description: Machine-readable manifest of every flat file: original path, category, entity, order, title, description, authority, evidence level, upload recommendation.
- Use when: Automation, verification, bulk description lookup.
- Do not use when: As Odoo product knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`0003__OPERATOR__document_descriptions_all.md`**
- Title: `Flat Upload — All Document Descriptions (copy sheet)`
- Description: Human-friendly copy sheet: for every file a Solaria title and paste-ready description with use/don't-use. Copy each into Solaria's per-document description field.
- Use when: Setting document descriptions during upload.
- Do not use when: As Odoo product knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`0004__OPERATOR__upload_order_all.md`**
- Title: `Flat Upload — Recommended Upload Order`
- Description: All files in recommended upload order (global context first, then core rules, source hierarchy, frameworks, maps/catalog, AI governance, module summaries, evidence, playbooks, tests, meta).
- Use when: Deciding upload sequence.
- Do not use when: As Odoo product knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`0005__OPERATOR__full_upload_testing_plan.md`**
- Title: `Flat Upload — Full Testing Plan (15+10+10)`
- Description: Testing plan after a full upload: 15 core, 10 red-team, 10 retrieval tests, with good/bad signals and triage for generic/overclaiming/edition/AI failures.
- Use when: Validating Solaria after upload.
- Do not use when: As product evidence (it is a testing artifact).
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`0006__OPERATOR__context_routing_guide.md`**
- Title: `Flat Upload — Category Routing Guide`
- Description: How Solaria should interpret filename categories and their authority order; states that META_QUALITY is not product evidence, TESTING is not answer content, MODULE_EVIDENCE is technical-validation support, CORE_RULES override.
- Use when: Understanding how categories route and rank.
- Do not use when: As product evidence.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`0007__OPERATOR__do_not_upload_even_in_full_mode.md`**
- Title: `Flat Upload — Do Not Upload (even in full mode)`
- Description: What must never be uploaded regardless of mode: sources, zips, .git, .claude, .usage.md, index.html, local settings, secrets, unsupported types.
- Use when: Guarding against uploading forbidden items.
- Do not use when: As Odoo product knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`0008__OPERATOR__push_to_new_repo_commands.md`**
- Title: `Flat Upload — Push to New Private Repo (commands)`
- Description: Git/GitHub CLI commands to push only this flat folder to a new private repo (solaria-odoo-flat-upload-all), plus a manual remote alternative.
- Use when: Optionally publishing the flat folder to its own repo.
- Do not use when: As Odoo product knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence


## GLOBAL_CONTEXT

**`0100__GLOBAL_CONTEXT__global_context_final.txt`**
- Title: `Behaviour / Agent Rules (FINAL paste source)`
- Description: FINAL paste-ready Solaria global context (V3): role, routing via document descriptions and hierarchy, answer structure, standard-before-custom ladder, edition discipline, evidence vocabulary, four-way AI separation, style rules. Paste into the global context field — do not upload as a document.
- Use when: Configuring Solaria: paste this complete text into the global context field. Refined V3 version of the 91 prompt (tighter, routing-via-descriptions, four-way AI separation).
- Do not use when: As an uploaded document (paste-only; uploading it would compete with itself in retrieval).
- Authority: highest_behaviour_authority · Evidence: not_product_evidence

**`0101__GLOBAL_CONTEXT__global_context_prompt_longform_md.md`**
- Title: `Behaviour / Agent Rules (paste-ready global context)`
- Description: Long-form global context prompt (V2 basis). SUPERSEDED FOR EXECUTION by final_upload_package/global_context_FINAL.txt — paste that version into Solaria; keep this document as the documented basis. Do not upload either prompt as a document.
- Use when: Configuring Solaria's global context/custom instructions for the Odoo workspace.
- Do not use when: As a knowledge document (it is configuration text).
- Authority: highest_behaviour_authority · Evidence: not_product_evidence

**`0102__GLOBAL_CONTEXT__global_context_prompt_longform_txt.txt`**
- Title: `Behaviour / Agent Rules (plain-text paste source)`
- Description: Plain-text V2 prompt (identical to the .md twin). SUPERSEDED FOR EXECUTION by final_upload_package/global_context_FINAL.txt — paste that version into Solaria instead.
- Use when: Copy-pasting the global context into Solaria.
- Do not use when: As a knowledge document.
- Authority: highest_behaviour_authority · Evidence: not_product_evidence


## CORE_RULES

**`0200__CORE_RULES__context_manifest_and_usage_rules.md`**
- Title: `Context Manifest / Knowledge Base Rules`
- Description: Master guide to the Deloitte Odoo Intelligence Pack: document hierarchy, source hierarchy, retrieval/routing logic, conflict and uncertainty rules, client-facing vs internal behaviour. Consult before answering from other documents. Highest authority together with the role rules.
- Use when: Deciding which document to trust, routing questions, resolving conflicts, uncertainty handling, client-facing vs internal answering.
- Do not use when: As a source of Odoo capabilities.
- Authority: high_routing_authority · Evidence: not_product_evidence

**`0201__CORE_RULES__document_type_usage_templates.md`**
- Title: `Context Manifest / Knowledge Base Rules`
- Description: Defines the 11 document types of this pack (behaviour, manifest, playbook, index, domain map, functional summary, source evidence, security evidence, decision framework, demo, visual) with authority levels, when-to-use rules and example descriptions.
- Use when: Weighing how much authority a retrieved document carries; writing descriptions for newly added documents.
- Do not use when: Content questions.
- Authority: high_routing_authority · Evidence: not_product_evidence

**`0202__CORE_RULES__solaria_role_and_answering_rules.md`**
- Title: `Behaviour / Agent Rules`
- Description: Highest-authority behaviour rules for acting as Deloitte's senior Odoo 19.0 Strategic Partner advisor: business-first 11-step answering structure, standard-before-custom ladder, Community/Enterprise separation, explicit uncertainty marking, no overclaiming. These rules override any conflicting document.
- Use when: Always — governs reasoning, answer structure, caution rules and tone in every answer.
- Do not use when: Never treated as evidence of Odoo functionality.
- Authority: highest_behaviour_authority · Evidence: not_product_evidence


## SOURCE_HIERARCHY

**`0400__SOURCE_HIERARCHY__community_vs_enterprise_map.md`**
- Title: `Functional Domain Map (edition boundaries)`
- Description: High-authority map of the Odoo 19.0 Community vs Enterprise boundary per business domain, from manifest-level analysis of both source trees (Enterprise = add-ons-only layer). Use for every edition question and for phrasing edition uncertainty. Subscription contents remain a commercial validation point.
- Use when: Any Community-vs-Enterprise question: what Enterprise adds per domain, edition implications for advisory/demos, edition uncertainty phrasing.
- Do not use when: Licensing/pricing contents of a client subscription (commercial validation) or module-internal details.
- Authority: high_source_map_authority · Evidence: source_structure_evidence

**`0401__SOURCE_HIERARCHY__document_usage_registry.json`**
- Title: `Context Manifest / Knowledge Base Rules (registry)`
- Description: Machine-readable registry of every document in the pack: type, authority, when to use / not use, limitations, confidence. Use to route questions and to answer 'which documents did you use'. Do not use as product knowledge.
- Use when: Routing; self-explanation of sources.
- Do not use when: As product knowledge.
- Authority: high_routing_authority · Evidence: not_product_evidence


## DECISION_FRAMEWORK

**`0600__DECISION_FRAMEWORK__standard_configuration_studio_custom_framework.md`**
- Title: `Standard-vs-Custom Decision Framework`
- Description: Deloitte decision framework for Odoo 19.0 solutioning: Standard → Configuration → Studio (Enterprise) → Automation → Custom development → External integration, with classification tests, red flags, Studio governance and a decision tree. Apply to every customization question, combined with module-level evidence.
- Use when: Every 'can Odoo do this / is this standard / should we customize / Studio? / build? / integrate?' question — apply the ladder and decision tree.
- Do not use when: Proving a feature exists (pair with catalog/module evidence).
- Authority: high_decision_framework_authority · Evidence: advisory_interpretation


## GLOBAL_MAP

**`0800__GLOBAL_MAP__global_dependency_map.yaml`**
- Title: `Index / Navigation Document (dependency map)`
- Description: Manifest-level dependency map of all 1,422 Odoo 19.0 modules: per-module direct dependencies with edition, top dependency hubs, and which Enterprise modules directly extend each core Community app. Use for architecture and 'what extends what' questions. Direct dependencies only.
- Use when: Architecture questions: what a module depends on, which Enterprise modules extend a core Community app, dependency hubs, cross-edition structure.
- Do not use when: Functional capability questions.
- Authority: high_source_map_authority · Evidence: source_structure_evidence

**`0801__GLOBAL_MAP__priority_module_recommendation.md`**
- Title: `Index / Navigation Document`
- Description: Lists the 26 Odoo 19.0 modules with deep intelligence packs (3 tiers with rationale) and recommended next-iteration additions. Use to know whether deep coverage exists for a module; if absent, answer from catalog + domain map at reduced confidence and say so.
- Use when: Checking whether a deep pack exists for a module; planning next knowledge-pack iterations; explaining pack coverage.
- Do not use when: Capability questions.
- Authority: high_source_map_authority · Evidence: meta_only


## MODULE_CATALOG

**`1000__MODULE_CATALOG__global_module_catalog.json`**
- Title: `Index / Navigation Document (source-derived catalog)`
- Description: Source-derived catalog of ALL 1,422 Odoo 19.0 modules (650 Community + 772 Enterprise): edition, dependencies, category, functional domain, summary, per-entry confidence. THE authority on whether a module exists and which edition ships it. Never cite a module absent from this catalog. Not proof of runtime behaviour.
- Use when: Confirming whether a module exists in Odoo 19.0, which edition ships it, what it depends on, its category/domain and manifest summary — for ALL 1,422 modules.
- Do not use when: Judging detailed runtime behaviour or feature depth (use module packs / live validation).
- Authority: high_source_map_authority · Evidence: source_structure_evidence


## DOMAIN_MAP

**`1500__DOMAIN_MAP__functional_domain_map.md`**
- Title: `Functional Domain Map`
- Description: Domain-level map of Odoo 19.0 (CRM, Sales, Finance, Supply Chain, Manufacturing, Project, HR, Services, Website/eCommerce, POS, Marketing, Subscriptions, BI, AI, Localization, Technical): purpose, key modules with edition, typical client questions, demo potential, watch-outs, AI angles and validation questions per domain. Use to scope solutions; go module-level for specifics.
- Use when: Scoping which domains/modules a business problem touches; workshop/demo planning; routing to module packs.
- Do not use when: Field-level or workflow-level claims (go module-level).
- Authority: high_source_map_authority · Evidence: functional_interpretation


## MODULE

**`2000__MODULE__account__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `account` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Invoicing (account).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2001__MODULE__account__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `account` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `account` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2002__MODULE__account__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `account` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Invoicing', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2003__MODULE__account_accountant__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `account_accountant` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Invoicing (account_accountant).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2004__MODULE__account_accountant__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `account_accountant` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `account_accountant` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2005__MODULE__account_accountant__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `account_accountant` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Invoicing', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2006__MODULE__account_reports__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `account_reports` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Accounting Reports (account_reports).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2007__MODULE__account_reports__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `account_reports` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `account_reports` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2008__MODULE__account_reports__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `account_reports` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Accounting Reports', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2009__MODULE__approvals__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `approvals` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Approvals (approvals).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2010__MODULE__approvals__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `approvals` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `approvals` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2011__MODULE__approvals__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `approvals` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Approvals', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2012__MODULE__base__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `base` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Base (base).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2013__MODULE__base__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `base` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `base` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2014__MODULE__base__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `base` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Base', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2015__MODULE__base_automation__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `base_automation` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Automation Rules (base_automation).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2016__MODULE__base_automation__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `base_automation` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `base_automation` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2017__MODULE__base_automation__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `base_automation` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Automation Rules', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2018__MODULE__contacts__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `contacts` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Contacts (contacts).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2019__MODULE__contacts__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `contacts` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `contacts` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2020__MODULE__contacts__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `contacts` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Contacts', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2021__MODULE__crm__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `crm` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for CRM (crm).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2022__MODULE__crm__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `crm` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `crm` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2023__MODULE__crm__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `crm` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize CRM', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2024__MODULE__documents__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `documents` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Documents (documents).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2025__MODULE__documents__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `documents` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `documents` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2026__MODULE__documents__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `documents` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Documents', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2027__MODULE__helpdesk__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `helpdesk` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Helpdesk (helpdesk).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2028__MODULE__helpdesk__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `helpdesk` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `helpdesk` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2029__MODULE__helpdesk__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `helpdesk` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Helpdesk', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2030__MODULE__hr__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `hr` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Employees (hr).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2031__MODULE__hr__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `hr` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `hr` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2032__MODULE__hr__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `hr` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Employees', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2033__MODULE__hr_recruitment__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `hr_recruitment` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Recruitment (hr_recruitment).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2034__MODULE__hr_recruitment__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `hr_recruitment` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `hr_recruitment` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2035__MODULE__hr_recruitment__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `hr_recruitment` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Recruitment', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2036__MODULE__hr_timesheet__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `hr_timesheet` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Task Logs (hr_timesheet).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2037__MODULE__hr_timesheet__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `hr_timesheet` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `hr_timesheet` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2038__MODULE__hr_timesheet__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `hr_timesheet` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Task Logs', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2039__MODULE__industry_fsm__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `industry_fsm` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Field Service (industry_fsm).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2040__MODULE__industry_fsm__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `industry_fsm` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `industry_fsm` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2041__MODULE__industry_fsm__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `industry_fsm` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Field Service', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2042__MODULE__knowledge__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `knowledge` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Knowledge (knowledge).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2043__MODULE__knowledge__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `knowledge` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `knowledge` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2044__MODULE__knowledge__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `knowledge` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Knowledge', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2045__MODULE__mail__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `mail` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Discuss (mail).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2046__MODULE__mail__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `mail` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `mail` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2047__MODULE__mail__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `mail` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Discuss', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2048__MODULE__marketing_automation__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `marketing_automation` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Marketing Automation (marketing_automation).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2049__MODULE__marketing_automation__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `marketing_automation` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `marketing_automation` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2050__MODULE__marketing_automation__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `marketing_automation` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Marketing Automation', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2051__MODULE__mrp__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `mrp` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Manufacturing (mrp).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2052__MODULE__mrp__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `mrp` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `mrp` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2053__MODULE__mrp__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `mrp` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Manufacturing', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2054__MODULE__mrp_workorder__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `mrp_workorder` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for MRP II (mrp_workorder).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2055__MODULE__mrp_workorder__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `mrp_workorder` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `mrp_workorder` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2056__MODULE__mrp_workorder__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `mrp_workorder` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize MRP II', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2057__MODULE__planning__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `planning` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Planning (planning).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2058__MODULE__planning__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `planning` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `planning` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2059__MODULE__planning__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `planning` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Planning', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2060__MODULE__point_of_sale__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `point_of_sale` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Point of Sale (point_of_sale).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2061__MODULE__point_of_sale__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `point_of_sale` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `point_of_sale` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2062__MODULE__point_of_sale__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `point_of_sale` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Point of Sale', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2063__MODULE__product__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `product` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Products & Pricelists (product).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2064__MODULE__product__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `product` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `product` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2065__MODULE__product__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `product` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Products & Pricelists', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2066__MODULE__project__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `project` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Project (project).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2067__MODULE__project__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `project` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `project` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2068__MODULE__project__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `project` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Project', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2069__MODULE__purchase__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `purchase` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Purchase (purchase).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2070__MODULE__purchase__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `purchase` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `purchase` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2071__MODULE__purchase__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `purchase` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Purchase', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2072__MODULE__quality__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `quality` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Quality Base (quality).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2073__MODULE__quality__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `quality` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `quality` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2074__MODULE__quality__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `quality` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Quality Base', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2075__MODULE__sale__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `sale` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Sales (sale).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2076__MODULE__sale__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `sale` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `sale` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2077__MODULE__sale__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `sale` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Sales', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2078__MODULE__sale_subscription__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `sale_subscription` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Subscriptions (sale_subscription).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2079__MODULE__sale_subscription__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `sale_subscription` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `sale_subscription` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2080__MODULE__sale_subscription__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `sale_subscription` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Subscriptions', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2081__MODULE__sign__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `sign` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Sign (sign).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2082__MODULE__sign__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `sign` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `sign` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2083__MODULE__sign__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `sign` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Sign', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2084__MODULE__spreadsheet_edition__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `spreadsheet_edition` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Spreadsheet (spreadsheet_edition).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2085__MODULE__spreadsheet_edition__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `spreadsheet_edition` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `spreadsheet_edition` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2086__MODULE__spreadsheet_edition__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `spreadsheet_edition` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Spreadsheet', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2087__MODULE__stock__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `stock` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Inventory (stock).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2088__MODULE__stock__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `stock` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `stock` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2089__MODULE__stock__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `stock` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Inventory', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2090__MODULE__stock_barcode__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `stock_barcode` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Barcode (stock_barcode).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2091__MODULE__stock_barcode__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `stock_barcode` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `stock_barcode` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2092__MODULE__stock_barcode__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `stock_barcode` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Barcode', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2093__MODULE__web_studio__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `web_studio` module (Enterprise). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Studio (web_studio).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2094__MODULE__web_studio__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `web_studio` module intelligence pack (Odoo 19.0, Enterprise): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `web_studio` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2095__MODULE__web_studio__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `web_studio` (Odoo 19.0, Enterprise): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Studio', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2096__MODULE__website__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `website` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for Website (website).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2097__MODULE__website__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `website` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `website` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2098__MODULE__website__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `website` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize Website', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2099__MODULE__website_sale__functional_summary.md`**
- Title: `Functional Module Summary`
- Description: Primary business-level reference for the Odoo 19.0 `website_sale` module (Community). Use for functional capabilities, processes, personas, fit-gap and demo angles. High authority for functional questions on this module; validate detailed behaviour against the module's evidence files and a live 19.0 database.
- Use when: Capabilities, business processes, personas, edition split, configuration/Studio/custom triggers, fit-gap considerations, demo angles or watch-outs for eCommerce (website_sale).
- Do not use when: Verifying exact runtime behaviour, other Odoo versions, pricing/licensing contents, or modules it merely mentions in passing.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2100__MODULE__website_sale__readme.md`**
- Title: `Index / Navigation Document`
- Description: Guide to the `website_sale` module intelligence pack (Odoo 19.0, Community): what each file contains and the reading order (narrative for meaning, evidence for existence). Use to route questions inside this module pack.
- Use when: Deciding which document of the `website_sale` pack answers a question; getting the module's one-line essence, dependencies and domain.
- Do not use when: As the sole basis for functional or customization conclusions.
- Authority: functional_guidance · Evidence: functional_interpretation

**`2101__MODULE__website_sale__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (module-specific)`
- Description: Module-specific application of the Deloitte standard-vs-custom framework for `website_sale` (Odoo 19.0, Community): what is likely standard, what configuration/Studio/automation can achieve, when custom or external integration is justified, and what to avoid. High authority for customization advice on this module.
- Use when: Any 'can/should we customize eCommerce', 'is this standard', 'Studio or custom or integration' question scoped to this module.
- Do not use when: Proving that a specific feature exists (use evidence files/catalog) or for other modules.
- Authority: functional_guidance · Evidence: functional_interpretation


## MODULE_EVIDENCE

**`5000__MODULE_EVIDENCE__account__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `account` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `account` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5001__MODULE_EVIDENCE__account__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `account` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `account`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5002__MODULE_EVIDENCE__account__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `account` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `account`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5003__MODULE_EVIDENCE__account__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `account` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `account`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5004__MODULE_EVIDENCE__account_accountant__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `account_accountant` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `account_accountant` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5005__MODULE_EVIDENCE__account_accountant__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `account_accountant` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `account_accountant`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5006__MODULE_EVIDENCE__account_accountant__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `account_accountant` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `account_accountant`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5007__MODULE_EVIDENCE__account_accountant__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `account_accountant` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `account_accountant`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5008__MODULE_EVIDENCE__account_reports__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `account_reports` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `account_reports` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5009__MODULE_EVIDENCE__account_reports__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `account_reports` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `account_reports`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5010__MODULE_EVIDENCE__account_reports__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `account_reports` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `account_reports`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5011__MODULE_EVIDENCE__account_reports__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `account_reports` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `account_reports`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5012__MODULE_EVIDENCE__approvals__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `approvals` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `approvals` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5013__MODULE_EVIDENCE__approvals__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `approvals` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `approvals`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5014__MODULE_EVIDENCE__approvals__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `approvals` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `approvals`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5015__MODULE_EVIDENCE__approvals__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `approvals` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `approvals`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5016__MODULE_EVIDENCE__base__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `base` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `base` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5017__MODULE_EVIDENCE__base__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `base` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `base`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5018__MODULE_EVIDENCE__base__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `base` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `base`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5019__MODULE_EVIDENCE__base__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `base` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `base`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5020__MODULE_EVIDENCE__base_automation__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `base_automation` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `base_automation` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5021__MODULE_EVIDENCE__base_automation__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `base_automation` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `base_automation`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5022__MODULE_EVIDENCE__base_automation__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `base_automation` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `base_automation`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5023__MODULE_EVIDENCE__base_automation__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `base_automation` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `base_automation`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5024__MODULE_EVIDENCE__contacts__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `contacts` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `contacts` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5025__MODULE_EVIDENCE__contacts__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `contacts` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `contacts`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5026__MODULE_EVIDENCE__contacts__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `contacts` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `contacts`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5027__MODULE_EVIDENCE__contacts__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `contacts` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `contacts`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5028__MODULE_EVIDENCE__crm__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `crm` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `crm` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5029__MODULE_EVIDENCE__crm__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `crm` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `crm`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5030__MODULE_EVIDENCE__crm__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `crm` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `crm`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5031__MODULE_EVIDENCE__crm__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `crm` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `crm`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5032__MODULE_EVIDENCE__documents__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `documents` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `documents` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5033__MODULE_EVIDENCE__documents__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `documents` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `documents`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5034__MODULE_EVIDENCE__documents__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `documents` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `documents`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5035__MODULE_EVIDENCE__documents__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `documents` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `documents`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5036__MODULE_EVIDENCE__helpdesk__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `helpdesk` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `helpdesk` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5037__MODULE_EVIDENCE__helpdesk__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `helpdesk` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `helpdesk`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5038__MODULE_EVIDENCE__helpdesk__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `helpdesk` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `helpdesk`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5039__MODULE_EVIDENCE__helpdesk__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `helpdesk` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `helpdesk`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5040__MODULE_EVIDENCE__hr__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `hr` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `hr` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5041__MODULE_EVIDENCE__hr__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `hr` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `hr`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5042__MODULE_EVIDENCE__hr__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `hr` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `hr`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5043__MODULE_EVIDENCE__hr__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `hr` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `hr`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5044__MODULE_EVIDENCE__hr_recruitment__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `hr_recruitment` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `hr_recruitment` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5045__MODULE_EVIDENCE__hr_recruitment__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `hr_recruitment` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `hr_recruitment`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5046__MODULE_EVIDENCE__hr_recruitment__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `hr_recruitment` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `hr_recruitment`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5047__MODULE_EVIDENCE__hr_recruitment__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `hr_recruitment` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `hr_recruitment`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5048__MODULE_EVIDENCE__hr_timesheet__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `hr_timesheet` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `hr_timesheet` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5049__MODULE_EVIDENCE__hr_timesheet__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `hr_timesheet` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `hr_timesheet`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5050__MODULE_EVIDENCE__hr_timesheet__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `hr_timesheet` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `hr_timesheet`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5051__MODULE_EVIDENCE__hr_timesheet__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `hr_timesheet` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `hr_timesheet`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5052__MODULE_EVIDENCE__industry_fsm__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `industry_fsm` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `industry_fsm` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5053__MODULE_EVIDENCE__industry_fsm__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `industry_fsm` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `industry_fsm`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5054__MODULE_EVIDENCE__industry_fsm__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `industry_fsm` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `industry_fsm`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5055__MODULE_EVIDENCE__industry_fsm__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `industry_fsm` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `industry_fsm`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5056__MODULE_EVIDENCE__knowledge__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `knowledge` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `knowledge` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5057__MODULE_EVIDENCE__knowledge__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `knowledge` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `knowledge`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5058__MODULE_EVIDENCE__knowledge__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `knowledge` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `knowledge`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5059__MODULE_EVIDENCE__knowledge__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `knowledge` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `knowledge`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5060__MODULE_EVIDENCE__mail__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `mail` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `mail` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5061__MODULE_EVIDENCE__mail__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `mail` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `mail`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5062__MODULE_EVIDENCE__mail__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `mail` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `mail`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5063__MODULE_EVIDENCE__mail__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `mail` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `mail`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5064__MODULE_EVIDENCE__marketing_automation__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `marketing_automation` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `marketing_automation` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5065__MODULE_EVIDENCE__marketing_automation__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `marketing_automation` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `marketing_automation`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5066__MODULE_EVIDENCE__marketing_automation__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `marketing_automation` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `marketing_automation`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5067__MODULE_EVIDENCE__marketing_automation__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `marketing_automation` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `marketing_automation`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5068__MODULE_EVIDENCE__mrp__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `mrp` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `mrp` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5069__MODULE_EVIDENCE__mrp__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `mrp` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `mrp`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5070__MODULE_EVIDENCE__mrp__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `mrp` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `mrp`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5071__MODULE_EVIDENCE__mrp__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `mrp` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `mrp`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5072__MODULE_EVIDENCE__mrp_workorder__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `mrp_workorder` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `mrp_workorder` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5073__MODULE_EVIDENCE__mrp_workorder__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `mrp_workorder` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `mrp_workorder`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5074__MODULE_EVIDENCE__mrp_workorder__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `mrp_workorder` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `mrp_workorder`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5075__MODULE_EVIDENCE__mrp_workorder__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `mrp_workorder` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `mrp_workorder`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5076__MODULE_EVIDENCE__planning__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `planning` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `planning` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5077__MODULE_EVIDENCE__planning__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `planning` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `planning`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5078__MODULE_EVIDENCE__planning__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `planning` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `planning`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5079__MODULE_EVIDENCE__planning__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `planning` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `planning`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5080__MODULE_EVIDENCE__point_of_sale__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `point_of_sale` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `point_of_sale` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5081__MODULE_EVIDENCE__point_of_sale__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `point_of_sale` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `point_of_sale`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5082__MODULE_EVIDENCE__point_of_sale__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `point_of_sale` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `point_of_sale`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5083__MODULE_EVIDENCE__point_of_sale__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `point_of_sale` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `point_of_sale`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5084__MODULE_EVIDENCE__product__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `product` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `product` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5085__MODULE_EVIDENCE__product__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `product` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `product`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5086__MODULE_EVIDENCE__product__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `product` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `product`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5087__MODULE_EVIDENCE__product__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `product` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `product`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5088__MODULE_EVIDENCE__project__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `project` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `project` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5089__MODULE_EVIDENCE__project__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `project` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `project`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5090__MODULE_EVIDENCE__project__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `project` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `project`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5091__MODULE_EVIDENCE__project__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `project` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `project`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5092__MODULE_EVIDENCE__purchase__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `purchase` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `purchase` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5093__MODULE_EVIDENCE__purchase__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `purchase` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `purchase`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5094__MODULE_EVIDENCE__purchase__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `purchase` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `purchase`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5095__MODULE_EVIDENCE__purchase__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `purchase` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `purchase`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5096__MODULE_EVIDENCE__quality__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `quality` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `quality` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5097__MODULE_EVIDENCE__quality__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `quality` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `quality`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5098__MODULE_EVIDENCE__quality__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `quality` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `quality`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5099__MODULE_EVIDENCE__quality__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `quality` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `quality`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5100__MODULE_EVIDENCE__sale__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `sale` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `sale` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5101__MODULE_EVIDENCE__sale__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `sale` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `sale`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5102__MODULE_EVIDENCE__sale__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `sale` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `sale`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5103__MODULE_EVIDENCE__sale__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `sale` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `sale`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5104__MODULE_EVIDENCE__sale_subscription__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `sale_subscription` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `sale_subscription` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5105__MODULE_EVIDENCE__sale_subscription__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `sale_subscription` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `sale_subscription`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5106__MODULE_EVIDENCE__sale_subscription__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `sale_subscription` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `sale_subscription`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5107__MODULE_EVIDENCE__sale_subscription__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `sale_subscription` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `sale_subscription`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5108__MODULE_EVIDENCE__sign__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `sign` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `sign` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5109__MODULE_EVIDENCE__sign__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `sign` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `sign`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5110__MODULE_EVIDENCE__sign__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `sign` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `sign`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5111__MODULE_EVIDENCE__sign__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `sign` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `sign`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5112__MODULE_EVIDENCE__spreadsheet_edition__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `spreadsheet_edition` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `spreadsheet_edition` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5113__MODULE_EVIDENCE__spreadsheet_edition__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `spreadsheet_edition` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `spreadsheet_edition`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5114__MODULE_EVIDENCE__spreadsheet_edition__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `spreadsheet_edition` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `spreadsheet_edition`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5115__MODULE_EVIDENCE__spreadsheet_edition__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `spreadsheet_edition` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `spreadsheet_edition`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5116__MODULE_EVIDENCE__stock__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `stock` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `stock` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5117__MODULE_EVIDENCE__stock__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `stock` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `stock`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5118__MODULE_EVIDENCE__stock__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `stock` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `stock`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5119__MODULE_EVIDENCE__stock__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `stock` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `stock`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5120__MODULE_EVIDENCE__stock_barcode__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `stock_barcode` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `stock_barcode` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5121__MODULE_EVIDENCE__stock_barcode__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `stock_barcode` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `stock_barcode`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5122__MODULE_EVIDENCE__stock_barcode__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `stock_barcode` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `stock_barcode`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5123__MODULE_EVIDENCE__stock_barcode__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `stock_barcode` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `stock_barcode`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5124__MODULE_EVIDENCE__web_studio__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `web_studio` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `web_studio` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5125__MODULE_EVIDENCE__web_studio__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `web_studio` module (Enterprise): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `web_studio`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5126__MODULE_EVIDENCE__web_studio__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `web_studio` module (Enterprise): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `web_studio`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5127__MODULE_EVIDENCE__web_studio__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `web_studio` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `web_studio`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5128__MODULE_EVIDENCE__website__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `website` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `website` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5129__MODULE_EVIDENCE__website__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `website` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `website`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5130__MODULE_EVIDENCE__website__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `website` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `website`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5131__MODULE_EVIDENCE__website__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `website` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `website`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5132__MODULE_EVIDENCE__website_sale__models.json`**
- Title: `Source-Code-Derived Evidence (data model)`
- Description: Source-derived data model of the Odoo 19.0 `website_sale` module (Community): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
- Use when: Verifying that a business object, field, relation or status value exists in `website_sale` in Odoo 19.0; grounding functional claims; data-mapping and migration design.
- Do not use when: Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5133__MODULE_EVIDENCE__website_sale__security_summary.md`**
- Title: `Security / Access Evidence`
- Description: Security baseline of the Odoo 19.0 `website_sale` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
- Use when: Role design baselines, permission questions, segregation-of-duties discussions involving `website_sale`.
- Do not use when: As the client's target security model (that is a project design task) or for org-specific role advice without client context.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5134__MODULE_EVIDENCE__website_sale__views_summary.md`**
- Title: `Source-Code-Derived Evidence (UI surface)`
- Description: Source-derived UI surface of the Odoo 19.0 `website_sale` module (Community): real menu paths, window actions, view types and printable reports, with consultant demo notes. Use for demo navigation and UI-surface questions; validate exact layouts in a live database.
- Use when: Demo navigation design ('where do users do X'), UI-surface questions, report inventory for `website_sale`.
- Do not use when: Judging UX quality or exact screen layouts (validate live); business meaning questions.
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`5135__MODULE_EVIDENCE__website_sale__workflow_summary.md`**
- Title: `Source-Code-Derived Evidence (workflows & automation)`
- Description: Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `website_sale` module (Community). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
- Use when: Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `website_sale`.
- Do not use when: Inferring exact transition conditions or timing behaviour (validate live).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence


## AI

**`6000__AI__odoo_ai_opportunity_map.md`**
- Title: `Strategy / Advisory (AI) with source-verified capability inventory`
- Description: Two-layer AI reference for Odoo 19.0: (1) source-verified inventory of the native Enterprise AI layer (AI agents, AI fields, AI server actions, domain assists, OCR family, pgvector prerequisite) and (2) Deloitte opportunity concepts per domain with governance requirements. Never blur shipping capability with concept.
- Use when: Any AI-in-Odoo question: what natively ships in 19.0 Enterprise (verified module list), where AI adds value per domain, governance requirements, demo guidance.
- Do not use when: Presenting §3-4 concepts (Company Brain, Copilots, Alerts Center) as product features — they are Deloitte concepts.
- Authority: advisory_playbook · Evidence: advisory_interpretation

**`6001__AI__ai_native_odoo_19__functional_summary.md`**
- Title: `Functional Module Summary (consolidated AI layer)`
- Description: Business-level explanation of the native AI layer of Odoo 19.0 Enterprise, grouped by capability (platform, front-office assists, drafting, document intelligence/OCR, specialized assists), with edition/infrastructure/commercial gates and what does NOT exist natively. Always give the two-part verdict (exists / quality-piloted).
- Use when: Explaining in business terms what the native AI layer does (platform, assists, document intelligence), its gates, and what does NOT exist natively.
- Do not use when: Quality/accuracy claims (pilot), concept design (playbook), module existence detail (inventory JSON).
- Authority: functional_guidance · Evidence: functional_interpretation

**`6002__AI__ai_native_odoo_19__governance_and_validation.md`**
- Title: `Security / Governance Evidence + advisory (AI)`
- Description: Governance and phrasing rules for AI in Odoo engagements: risk table, AI register, validation protocol (pilot, leakage test), EU AI Act mapping, demo-safe rules and client-safe wording patterns with explicit examples of what never to promise. High authority for how to talk about and govern AI.
- Use when: Any AI risk, compliance (EU AI Act), validation-protocol or phrasing question: risk table, AI register, pilot/leakage protocols, demo-safe rules, client-safe wording with ✅/❌ examples.
- Do not use when: Capability existence (inventory) or value framing (functional summary).
- Authority: functional_guidance · Evidence: functional_interpretation

**`6003__AI__ai_native_odoo_19__inventory.json`**
- Title: `Source-Code-Derived Evidence (AI inventory)`
- Description: Source-verified inventory of all 28 native AI and OCR-digitization modules in Odoo 19.0 (all Enterprise; pgvector and IAP gates noted). THE authority on whether a native AI module exists. Existence only — output quality requires a pilot on client data.
- Use when: Verifying whether a native AI/OCR module exists in Odoo 19.0, its edition (all Enterprise), dependencies and manifest summary — all 28 modules.
- Do not use when: Judging output quality or runtime behaviour (pilot required); inferring model/hosting facts (commercial validation).
- Authority: source_derived_metadata · Evidence: source_metadata_evidence

**`6004__AI__ai_native_odoo_19__readme.md`**
- Title: `Index / Navigation Document (AI evidence pack)`
- Description: Guide to the consolidated native-AI evidence pack for Odoo 19.0: what each file covers (inventory JSON, functional summary, standard-vs-custom, governance) and the non-negotiable AI answering rules (Enterprise-only, two-part verdict, concepts are not features).
- Use when: Routing any AI-in-Odoo question to the right file of the consolidated pack; the three sentences that must survive every AI answer.
- Do not use when: As the capability inventory itself (that is the JSON).
- Authority: functional_guidance · Evidence: functional_interpretation

**`6005__AI__ai_native_odoo_19__standard_vs_custom.md`**
- Title: `Standard-vs-Custom Decision Framework (AI layer)`
- Description: Places AI requests on the Deloitte solution ladder for Odoo 19.0: what is native (Enterprise), what is configuration (agents, AI fields, AI steps — registered artifacts), when custom AI or external AI platforms are justified, and what to avoid. Use for any AI build/buy scoping question.
- Use when: Placing AI requests on the solution ladder: native vs configuration (agents/AI fields/AI steps) vs custom AI vs external AI platforms; what to avoid.
- Do not use when: Proving existence (inventory JSON) or phrasing rules (governance doc).
- Authority: functional_guidance · Evidence: functional_interpretation


## PLAYBOOK

**`7000__PLAYBOOK__deloitte_odoo_partner_positioning.md`**
- Title: `Strategy / Deloitte Advisory Playbook (internal)`
- Description: INTERNAL Deloitte positioning playbook: why Odoo matters strategically, how Deloitte differentiates (strategy + compliance + transformation + implementation + AI governance), audience-specific narratives and engagement patterns. Internal framing — adapt before any client-facing use.
- Use when: Internal pursuit framing: why Odoo matters, the Deloitte difference, executive/functional/technical narratives, engagement patterns, competitive framing.
- Do not use when: Client-facing use without adaptation (strip internal competitive framing); product feature claims; licensing/pricing statements.
- Authority: advisory_playbook · Evidence: advisory_interpretation

**`7001__PLAYBOOK__odoo_ai_inside_erp_strategy.md`**
- Title: `Strategy / Deloitte Advisory Playbook (AI)`
- Description: Deloitte strategy for AI inside Odoo 19.0: why AI belongs in the process, Company Brain / Operations Copilot / Alerts Center / Role Assistants as labeled Deloitte concepts, governance framework (AI register, human-in-the-loop, EU AI Act, data boundaries) and a phased implementation path. Capability claims defer to the AI opportunity map.
- Use when: AI-in-ERP strategy questions: inside-vs-outside rationale, the four Deloitte concepts (labeled), governance framework (register, human-in-the-loop, AI Act, data boundaries), phased implementation path, demo ideas, risks.
- Do not use when: Claiming concepts are Odoo features (capability inventory lives in 06); model/hosting specifics (contract validation).
- Authority: advisory_playbook · Evidence: advisory_interpretation

**`7002__PLAYBOOK__odoo_client_discovery_question_bank.md`**
- Title: `Strategy / Deloitte Advisory Playbook (discovery tool)`
- Description: Practical discovery question bank for Deloitte Odoo engagements: executive and per-domain questions plus AI-opportunity and customization-risk probes. Every answer should map to a functional domain and feed the fit-gap register.
- Use when: Preparing discovery workshops: curated questions per audience/domain (executive, sales, finance, supply chain, manufacturing, HR, services, FSM, web, BI, security, AI, customization-risk).
- Do not use when: As answers (it contains questions); capability claims.
- Authority: advisory_playbook · Evidence: advisory_interpretation

**`7003__PLAYBOOK__odoo_demo_storyline_playbook.md`**
- Title: `Demo / Storyline Document`
- Description: Deloitte demo craft for Odoo 19.0: executive/functional/technical demo structures, storytelling patterns (day-in-the-life, order #1042), domain demo seeds, edition honesty and responsible AI demo rules. Medium authority — every step must be rehearsed in a live database before client use.
- Use when: Building client demos: executive/functional/technical structures, storytelling patterns, domain demo seeds, responsible AI demo rules, preparation checklist.
- Do not use when: As technical proof of any capability; demo steps must be rehearsed in a live 19.0 database first.
- Authority: advisory_playbook · Evidence: advisory_interpretation

**`7004__PLAYBOOK__odoo_fit_gap_methodology.md`**
- Title: `Strategy / Deloitte Advisory Playbook`
- Description: Deloitte method for Odoo 19.0 fit-gap analysis: FIT/GAP verdict classes with evidence discipline, question framework, anti-overcustomization tactics, recommendation structure and validation checklist. Use to run fit-gap work; feature claims still need catalog/module evidence.
- Use when: Running or structuring Odoo 19.0 fit-gap analysis: verdict classes, evidence discipline, anti-overcustomization tactics, register structure, good/bad examples.
- Do not use when: Proving Odoo features (needs catalog/module evidence); pricing or effort commitments.
- Authority: advisory_playbook · Evidence: advisory_interpretation

**`7005__PLAYBOOK__odoo_implementation_roadmap_template.md`**
- Title: `Strategy / Deloitte Advisory Playbook (methodology template)`
- Description: Phase-and-gate roadmap template for Odoo programs: discovery → fit-gap → prototype → configuration-first build → gated customization → integrations → migration → security → testing → training → go-live → hypercare → continuous improvement, with deliverables and decision gates per phase.
- Use when: Structuring Odoo implementation roadmaps: 13 phases with purposes, activities, deliverables and decision gates (incl. the customization gate G1 and upgrade governance).
- Do not use when: Committing durations/prices (engagement-specific); technical how-tos.
- Authority: advisory_playbook · Evidence: advisory_interpretation

**`7006__PLAYBOOK__odoo_requirement_to_solution_mapping_guide.md`**
- Title: `Strategy / Deloitte Advisory Playbook (method)`
- Description: Deloitte recipe for requirement-to-solution mapping on Odoo 19.0: normalization template, requirement classification, module mapping rules (never propose uncataloged modules), solution-level decision, recommendation template with assumptions, and six worked examples.
- Use when: Turning a client requirement into an Odoo-native recommendation: normalize → classify → map via catalog/domain map → decide solution level → write verdict with evidence/assumptions → validate; includes worked examples.
- Do not use when: Module capability proof (defer to catalog/module docs).
- Authority: advisory_playbook · Evidence: advisory_interpretation


## EXECUTIVE

**`7500__EXECUTIVE__executive_orientation.md`**
- Title: `Strategy / orientation (executive)`
- Description: Executive orientation: what the Deloitte Odoo Intelligence Pack makes Solaria capable of, why it matters for Deloitte's Odoo positioning, how to use it in client conversations, and the built-in guardrails against overpromising. For partners/senior managers; also uploadable so Solaria can explain itself to executives.
- Use when: Explaining to Deloitte leadership what this Solaria configuration is, what it can/cannot do, how to use it in pursuits, and the guardrails against overpromising.
- Do not use when: Detailed functional or technical questions.
- Authority: advisory_playbook · Evidence: advisory_interpretation


## CONSULTANT

**`7800__CONSULTANT__functional_consultant_orientation.md`**
- Title: `Strategy / orientation (functional consultants)`
- Description: Consultant orientation: how to get evidence-based answers from Solaria (question patterns, control levers like 'which documents support that'), how to use it per activity (discovery, fit-gap, demo prep, standard-vs-custom, planning), and the list of things that always need live Odoo validation.
- Use when: Coaching consultants on asking evidence-forcing questions and using Solaria for discovery, fit-gap, demos, customization decisions and implementation planning — plus what still requires live validation.
- Do not use when: As Odoo product knowledge.
- Authority: advisory_playbook · Evidence: advisory_interpretation


## TESTING

**`8000__TESTING__acceptance_tests_after_batch_1.md`**
- Title: `Context Manifest / Knowledge Base Rules (acceptance suite)`
- Description: Batch-1 acceptance suite: 8 tests with expected answers, required/fail signals and per-test fixes; gate >=7/8 with zero critical fails. Operator artifact — never upload (test integrity).
- Use when: Testing after Batch 1: 8 tests (role, ladder, edition, uncertainty, hierarchy, overclaim refusal, tone, self-citation) with expected answers, signals and fixes. Gate >=7/8, zero critical.
- Do not use when: Uploading to Solaria (would invalidate testing).
- Authority: testing_artifact · Evidence: testing_only

**`8001__TESTING__acceptance_tests_after_batch_2.md`**
- Title: `Context Manifest / Knowledge Base Rules (acceptance suite)`
- Description: Batch-2 acceptance suite: 10 tests incl. the critical negative-existence and AI-concept probes; gate >=8/10 with zero critical fails. Operator artifact — never upload.
- Use when: Testing after Batch 2: 10 tests (domain routing, existence incl. negative-existence, source_origin, dependencies, AI separation, coverage honesty, overclaim re-probes). Gate >=8/10, zero critical.
- Do not use when: Uploading to Solaria.
- Authority: testing_artifact · Evidence: testing_only

**`8002__TESTING__acceptance_tests_after_batch_3.md`**
- Title: `Context Manifest / Knowledge Base Rules (acceptance suite)`
- Description: Batch-3 acceptance suite: 12 functional-domain tests with pass/fail criteria; gate >=10/12 together with a clean red-team run. Operator artifact — never upload.
- Use when: Testing after Batch 3: 12 domain tests (quote-to-cash through field service and AI-native-vs-custom). Gate >=10/12 plus red-team zero-critical; then stop uploading.
- Do not use when: Uploading to Solaria.
- Authority: testing_artifact · Evidence: testing_only

**`8003__TESTING__answer_quality_rubric.md`**
- Title: `Context Manifest / Knowledge Base Rules (scoring rubric)`
- Description: 0-5 answer-quality rubric with 10 criteria, hard floors (edition accuracy, uncertainty handling), scoring sheet and release thresholds. Operator artifact — not for upload.
- Use when: Scoring any Solaria answer 0-5 on 10 criteria (business interpretation through concise clarity) with hard floors on edition accuracy and uncertainty handling; includes the scoring sheet and release bars.
- Do not use when: As Odoo knowledge.
- Authority: testing_artifact · Evidence: testing_only

**`8004__TESTING__red_team_tests.md`**
- Title: `Context Manifest / Knowledge Base Rules (adversarial suite)`
- Description: Red-team suite: 15 adversarial probes with safe patterns, failure patterns and anchor documents; zero critical failures required. Operator artifact — never upload.
- Use when: Adversarially probing Solaria after Batch 3: 15 questions targeting overclaiming, edition confusion, custom-first, concept-as-product, caveat-stripping, code-first and compliance promises; 6 critical probes gate at zero failures.
- Do not use when: Uploading to Solaria (would let it study for the exam).
- Authority: testing_artifact · Evidence: testing_only

**`8005__TESTING__simulated_answer_benchmark.md`**
- Title: `Context Manifest / Knowledge Base Rules (benchmark)`
- Description: Simulated answer benchmark: 10 reference outlines with supporting documents and red flags, for human testers to compare Solaria's real answers against. Operator artifact — never upload.
- Use when: Comparing Solaria answers to 10 ideal outlines (quote-to-cash, editions, approvals, demos, AI CV screening, customization, Studio-vs-custom, AI safety, FSM, validation protocol) with supporting documents and red flags per question.
- Do not use when: Uploading to Solaria; as Odoo knowledge (outlines are test references).
- Authority: testing_artifact · Evidence: testing_only

**`8006__TESTING__solaria_acceptance_test_script_v2.md`**
- Title: `Context Manifest / Knowledge Base Rules (acceptance tests)`
- Description: Operator acceptance-test script: 12 batch-aligned questions with good/bad answer criteria, the documents Solaria should use, per-question fix actions and scoring thresholds for releasing to consultants.
- Use when: Testing Solaria after each batch: 12 batch-aligned questions with good/bad answer patterns, expected documents and per-question fix actions; scoring rules.
- Do not use when: As Odoo knowledge (the answers are patterns, not facts).
- Authority: testing_artifact · Evidence: testing_only

**`8007__TESTING__solaria_test_questions.md`**
- Title: `Context Manifest / Knowledge Base Rules (validation set)`
- Description: 15 acceptance-test questions for validating the configured Solaria (quote-to-cash, edition splits, customization challenges, demos, AI governance, methodology), each with expected answer pattern, documents Solaria should use, and warning signs of a bad answer.
- Use when: Testing Solaria after each upload batch: 15 questions with expected patterns, documents that should be used, and warning signs.
- Do not use when: As Odoo knowledge (expected answers are patterns, not full facts).
- Authority: testing_artifact · Evidence: testing_only


## UPLOAD_GUIDE

**`8500__UPLOAD_GUIDE__batch_1_exact_upload_checklist_v2.md`**
- Title: `Context Manifest / Knowledge Base Rules (upload checklist)`
- Description: Exact Batch-1 upload checklist: the 6 governance documents with pasteable Solaria descriptions, upload order, expected post-upload behaviour and 3 acceptance-test questions with pass/fail criteria. Operator document.
- Use when: Uploading Batch 1 (6 governance files): exact order, pasteable description per file, expected behaviour and a 3-question acceptance test with pass/fail criteria.
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8501__UPLOAD_GUIDE__batch_1_manifest.json`**
- Title: `Context Manifest / Knowledge Base Rules (upload manifest)`
- Description: Exact Batch-1 upload manifest (JSON): 6 governance documents with upload order, paste-ready descriptions, expected effect on Solaria, acceptance-test questions and pass/fail criteria. Operator artifact — not for upload.
- Use when: Uploading Batch 1: the 6 governance files with order, pasteable descriptions, expected effects, acceptance questions and pass/fail criteria.
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8502__UPLOAD_GUIDE__batch_2_exact_upload_checklist_v2.md`**
- Title: `Context Manifest / Knowledge Base Rules (upload checklist)`
- Description: Exact Batch-2 upload checklist: the 5 navigation/evidence files with pasteable descriptions, the capability each adds, and 3 acceptance-test questions with pass/fail criteria. Operator document.
- Use when: Uploading Batch 2 (catalog, domain map, dependency map, AI map, priorities): descriptions, expected capability gains, 3 acceptance tests.
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8503__UPLOAD_GUIDE__batch_2_manifest.json`**
- Title: `Context Manifest / Knowledge Base Rules (upload manifest)`
- Description: Exact Batch-2 upload manifest (JSON): 5 navigation/evidence documents with order (module catalog last + retrieval-risk mitigation), descriptions, expected effects, tests and pass/fail criteria. Operator artifact — not for upload.
- Use when: Uploading Batch 2: the 5 navigation/evidence files (catalog last, with its size-risk mitigation), descriptions, tests, pass/fail criteria.
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8504__UPLOAD_GUIDE__batch_3_functional_summary_selection_v2.md`**
- Title: `Context Manifest / Knowledge Base Rules (upload checklist)`
- Description: Batch-3 selection: 14 module functional summaries (sale, account, crm, stock, purchase, mrp, project, hr_recruitment, helpdesk, documents, sign, sale_subscription, industry_fsm, website_sale) with per-file rationale, description template and spot-test questions. Operator document.
- Use when: Uploading the first 14 module functional summaries (summaries only): per-file rationale, description template and a 10-second spot-test question each.
- Do not use when: As Odoo knowledge; not a recommendation to bulk-upload module evidence files.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8505__UPLOAD_GUIDE__batch_3_manifest.json`**
- Title: `Context Manifest / Knowledge Base Rules (upload manifest)`
- Description: Exact Batch-3 upload manifest (JSON): 18 files — functional summaries only plus the AI pack's summary and governance doc — with order, descriptions, per-file test questions and pass/fail criteria. Supersedes the V2 selection. Operator artifact — not for upload.
- Use when: Uploading Batch 3: 18 functional summaries incl. platform rungs (web_studio, base_automation) and the AI pack unit, with per-file tests. Supersedes the V2 14-file selection.
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8506__UPLOAD_GUIDE__batch_4_later_evidence_manifest.json`**
- Title: `Context Manifest / Knowledge Base Rules (later-evidence manifest)`
- Description: Batch-4 later-evidence manifest (JSON): evidence files grouped by use case with explicit demand triggers and first candidates — uploaded per module per need, never in bulk. Operator artifact — not for upload.
- Use when: Deciding later evidence uploads: file categories grouped by use case (technical validation, security/roles, workflow design, UI/demo, customization, AI governance, methodology, remaining summaries) with triggers and first candidates.
- Do not use when: As a recommendation to bulk-upload; as Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8507__UPLOAD_GUIDE__context_overload_strategy.md`**
- Title: `Context Manifest / Knowledge Base Rules (context governance)`
- Description: Context-overload strategy: why staged uploads, overload/underload signals, expansion triggers, hard volume limits and the 6-probe retrieval-quality checklist run after every expansion. Operator artifact — not for upload.
- Use when: Managing Solaria's corpus: overload/underload signals, expansion triggers, the retrieval-quality checklist (6 probes after every expansion), hard limits (29 first, <=10 per step, ~60 ceiling).
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8508__UPLOAD_GUIDE__do_not_upload_initially_v2.md`**
- Title: `Context Manifest / Knowledge Base Rules (operator guardrail)`
- Description: Guardrail list of files not to upload initially (usage companions, reports, bulk evidence files) with the demand-triggers that justify each later upload and a volume guardrail. Protects retrieval quality. Operator document.
- Use when: Deciding what to keep OUT of Solaria initially and which triggers justify each later upload; includes the volume guardrail.
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8509__UPLOAD_GUIDE__do_not_upload_manifest.md`**
- Title: `Context Manifest / Knowledge Base Rules (guardrail — authoritative)`
- Description: Authoritative do-not-upload manifest: never-upload categories (usage files, index, reports, operator/test documents, prompt copies, source folders) with reasons, plus the demand-gated not-now list. Operator artifact — not for upload.
- Use when: Checking what must never or not-yet be uploaded (usage companions, reports, operator docs, test suites, prompt copies, source folders) and why.
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8510__UPLOAD_GUIDE__document_description_copy_paste.md`**
- Title: `Context Manifest / Knowledge Base Rules (upload aid)`
- Description: Copy-paste-ready Solaria description texts for every important document in the pack, with upload priorities and authority levels, plus templates for module evidence files. For the human uploader.
- Use when: Uploading documents: copy the matching description into Solaria's description field.
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8511__UPLOAD_GUIDE__document_descriptions_batch_1.md`**
- Title: `Context Manifest / Knowledge Base Rules (paste sheet)`
- Description: Batch-1 paste sheet: exact Solaria document titles and descriptions with authority and routing guidance for the 6 governance files. Operator artifact — not for upload.
- Use when: Pasting Batch-1 titles and descriptions: exact Solaria title + description + authority + use/don't-use per file.
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8512__UPLOAD_GUIDE__document_descriptions_batch_2.md`**
- Title: `Context Manifest / Knowledge Base Rules (paste sheet)`
- Description: Batch-2 paste sheet: exact Solaria titles and descriptions for the 5 navigation/evidence files, with the catalog-last ordering note. Operator artifact — not for upload.
- Use when: Pasting Batch-2 titles and descriptions (catalog-last note included).
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8513__UPLOAD_GUIDE__document_descriptions_batch_3.md`**
- Title: `Context Manifest / Knowledge Base Rules (paste sheet)`
- Description: Batch-3 paste sheet: exact Solaria titles and descriptions for the 18 functional-summary/AI files, with AI review flags. Operator artifact — not for upload.
- Use when: Pasting Batch-3 titles and descriptions for all 18 files (AI items flagged for the review checkbox).
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8514__UPLOAD_GUIDE__future_upload_roadmap.md`**
- Title: `Context Manifest / Knowledge Base Rules (roadmap)`
- Description: Future upload roadmap: staged plan (demo builds, technical deep-dives, security design, AI strategy, methodology, remaining summaries) with explicit triggers per stage. Operator artifact — not for upload.
- Use when: Planning uploads beyond Batch 3: stages 0-8 (immediate through remaining summaries) each with explicit triggers; never/exclusion pointer; monthly governance.
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8515__UPLOAD_GUIDE__human_go_no_go_checklist.md`**
- Title: `Context Manifest / Knowledge Base Rules (go/no-go gate)`
- Description: The binary human go/no-go checklist for the Solaria upload: pre-flight (repo, branch, no source code), global context, per-batch gates with test thresholds, AI governance review, release rules. Any unchecked box = stop. Operator artifact — not for upload.
- Use when: Gating the entire upload: binary checkboxes for repo/branch hygiene, source-code exclusion, context pasted, per-batch gates, AI review, caveat communication and live-validation rules. Any unchecked box stops the section.
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8516__UPLOAD_GUIDE__readme.md`**
- Title: `Context Manifest / Knowledge Base Rules (V3 operator guide — authoritative)`
- Description: Authoritative V3 operator guide for the Solaria upload: step-by-step process with per-batch acceptance gates, stop rules, Batch-4 evidence decisions and troubleshooting. Supersedes the V2 upload_ready kit for execution. Not for upload to Solaria.
- Use when: Executing the final Solaria upload: 8-step process, per-batch gates, when to stop, Batch-4 decisions, troubleshooting generic/overconfident answers. Supersedes upload_ready/ for execution.
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8517__UPLOAD_GUIDE__readme_v2.md`**
- Title: `Context Manifest / Knowledge Base Rules (operator kit)`
- Description: Step-by-step operator guide for uploading the pack to Solaria: global-context paste, batch-by-batch uploads with descriptions, per-batch testing, troubleshooting for generic answers, and expansion rules. For the human configuring Solaria — not for upload.
- Use when: Executing the Solaria upload end-to-end: the 8-step procedure, what to paste where, troubleshooting generic answers, and how to expand later.
- Do not use when: As Odoo knowledge.
- Authority: meta_quality_artifact · Evidence: not_product_evidence

**`8518__UPLOAD_GUIDE__upload_recommendations.md`**
- Title: `Context Manifest / Knowledge Base Rules (upload plan)`
- Description: Operational upload plan for this pack: 5 batches (behaviour → navigation → module narratives → evidence → playbooks), what to withhold, per-batch test focus and maintenance guidance. Primarily for the human maintainer.
- Use when: Planning/executing the Solaria upload: batches, what not to upload, testing per batch, maintenance.
- Do not use when: Odoo content questions.
- Authority: meta_quality_artifact · Evidence: not_product_evidence


## META_QUALITY

**`9000__META_QUALITY__evidence_and_claims_audit.md`**
- Title: `Context Manifest / Knowledge Base Rules (claims audit)`
- Description: V2 evidence-and-claims audit: fixes applied (exact dependency rows, uncataloged reference removed, security-evidence rendering corrected, behaviour vocabulary hardened), clean checks (no unsupported standard-Odoo claims; AI concepts consistently labeled) and the remaining caveated watchlist. Maintainer document.
- Use when: Reviewing which overclaim risks were found and fixed in V2 (issue → file → fix → residual risk) and which honest unknowns remain on the watchlist.
- Do not use when: Odoo capability questions.
- Authority: meta_quality_artifact · Evidence: meta_only

**`9001__META_QUALITY__file_type_compliance_report.md`**
- Title: `Context Manifest / Knowledge Base Rules (compliance)`
- Description: Generated compliance listing of every file in the solaria folder confirming only supported extensions (.md .json .yaml .yml .txt .html .xml) are present.
- Use when: Verifying all pack files use Solaria-supported extensions.
- Do not use when: Anything else.
- Authority: meta_quality_artifact · Evidence: meta_only

**`9002__META_QUALITY__inventory_and_extraction_plan.md`**
- Title: `Context Manifest / Knowledge Base Rules (inventory annex)`
- Description: Documents the sources behind this pack: Odoo Community 19.0 final (650 modules incl. server layer) and Enterprise 19.0 add-ons snapshot 2026-07-02 (772 modules), version evidence, extraction method, coverage and risks. Use for 'how was this built / what are its limits' questions.
- Use when: Questions about what sources this pack was built from, version confirmation, module counts, method, coverage limits and risks.
- Do not use when: Module capability questions (use domain map/module packs).
- Authority: meta_quality_artifact · Evidence: meta_only

**`9003__META_QUALITY__quality_control_report.md`**
- Title: `Context Manifest / Knowledge Base Rules (quality control)`
- Description: Quality-control report of this pack iteration: coverage (26 deep packs of 1,422 modules), known gaps, uncertainty areas, hallucination risks, raw-code and sensitive-data checks, recommended manual reviews and next-iteration plan. Use to answer 'what are this pack's limits'.
- Use when: Questions about pack completeness, known gaps, uncertainty areas, hallucination risks and recommended manual checks.
- Do not use when: Odoo capability questions.
- Authority: meta_quality_artifact · Evidence: meta_only

**`9004__META_QUALITY__v2_final_release_notes.md`**
- Title: `Context Manifest / Knowledge Base Rules (release notes)`
- Description: V2 release notes of the Deloitte Odoo Intelligence Pack: what changed and why, new module packs (incl. the consolidated AI evidence pack), hardened behaviour rules, the upload-ready kit, acceptance-test plan, known limitations and the next-iteration backlog.
- Use when: A summary of everything V2 changed: improvements, new files, modified files, upload order, acceptance plan, known limitations, iteration-3 backlog.
- Do not use when: Odoo capability questions.
- Authority: meta_quality_artifact · Evidence: meta_only

**`9005__META_QUALITY__v2_initial_audit_report.md`**
- Title: `Context Manifest / Knowledge Base Rules (V2 audit)`
- Description: V2 audit of the pack: verified strengths, findings (approximated dependency rows, one uncataloged module reference, security-table misrepresentation, upload-kit gap), fix plan and priority ranking. Maintainer document.
- Use when: Understanding what V2 reviewed, which weaknesses were found (strengths, generic spots, evidence breaches) and the priority ranking of improvements.
- Do not use when: Odoo capability questions.
- Authority: meta_quality_artifact · Evidence: meta_only

**`9006__META_QUALITY__v2_module_improvement_report.md`**
- Title: `Context Manifest / Knowledge Base Rules (V2 module worklog)`
- Description: V2 module worklog: 14 packs reviewed, dependency/claims fixes applied corpus-wide, security summaries regenerated, purchase strengthened, 9 new packs added (finance depth, platform, supply-chain depth, consolidated AI), and the iteration-3 candidate list. Maintainer document.
- Use when: Knowing which module packs were reviewed/improved in V2, what changed per document, what was deliberately left unchanged, and next candidates.
- Do not use when: Module capability questions (use the packs).
- Authority: meta_quality_artifact · Evidence: meta_only

**`9007__META_QUALITY__v2_self_check.md`**
- Title: `Context Manifest / Knowledge Base Rules (self-check)`
- Description: V2 final self-check: pass/fail with evidence for the 11 release-gate questions (code-free outputs, supported file types, registry/usage completeness, upload readiness, edition and AI discipline, standard-first stance, caveat coverage, and whether the new packs add real value). Maintainer document.
- Use when: Verifying the V2 release gate: 11 checks (raw code, file types, descriptions, registry, usage files, upload practicality, edition boundaries, AI separation, standard-first stance, caveats, pack value) with pass/fail evidence.
- Do not use when: Anything else.
- Authority: meta_quality_artifact · Evidence: meta_only

**`9008__META_QUALITY__v3_final_preupload_report.md`**
- Title: `Context Manifest / Knowledge Base Rules (V3 release report)`
- Description: V3 final pre-upload report: everything the gate produced (manifests, FINAL prompt, description sheets, acceptance/red-team suites, rubric, benchmark, overload strategy, roadmap, go/no-go checklist), exact batch lists, remaining risks and the conditional-go recommendation with the next human action. Maintainer document.
- Use when: The V3 summary: what changed, exact Batch 1/2/3 lists, exclusions, acceptance approach, remaining risks, the final go recommendation and the next human action.
- Do not use when: Odoo capability questions.
- Authority: meta_quality_artifact · Evidence: meta_only

**`9009__META_QUALITY__v3_preupload_readiness_audit.md`**
- Title: `Context Manifest / Knowledge Base Rules (V3 gate audit)`
- Description: V3 pre-upload readiness audit: conditional-go verdict, exact first uploads, batch-size judgments (6/5/18), contradictions resolved (Batch-3 expansion to include platform rungs and the AI unit; final prompt supersedes 91), AI-safety assessment, repo cleanup (stray staged junk files removed) and remaining gate concerns. Maintainer document.
- Use when: Understanding the V3 readiness verdict: batch-size judgments, contradictions found and resolved (Batch-3 expansion, prompt supersession), AI-document safety assessment, repo-hygiene fixes and remaining go/no-go concerns.
- Do not use when: Odoo capability questions.
- Authority: meta_quality_artifact · Evidence: meta_only

**`9010__META_QUALITY__v3_self_check.md`**
- Title: `Context Manifest / Knowledge Base Rules (V3 self-check)`
- Description: V3 final self-check: pass/fail evidence for the 15 pre-upload gate checks (supported file types, code-free outputs, upload-package completeness, manifests and test suites present, registry and usage companions updated). Maintainer document.
- Use when: Verifying the V3 release gate: 15 checks (file types, no raw code, package completeness, manifests, prompt, descriptions, test suites, rubric, strategy, checklist, registry, usage companions, final report) with pass/fail evidence.
- Do not use when: Anything else.
- Authority: meta_quality_artifact · Evidence: meta_only

**`9999__META_QUALITY__flat_upload_packaging_report.md`**
- Title: `Flat Upload — Packaging Report (META/QUALITY)`
- Description: Meta/quality report of the flattening step: files scanned/copied/excluded, category counts, validation results, next actions. Not Odoo product evidence.
- Use when: Understanding how this package was built and validated.
- Do not use when: As Odoo product evidence.
- Authority: meta_quality_artifact · Evidence: meta_only
