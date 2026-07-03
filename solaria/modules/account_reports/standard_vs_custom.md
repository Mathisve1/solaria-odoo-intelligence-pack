# Accounting Reports (`account_reports`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only (requires `account_accountant`). Statutory reporting is the domain where "custom" carries compliance risk — the ladder here is short and strict.

## Likely standard (Enterprise)
Balance Sheet, P&L, Cash Flow, Executive Summary, Trial Balance, General/Partner Ledgers, Aged AR/AP, Tax Report · drill-down to entries · period comparisons · automated account returns per company (cron) · scheduled report distribution · customer statements · deferred revenue/expense engines · country statutory variants via `l10n_*_reports` packs.

## Configuration possibilities
Report variants, comparison periods, return periodicity, distribution lists, and — decisively — the upstream configuration that feeds figures (CoA, tax grids, fiscal positions).

## Studio possibilities
None. Statutory engines are not Studio territory, full stop.

## Automation possibilities
Deadline-calendar activities, distribution governance, exception nudges (e.g., unposted entries before a return). Never automate figure manipulation.

## Custom development is justified when
- A required statutory format has NO country pack (catalog-verified absence) — build as localization-grade development with local tax expert sign-off and a maintenance owner.
- Custom e-filing transmission where the national channel isn't covered (verify pack scope first).

## External integration is justified when
- Group consolidation/EPM owns group statements (Odoo feeds entity data) · national e-filing portals · data warehouse for management analytics (management reporting ≠ this module's job).

## What to avoid
- Rebuilding any statutory report as pivots/spreadsheets — compliance and audit risk.
- "Small fixes" to report handler behavior via server actions — invisible compliance drift.
- Promising country coverage from the engine's existence — the pack decides, per country.
- Using this engine for management-BI wishes — route those to spreadsheet/BI honestly.

## Deloitte recommendation principles
Statutory outputs get a per-country evidence table (output → pack → validation owner) in every finance fit-gap. Deloitte tax/audit network validates completeness — that validation IS the billable differentiator vs pure-play integrators. Keep management reporting explicitly out of statutory scope discussions.

## Validation questions
1. Complete list of statutory outputs per country/entity — and the matching pack for each (catalog reference)?
2. Who validates figures pre-filing today, and what evidence do they need from the system?
3. Group reporting: what leaves Odoo, in what format, to which platform?
