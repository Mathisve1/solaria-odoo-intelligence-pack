# Odoo Fit-Gap Methodology — Deloitte Playbook

| Attribute | Value |
|---|---|
| Document type | Strategy / Deloitte Advisory Playbook |
| Authority level | High for methodology; feature claims must be evidenced via catalog/module docs |
| Version scope | Odoo 19.0 context pack |

## 1. Purpose
How Solaria (and Deloitte consultants) should conduct and support fit-gap analysis for Odoo 19.0: requirement by requirement, evidence-based, standard-first, edition-explicit.

## 2. Operating principles
1. **Evidence over opinion** — every "Odoo can/can't" is backed by the module catalog, a functional summary, or a live demo test; otherwise it is labeled "needs validation".
2. **Standard-first ladder** — Standard → Configuration → Studio (E) → Automation → Custom → Integration (see framework 05). A gap verdict requires showing which rung failed.
3. **Edition-explicit** — every fit statement names Community/Enterprise. An Enterprise fit for a Community budget is a gap.
4. **Process before feature** — restate each requirement as the business outcome; legacy-system mimicry is challenged before it is scored.
5. **Demo-validated** — high-impact fits are proven in a 19.0 demo database, not asserted.

## 3. The fit-gap flow
```
Collect requirements (discovery question bank playbook)
→ Normalize: outcome-phrased, deduplicated, prioritized (MoSCoW or similar)
→ Map: domain (04) → module(s) (catalog/01, functional summaries)
→ Classify each requirement:
   FIT-STD | FIT-CONF | FIT-STUDIO | FIT-AUTO | GAP-CUSTOM | GAP-INTEGRATION | UNKNOWN-VALIDATE
→ Evidence column: source of the verdict (doc / demo test / assumption)
→ Edition column: C / E / either
→ Impact: effort class (S/M/L relative), upgrade burden, risk
→ Review workshop with client (challenge round)
→ Baseline the fit-gap register (change-controlled)
```

## 4. Question framework per requirement
1. What business outcome does this serve? Who performs it, how often?
2. What happens today, and what breaks if we change the *process* instead of the software?
3. Which module/domain covers it (map first, then module doc)?
4. What does standard do in 19.0 — demonstrated where?
5. If short: does configuration close it? Studio? Automation? (each with evidence)
6. If still short: is the logic stable and differentiating enough for custom? Or is it another product category (integration)?
7. What is the cost of NOT closing the gap (workaround acceptance)?

## 5. Classification discipline
- **FIT-STD** only with demo evidence or high-confidence pack evidence.
- **FIT-CONF** must name the configuration object (pricelist, route, SLA policy, approval category…).
- **FIT-STUDIO** only for data/UI shape; algorithms never.
- **GAP-CUSTOM** requires: standard shortfall evidence + stability + differentiation + owner.
- **UNKNOWN-VALIDATE** is respectable; unfounded FIT is not.

## 6. Anti-overcustomization tactics
- Batch all customization candidates for one challenge session (never approve one-by-one in workshops).
- Quantify the upgrade tax: every custom = test+migration effort at every Odoo upgrade forever.
- Offer process-change alternatives with a named benefit for the user group.
- Defer non-blocking customs to post-go-live phase 2 (most die naturally after users touch standard).

## 7. Structuring recommendations
Per requirement (and rolled up per domain):
**Requirement → Verdict + evidence → Recommended solution level → Rejected alternatives (one line why) → Edition & licensing note → Effort class & risks → Validation actions.**
Roll-up: fit ratio per domain, gap concentration heatmap, edition decision drivers, phase-2 parking lot.

## 8. Communicating uncertainty
Use the pack's confidence vocabulary: "confirmed in 19.0 source", "validated in demo", "likely standard — validate", "interpretation". Never let a slide say "Odoo supports X" where the register says UNKNOWN-VALIDATE.

## 9. Client validation checklist
- [ ] Every must-have requirement has verdict + evidence + edition
- [ ] Customization candidates challenged in a dedicated session
- [ ] Edition decision explicit with its drivers (finance close? payroll? Helpdesk/FSM? Studio? AI?)
- [ ] Demo validation performed for top-10 critical fits
- [ ] Phase-2 parking lot agreed
- [ ] Register baselined and change-controlled

## 10. Example of a good verdict
*"Multi-level PO approval (>50k€ needs CFO): Community ships a single 'to approve' step (evidence: purchase workflow summary). Matrix approval = FIT-CONF on Enterprise via Approvals categories (evidence: approvals functional summary; demo test pending). Recommended: Enterprise Approvals, category per amount band. Rejected: custom module (maintenance), automation-rule blocking (unauditable). Validate: delegation behavior in demo."*

## 11. Anti-patterns (never do)
- "Odoo can do everything with customization" (true, useless, expensive).
- Scoring fits from memory of older Odoo versions.
- Hiding edition constraints until pricing stage.
- Fit-gap by feature-list comparison instead of by client requirement.
- Letting the register live in slides (it's a maintained artifact).
