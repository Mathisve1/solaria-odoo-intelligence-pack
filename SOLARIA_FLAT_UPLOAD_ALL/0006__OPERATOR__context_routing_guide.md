# Context Routing Guide — How Solaria Should Read Filename Categories

Every flat file starts with `[ORDER]__[CATEGORY]__…`. The **CATEGORY** tells Solaria what kind of document it is and how much to trust it. This guide is also worth pasting into Solaria's context (or summarizing in the global context) so the model honours the categories.

## Authority order (highest first)
1. **CORE_RULES** — behaviour, routing manifest, document-type templates. **These override every lower-level document.** They define business-first reasoning, the standard-before-custom ladder, Community/Enterprise discipline, the evidence vocabulary and the generic-answer kill-switch.
2. **GLOBAL_CONTEXT** — the paste-in prompt. Same authority as CORE_RULES; it is configuration, not a knowledge document.
3. **SOURCE_HIERARCHY** — Community-vs-Enterprise map and the document usage registry. Authority on editions and on which document to trust.
4. **DECISION_FRAMEWORK** — the standard/configuration/Studio/custom/integration ladder. Authority on *how to decide*, not on what exists.

## Evidence and knowledge layers
5. **MODULE_CATALOG** — the authority on **what modules exist and in which edition** (all 1,422). Never cite a module absent from it.
6. **GLOBAL_MAP** — dependency map and priority/coverage index. Architecture and coverage awareness.
7. **DOMAIN_MAP** — routes business problems to domains and candidate modules.
8. **MODULE** — functional summaries, standard_vs_custom, READMEs. **Primary source for business/functional answers** about a module. Interpretation of 19.0 source structure; behaviour needs live validation.
9. **MODULE_EVIDENCE** — models.json, views/security/workflow summaries. **Supports technical validation and implementation scoping, NOT business-first answers.** Proves that structures exist; does not prove runtime behaviour or UX. On *existence* questions this beats narrative; on *meaning* questions the MODULE functional summary beats this.
10. **AI** — the native AI inventory, functional summary, governance doc and opportunity map. Keep the four-way separation: native-verified / Deloitte-concept / custom-opportunity / validation-required. Never present a Deloitte concept as an Odoo product feature.

## Advisory and human-facing layers
11. **PLAYBOOK** — Deloitte advisory method (fit-gap, demo, roadmap, discovery, positioning, AI strategy). Use for framing and method. **Do not treat as source evidence** that a feature exists.
12. **EXECUTIVE / CONSULTANT** — orientation for how humans use Solaria. Not product evidence.
13. **UPLOAD_GUIDE** — operator process (upload plans, checklists, descriptions). Not product knowledge.

## Non-product layers (must never become answer content)
14. **TESTING** — acceptance suites, red-team probes, rubric, benchmark, test questions. **For evaluating Solaria, not for answering questions.** If asked something that matches a test, answer from the knowledge documents, not from the test's expected-answer text.
15. **META_QUALITY** — audit, QC, compliance, release and self-check reports, plus the build/inventory plan. **Describes the pack's own quality and limits — NOT Odoo product evidence.** Use only to explain pack coverage, known risks or how the pack was built.

## Hard rules to repeat in every answer
- **META_QUALITY is not product evidence. TESTING is not answer content. MODULE_EVIDENCE is technical-validation support, not business-first answers.**
- **CORE_RULES and GLOBAL_CONTEXT override lower documents** on any conflict.
- Respect **Community vs Enterprise** and **standard vs configuration vs Studio vs automation vs custom vs integration** boundaries at all times.
- Existence is proven by MODULE_CATALOG / MODULE_EVIDENCE; **behaviour is never proven by this pack** — it needs live Odoo 19.0 validation.
