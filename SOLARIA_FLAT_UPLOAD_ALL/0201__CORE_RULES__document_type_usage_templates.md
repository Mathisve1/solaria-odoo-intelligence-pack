# Document Type Usage Templates — Solaria Odoo Intelligence Pack

| Attribute | Value |
|---|---|
| Document type | Context Manifest / Knowledge Base Rules |
| Authority level | High |
| Purpose | Standard usage template per document type; source for every `.usage.md` and registry entry |

Each document in this pack belongs to one of the 11 types below. When uploading a document to Solaria, use the matching template to write its description/usage instruction.

---

## 1. Behaviour / Agent Rules
- **Authority:** Highest — governs every answer.
- **Use when:** Always active; shapes reasoning, structure, caution and tone.
- **Do not use when:** Never treated as evidence of Odoo functionality.
- **Combine with:** Everything — it tells Solaria how to use the rest.
- **Limitations:** Contains no product facts.
- **Example description:** "Highest-authority behaviour rules. Follow these rules in every answer: business-first structure, standard-before-custom, Community/Enterprise separation, explicit uncertainty marking. These rules override any conflicting document."

## 2. Context Manifest / Knowledge Base Rules
- **Authority:** Highest (with type 1).
- **Use when:** Deciding which document to trust, how to route a question, how to resolve conflicts.
- **Do not use when:** As a source of module capabilities.
- **Combine with:** The registry JSON for machine-readable routing.
- **Limitations:** Describes the pack, not Odoo.
- **Example description:** "Master guide to this knowledge pack: document hierarchy, source hierarchy, routing logic, conflict and uncertainty rules. Consult before answering from other documents."

## 3. Strategy / Deloitte Advisory Playbook
- **Authority:** High for advisory method and framing; medium for anything product-related.
- **Use when:** Fit-gap method, demo preparation, positioning, roadmaps, discovery, AI-in-ERP strategy.
- **Do not use when:** Verifying that a specific Odoo feature exists — that needs catalog/module evidence.
- **Combine with:** Functional summaries (for the facts) + standard-vs-custom framework (for the recommendation logic).
- **Limitations:** Methodology and concepts, not source proof; examples are illustrative, not commitments.
- **Example description:** "Deloitte advisory playbook. Use for methodology and client framing. Do not cite as proof of Odoo functionality; validate feature claims against the module catalog and functional summaries."

## 4. Index / Navigation Document
- **Authority:** Medium — routing only.
- **Use when:** Finding which module/document covers a topic (catalog, dependency map, priority list, index.html).
- **Do not use when:** As the sole basis for a detailed conclusion.
- **Combine with:** The module documents it points to.
- **Limitations:** Inventory-level truth (existence, dependencies, edition), not behavior.
- **Example description:** "Navigation/inventory document for the Odoo 19.0 pack. Use to locate modules and documents, confirm a module exists and in which edition. For details, open the module's own documents."

## 5. Functional Domain Map
- **Authority:** Medium-high for domain-level reasoning.
- **Use when:** Scoping which domains/modules a business problem touches; workshop and demo planning.
- **Do not use when:** Field-level or workflow-level claims.
- **Combine with:** Module functional summaries for depth; catalog for completeness.
- **Limitations:** Groups modules by business domain; individual capabilities still need module-level validation.
- **Example description:** "Domain-level map of Odoo 19.0 (CRM, Sales, Finance, Supply Chain, HR, Services, Website, …) with Community/Enterprise split, demo potential and watch-outs per domain. Use to scope solutions; go module-level for specifics."

## 6. Functional Module Summary
- **Authority:** High for business/functional questions about that module.
- **Use when:** "What does module X do / who uses it / how does it fit / what should we demo / where are the gaps?"
- **Do not use when:** Exact runtime behavior, pricing, other Odoo versions.
- **Combine with:** models.json / views / security / workflow evidence for validation; 05 framework for customization advice.
- **Limitations:** Interpretation layer on 19.0 source structure; behavior details flagged for demo-database validation.
- **Example description:** "Primary business-level reference for the <module> module in Odoo 19.0 (<edition>). Use for functional capabilities, processes, personas, fit-gap and demo angles. Validate detailed behavior against the module's evidence files."

## 7. Source-Code-Derived Evidence
- **Authority:** High for existence of models, fields, relations, menus, actions, dependencies.
- **Use when:** Verifying that a data structure/menu/report exists in 19.0; grounding functional claims.
- **Do not use when:** Inferring UX quality or exact computed behavior; answering business "why" questions on its own.
- **Combine with:** The module's functional_summary to translate structure into meaning.
- **Limitations:** Structure ≠ behavior; extraction is automated and curated but not exhaustive.
- **Example description:** "Source-derived metadata extracted from the Odoo 19.0 <module> module (models, fields, relations, menus, views). High authority on what exists; translate into business meaning using the functional summary."

## 8. Security / Access Evidence
- **Authority:** High for groups, access rights and record rules as shipped.
- **Use when:** Role design, segregation-of-duties discussions, permission questions.
- **Do not use when:** As the client's target security model — that is a design decision.
- **Combine with:** Client role requirements; implementation roadmap security workstream.
- **Limitations:** Shows shipped defaults in 19.0, not client-specific configuration.
- **Example description:** "Security groups, access rights and record rules shipped with <module> in Odoo 19.0. Use as the baseline for role design; the client's actual security model must be designed and validated per project."

## 9. Standard-vs-Custom Decision Framework
- **Authority:** High for advisory recommendations.
- **Use when:** Any "can/should we customize / is this standard / Studio or module?" question.
- **Do not use when:** It cannot prove a feature exists — pair with evidence.
- **Combine with:** Module standard_vs_custom docs (module-specific application of the framework).
- **Limitations:** Decision logic, not a feature list.
- **Example description:** "Deloitte decision framework: Standard → Configuration → Studio → Automation → Custom → External integration, with red flags and a decision tree. Apply to every customization question, combined with module-level evidence."

## 10. Demo / Storyline Document
- **Authority:** Medium — narrative guidance.
- **Use when:** Building demo scripts, storylines, personas, executive narratives.
- **Do not use when:** As technical proof; demo claims still need a rehearsal in a real 19.0 database.
- **Combine with:** views_summary (real menu paths), functional summaries (real capabilities).
- **Limitations:** Storytelling patterns; every demo must be rehearsed against an actual database.
- **Example description:** "Demo storytelling guidance. Use to structure client demos. All demo steps must be verified in a live Odoo 19.0 environment before presenting."

## 11. Visual Reference
- **Authority:** Low-medium; illustration only.
- **Use when:** Explaining what a screen/process roughly looks like.
- **Do not use when:** Inferring functionality, configuration or versions from pixels.
- **Combine with:** The module documents that describe the underlying functionality.
- **Limitations:** May be outdated or edition-specific; no visual references are included in this first pack version.
- **Example description:** "Screenshot/visual reference for illustration only. Do not derive functional or technical claims from this image."
