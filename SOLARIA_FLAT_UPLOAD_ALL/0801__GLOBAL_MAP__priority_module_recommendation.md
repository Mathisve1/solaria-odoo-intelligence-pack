# Priority Module Recommendation — Deep Analysis Order for Deloitte Solaria

| Attribute | Value |
|---|---|
| Document type | Index / Navigation + advisory rationale |
| Authority level | Medium — routing and prioritization |
| Version scope | Odoo 19.0 |
| Confidence | High (based on full 1,422-module inventory) |

## 1. Prioritization criteria

Modules were prioritized by: (1) frequency in Deloitte client conversations, (2) core ERP flow coverage (quote-to-cash, procure-to-pay, plan-to-produce, hire-to-retire, service delivery), (3) demo value, (4) fit-gap decision weight (incl. edition decisions), (5) AI-in-Odoo relevance, (6) partner-positioning value.

## 2. Deep packs built (V1: 26 modules · V2 added 8 more + a consolidated AI pack — see `modules/`)

**Tier 1 — Core ERP flows (deepest treatment)**
| Module | Edition | Why first |
|---|---|---|
| `sale` | C | Quote-to-cash backbone; most demoed app |
| `account` | C | Invoicing core; anchor of the edition decision (with Enterprise `account_accountant`/`account_reports` covered in its pack) |
| `crm` | C | Front of funnel; first app in most journeys |
| `stock` | C | Fulfillment backbone; logistics deals |
| `purchase` | C | Procure-to-pay; approval/compliance conversations |
| `mrp` | C | Manufacturing deals; digital factory story |
| `project` | C | Services industry backbone |
| `hr` | C | Employee master; gateway to payroll (E) discussions |

**Tier 2 — High-frequency apps**
`hr_recruitment` (C), `hr_timesheet` (C), `website_sale` (C), `point_of_sale` (C), `helpdesk` (E), `documents` (E), `sign` (E), `sale_subscription` (E), `planning` (E), `industry_fsm` (E), `knowledge` (E), `approvals` (E), `marketing_automation` (E), `website` (C).

**Tier 3 — Foundations (leaner packs, context for architects)**
`base` (C), `mail` (C), `product` (C), `contacts` (C).

**V2 additions (Tier 2 depth)**
| Pack | Edition | Rationale |
|---|---|---|
| `account_accountant` | E | The close layer that decides the finance edition (reconciliation, lock dates, fiscal years) |
| `account_reports` | E | Statutory & management reporting engine + automated returns — top CFO topic |
| `web_studio` | E | Ladder rung 3, incl. source-verified Studio approval rules |
| `base_automation` | C | Ladder rung 4 — automation is Community, an important correction |
| `spreadsheet_edition` | E | Management-reporting/export-killer story |
| `quality` (merges `quality`+`quality_control`) | E | In-flow quality gates for supply chain & manufacturing |
| `mrp_workorder` | E | Shop Floor execution — the digital-factory demo core |
| `stock_barcode` | E | Paperless warehouse — highest-ROI logistics add-on |
| `ai_native_odoo_19` (consolidated) | E | All 28 native AI/OCR modules + governance & safe-phrasing rules |

## 3. Recommended next-iteration additions (updated after V2)

1. **HR depth:** `hr_payroll` + one or two priority country payrolls, `hr_holidays`, `hr_expense`, `hr_appraisal`.
2. **Finance remainder:** `account_asset`, `account_budget`, `account_followup`, `account_consolidation` (currently summarized in the account/reports packs).
3. **Supply chain remainder:** `mrp_mps`, `mrp_plm`, `maintenance`, `repair`, `purchase_requisition`.
4. **Platform remainder:** `appointment`, `iot`, `voip`.
5. **Marketing/comms:** `mass_mailing`, `social`, `whatsapp`, `survey`, `website_event`.
6. **Vertical/regional:** e-invoicing/EDI (`account_edi_*`, Peppol), priority-country `l10n_*` bundles per Deloitte market focus.
Prioritize by the acceptance-test question log (see `upload_ready/`) — measured demand beats guessing.

## 4. Not prioritized (and why)

- 538 `l10n_*` localization modules — inventoried in the catalog; deep analysis only per active client country.
- Themes, payment provider connectors, test modules, bridge/glue modules — inventory-level coverage is sufficient; behavior follows their parent apps.
- Niche apps (lunch, fleet detail, frontdesk, room) — low conversation frequency; catalog entries exist.

## 5. How to use this document

Use it to (a) route deep questions to existing packs, (b) set expectations when a question hits a module without a deep pack (answer from catalog + domain map, tag lower confidence), and (c) plan the next knowledge-pack iteration with Deloitte practice leadership.
