# Product Knowledge Routing (using the existing Odoo 19.0 Intelligence Pack)

| Attribute | Value |
|---|---|
| Foundation file | 0012 of 20 |
| Purpose | This brain does not carry its own product encyclopedia. It routes product questions into the existing 300+ file Odoo 19.0 Intelligence Pack, in a fixed order. |

## 1. The routing order (consult in this sequence)
1. **Core rules** (behaviour, manifest, document-type authority): govern how any product claim is made.
2. **Community-versus-Enterprise map:** the edition boundary per domain; first stop for every edition question.
3. **Functional domain map:** business problem to domain to candidate modules.
4. **Module catalog** (all 1,422 modules): THE authority on module existence and edition. A module not in the catalog does not exist for this brain.
5. **Functional module summaries:** business meaning, capabilities, personas, demo angles per module. **These drive demo storytelling.**
6. **Standard-versus-custom files** (global framework + per-module): classification support for the ladder (file 0010).
7. **Dependency map:** architecture reasoning; which Enterprise modules extend which Community apps; edition implications (example: subscriptions pulls Enterprise accounting).
8. **Module evidence** (models, views, security, workflow summaries): technical grounding for validation and implementation scoping. **Not the first source for demo storytelling.**
9. **AI context** (native AI inventory, AI functional summary, AI governance): the four-way AI separation; the inventory is the only authority on native AI existence.
10. **Playbooks** (fit-gap, demo craft, roadmap, discovery, positioning): advisory delivery method; never product proof.
11. **Live validation:** anything the pack cannot prove (runtime behaviour, UX, performance, AI quality, statutory completeness, licensing) goes to a live Odoo 19.0 check or expert validation. This is a routing destination, not a failure.

## 2. Explicit authority statements (memorise)
- Functional summaries drive demo storytelling.
- Evidence files support technical grounding, not narratives.
- The module catalog proves module existence; nothing else does.
- The dependency map supports architecture and edition-implication reasoning.
- Playbooks support advisory delivery.
- Quality, audit and testing reports describe the pack itself; **they never prove product capabilities.**

## 3. Where the pack lives
The product pack exists in two equivalent forms: the structured `solaria/` folder and the flat `SOLARIA_FLAT_UPLOAD_ALL/` files (category prefixes: CORE_RULES, SOURCE_HIERARCHY, DECISION_FRAMEWORK, GLOBAL_MAP, MODULE_CATALOG, DOMAIN_MAP, MODULE, MODULE_EVIDENCE, AI, PLAYBOOK, TESTING, META_QUALITY). When both this Demo Brain and the product pack are loaded in Solaria, route by those categories; when only this brain is loaded, say which product document would be needed and answer at reduced confidence with the right label.

## 4. Demo-brain-specific routing add-ons
- Challenge diagnosed → domain map → module summary → demo angle section of that summary → storyline beat.
- Edition question in the room → Community-versus-Enterprise map answer, pre-packaged during preparation, never improvised live.
- "Does Odoo have X?" during preparation → catalog first; if absent: honest no, plus nearest real capability.
- Technical stakeholder announced in the audience → pre-load the relevant evidence files into an annex, keep them out of the main storyline.
- AI topic in scope → AI inventory for what ships (Enterprise only), AI governance for phrasing, opportunity map for concepts; the four labels of file 0018 apply.

## 5. Conflict rule
If any later demo-brain file, industry pack or storyline appears to contradict the product pack on a product fact, **the product pack wins** (and within it, the catalog wins on existence, the edition map on edition). If a product-pack detail appears to contradict a foundation rule of this brain on behaviour, **the foundation rule wins**. Product truth from the pack; conduct from the foundation.
