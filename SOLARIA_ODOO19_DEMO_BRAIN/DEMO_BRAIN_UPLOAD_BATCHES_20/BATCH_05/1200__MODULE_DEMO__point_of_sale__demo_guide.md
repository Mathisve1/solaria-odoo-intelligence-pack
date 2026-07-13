# Module Demo Pack: Point of Sale (`point_of_sale`)

| Attribute | Value |
|---|---|
| Edition | Community core; fiscal/hardware layers Enterprise |
| Category | MODULE_DEMO (demo guidance only; product truth lives in the Intelligence Pack module docs, routed via foundation 0012) |
| Rule | Every claim keeps its edition tag and claim label (foundation 0018); nothing here is demo-ready until rehearsed (foundation 0017) |

## Demo purpose
The store that books itself: fast register, session close posting to accounting, one stock with the webshop.

## Best personas
Retail ops, store managers, CFO (session close), cashiers

## Prerequisites
- POS config with payment methods
- barcodes on products
- receipt printer if in-person (or labelled simulation)

## Minimum demo data
- Store catalog with barcodes
- opened session with a float
- a return case
- prior sessions for reports

## Recommended flow
- Scan-scan-pay in seconds
- a return handled
- close the session with cash control
- show the journal entry it produced
- same product visible in webshop stock

## Wow moments
- Speed at the register
- the session close writing the books
- one-stock across store and web

## Common mistakes
- Country fiscal claims without the l10n check (hard gate in retail)
- ignoring offline questions
- demoing without barcodes

## Standard vs custom notes
- Configs, payment methods, receipts: configuration
- register UI changes: JS development, priced honestly
- fiscal certification: country modules plus commercial validation

## Community vs Enterprise notes
Register and restaurant Community; IoT hardware layer, preparation displays, several fiscal certifications Enterprise

## Likely objections
- Fiscal compliance here (catalog check per country plus validation, never assumed)
- our terminals (per-connector check)
- offline (envelope validated on site)

## Validation checklist
- Country fiscal module status
- hardware matrix pilot
- session accounting mapping with finance

## Backup flow
Second staged session; screenshots of close flow
