# Batch 1 — Exact Upload Checklist (Governance & Reasoning Core)

**Goal:** after this batch, Solaria answers *in the right way* (structure, edition discipline, caution) even before it has deep module knowledge.
**Prerequisite:** global context pasted from `91_solaria_global_context_prompt.txt` (see kit README step 1).

## Upload these 6 files, in this order, with these exact descriptions

### 1. `00_solaria_role_and_answering_rules.md`
**Why:** the behaviour constitution — everything else assumes it.
**Description to paste:**
> Highest-authority behaviour rules for acting as Deloitte's senior Odoo 19.0 Strategic Partner advisor. Follow in every answer: business-first 11-step structure, standard-before-custom ladder, Community/Enterprise separation, controlled evidence vocabulary, generic-answer kill-switch, no overclaiming. These rules override any conflicting document.

### 2. `00_context_manifest_and_usage_rules.md`
**Why:** tells Solaria which document to trust for which question.
**Description to paste:**
> Master guide to the Deloitte Odoo Intelligence Pack: document hierarchy, source hierarchy, retrieval/routing logic, conflict and uncertainty rules, client-facing vs internal behaviour. Consult before answering from other documents. Highest authority together with the role rules.

### 3. `00_document_type_usage_templates.md`
**Why:** defines the 11 document types and their authority weights.
**Description to paste:**
> Defines the 11 document types of this pack (behaviour, manifest, playbook, index, domain map, functional summary, source evidence, security evidence, decision framework, demo, visual) with authority levels, when-to-use rules and example descriptions. Use when weighing how much authority a retrieved document carries.

### 4. `03_community_vs_enterprise_map.md`
**Why:** the edition question appears in almost every Odoo conversation.
**Description to paste:**
> High-authority map of the Odoo 19.0 Community vs Enterprise boundary per business domain, from manifest-level analysis of both source trees (Enterprise = add-ons-only layer). Use for every edition question and for phrasing edition uncertainty. Subscription contents remain a commercial validation point.

### 5. `05_standard_vs_configuration_vs_custom_framework.md`
**Why:** the customization ladder is Deloitte's core advisory stance.
**Description to paste:**
> Deloitte decision framework for Odoo 19.0 solutioning: Standard → Configuration → Studio (Enterprise) → Automation → Custom development → External integration, with classification tests, red flags, Studio governance and a decision tree. Apply to every customization question, combined with module-level evidence.

### 6. `00_document_usage_registry.json`
**Why:** lets Solaria explain and route its own knowledge base.
**Description to paste:**
> Machine-readable registry of every document in the Deloitte Odoo Intelligence Pack: type, authority, upload priority, when to use / not use, combinations, limitations and confidence notes. Use to route questions and to answer "which documents did you use".

## Expected Solaria behaviour after Batch 1
- Structured answers (business interpretation first, recommendation last) with edition tags and validation caveats.
- Openly limited on module depth ("the functional summaries are not yet loaded") rather than inventing specifics — that honesty is a PASS signal, not a failure.

## Acceptance test (all 3 must pass)

**Q1. "Should we customize an approval flow or use standard Odoo?"**
- **PASS:** challenges the requirement; walks the ladder; names the Approvals app as Enterprise and native per-app steps; distinguishes advisory vs blocking; ends with validation questions.
- **FAIL:** jumps to "build a custom module", or gives an edition-free generic answer.

**Q2. "Is Odoo Studio included in Odoo?"**
- **PASS:** Studio = Enterprise-only (`web_studio`); Community lacks rung 3; subscription contents = commercial validation.
- **FAIL:** "yes, Odoo includes Studio" without edition qualification.

**Q3. "Which documents did you use for that last answer?"**
- **PASS:** names actual pack documents (e.g., the framework 05, the C-vs-E map) with their roles.
- **FAIL:** cannot name documents or invents titles.

**If any question fails:** check the file's description was pasted (most common miss), then re-ask once; if still failing, see kit README troubleshooting §"generic answers".
