# Odoo 19.0 Repository Inventory and Extraction Plan

| Attribute | Value |
|---|---|
| Document type | Context Manifest / Knowledge Base Rules (inventory annex) |
| Authority level | High for source-coverage questions |
| Version scope | Odoo 19.0 |
| Evidence type | Manifest + repository structure inspection |
| Confidence | High (directly verified in source) |

## 1. Detected sources

| Source | Original archive | Working copy analyzed | Verified |
|---|---|---|---|
| Odoo **Community** 19.0 | `odoo-19.0.zip` (239 MB) | `_sources/community/odoo-19.0/` | Yes |
| Odoo **Enterprise** 19.0 | `2026-07-02 - enterprise-19.0.zip` (125 MB, snapshot dated 2026-07-02) | `_sources/enterprise/enterprise-19.0/` | Yes |

Original archives were not modified; analysis was performed on extracted working copies outside this `solaria` folder.

## 2. Version confirmation — both sources are Odoo 19.0

- Community `odoo/release.py` states `version_info = (19, 0, 0, FINAL, 0, '')` → **Odoo 19.0 final**. Confidence: high.
- The Enterprise tree is named `enterprise-19.0` and its module manifests align with the 19.0 dependency graph: **all 1,422 modules' declared dependencies resolve inside the two trees with zero unresolved references**, which would not happen if the trees were from different series. Confidence: high.
- No master/future-branch content was detected. All statements in this pack are scoped to **Odoo 19.0 only**. The Enterprise snapshot is dated 2026-07-02; later 19.0 point-updates may differ in detail.

## 3. Module counts

| Source | Modules | Of which standalone apps (`application=True`) |
|---|---|---|
| Community — `addons/` | 626 | 34 |
| Community — `odoo/addons/` (server-embedded: `base`, `web`, …) | 24 | — |
| **Community total** | **650** | 34 |
| **Enterprise total** (flat add-ons tree) | **772** | 43 |
| **Grand total** | **1,422** | 77 |

Zero manifest parse errors. Zero module-name overlap between the two trees — Enterprise never replaces a Community module; it extends via new modules.

## 4. Source structure observations

1. **Community includes the full Odoo server/base layer** — `odoo-bin`, the `odoo/` framework package, and the ORM live here. Answer implication: everything Enterprise does runs *on top of* Community.
2. **Enterprise is add-ons only** — a flat directory of 772 addon folders; no server code. It cannot run without the Community code base.
3. Enterprise weight is concentrated in: statutory/localization reporting (~317 localization modules incl. payroll countries), Accounting (`account_accountant` and reports), Helpdesk, Documents, Sign, Knowledge, Planning, Field Service, Approvals, Quality, PLM, Social/WhatsApp marketing, Subscriptions, Studio, and Spreadsheet/Dashboards.
4. Community carries the core business apps: CRM, Sales, Invoicing (`account`), Inventory, Purchase, Manufacturing, Project, HR, Recruitment, Timesheets, Website, eCommerce, POS, Email Marketing, Events.
5. Heavy use of **bridge modules** (`auto_install=True`) that activate automatically when two apps coexist — important when explaining "why did this feature appear?"

## 5. Files analyzed vs ignored

**Analyzed for functional intelligence:** `__manifest__.py`, `models/`, `views/`, `security/` (incl. `ir.model.access.csv`), `data/`, `wizard/`, `report/`, `controllers/` (presence + functional relevance).

**Ignored:** `i18n/`, `tests/` (except when a manifest/test reveals otherwise-invisible behavior — then noted, never copied), `static/`, `demo/` data, `__pycache__/`, build artifacts. No secrets, credentials or environment files were found in scope or copied; source `.env`-style files were not present in either tree.

## 6. Risks and limitations

| Risk | Mitigation in this pack |
|---|---|
| Source structure ≠ runtime behavior (compute logic, onchanges, exact UI) | Everything behavior-level is tagged "validate in a 19.0 demo database" |
| Enterprise snapshot is one point-in-time (2026-07-02) | Noted here and in the QC report |
| Manifest summaries are marketing-brief; some modules have none | Catalog carries a per-entry `confidence` field |
| Licensing/pricing questions are commercial, not source-derivable | Pack never makes pricing claims; flags licensing validation |
| Deep packs cover 26 priority modules, not all 1,422 | Catalog + dependency map cover 100% at inventory level; QC report lists next-iteration candidates |

## 7. Proposed pack structure (as built)

```
solaria/
  00_* : behaviour, manifest, templates, registry, inventory (this file)
  01–07 : global maps (catalog JSON, dependency YAML, Community-vs-Enterprise,
          domain map, standard-vs-custom framework, AI opportunity map, priorities)
  modules/<name>/ : deep packs (README, functional_summary, models.json,
          views_summary, security_summary, workflow_summary, standard_vs_custom)
  playbooks/ : 7 Deloitte advisory playbooks
  90–93 : upload plan, global context prompt (md+txt), test questions, copy-paste descriptions
  index.html : human navigation index
  99_* : quality control + file-type compliance reports
```

## 8. Priority modules for deep extraction (26)

Foundation: `base`, `mail`, `product`, `contacts`.
Core Community apps: `crm`, `sale`, `account`, `stock`, `purchase`, `mrp`, `project`, `hr`, `hr_recruitment`, `hr_timesheet`, `website`, `website_sale`, `point_of_sale`.
Enterprise apps: `helpdesk`, `planning`, `documents`, `sign`, `knowledge`, `approvals`, `sale_subscription`, `industry_fsm`, `marketing_automation`.

Rationale: these carry the core ERP flows (quote-to-cash, procure-to-pay, plan-to-produce, hire-to-retire, service delivery), the most frequent client conversations, and the clearest Community-vs-Enterprise storylines. See `07_priority_module_recommendation.md`.

## 9. How source_origin is tracked

Every catalog entry, dependency entry, model record and module document carries `source_origin`: `community` / `enterprise` / `community + enterprise` (Enterprise extending Community) / `unknown`, plus `version_scope: 19.0`, an `evidence_type` (manifest / model / view / security / workflow / interpretation) and a `confidence` rating. Functional interpretations are always labeled as interpretation, never as source proof.

## 10. Execution approach used

1. Parse all 1,422 manifests → global catalog + dependency map (script-assisted, no code copied into outputs).
2. Deep-extract the 26 priority modules: models/fields via Python AST, views/menus/actions/reports/crons/server-actions via XML parsing, access rights via `ir.model.access.csv`, groups/record rules via security XML → structured metadata only.
3. Hand-write consulting-grade functional documents on top of that evidence.
4. Generate `.usage.md` companions and the document usage registry.
5. QC pass: file-type compliance, no-raw-code check, uncertainty audit.

## 11. Blockers

None. Both sources detected, extracted, version-confirmed and analyzable.
