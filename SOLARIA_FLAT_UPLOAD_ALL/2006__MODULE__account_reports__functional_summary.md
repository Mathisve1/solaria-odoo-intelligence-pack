# Accounting Reports (`account_reports`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `account_reports` |
| Display name | Accounting Reports |
| Source origin | **Enterprise** |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `account_accountant` (⇒ transitively full Enterprise accounting) |
| Functional domain | Accounting & Finance (statutory & management reporting) |
| Confidence | High for report inventory/menus (source-verified); figures/format correctness per country requires expert validation |

## Business purpose
The financial reporting engine of Odoo 19.0 Enterprise: Balance Sheet, Profit & Loss, Cash Flow, Executive Summary, Trial Balance, General Ledger, Partner Ledger, Aged Receivable/Payable, Tax Report — live, drillable, comparable — plus the **automated account-returns workflow** (periodic tax/statutory returns generated and refreshed by cron, source-verified). It is the reason a CFO sees Odoo as an accounting system rather than an invoicing tool.

## Main users / personas
CFOs/finance managers (statements, executive summary), accountants (ledgers, tax reports, returns), controllers (comparisons, budgets context), auditors/advisors (drill-down evidence), group finance (per-company returns — the returns cron runs "for every company", source-verified).

## Business problems solved
- Reporting via exports/Excel → live reports with **drill-down from any figure to the journal entries** (the defining demo gesture; validate exact drill paths live).
- Statutory formats per country → base engine here + ~114 `l10n_*_reports` Enterprise localization packs (check the catalog per client country; completeness = local expert validation).
- Return deadlines chaos → account returns generated/refreshed automatically per period and company; scheduled report sending (second shipped cron).
- Dunning at scale → `account_followup` builds on this layer (separate module; covered at map level).

## Main business capabilities (source-verified structures)
- 43 defined models — dominated by **report handlers** per report type (aged partners, cash flow, deferred revenue/expense, general ledger, tax, journal report, customer statements…): each statement is an engine, not a template.
- Deferred revenue/expense handlers — accrual automation exists at engine level (validate the workflow live before promising specifics).
- 27 menus under Reporting (the CFO navigation surface); comparison/period tooling; annotations (validate scope live).
- Customer statements handler — periodic partner statements as a report object.

## Fit with other modules
Requires `account_accountant`. Country packs (`l10n_*_reports`) plug statutory variants into this engine. `account_followup` (dunning), budgets/assets/consolidation modules produce/consume adjacent figures. Spreadsheet (E) can host management views on top.

## Standard vs edition
Community has NO equivalent: ledgers exist as views/pivots, but statements, tax reports and returns automation are Enterprise — this is the sharpest finance edition line and often the deal decider.

## Configuration opportunities
Report variants/comparisons, fiscal positions/tax grids feeding tax reports (configured in core), return periodicity, scheduled sending recipients, per-country activation via localization packs.

## Studio / automation opportunities
None for report logic (engine + localization domain). Automation: close-calendar activities around return deadlines, distribution governance. Custom report *layouts* for management purposes → prefer spreadsheet/BI patterns over touching statutory engines.

## Custom development triggers
A statutory format with no `l10n_*_reports` coverage (verify catalog + local partner ecosystem first) — then treat as compliance development with local-expert sign-off, structured like a localization.

## External integration triggers
Group consolidation/EPM platforms (Odoo feeds entity trial balances), e-filing portals where returns must be transmitted via national channels (check the country pack's scope first), data warehouses for cross-system analytics.

## Common client questions
"Is our country's tax report included?" — engine yes; the country pack decides — check `l10n_XX_reports` in the catalog, then validate completeness with Deloitte tax. · "Can we drill from the P&L to the invoice?" — designed drill-down; demo it live. · "IFRS + local GAAP?" — multi-ledger patterns exist in 19.0 core (Multi-Ledger menu, source-verified in `account`); exact dual-reporting setups require finance-architecture validation. · "Replace our BI?" — no: this is statutory/financial reporting; management analytics boundary belongs to the BI discussion.

## Fit-gap considerations
For any client producing statements or filing returns, this module (plus country packs) is effectively mandatory — scope it by listing every statutory output in discovery and mapping each to a pack (evidence in the catalog) or a gap. Most "reporting gaps" turn out to be management reporting (spreadsheet/BI boundary), not statutory.

## Deloitte demo angles
1. **CFO drill:** Balance Sheet → click a figure → journal entries → back; period comparison on. The single most persuasive finance demo in Odoo.
2. **Return rhythm:** show the returns view with generated periods — "your VAT calendar runs itself" (label: configured per country pack).
3. **Statement pack:** aged balances + customer statement for a live partner.

## Implementation watch-outs
- Report correctness = configuration correctness (CoA, tax grids, fiscal positions) — reports expose upstream sloppiness; budget config time accordingly.
- Country pack completeness must be validated by local tax experts BEFORE client commitments — Deloitte's own compliance network is the differentiator here.
- Opening balances/migration quality decides whether comparatives are usable.

## Risks and assumptions
Report/menu/cron inventory is source-verified. Figure correctness, drill specifics, deferred/return workflows and e-filing scope are runtime + country matters → expert validation mandatory. This pack does not constitute tax advice. Enterprise licensing required.

## Validation checklist
- [ ] Statutory output inventory mapped to `l10n_*_reports` packs (catalog evidence) per country
- [ ] Country pack completeness reviewed with local Deloitte tax
- [ ] Drill-down and comparison demo rehearsed on migrated data
- [ ] Return periodicity/e-filing path confirmed per jurisdiction
