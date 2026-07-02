# Product (`product`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `product` |
| Display name | Product |
| Source origin | **Community** (foundation; consumed by sale/purchase/stock/mrp/POS/eCommerce) |
| Version scope | Odoo 19.0 |
| Dependencies | `base`, `uom`, `mail` ecosystem |
| Functional domain | Product master data |
| Confidence | High (source-verified: 26 defined models) |

## Business purpose
The single product master: templates and variants, attributes, categories, units of measure and packagings, vendor pricing, pricelists and documents — one definition consumed identically by selling, buying, stocking, making and web channels.

## Main users / personas
Product/master-data owners, sales ops (pricing), procurement (supplier info), warehouse (UoM/packaging), web/e-commerce (content), finance (categories→accounts).

## What it provides (source-verified)
- **Template/variant model:** `product.template` + `product.product` (variants) generated from attributes (`product.attribute(.value)`, template attribute lines/exclusions) — variant logic is data, not code.
- **Pricing:** `product.pricelist(.item)` rule engine (segment/qty/date/currency), supplier prices (`product.supplierinfo`).
- **Structure:** categories (finance/valuation mapping hooks), tags, combos (`product.combo(.item)` — 19.0 bundle mechanics for POS/sales), documents per product (`product.document`), packagings & UoM (`product.uom` patterns, `uom` module).
- **Governance groups:** "Manage Product Variants", "Basic Pricelists" — features gated by groups/settings.

## Consulting relevance
- Product master quality is the #1 predictor of implementation success across sales/stock/manufacturing — data workstream from day one.
- Variant explosion strategy (attributes vs separate products) is a design decision with UX, stock and reporting consequences.
- Category tree drives account/valuation mapping — co-design with finance.
- UoM/packaging design (buy in pallets, stock in units, sell in boxes) — model it early, it touches everything.

## Standard vs Enterprise
Fully Community. Enterprise consumers add contexts (barcodelookup enrichment, PLM for engineering changes, rental/subscription pricing extensions).

## Configuration opportunities
Attributes/variants, categories, UoM/packagings, pricelists, tags, combos, product documents, vendor price grids.

## Studio / automation opportunities
Automation: completeness checks (missing image/weight/EAN → activity), lifecycle nudges. Studio (E): classification fields (brand, season, compliance flags) — governed taxonomy, or reporting fragments.

## Custom development / integration triggers
PIM integration for rich-content catalogs at scale (system-of-record decision), configurator depth beyond variants/combos (CPQ territory), GS1/industry data pool feeds.

## Common questions
"Variants or separate SKUs?" — attributes/variants when logic is combinatorial; separate products when lifecycle/planning differs — workshop it. · "Multiple barcodes/units per product?" — packagings & UoM structures: yes; validate specific patterns live. · "Bundles?" — combos (19.0) for POS/sale contexts + BoM kits for logistics — different tools, know which. · "Who may change prices?" — pricelist rights split from product rights.

## Watch-outs
- Duplicate/legacy product data imported uncleansed = permanent debt; cleanse first.
- Variant explosion (10×10×10 = 1000 SKUs) — design attribute strategy consciously.
- Category-to-accounting mapping changes are disruptive later — finance sign-off up front.

## Validation checklist
- [ ] Product data model workshop (variants/UoM/categories) with all consumers at the table
- [ ] Data cleansing/ownership plan
- [ ] Pricing model reproduced in pricelists
- [ ] Category→accounting mapping signed by finance
