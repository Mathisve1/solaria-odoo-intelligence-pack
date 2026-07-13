# Challenge Diagnosis Framework

| Attribute | Value |
|---|---|
| Foundation file | 0006 of 20 |
| Principle | The stated requirement is a symptom. Diagnose before prescribing. The brain must not treat every requested feature as the real problem. |

## 1. The seven layers to distinguish
1. **Stated requirement:** what the client asked for ("we need barcode scanners").
2. **Visible pain:** what hurts day to day ("shipments go out wrong").
3. **Root cause:** why it actually happens ("no location discipline; picking from memory; product master has no barcodes").
4. **Business impact:** what it costs (returns, credit notes, customer churn, overtime).
5. **Hidden risk:** what nobody said out loud (key-person dependency, audit exposure, a failed previous project).
6. **Desired business outcome:** what better looks like in business terms (first-time-right shipping above 99%).
7. **Possible Odoo response:** capability mapped honestly, with edition and ladder classification.

## 2. The diagnosis chain (use this structure per challenge)
```
Client statement
→ Current process (how it really runs today, incl. the Excel layer)
→ Pain (who suffers, how often)
→ Root cause (process, data, system, skills or governance?)
→ Business consequence (quantified where possible)
→ Challenger insight (what the client has not considered; file 0007)
→ Relevant Odoo capability (module + edition + claim label)
→ Demo moment (how we make it visible in the storyline)
→ Validation question (what we must confirm before promising)
```

## 3. Diagnosis rules
- Ask "what happens today, step by step?" before accepting any requirement; the current process usually reveals the root cause.
- Classify each root cause: process, data quality, system capability, skills/adoption, or governance. Only system-capability causes are primarily demo material; the others become advisory points (and often stronger Challenger insights).
- One challenge, one chain. Do not blend three pains into one vague theme; the storyline needs precise moments.
- The most urgent problem and the most politically sensitive problem (intake E) get explicit handling decisions: feature it, mention it carefully, or keep it out of the room.
- If the client's requested feature does not address its own root cause, say so and propose the demo moment that does. That is the single most valuable behaviour of this brain.

## 4. Worked micro-example (pattern, adapt per client)
- Statement: "We need better reporting."
- Current process: controllers export to Excel monthly and rebuild the same workbook.
- Pain: two days per month per controller; numbers disputed in management meetings.
- Root cause: no shared live source of truth; definitions differ per department (data + governance, not only system).
- Consequence: slow decisions, meeting time spent arguing about whose number is right.
- Insight: the cost is not report-building time; it is decision latency and eroded trust in numbers.
- Odoo capability: live pivots standard; spreadsheet dashboards with live links (Enterprise, spreadsheet_edition); statutory reporting separate (account_reports, Enterprise). Labels per claim.
- Demo moment: change one order live, watch the management sheet move.
- Validation: which 10 reports run the business (get samples); definitions workshop needed.

## 5. Output form
Deliver diagnoses as a compact table (one row per challenge) plus a short narrative for the top two. This table feeds stages 5 to 10 of the workflow and the storyline design directly.
