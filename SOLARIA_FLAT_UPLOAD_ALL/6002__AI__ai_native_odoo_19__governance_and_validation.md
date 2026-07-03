# Native AI in Odoo 19.0 — Governance, Validation and Safe Phrasing

| Attribute | Value |
|---|---|
| Document type | Security/Governance evidence + advisory (AI layer) |
| Authority | High for governance method and phrasing rules; capability claims defer to `ai_module_inventory.json` |
| Scope | Everything AI in Odoo 19.0 engagements — native activation and Deloitte-built extensions |

## 1. The credibility contract (why this document exists)
One overclaimed AI demo costs more trust than ten honest ones earn. This document is the enforcement layer: what to validate, what to register, and exactly how to phrase AI capabilities to clients.

## 2. Governance risks (name them proactively)

| Risk | Reality | Control |
|---|---|---|
| Output quality variance | Source proves modules exist, not that outputs are good | Per-capability pilot on client data; acceptance/correction metrics before rollout |
| Data boundary opacity | Model hosting, region, retention are not source-derivable | Contractual validation with Odoo before processing client data |
| Access leakage via AI | Agents grounded on Documents/Knowledge may surface records the asker can't open | Leakage test protocol (§4) before enabling agents on shared corpora |
| Metered cost surprise | OCR family is IAP pay-per-use | Volume-based cost estimate in every business case |
| Infrastructure gate | pgvector required (`ai_auto_install`); hosting-model differences | Architecture check in phase 0 |
| Regulatory exposure | Recruitment/worker-related AI = EU AI Act high-risk class | Human decision, documented criteria, candidate transparency, DPIA where personal data — Deloitte compliance involvement mandatory |
| Silent scope creep | AI fields/steps added ad hoc by key users | AI register (§3) |
| Automation overreach | AI touching posting/tax/reservation/pricing execution | Hard exclusion — deterministic domains stay deterministic |

## 3. The AI register (minimum governance artifact)
One line per AI artifact (agent, prompt, AI field, AI server-action step, OCR activation): purpose · data scope (models/workspaces) · model/endpoint (as contracted) · owner · human-in-the-loop point · review date · pilot metrics. No register, no production AI — make it a project gate.

## 4. Validation protocol (before any client commitment)
1. **Gate check:** edition, pgvector/hosting, IAP budget.
2. **Pilot on real data:** ≥1 representative month of documents / ≥50 real cases; measure acceptance rate, correction rate, latency.
3. **Leakage test:** low-privilege test user asks agents for content behind their access boundary — must fail to retrieve; repeat after corpus changes.
4. **Failure drill:** what does the process do when AI is wrong/slow/down (fallback path documented).
5. **Sign-off:** process owner + (where in scope) compliance; register updated.

## 5. Demo-safe rules
- Live-demo only capabilities rehearsed the same day, with a recorded fallback.
- Always show the human validation step — frame the review queue as the feature, not the apology.
- Label every scene: "shipping capability (validated in our pilot)" vs "Deloitte concept (mockup)". Never mix within one flow without saying so.
- No accuracy numbers on slides unless they come from a client-data pilot with stated scope.

## 6. Client-safe phrasing (copy these patterns)
- ✅ *"Odoo 19.0 Enterprise ships native invoice digitization; in your pilot on 250 of your vendor bills we measured X% touchless — here is the validation queue for the rest."*
- ✅ *"An AI agent grounded on your procedures is natively supported; quality depends on your knowledge base, so we start with a governed pilot corpus."*
- ✅ *"The Company Brain is a Deloitte-designed solution we build on Odoo's native AI platform — it is not an out-of-the-box Odoo product."*
- ❌ "Odoo's AI will handle your invoices automatically."
- ❌ "The AI screens candidates for you." (High-risk domain: AI assists, humans decide — say exactly that.)
- ❌ Any sentence with "Company Brain" or "Copilot" implying shipped product.

## 7. What NOT to promise (the hard list)
Accuracy/deflection percentages without pilots · autonomous financial postings · autonomous candidate decisions · specific LLM/hosting facts not contractually confirmed · AI features to Community-edition clients · offline/edge AI behavior · future-roadmap AI ("Odoo will…").

## 8. Where Deloitte adds the billable value
Not in showing AI — in making it governed: readiness assessment (data/process), pilot design with metrics, AI register + review rituals, EU AI Act mapping, leakage testing, adoption tracking. Position governance as the product; the modules are the raw material.
