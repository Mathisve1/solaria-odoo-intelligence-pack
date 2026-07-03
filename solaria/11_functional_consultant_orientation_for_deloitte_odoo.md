# Functional Consultant Orientation — Working with Solaria on Odoo 19.0

| Attribute | Value |
|---|---|
| Document type | Orientation / method (internal Deloitte audience) |
| Audience | Functional consultants, business analysts, solution architects |
| Scope | Odoo 19.0 (Community + Enterprise, snapshot 2026-07-02) |

## What you have
Solaria is configured with a source-derived Odoo 19.0 knowledge pack: a catalog of all 1,422 modules (existence + edition authority), deep packs for 34 priority modules plus a consolidated native-AI evidence pack, decision frameworks and Deloitte playbooks. It follows strict rules: standard-before-custom, edition tagging, controlled evidence vocabulary, and honest coverage limits.

## How to ask good questions (the difference between gold and mush)
- **Give business context, ask for the ladder.** ✅ "Belgian wholesaler, 40 users, wants customer-specific pricing visible in a webshop — walk the standard-vs-custom ladder." ❌ "Can Odoo do pricing?"
- **Name the domain or module when you know it** ("in `sale`/eCommerce…") — you'll hit the deep pack instead of the domain map.
- **Ask for the verdict format** you need: "classify as FIT-STD/FIT-CONF/…/UNKNOWN-VALIDATE with evidence" — the fit-gap vocabulary is built in.
- **Ask one flow at a time.** Quote-to-cash, then procure-to-pay — not "explain Odoo".

## How to force evidence-based answers (your control levers)
- "**Which documents support that, and at what confidence?**" — it must cite pack documents and grade claims (confirmed in source / shipping capability—validate live / interpretation / general knowledge).
- "**Is that Community or Enterprise — and what exactly is the module name?**" — module names must exist in the catalog; call out anything unnamed.
- "**What would you validate in a live database before I put this in a deliverable?**" — turns any answer into a checklist.
- If an answer would fit any ERP, reject it and say so — the pack's own rules forbid generic answers; quoting that rule works.

## Using Solaria per activity

**Discovery workshops.** Ask for a tailored question set ("discovery questions for a food manufacturer, focus supply chain + quality") — it draws on the question bank + domain map. Log answers against domains; feed them back for a first module scoping.

**Module scoping / fit-gap.** Per requirement: normalize → ask for mapping + ladder verdict + rejected alternatives + validation step (the requirement-to-solution recipe). Batch your customization candidates and ask it to challenge them — it is deliberately opinionated there. The register stays yours; Solaria drafts, you own verdicts.

**Demo preparation.** Ask for a storyline for a named audience ("CFO, 20 minutes, quote-to-cash with finance close uplift") — expect scenes, edition labels and the rehearsal caveat. Menu-path level detail needs that module's views evidence uploaded — ask the Solaria owner if it's missing. **Never demo an unrehearsed step; the pack will remind you, take the reminder seriously.**

**Standard-vs-custom decisions.** Give it the requirement + why configuration allegedly fails; ask for the ladder walk. Expect it to propose Studio approval rules / Approvals app / automation rules before any custom verdict — that ordering is the Deloitte stance, use it in client discussions.

**Implementation planning.** Ask for phase/gate skeletons, migration state-mapping questions (workflow evidence), security-baseline questions (security evidence), watch-outs per module. It knows the roadmap template's gates, including the customization gate.

## What still requires live Odoo validation (always)
Exact runtime behavior and UX flows · computed/wizard specifics · OCR/AI output quality (pilot on client data) · performance/volumes · country statutory completeness (Deloitte tax experts) · anything licensing/pricing (commercial) · portal/offline envelopes (POS, FSM, barcode) · signature legal levels (legal). Solaria flags these; your job is to keep the flags in the deliverable and close them with a demo database, not to delete them.

## Escalation and feedback
Generic answers → troubleshooting list in `upload_ready/README.md`. Missing module depth → the module may not be uploaded/deep-packed yet (`07_priority_module_recommendation.md` says which is which) — request it from the Solaria owner. Wrong or outdated claims → report with the exact question + answer; the pack is versioned and maintained (this feedback is the iteration-3 backlog).

## The professional rule
Solaria accelerates you; it does not sign your work. Everything client-facing passes human review against a live 19.0 environment for its load-bearing claims. That discipline is not overhead — it is exactly what differentiates Deloitte's Odoo advisory.
