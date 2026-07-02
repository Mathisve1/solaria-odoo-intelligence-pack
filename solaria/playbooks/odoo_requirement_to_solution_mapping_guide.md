# Requirement-to-Solution Mapping Guide — Deloitte Odoo Playbook

| Attribute | Value |
|---|---|
| Document type | Strategy / Deloitte Advisory Playbook (method) |
| Authority level | High for method; module claims defer to catalog/module docs |
| Version scope | Odoo 19.0 context pack |

## 1. Purpose
The repeatable recipe for turning a raw client requirement into an Odoo-native solution proposal (or an honest gap verdict): normalize → classify → map → decide level → write recommendation → validate.

## 2. Step 1 — Normalize the requirement
Rewrite as: **[Actor] needs to [outcome] [conditions/frequency] so that [business value].**
- Strip solution language ("we need a button that…" → what outcome?).
- Attach: volume, frequency, actor count, legal/contractual flags, source (who said it).
- Assign requirement ID; deduplicate.

## 3. Step 2 — Classify the requirement type
| Type | Typical solution altitude |
|---|---|
| Process flow ("order must pass credit check") | standard states + configuration + automation |
| Data shape ("we track a rig number") | configuration/Studio field |
| Calculation/logic ("prices follow formula X") | configuration engines (pricelists, taxes) or custom |
| Document/output ("our delivery note layout") | templates/report configuration |
| Control/compliance ("4-eyes on payouts") | groups/rules/approvals(E)/native controls |
| Visibility/reporting ("margin per crew per week") | pivots/spreadsheet/BI boundary |
| Interface ("orders come from EDI") | connector catalog check → integration |
| Experience ("scanning must be one-handed") | edition feature (barcode E) or UX validation |

## 4. Step 3 — Map to domain and modules
1. Domain via `04_functional_domain_map.md`.
2. Candidate modules via `01_global_module_catalog.json` (existence + edition) — **never propose a module not in the catalog**.
3. Depth via `modules/<name>/functional_summary.md` + evidence files.
4. Note the edition of every module named (03 map for the boundary story).

## 5. Step 4 — Decide the solution level
Walk the 05 ladder (Standard → Configuration → Studio → Automation → Custom → Integration) and stop at the first sufficient rung; record why lower rungs failed. Use the module's own `standard_vs_custom.md` for module-specific traps.

## 6. Step 5 — Write the functional recommendation
Template:
- **Requirement** (normalized, ID)
- **Verdict:** FIT-STD / FIT-CONF / FIT-STUDIO / FIT-AUTO / GAP-CUSTOM / GAP-INTEGRATION / UNKNOWN-VALIDATE
- **Solution:** modules (with edition) + the specific mechanism (e.g., "pricelist formula rule", "SLA policy per team", "approval category 'Spend >50k'")
- **Evidence:** pack document / demo test / assumption (labeled)
- **Assumptions captured:** explicitly listed, each with an owner and validation route
- **Impact:** effort class (S/M/L relative), upgrade burden, dependencies
- **Validation step:** what will be shown in the prototype to close the verdict

## 7. Step 6 — Validate with demo/prototype
Every FIT that is business-critical, and every UNKNOWN, gets a prototype scene (conference-room pilot). The register's evidence column flips from "doc" to "demo" — that's when commitments may be made.

## 8. Example mappings
1. *"Sales reps may give max 10% discount; more needs manager."* → Control · Sales · FIT-CONF+AUTO (discount group + automation alert) on C; blocking gate → E Approvals or custom (challenge first). Evidence: sale standard_vs_custom.
2. *"We must trace which batch went to which customer."* → Process · Inventory · FIT-STD (lots + traceability), demo the trace report. Evidence: stock functional summary.
3. *"Technicians collect a signature on a checklist on site."* → Experience/Document · Field Service · FIT-STD on E (`industry_fsm` worksheets); Community → honest edition gap.
4. *"Invoices to public sector must go via Peppol."* → Interface/Compliance · Finance/Localization · check `l10n_*`/EDI modules in catalog per country → FIT-STD/CONF (E for some countries) or GAP; validate with local tax experts.
5. *"HR wants CVs summarized and ranked."* → AI · Recruitment · native parsing/AI assist (E) with human decision + AI Act governance; ranking beyond native = GAP-CUSTOM with high-risk compliance duties. Evidence: 06 + hr_recruitment pack.
6. *"Weekly margin per project in one view."* → Visibility · Project/Timesheet · FIT-CONF (analytic design + pivots/spreadsheet E) — the real work is analytic design + timesheet adoption, say so.

## 9. Capturing assumptions
Every assumption gets: statement, owner, validation route (demo/db check/expert/vendor), due date, and a consequence note ("if false → verdict flips to X"). Assumption tables travel with the register into design sign-off.

## 10. Quality bar for recommendations
A recommendation is client-ready when: outcome-phrased ✓ module+edition named ✓ mechanism specific ✓ evidence labeled ✓ alternatives dismissed with reasons ✓ validation step defined ✓ no pricing/licensing invented ✓.
