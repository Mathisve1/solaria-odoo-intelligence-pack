# Standard vs Configuration vs Studio vs Custom vs Integration — Deloitte Decision Framework for Odoo 19.0

| Attribute | Value |
|---|---|
| Document type | Standard-vs-Custom Decision Framework |
| Authority level | High for advisory recommendations |
| Version scope | Odoo 19.0 |
| Evidence type | Consulting framework grounded in 19.0 module analysis |
| Confidence | High as decision logic; feature-existence claims must be paired with catalog/module evidence |

Apply this framework whenever the question is any variant of: *Can Odoo do this? Is this standard? Should we customize? Can we use Studio? Should we build a module? Should we integrate externally? Should we change the standard flow?*

## 1. The six solution levels (plus one honesty level)

| # | Level | What it means in Odoo 19.0 | Upgrade burden | Who owns it |
|---|---|---|---|---|
| 1 | **Standard** | The shipped behavior of installed modules, used as designed | None | Odoo |
| 2 | **Configuration** | Settings, master data, stages, teams, routes, journals, taxes, pricelists, approval thresholds, mail/report templates, access groups | None–low | Functional consultant |
| 3 | **Studio** (Enterprise) | No-code fields, views, models, menus; exports as a module under the hood | Low–medium (must be inventoried & governed) | Key user + consultant, governed |
| 4 | **Automation / server actions** | `base_automation` rules (Community!), scheduled actions, AI server actions & AI fields (Enterprise) | Low–medium | Consultant, versioned |
| 5 | **Custom module development** | Python/XML/OWL extensions via inheritance | Medium–high (every upgrade) | Deloitte engineering, full SDLC |
| 6 | **External integration** | Capability lives in another system; Odoo exchanges data via API/EDI/iPaaS | Interface maintenance | Architecture team |
| 0 | **Strategic assumption — needs validation** | We believe X but have not verified it in a 19.0 environment | — | Whoever claims it |

Level 0 is not a solution — it is the honest label for anything not yet proven. Solaria must use it explicitly.

## 2. The decision tree

```
Requirement received
│
├─ 1. Is it a real requirement or a copy of the legacy system?
│     └─ "Because our old system did it" → challenge first (see §4)
│
├─ 2. Does standard Odoo 19.0 cover it? (catalog + module functional_summary)
│     ├─ YES, in the client's edition → adopt standard; adapt the process, not the software
│     ├─ YES, but Enterprise-only → edition/licensing decision, not a build decision
│     └─ NO / partially → continue
│
├─ 3. Can configuration close the gap? (settings, master data, stages, routes,
│     templates, groups, approval settings)
│     └─ YES → configure; document the design decision
│
├─ 4. Is it a data/UI shape gap (extra field, relabel, simplified view, new report layout)?
│     ├─ Enterprise → Studio, under governance rules (§5)
│     └─ Community → small custom module (Studio unavailable) or challenge the need
│
├─ 5. Is it behavioral glue (when X happens, do Y; reminders; escalations; simple derived data)?
│     └─ Automation rules / scheduled actions / AI fields & AI server actions (E) → level 4
│
├─ 6. Is it core differentiating business logic that belongs INSIDE the ERP?
│     ├─ YES, and stable & well-specified → custom module (inheritance, never core edits) — level 5
│     └─ Unstable/experimental → prototype with level 2–4 first; build only what survives contact with users
│
└─ 7. Is it a capability of another system class (PLM-heavy CAD, APS finite scheduling,
      hyperscale eCommerce, enterprise BI/warehouse, banking, national EDI platforms, HCM suites)?
      └─ YES → external integration with a clean boundary — level 6
```

At every step downward, record: the gap, why the level above was insufficient, the owner, and the upgrade impact. That record *is* the fit-gap deliverable.

## 3. Classification tests (fast heuristics)

- **Standard test:** Can a consultant show it in a vanilla 19.0 database within a day? If unsure → Level 0 until validated.
- **Configuration test:** Can it be achieved without creating fields or code? (Master data and settings count; Studio does not.)
- **Studio test:** Is it additive (new field/view/report), low-logic, and would the business die without it? Studio is for shape, not for algorithms.
- **Automation test:** Can it be expressed as trigger → condition → action on existing data?
- **Custom test:** Is it stable, differentiating, specific, and impossible above? All four must be true.
- **Integration test:** Would building it in Odoo mean re-implementing another product category? Then don't.

## 4. Red flags — challenge before proceeding

1. **Replacing native workflows without a stated reason** (e.g., rebuilding the sales order flow "the way we work today").
2. **Over-customizing early** — custom requests during discovery/prototype phases before users have tried standard.
3. **Hard-coding business logic that should be configuration** (tax rules, approval limits, price logic in code).
4. **Building outside Odoo what Odoo does natively** (external ticketing next to Helpdesk, external e-sign next to Sign, external DMS next to Documents — when the client has Enterprise).
5. **Promising Enterprise functionality without verifying edition/licensing** (Studio, Payroll, statutory reports, AI, Helpdesk/FSM/Planning are Enterprise in 19.0).
6. **Mixing Community and Enterprise claims** in one recommendation without labels.
7. **Using AI where deterministic ERP logic is safer** (tax determination, posting rules, stock reservation are rule domains, not LLM domains).
8. **Client-specific changes during discovery** — no build decisions before fit-gap is signed off.
9. **"Just a small module" accumulation** — ten small modules = one big upgrade problem; consolidate and govern.
10. **Modifying standard code directly** — never; inheritance only. Core edits void upgradability.

## 5. Studio governance rules (when Studio is chosen)

- Registry of every Studio change (what, why, owner, date) — Studio customizations are exportable as a module; inventory them per release.
- No business-critical algorithms in Studio; those belong in reviewed custom modules.
- Test Studio artifacts in staging before upgrades, like any customization.
- One approver role for new Studio fields to prevent field sprawl.

## 6. When custom development IS the right answer

Custom is not failure — undisciplined custom is. Legitimate triggers:
- Differentiating logic core to the client's margin (their "secret sauce" pricing, allocation, planning heuristics) that must live in the transaction flow.
- Regulatory behavior not covered by any `l10n_*` module (verify in catalog first, and consider contributing/vendor modules).
- Volume/UX-critical steps where a purpose-built screen measurably outperforms standard (e.g., high-speed order entry).
- Integration adapters themselves (level 6 usually needs some level 5 glue).
Requirements: written spec, inheritance-only design, automated tests, upgrade plan, named owner.

## 7. When external integration IS the right answer

- The capability is another product category (see decision tree step 7).
- A regulated/incumbent system must remain the system of record (payroll bureau, national EDI hub, PIM/PLM, bank platforms).
- Group architecture dictates a shared service (identity, master data management, BI platform).
Design rules: one system of record per data object; explicit interface contract; idempotent, monitored flows; avoid bidirectional sync of the same field; prefer standard connectors (catalog lists delivery carriers, payment providers, marketplace connectors, Peppol/EDI localizations) before iPaaS custom flows.

## 8. Answer template for Solaria

When applying this framework, structure the recommendation as:

1. **Requirement restated** (business terms) + challenge if it smells like legacy replication.
2. **Standard coverage** — with edition tag and evidence (module, confidence).
3. **Gap** — precisely what standard does not do.
4. **Recommended level** — with the 2–3 tests that justify it.
5. **Rejected levels** — one line each on why not.
6. **Impact** — upgrade burden, ownership, effort class (S/M/L, relative only, no price commitments).
7. **Validation actions** — what must be demoed/verified before this becomes a commitment.
