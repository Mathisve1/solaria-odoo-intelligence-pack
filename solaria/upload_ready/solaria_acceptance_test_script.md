# Solaria Acceptance Test Script — 12 Questions (run after each batch; full pass expected after Batch 3)

| Attribute | Value |
|---|---|
| Usage | Ask verbatim in a fresh Solaria session. Log PASS/FAIL + notes per question. Questions 1–4 must pass from Batch 1; 5–8 from Batch 2; 9–12 from Batch 3. |
| Relationship to `92_solaria_test_questions.md` | 92 is the full 15-question validation set with detailed patterns; this script is the operator's fast, batch-aligned subset with fix actions. |

---

**Q1. "A client wants to heavily customize their sales process to match their legacy system. What do you advise?"** *(Batch 1)*
- **Good:** challenges legacy replication; standard-first ladder; batch-challenge tactic; upgrade-tax argument; ends with validation questions.
- **Bad:** "Odoo is very flexible and can be customized."
- **Docs:** role rules, 05 framework.
- **If it fails:** check 05's description was pasted; re-upload role rules.

**Q2. "Is Studio included in every Odoo installation?"** *(Batch 1)*
- **Good:** Studio (`web_studio`) = Enterprise-only; Community lacks rung 3; commercial validation caveat.
- **Bad:** unqualified yes/no.
- **Docs:** 03 map, 05.
- **Fix:** verify 03 uploaded with description.

**Q3. "Which documents did you use, and how trustworthy are they?"** *(Batch 1)*
- **Good:** names real documents + authority levels (registry vocabulary).
- **Bad:** no citations or invented names.
- **Fix:** registry JSON missing/undescribed — re-upload it.

**Q4. "Draft two sentences for a client email about whether Odoo can handle their approval workflows."** *(Batch 1)*
- **Good:** client-appropriate tone, edition-safe, includes a validation phrase; no internal heuristics.
- **Bad:** overpromising ("Odoo fully supports all approval workflows").
- **Docs:** role rules (client-facing mode).
- **Fix:** re-check global context prompt was pasted completely (client-facing rules live there too).

**Q5. "Does Odoo 19 have a module for equipment rental? Which edition?"** *(Batch 2)*
- **Good:** consults catalog; names `sale_renting` (Sales/Rental family) with edition; declares depth limits (no deep pack) honestly.
- **Bad:** guessing or inventing module names.
- **Docs:** catalog 01, 07.
- **Fix:** catalog upload incomplete — re-upload (largest file).

**Q6. "What exactly is AI in Odoo 19 — and what is just a concept?"** *(Batch 2)*
- **Good:** Enterprise-only native inventory (agents, AI fields/server actions, domain assists, OCR family) + pgvector/IAP gates + two-part verdict; Company Brain/Copilots labeled Deloitte concepts.
- **Bad:** blurred capability/concept, or AI attributed to Community.
- **Docs:** 06 (and `ai_native_odoo_19` pack if uploaded).
- **Fix:** 06 description check; consider uploading the AI pack early.

**Q7. "We're a manufacturing company — which Odoo modules should we look at and what's Enterprise there?"** *(Batch 2)*
- **Good:** `mrp`+`stock`+`purchase`+`product` (C) core; `mrp_workorder`, `mrp_mps`, `mrp_plm`, quality, barcode, IoT (E); APS honesty.
- **Bad:** edition-free list or APS promises.
- **Docs:** 04, 02, catalog.

**Q8. "Why does selling subscriptions force an Enterprise accounting decision?"** *(Batch 2)*
- **Good:** `sale_subscription` depends on `account_accountant` (manifest evidence) → edition implication drawn.
- **Bad:** no dependency reasoning.
- **Docs:** 02 dependency map, catalog.

**Q9. "How would you demo the quote-to-cash flow to a CFO?"** *(Batch 3)*
- **Good:** storyline (quote → portal sign/pay → delivery → invoice → payment state), edition labels, rehearsal caveat, CFO-value framing.
- **Bad:** feature list without narrative or edition labels.
- **Docs:** sale + account functional summaries (+ demo playbook if loaded).

**Q10. "Client on Community wants helpdesk functionality. Options?"** *(Batch 3)*
- **Good:** Helpdesk = Enterprise-only; honest options: edition upgrade / project-as-tickets compromise (losses named: SLA, ratings, bridges) / external tool — in Deloitte preference order.
- **Bad:** claiming a Community helpdesk app exists.
- **Docs:** helpdesk functional summary, 03.

**Q11. "Can Odoo automatically create vendor bills from emailed PDFs, and how reliable is it?"** *(Batch 3)*
- **Good:** two-part verdict: capability ships (E, OCR/IAP — documents/account context); reliability = pilot on client documents, never a quoted rate; validation queue framed as the control.
- **Bad:** quoted accuracy percentages or Community attribution.
- **Docs:** account/documents summaries, 06/AI pack.

**Q12. "Give me three discovery questions to qualify a field-service opportunity."** *(Batch 3)*
- **Good:** concrete FSM-relevant questions (intervention types/volumes, device/connectivity reality, parts/van stock, proof-of-service needs) — usable in a workshop tomorrow.
- **Bad:** generic "what are your requirements?" questions.
- **Docs:** industry_fsm summary (question bank playbook deepens this later).

---

## Scoring and actions
- **12/12:** release to consultants; schedule the second fresh-session run this week.
- **9–11:** release with known-gap notes; fix failed items via their per-question fix actions.
- **≤8:** stop; work the kit README troubleshooting list; do not expand uploads until ≥11.
- Log every run (date, batch state, per-question result) — the log is iteration-3 input.
