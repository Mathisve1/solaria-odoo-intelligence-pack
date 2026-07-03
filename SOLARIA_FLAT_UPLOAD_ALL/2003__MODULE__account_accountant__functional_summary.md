# Accounting (`account_accountant`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `account_accountant` |
| Display name | Invoicing → **Accounting** (this module upgrades the app) |
| Source origin | **Enterprise** |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `account`, `mail_enterprise`, `web_tour` |
| Functional domain | Accounting & Finance (Enterprise close layer) |
| Confidence | High for structures; reconciliation matching behavior and rates need live validation |

## Business purpose
The module that turns Community "Invoicing" into the full **Accounting** app: the bank reconciliation workbench (with auto-reconciliation assistance), fiscal year management, and governed lock dates. It is the smallest module with the largest edition consequence — most "we need real accounting" conversations resolve to installing this plus `account_reports`.

## Main users / personas
Accountants/bookkeepers (reconciliation, entries), finance managers/controllers (lock dates, close discipline), external accountants/fiduciaries (client-file workflows), auditors (period control evidence).

## Business problems solved
- Manual bank matching → reconciliation workbench + shipped **auto-reconcile cron** ("Try to reconcile automatically your statement lines", source-verified) and `account.auto.reconcile.wizard`.
- Uncontrolled period changes → **lock dates with a governed exception flow** (`account.change.lock.date` wizard here; `account.lock_exception` lifecycle `active → revoked/expired` in the core) — auditable reopening instead of silent edits.
- Fiscal calendar rigidity → `account.fiscal.year` incl. group-gated years ≠ 12 months (opening/short years; involve auditors before enabling).
- Clerk-vs-closer role blur → "Invoicing & Banks" group splits daily AR/AP work from full accounting rights (source-verified group).

## Main business processes (source-verified structures)
1. **Bank-to-book:** statement lines in → workbench matching (rules/auto-suggestions) → residual handling (write-offs per configuration) → reconciled. `account.reconcile.wizard` supports manual reconciliation cases.
2. **Close rhythm:** transactions posted → review/control menus (core) → lock dates advanced per role → exceptions only via governed flow.
3. **Fiscal year events:** define year boundaries, handle opening balances (with core tooling).

## Fit with other modules
Strict layering: everything here extends `account` (16 model extensions vs 4 new models — this is an overlay, not a parallel system). `account_reports` builds on it; `sale_subscription` requires it (recurring billing implies Enterprise accounting); OCR extract modules assume its workflows for touchless AP.

## Standard vs edition (say it precisely)
- Community: invoices, bills, payments, taxes, basic statement import — see the `account` pack.
- **This module (Enterprise): reconciliation workbench, auto-reconcile, fiscal years, lock-date governance.**
- Statutory/management reports: NOT here — `account_reports`.
The three-layer story (account → account_accountant → account_reports) is the correct way to answer "what does Enterprise accounting actually add".

## Configuration opportunities
Reconciliation models/matching rules (validate exact rule types live), lock-date policy per role, fiscal years, bank feeds/import formats (hosting-dependent — validate), journals for bank/cash.

## Studio / automation opportunities
Automation: exception nudges (unreconciled > N days → activity for accountant), close-checklist activities per period. Keep matching logic in reconciliation models (configuration), never in ad-hoc automations. Studio: no meaningful role here — finance objects should not be reshaped casually.

## Custom development triggers
Rare and suspect in this layer: bespoke matching beyond reconciliation models (validate rule expressiveness first with real statement data), bank formats not covered by shipped/localization import modules.

## External integration triggers
Banking platforms/treasury systems (statement feeds in, payment files out — check `account_batch_payment`/SEPA/country modules first), fiduciary exchange platforms.

## Common client questions
"What auto-reconciliation rate can we expect?" — **never promise a number**; rates depend on statement quality and rule tuning — pilot with 2–3 months of real statements. · "Can we reopen a closed period?" — yes, via governed lock-date exceptions (auditable) — a governance feature, demo it to CFOs. · "Do we need this or is Invoicing enough?" — walk the close/compliance checklist from the `account` pack; if they close books formally, they need this layer.

## Fit-gap considerations
This module usually isn't the gap — it's the answer to gaps discovered in the `account` fit-gap (reconciliation effort, period control). Real gaps live above it (statutory formats → `account_reports` + localizations) or outside (treasury, consolidation scope).

## Deloitte demo angles
1. **The reconciliation minute:** import a statement → watch auto-matches → resolve one exception manually → bank balance ties out. Rehearse with realistic data; this demo dies with toy data.
2. **CFO governance:** advance a lock date → attempt a back-dated entry as a clerk (blocked) → exception flow with trail.

## Implementation watch-outs
- Reconciliation rule tuning is a real workstream with real statement history — plan it, don't improvise post-go-live.
- Bank connectivity is hosting/region dependent — validate early, have import-format fallback.
- Lock-date policy must be agreed with auditors/external accountants before go-live.

## Risks and assumptions
Structures verified (wizards, cron, groups, fiscal year model). Matching algorithms, rule types and connect/feed availability are runtime/hosting matters → validate live. Enterprise licensing required.

## Validation checklist
- [ ] Reconciliation piloted on real statements (3 months) with tuned rules
- [ ] Lock-date policy signed by finance + auditors
- [ ] Bank feed/import path confirmed for the hosting model
- [ ] Role split (Invoicing & Banks vs full accountant) mapped to the client team
