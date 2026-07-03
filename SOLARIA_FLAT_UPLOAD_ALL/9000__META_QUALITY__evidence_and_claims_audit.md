# Evidence and Claims Audit — V2

| Attribute | Value |
|---|---|
| Document type | Context Manifest / Knowledge Base Rules (claims audit) |
| Method | Machine-assisted checks (dependency rows vs manifests; module-name references vs catalog; phrase sweeps for "standard Odoo", concept labeling, edition tags) + manual review of the sampled documents |
| Sample | Global maps (03/04/05/06) · 7 playbooks · functional summaries: sale, account, crm, stock, purchase, hr, industry_fsm, point_of_sale (8) · standard_vs_custom: sale, account, purchase, mrp, helpdesk, sign, subscription, website_sale (8) · AI map · C-vs-E map · plus full-corpus phrase sweeps |
| Date | 2026-07-02 (V2) |

## 1. Issues found and fixed (issue → files → fix → residual risk)

### A1 — Approximated dependency rows (evidence-discipline breach)
- **Issue:** ~16 functional summaries stated "conceptual" dependencies instead of exact manifest `depends`; three were materially misleading (`sale` omitted `account_payment`; `industry_fsm` cited Community `project`/`hr_timesheet` instead of the actual Enterprise `project_enterprise`/`timesheet_grid`/`base_geolocalize`; `purchase` listed transitive `product`).
- **Files:** modules/{sale, account, purchase, industry_fsm, point_of_sale, hr, project, website, website_sale, stock, mrp, crm, hr_timesheet, helpdesk, contacts, mail}/functional_summary.md
- **Fix applied:** rows replaced with exact manifest values, relabeled "**Dependencies (manifest, direct)**", with clarifying parentheticals (e.g., the FSM row now itself teaches the Enterprise-layering point).
- **Residual risk:** none for the 16; remaining summaries (approvals, planning, sign, etc.) were machine-checked as accurate.

### A2 — Uncataloged module referenced
- **Issue:** `sale_blanket_order` (ecosystem/OCA name, not in the official 19.0 catalog) named in the sale summary — violating the pack's "never cite uncataloged modules" rule.
- **File:** modules/sale/functional_summary.md
- **Fix applied:** sentence rewritten around the honest answer (no official sales blanket-order app in 19.0; `purchase_requisition` covers the purchase side; native patterns + demo validation for sales-side needs).
- **Residual risk:** none found elsewhere — full-corpus check of module-style tokens against the catalog found no other uncataloged references.

### A3 — Security summaries misrepresented group-modification records
- **Issue:** `res.groups` records that *modify existing groups* (adding implied rights) rendered as unnamed "groups defined by this module" (`—` rows) in 11+ generated security summaries — misleading evidence presentation.
- **Files:** modules/{mail, website_sale, sale_subscription, hr_timesheet, website, hr_recruitment, helpdesk, purchase, point_of_sale, …}/security_summary.md
- **Fix applied:** generator logic corrected; all security summaries regenerated with a separate, honest section: "Existing groups this module modifies… they do not create new roles". Verified: zero `—`-name rows remain.
- **Residual risk:** implied-rights parsing is heuristic for exotic eval expressions; the section refers readers to the module's security file for full detail — flagged for iteration 3 refinement (parse `implied_ids` eval expressions more robustly).

### A4 — Thin capabilities section (genericness)
- **Issue:** `purchase` functional summary's capabilities section was list-thin vs Tier-1 siblings.
- **Fix applied:** rewritten with source-verified structures (native approval state, `purchase.bill.line.match`, bill-to-PO wizard, reminder group, replenishment grouping) — each carrying its evidence hook.
- **Residual risk:** none material; other Tier-1 summaries reviewed and retained (rewriting them further would be churn, not improvement).

### A5 — Behaviour-rule strengthening (prevention layer)
- **Issue:** uncertainty language existed but was not a *controlled* vocabulary; no explicit anti-generic rule; no self-description rule.
- **Files:** 00_solaria_role_and_answering_rules.md, 00_context_manifest_and_usage_rules.md, 91 prompt (.md+.txt)
- **Fix applied:** added the six-grade evidence vocabulary table, the AI two-part-verdict rule, the generic-answer kill-switch (rule 11), the self-description rule (12); prompt twins updated identically; manifest routing now points AI questions to the consolidated evidence pack.
- **Residual risk:** vocabulary works only if uploads include the behaviour docs — mitigated by Batch-1 checklist prominence.

## 2. Checks that found no issues (clean bill)

| Check | Method | Result |
|---|---|---|
| Unsupported "standard Odoo" claims | Corpus sweep for "standard Odoo" outside version-scoped statements | 0 hits in module docs/playbooks |
| AI concept separation | Sweep of all "Company Brain"/Copilot/Alerts-Center mentions (20+) | Every instance labeled as Deloitte concept or IS the labeling rule |
| Missing edition tags in sampled docs | Manual review of the 16-document sample | All sampled capability statements carry C/E tags or edition sections |
| Missing validation caveats | Manual review of behaviour-level claims in sample (portal actions, OCR quality, SLA timers, offline envelopes, proration) | Caveats present in place; confidence rows present in all module summaries |
| Registry vs document consistency | Spot-check of descriptions vs current content post-V2-edits | Consistent; registry regenerated at V2 close to capture edited docs |
| Confidence-label consistency | Review of metadata tables across sample | Uniform pattern ("high for structures; behaviour needs live validation") |
| Playbook overclaim risk | Review of all 7 playbooks' product statements | Product claims consistently deferred to evidence documents |

## 3. Statements that remain by design (watchlist, correctly caveated)
POS/FSM/barcode offline envelopes · subscription proration/portal self-service depth · OCR/AI output quality · SLA timer semantics · signature legal levels · bank connectivity by hosting · statutory completeness per country. Each carries "validate live/expert" language where it appears; these are honest unknowns, not defects — reviewers must not strip the caveats.

## 4. Vague-for-a-consultant scan
The audit's "would a Deloitte consultant act on this?" pass flagged only the A4 case (fixed). Generated evidence docs deliberately contain labeled generic closing guidance — retained (see 98 audit F4 rationale).

## 5. Conclusion
The pack's claim hygiene now matches its architecture: manifest facts are exact, uncataloged names are banned in practice (not just in rules), generated evidence renders what records actually do, and the behaviour layer enforces a controlled vocabulary. Remaining risks are concentrated in the documented watchlist and the A3 parsing refinement, both queued for iteration 3.
