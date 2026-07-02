# Invoicing (`account`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition note: `account` = Community "Invoicing". Full Accounting = Enterprise (`account_accountant`, `account_reports`, assets, budgets, follow-ups, OCR). State the edition in every finance recommendation.

## Likely standard (Community)
Customer invoices / vendor bills / credit notes · payments with lifecycle · taxes, fiscal positions · journals & manual entries · partner ledgers · basic bank statement import · multi-currency · analytic distribution · portal invoices · document numbering · country base charts (per Community `l10n_*`).

## Configuration possibilities
Chart of accounts, taxes, fiscal positions, journals, payment terms, sequences, invoice layout/branding, analytic plans, rounding, incoterms, access groups (billing vs accountant vs adviser), lock dates policy (with governed exceptions — `account.lock_exception` is shipped).

## Studio possibilities (E) — use sparingly in finance
Reference/classification fields on invoices (project code, grant code), layout tweaks. **Never**: tax logic, posting logic, sequences, rounding via Studio.

## Automation possibilities
Reminder nudges, anomaly flags (missing analytic, unusual amounts → activity for review), auto-tagging analytic by rules. Keep automations advisory in finance — posting stays deterministic and human-validated (or handled by shipped features like OCR+validation queues in E).

## Custom development is justified when
- A statutory format/report has no `l10n_*`/EDI module (verify catalog + Odoo roadmap + local partner modules first) — then build as a proper localization-style module with compliance sign-off.
- Bespoke payment/bank file formats not shipped (check `account_batch_payment`, SEPA, country payment modules in E first).
- Genuine revenue-recognition schemes beyond shipped deferral features (E) — with auditor involvement.

## External integration is justified when
- Group consolidation/planning suites are corporate standard (Odoo feeds them; consolidation module E may still serve entity-level).
- Banking hubs/treasury systems own payments.
- A tax engine is mandated (native external-tax pattern exists in E — prefer it).
- Payroll remains at a bureau: integrate summary journal postings.

## What to avoid
- Custom invoice states or parallel "approval" states on `account.move` — breaks audit logic and every localization.
- Rebuilding statutory reports as pivots/spreadsheets — compliance risk; use `account_reports` (E) or scoped external reporting.
- Editing posted entries by "technical" means — inalterability and audit trail exist for a reason.
- Scoping finance without naming the edition — the most expensive silent assumption in Odoo deals.

## Deloitte recommendation principles
Finance recommendations always carry: country module evidence (catalog), edition statement, and a validation step with local tax/audit experts. Prefer shipped compliance modules over creativity. Anything touching posted data is deterministic and tested — no AI, no ad-hoc scripts, in the posting path.

## Validation questions
1. Which countries, which statutory outputs, which e-invoicing mandates — and which `l10n_*` modules cover them (evidence)?
2. Close process today vs target: which Enterprise modules close the gap; what remains external?
3. Bank connectivity requirements vs hosting model?
4. Who signs off tax configuration, and how are changes governed after go-live?
