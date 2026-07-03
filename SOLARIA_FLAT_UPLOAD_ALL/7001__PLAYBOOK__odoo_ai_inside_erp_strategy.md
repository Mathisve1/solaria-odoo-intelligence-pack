# AI Inside the ERP — Deloitte Odoo Strategy Playbook

| Attribute | Value |
|---|---|
| Document type | Strategy / Deloitte Advisory Playbook (AI) |
| Authority level | High for strategy/governance method; capability claims defer to `06_odoo_ai_opportunity_map.md` (source-verified inventory) |
| Version scope | Odoo 19.0 |

## 1. The thesis
AI creates ERP value when it lives **inside the process** — at the moment of work, on governed business data — not in external chat tabs fed with screenshots and exports. Odoo 19.0 Enterprise makes this concrete: a native AI layer (agents, AI fields, AI server actions, domain assists, OCR family — all verified at module level in this pack) sits directly on the transactional data model. Deloitte's role: turn that raw capability into governed, role-shaped, measurable copilots.

## 2. Closed ERP vs external AI tools
| Dimension | AI inside Odoo | External AI tools on the side |
|---|---|---|
| Data boundary | stays in the platform (validate IAP/model hosting!) | copy-paste/exports leak context and control |
| Permissions | can inherit record-level security (must be tested) | typically none |
| Actionability | can act (create records, fields, server actions) | advice only, human re-types |
| Auditability | traceable in chatter/logs if designed | invisible |
| Governance | one register, one owner | shadow AI sprawl |
The honest caveats stay: model quality, hosting/region, IAP metering and pgvector prerequisites are validation items, not assumptions.

## 3. The four Deloitte concepts (label as concepts, always)
1. **Company Brain** — a governed assistant grounded on curated Knowledge articles + Documents + key records ("how do we handle returns over 500€?", "status of order 1042?"). Native foundation: `ai_app` agents + `ai_documents_source`/`ai_knowledge`. Deloitte layer: corpus curation standards, access inheritance testing, answer-quality metrics, escalation to humans.
2. **Operations Copilot** — role-embedded assistance at process moments: AP clerk (bill exceptions queue), sales rep (account briefing before a call), planner (exception explanations). Native foundation: AI fields, AI server actions, OCR validation queues. Deloitte layer: per-role prompt/agent design, acceptance-rate KPIs.
3. **Alerts Center** — one governed exception inbox (margin dips, SLA risk, credit exposure, stock anomalies, close anomalies). Foundation: automation rules + scheduled actions (deterministic first), AI for ranking/explanation only. Deloitte layer: alert taxonomy, ownership, threshold governance, fatigue management.
4. **Role Assistants** — persona-scoped variants (CFO monthly narrative, CRO pipeline hygiene, COO backlog risk) with explicit data contracts and sign-off rituals.

## 4. Governance framework (the Deloitte deliverable)
- **AI register:** every agent/AI field/AI server action inventoried (purpose, data scope, owner, model/endpoint, review date).
- **Data boundaries:** what leaves the environment (IAP endpoints, model hosting/region, retention) — contractually validated; pgvector/hosting prerequisites documented.
- **Human-in-the-loop:** default for anything touching money, people or customers; autonomy only after measured quality + explicit sign-off; posting/tax/reservation logic stays deterministic — always.
- **Access inheritance testing:** AI answers must not leak records the asker cannot open (test protocol before enabling agents on documents/knowledge).
- **Regulatory:** EU AI Act mapping (recruitment/worker-related AI = high-risk: documented criteria, human decision, transparency to candidates); privacy impact assessments where personal data is processed.
- **Quality ops:** acceptance/correction-rate metrics per assist; periodic prompt/agent review; incident path for bad outputs.

## 5. Implementation path
1. **Phase 0 — readiness:** master-data hygiene, adopted standard processes, Knowledge/Documents corpus baseline. AI on chaos amplifies chaos.
2. **Phase 1 — native quick wins (weeks):** OCR family (bills, statements, expenses, CVs), AI drafts, document auto-sorting — measurable, low-risk, all with validation queues.
3. **Phase 2 — first copilot (one role):** narrow scope, human-in-the-loop, KPIs from day one.
4. **Phase 3 — Alerts Center:** deterministic rules first, AI ranking second.
5. **Phase 4 — Company Brain:** after corpus governance exists; pilot group, leakage tests, then scale.
6. **Continuous:** register reviews, model/prompt versioning, value reporting.

## 6. Demo ideas (rules from the demo playbook apply)
- Vendor bill PDF → OCR → validation queue → posted (native, live).
- "Sort this messy documents inbox" (native ai_documents, live, show review step).
- Recruiter: CV → parsed applicant → AI summary → human decision recorded (native + governance narrative).
- Company Brain concept: scripted mockup answering a policy + a status question — explicitly labeled concept.

## 7. Risks and honesty list
- Module existence ≠ output quality — pilot before promising (the pack verifies existence only).
- IAP = pay-per-use economics; include in run-rate.
- Model/hosting specifics not source-derivable — contract-level validation.
- Adoption risk: assistants that are wrong twice get abandoned — quality gates before rollout.
- Overreach risk: AI in deterministic domains (tax, posting, reservation) is an audit finding, not innovation.

## 8. Where Odoo standard ends and custom AI begins
Standard (E): the module inventory in 06 §1. Configuration: agents/AI fields/server actions within shipped tooling. Custom: external model orchestration, event-stream triggers, bespoke UIs, cross-system copilots. Integration: enterprise LLM platforms/CDPs where group architecture mandates. Apply the 05 ladder to AI exactly like any other capability.

## 9. Deloitte positioning
Deloitte sells **governed AI-in-ERP transformation**: readiness (data/process), native activation, copilot design, governance/compliance (AI Act), value measurement. The differentiator is not building AI demos — it is making AI auditable, adopted and boring enough to trust.
