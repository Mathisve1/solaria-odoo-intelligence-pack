# Module Demo Pack: eCommerce (`website_sale`)

| Attribute | Value |
|---|---|
| Edition | Community |
| Category | MODULE_DEMO (demo guidance only; product truth lives in the Intelligence Pack module docs, routed via foundation 0012) |
| Rule | Every claim keeps its edition tag and claim label (foundation 0018); nothing here is demo-ready until rehearsed (foundation 0017) |

## Demo purpose
The zero-interface webshop: order to stock to invoice without a single connector.

## Best personas
eCommerce manager, COO, CFO (reconciliation)

## Prerequisites
- Shop with client-flavoured catalog
- payment sandbox
- B2B pricelist user if B2B

## Minimum demo data
- 15+ products with images
- customer account with a saved cart
- order history for dashboards
- one return case

## Recommended flow
- Shop as the customer (B2B price appears after login)
- checkout with payment
- flip to backoffice: delivery order exists, invoice exists, same customer record
- abandoned-cart beat

## Wow moments
- The flip: web order already in the warehouse queue
- B2B login price change
- recovered abandoned cart

## Common mistakes
- Skipping the backoffice flip (the whole argument)
- hyperscale promises
- checkout customisation hand-waving

## Standard vs custom notes
- Checkout steps, pricing visibility, recovery: configuration
- checkout logic changes: development, priced honestly
- live carrier rates at checkout: Enterprise connectors

## Community vs Enterprise notes
Core shop Community; carriers/tax engines at checkout, subscription selling, WhatsApp are Enterprise

## Likely objections
- Performance and SEO (hosting/architecture validation)
- our PSP (per-provider check)
- content scale (PIM boundary)

## Validation checklist
- Checkout with their real tax/delivery matrix
- PSP sandbox e2e
- catalog content readiness plan

## Backup flow
Pre-placed order for the flip; payment sandbox fallback to transfer method
