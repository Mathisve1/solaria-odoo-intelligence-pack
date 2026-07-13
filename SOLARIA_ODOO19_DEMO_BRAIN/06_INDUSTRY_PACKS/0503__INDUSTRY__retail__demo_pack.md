# Industry Demo Pack: Retail

| Attribute | Value |
|---|---|
| Category | INDUSTRY (defaults to confirm; never a substitute for client intake) |
| Product truth | All module claims route via the Intelligence Pack (foundation 0012); editions labelled; statutory items always validation |

## Operating model
Sell to consumers across stores and web; margin lives in assortment, sell-through, shrinkage and channel coherence; fiscal compliance per country is decisive.

## Common pain points
- Store and web stock out of sync
- End-of-day chaos
- Promotions hard to run consistently
- No single customer view across channels

## Common process flows
- POS sales with session close to accounting
- Click-and-collect and returns across channels
- Replenishment store-by-store
- Loyalty and promotions

## Relevant Odoo modules
- point_of_sale, website_sale, stock, loyalty family (Community)
- pos_enterprise features, IoT hardware layer, fiscal certification modules per country (Enterprise, labelled, country-checked)

## Relevant KPIs
Sell-through, shrinkage, basket size, channel stock accuracy, session discrepancy, return rate

## Suitable demo storyline
One product sold twice: once in the webshop, once at the register, both hitting the same stock and books; end with the session close posting itself (storylines 2110 and order-to-cash patterns)

## Persona emphasis
Retail ops lead as COO pattern, store manager as operations manager, CFO for the fiscal story, cashiers as end users

## Challenger insights
- Channel conflict is usually stock-truth conflict: one inventory ends the web-versus-store war
- The fiscal close of a store should be a non-event, not an evening

## Likely objections
- Fiscal certification in our country? (catalog check per l10n POS module plus commercial validation, never assumed)
- Offline behaviour? (designed for it; validate the envelope on site)
- Hardware? (connector and device validation)

## Data required for demo
Store config with payment methods, product barcodes, webshop with the same catalog, one click-and-collect order, session with a small engineered discrepancy

## Localisation and validation concerns
- POS fiscal certification per country is a hard gate (validation always)
- Payment terminal connectors per acquirer (validation)

## What not to overclaim
- Country fiscal compliance from module existence
- Enterprise-retail promotion engines beyond the loyalty scope
- Offline specifics without site testing
