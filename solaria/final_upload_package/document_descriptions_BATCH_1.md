# Batch 1 — Exact Document Titles & Descriptions (paste sheet)

For each file: upload → set title → paste description → save. Do not improvise wording. Paths relative to `solaria/`.

---

## 1. `00_solaria_role_and_answering_rules.md`
- **Solaria title:** `Odoo Advisor — Behaviour & Answering Rules (highest authority)`
- **Description (paste):** Highest-authority behaviour rules. Use in every Odoo answer to enforce business-first reasoning, the standard-before-custom ladder, Community/Enterprise separation, the controlled evidence vocabulary and the generic-answer kill-switch. Do not use as evidence of product capabilities. Overrides any conflicting document.
- **Authority:** Highest.
- **Use when:** Always — governs every answer.
- **Do not use when:** Never as product evidence.

## 2. `00_context_manifest_and_usage_rules.md`
- **Solaria title:** `Odoo Knowledge Pack — Routing & Trust Manifest (highest authority)`
- **Description (paste):** Master guide to this knowledge pack. Use to decide which document answers which question: document hierarchy, source hierarchy, routing logic, conflict and uncertainty rules, client-facing vs internal behaviour. Consult before answering from other documents. Do not use as product knowledge.
- **Authority:** Highest (with role rules).
- **Use when:** Choosing documents, resolving conflicts, handling missing evidence.
- **Do not use when:** As a source of Odoo capabilities.

## 3. `00_document_type_usage_templates.md`
- **Solaria title:** `Odoo Knowledge Pack — Document Types & Authority Levels`
- **Description (paste):** Defines the 11 document types of this pack (behaviour, manifest, playbook, index, domain map, functional summary, source evidence, security evidence, decision framework, demo, visual) with authority levels and combination rules. Use when weighing how much authority a retrieved document carries. Do not use for product facts.
- **Authority:** High (governance).
- **Use when:** Grading trust in a retrieved document.
- **Do not use when:** Content questions.

## 4. `03_community_vs_enterprise_map.md`
- **Solaria title:** `Odoo 19.0 — Community vs Enterprise Boundary Map`
- **Description (paste):** High-authority map of the Odoo 19.0 Community vs Enterprise boundary per business domain, from source analysis of both trees (Enterprise = add-ons-only layer). Use for every edition question and for phrasing edition uncertainty. Do not use for what a client subscription includes — always commercial validation.
- **Authority:** High for edition questions.
- **Use when:** Any Community/Enterprise question; edition implications for advisory and demos.
- **Do not use when:** Licensing/pricing contents; module-internal details.

## 5. `05_standard_vs_configuration_vs_custom_framework.md`
- **Solaria title:** `Deloitte Framework — Standard vs Configuration vs Studio vs Custom vs Integration`
- **Description (paste):** Deloitte decision framework for Odoo 19.0 solutioning: Standard, Configuration, Studio (Enterprise), Automation, Custom development, External integration — with classification tests, red flags and a decision tree. Use for every customization, build-vs-configure and integration question. Do not use to prove a feature exists — pair with catalog or module evidence.
- **Authority:** High for advisory recommendations.
- **Use when:** Any "can/should we customize/build/integrate" question.
- **Do not use when:** Feature-existence proof.

## 6. `00_document_usage_registry.json`
- **Solaria title:** `Odoo Knowledge Pack — Document Usage Registry (machine-readable)`
- **Description (paste):** Machine-readable registry of every document in the Deloitte Odoo Intelligence Pack: type, authority, when to use / not use, combinations, limitations, confidence. Use to route questions to the right documents and to answer "which documents did you use". Do not use as product knowledge.
- **Authority:** High (routing/governance).
- **Use when:** Routing; self-explanation of sources; checking a document's limits.
- **Do not use when:** As content.
