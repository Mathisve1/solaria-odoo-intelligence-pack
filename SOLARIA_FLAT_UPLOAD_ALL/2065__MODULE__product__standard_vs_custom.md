# Product (`product`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: fully Community foundation.

## Likely standard
Templates/variants from attributes · pricelist rule engine · supplier price grids · categories/tags · UoM & packagings · combos/bundles (19.0) · product documents · rights split (variants, pricelists groups).

## Configuration possibilities
Attribute strategy, categories, UoM/packaging schemes, pricelists, combos, documents, vendor grids.

## Studio possibilities (E)
Classification fields under a governed taxonomy (brand, season, compliance). Not pricing logic.

## Automation possibilities
Data-completeness nudges, lifecycle transitions (end-of-life flags), price-review reminders.

## Custom development is justified when
- Industry data standards (GS1 pools, ETIM) feeds — adapters.
- Configurator logic beyond variants/combos (CPQ class).

## External integration is justified when
- PIM owns rich content at catalog scale (define system of record per field group) · supplier catalogs/punch-out.

## What to avoid
- Importing legacy chaos then "cleaning later".
- Variant explosion without a strategy.
- Duplicate product definitions per channel.
- Pricing logic in code when pricelists express it.

## Deloitte recommendation principles
Run the product-model workshop before any app configuration; give the master data a named owner; decide PIM boundaries explicitly for content-heavy retailers.

## Validation questions
1. Who owns product data, and what's its current quality (measured)?
2. Variant vs SKU strategy per family?
3. Which fields does each channel need — and where do they live?
