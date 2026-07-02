# Priority Module Recommendation — Deep Analysis Order for Deloitte Solaria

| Attribute | Value |
|---|---|
| Document type | Index / Navigation + advisory rationale |
| Authority level | Medium — routing and prioritization |
| Version scope | Odoo 19.0 |
| Confidence | High (based on full 1,422-module inventory) |

## 1. Prioritization criteria

Modules were prioritized by: (1) frequency in Deloitte client conversations, (2) core ERP flow coverage (quote-to-cash, procure-to-pay, plan-to-produce, hire-to-retire, service delivery), (3) demo value, (4) fit-gap decision weight (incl. edition decisions), (5) AI-in-Odoo relevance, (6) partner-positioning value.

## 2. Deep packs built in this iteration (26 modules — see `modules/`)

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

## 3. Recommended next-iteration additions

1. **Finance depth:** `account_accountant`, `account_reports`, `account_asset`, `account_budget` as their own packs (currently summarized inside the `account` pack) — highest advisory payoff.
2. **HR depth:** `hr_payroll` + one or two priority country payrolls, `hr_holidays`, `hr_expense`, `hr_appraisal`.
3. **Supply chain depth:** `stock_barcode`, `quality_control`, `mrp_workorder`, `mrp_mps`, `mrp_plm`, `maintenance`, `repair`, `purchase_requisition`.
4. **Platform:** `web_studio`, `base_automation`, `spreadsheet_edition`, `appointment`, `iot`.
5. **AI family:** `ai`, `ai_app`, `ai_fields` + domain AI modules — as one consolidated "AI in Odoo 19" evidence pack.
6. **Marketing/comms:** `mass_mailing`, `social`, `whatsapp`, `survey`, `website_event`.
7. **Vertical/regional:** e-invoicing/EDI (`account_edi_*`, Peppol), priority-country `l10n_*` bundles per Deloitte market focus.

## 4. Not prioritized (and why)

- 538 `l10n_*` localization modules — inventoried in the catalog; deep analysis only per active client country.
- Themes, payment provider connectors, test modules, bridge/glue modules — inventory-level coverage is sufficient; behavior follows their parent apps.
- Niche apps (lunch, fleet detail, frontdesk, room) — low conversation frequency; catalog entries exist.

## 5. How to use this document

Use it to (a) route deep questions to existing packs, (b) set expectations when a question hits a module without a deep pack (answer from catalog + domain map, tag lower confidence), and (c) plan the next knowledge-pack iteration with Deloitte practice leadership.
