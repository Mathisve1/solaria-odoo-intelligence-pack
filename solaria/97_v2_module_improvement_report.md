# V2 Module Improvement Report

| Attribute | Value |
|---|---|
| Document type | Context Manifest / Knowledge Base Rules (V2 module worklog) |
| Scope | Review of the 14 prioritized existing packs + creation of 9 new packs |
| Date | 2026-07-02 (V2) |

## 1. Modules reviewed (existing, 14)
sale, account, crm, stock, purchase, mrp, project, hr_recruitment, helpdesk, documents, sign, sale_subscription, industry_fsm, website_sale — each reviewed across README, functional_summary, standard_vs_custom and workflow_summary (plus hr, project-family and foundation modules swept by the machine checks).

## 2. Modules improved and documents changed

| Module | Documents changed | Change |
|---|---|---|
| sale | functional_summary | Exact manifest dependencies; uncataloged `sale_blanket_order` reference replaced with honest catalog-true guidance |
| account | functional_summary | Exact manifest dependencies |
| purchase | functional_summary; security_summary (regen) | Exact dependencies (transitive `product` removed); capabilities section rebuilt with source-verified structures (bill-line matching, native approval state, reminder group); group-modification rendering fixed |
| industry_fsm | functional_summary | Dependencies corrected to the Enterprise layer (`project_enterprise`, `timesheet_grid`, `base_geolocalize`) — a materially better edition story |
| crm, stock, mrp, hr, project, website, website_sale, point_of_sale, hr_timesheet, helpdesk, contacts, mail | functional_summary | Exact manifest dependency rows |
| mail, website_sale, sale_subscription, hr_timesheet, website, hr_recruitment, helpdesk, purchase, point_of_sale (+3 more) | security_summary (regenerated) | Group-modification records now rendered honestly ("Existing groups this module modifies") instead of unnamed definition rows |
| all 26 V1 packs | README/models.json/views/workflow (regenerated) | Deterministic regeneration with the improved generator — content-identical except the security fix; confirms reproducibility |

## 3. Common issues found
1. Dependency rows written for readability instead of evidence exactness (systemic — fixed corpus-wide, new labeling convention "Dependencies (manifest, direct)").
2. One uncataloged ecosystem module name (isolated).
3. Generated security tables misrepresenting group-*modification* records (systemic in the generator — fixed at the source).
4. One thin capabilities section (purchase).

## 4. What was intentionally NOT changed
- The 14 packs' business narratives, fit-gap sections, demo angles and validation checklists — reviewed and judged consulting-grade; rewriting them would be churn without quality gain (V2 principle: targeted improvement over regeneration).
- Generated views/workflow generic closing sections — labeled generic by design, harmless, and consistent (98 audit F4 rationale).
- Foundation packs (base, mail, product, contacts) beyond dependency fixes — leaner by design (Tier 3).
- Authority-level vocabulary variance — meaningful as-is; normalization deferred (98 audit F12).

## 5. New packs added in V2 (9)

| Pack | Edition | Why now |
|---|---|---|
| `account_accountant` | E | Finance-depth gap: the edition-deciding close layer (reconciliation, lock dates, fiscal years) |
| `account_reports` | E | The statutory/management reporting engine + returns automation — top CFO conversation |
| `web_studio` | E | Rung 3 of the ladder, incl. newly-evidenced **Studio approval rules** — changes classic approval verdicts |
| `base_automation` | C | Rung 4; corrects the "automation needs Enterprise" misconception with evidence |
| `spreadsheet_edition` | E | The export-killer management-reporting story (cell threads + revisions source-verified) |
| `quality` (merges `quality`+`quality_control`) | E | In-flow quality gates; manufacturing edition driver |
| `mrp_workorder` | E | Shop Floor app + operator change proposals — the digital-factory demo core |
| `stock_barcode` | E | Highest-ROI warehouse add-on; thin-overlay architecture point evidenced |
| `ai_native_odoo_19` (consolidated) | E | 28-module AI evidence layer + governance/phrasing doc — the fastest-growing question category |

Each new pack: 7 standard files (5 generated from fresh source extraction + 2 hand-written), except the AI pack's special format (README, inventory JSON, functional summary, standard-vs-custom, governance doc). All registered with `.usage.md` companions.

## 6. Next module candidates (iteration 3)
`hr_payroll` + 1–2 priority country payrolls · `hr_holidays`, `hr_expense`, `hr_appraisal` · `mrp_mps`, `mrp_plm`, `maintenance`, `repair`, `purchase_requisition` · `appointment`, `voip`, `whatsapp` · `mass_mailing`, `social`, `survey`, `website_event` · e-invoicing/EDI country bundles per Deloitte market focus. Prioritize by the question log from the acceptance-test runs (see `upload_ready/solaria_acceptance_test_script.md` §Scoring).
