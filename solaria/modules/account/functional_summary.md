# Invoicing (`account`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `account` |
| Display name | Invoicing (Community app name) |
| Source origin | **Community**. Enterprise turns it into full Accounting via `account_accountant`, `account_reports`, `account_asset`, `account_budget`, `account_followup`, OCR extract modules, `l10n_*_reports` |
| Version scope | Odoo 19.0 |
| Dependencies | `base`, `product`, `analytic`, `portal`, payment ecosystem |
| Functional domain | Accounting & Finance |
| Confidence | High for structures; posting/tax edge behavior needs live validation with finance experts |

## Business purpose
The financial spine of Odoo: customer invoices, vendor bills, payments, taxes, journals and the journal-entry engine every other app posts into. In Community it is presented as "Invoicing"; the full close/compliance layer is Enterprise.

## Main users / personas
AR clerks, AP clerks, accountants, finance managers/CFO (with Enterprise reporting), auditors (read paths), customers/vendors via portal documents.

## Business problems solved
- Fragmented billing → one invoice engine used by Sales, POS, eCommerce, Subscriptions, Projects.
- Manual AP typing → (Enterprise) OCR bill capture; (Community) structured bill entry with PO matching via purchase.
- Tax complexity → tax engine + fiscal positions + localization packages (`l10n_*`).
- Payment tracking → payments, reconciliation primitives, payment state on invoices.

## Main business processes (source-verified lifecycle)
- `account.move` (one model for invoices, bills, credit notes, journal entries): **draft → posted → (reversal/credit note)**, cancel where allowed. Posted = immutable accounting with audit trail fields; inalterability hashing exists via group "Show Inalterability Features" (validate per country).
- `account.payment`: **draft → in_process → paid / rejected / canceled** — payment lifecycle is explicit in 19.0.
- Bank statements (`account.bank.statement`, lines) for import/reconciliation basics; full reco workbench is Enterprise (`account_accountant`).
- Follow-up/dunning: Enterprise (`account_followup`); Community has payment reminders at basic level (validate exact scope live).

## Key functional capabilities
- Chart of accounts (`account.account` with tags/groups), journals, multi-company code mapping (`account.code.mapping` — 19.0 multi-company CoA alignment), lock-date exceptions (`account.lock_exception` — governed reopening, source-verified).
- Tax engine (`account.tax`), cash rounding, incoterms, terms, analytic distribution built-in (`analytic.mixin` patterns).
- Document import mixin (`account.document.import.mixin`) — file-to-record intake surface (E OCR plugs here).
- Portal invoices, e-invoicing groundwork per localization (Peppol/EDI in `l10n_*`/`account_edi_*` modules — check catalog per country).
- Menus mirror finance org: Customers / Vendors / Accounting (Transactions, Closing, Review/Control, Audit Trail, Secure Entries) / Reporting / Configuration.

## Fit with other modules
Every transactional app posts here: `sale` (invoices), `purchase` (bills), `stock`/`stock_account` (valuation entries), `point_of_sale` (session postings), `hr_expense`, `sale_subscription` (E). Payment providers reconcile portal/web payments. Analytic accounting bridges to `project` profitability.

## Standard in 19.0 Community
Invoices/bills/credit notes, payments, taxes & fiscal positions, journals & entries, partner ledgers via views, basic bank statement handling, portal, multi-currency (with `currency` config), analytic distribution, audit trail visibility, country charts via Community `l10n_*` (base charts largely Community).

## Enterprise-specific (name explicitly in client conversations)
`account_accountant` (full Accounting app incl. reconciliation workbench), `account_reports` (P&L/BS/tax/statutory + ~114 country reporting packs), assets, budgets, consolidation, SEPA/batch payments, follow-up automation, OCR (invoice/statement/expense), AI drafts (`ai_account`), live currency rates, inter-company automation. **The Community/Enterprise line runs through finance — this is often the edition decision.**

## Configuration opportunities
CoA (from localization), taxes/fiscal positions, journals, payment terms, sequences/numbering, invoice layouts (document layout), analytic plans, currencies, rounding, terms, incoterms, approval-ish controls via groups (e.g., "Validate bank account").

## Studio / automation opportunities
Automation: reminders, exception flags (missing refs), auto-tagging analytic on rules. Studio (E): extra reference fields on invoices, layout tweaks. Keep posting logic, tax logic, sequences OUT of Studio/automations — deterministic finance rules belong in configuration or reviewed modules.

## Custom development triggers
Country/statutory gaps not covered by any `l10n_*` module (verify catalog + local experts first); exotic revenue recognition (check E deferred revenue features first); bespoke payment file formats (check localization payment modules first).

## External integration triggers
Banking platforms (beyond shipped sync/import — bank connectivity varies by hosting/region: validate), group consolidation suites (HFM/Tagetik style), tax engines (Avatax pattern is native E), payroll bureaus posting summary entries.

## Common client questions
"Is our country supported?" → check `l10n_xx` (+ `l10n_xx_reports` E) in the catalog, then validate completeness with local Deloitte tax. · "Bank integration?" → hosting/region dependent — validate; statement import is standard. · "Approval on vendor bills?" → basic via status/rights; formal flows → Approvals (E)/3-way match (E). · "Audit trail?" → posted immutability + audit trail menus (validate country inalterability needs).

## Fit-gap considerations
Invoicing fit is near-universal. The real fit-gap is *close & compliance*: if the client produces statutory reports, files VAT digitally, runs assets/budgets — Enterprise modules or external tooling must be scoped. Never scope finance on Community by default.

## Deloitte demo angles
1. **AR flow:** quote→invoice→portal payment→payment state changes — finance sees control, sales sees speed.
2. **AP flow (E):** drop PDF bill → OCR fills → 3-way match (with purchase) → pay via batch/SEPA.
3. **CFO story (E):** live P&L/BS drill-down in `account_reports`; lock dates + audit trail for governance.

## Implementation watch-outs
- CoA and tax design decide project success; freeze early, version changes formally.
- Open-item migration (AR/AP balances) and opening balances need a rehearsed cutover script.
- Multi-company: code mappings, inter-company flows, shared CoA decisions upfront.
- Don't rebuild statutory reports as custom pivots — use `account_reports` (E) or scoped external reporting.

## Risks and assumptions
Model/menus/groups verified in source. Exact reconciliation UX, reminder scope in Community, e-invoicing country flows and bank sync availability are runtime/hosting matters → validate with finance + local compliance experts. This pack does not constitute tax advice.

## Validation checklist
- [ ] `l10n_*` module(s) for each client country present + completeness reviewed with local experts
- [ ] Statutory/e-invoicing mandates mapped to modules (Peppol/EDI) per country
- [ ] Edition decision validated against close/compliance requirements
- [ ] Bank connectivity validated for hosting model
- [ ] Migration approach for open items rehearsed
