# eCommerce (`website_sale`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: shop core is Community; live carrier rates, external tax, subscription/rental commerce, marketplaces are Enterprise.

## Likely standard (Community)
Catalog with variants & web categories · pricelists per site/segment (B2B/B2C) · configurable checkout steps + extra fields · payment providers · abandoned-cart handling · customer portal (orders, invoices) · merchandising (ribbons, images) · product feeds structure · SEO on catalog.

## Configuration possibilities
Checkout steps, price/tax display, B2B visibility modes, providers & delivery methods, categories/ribbons, recovery emails, per-site catalogs and pricelists.

## Studio possibilities (E)
Product attribute/spec fields for display; back-office order fields. Checkout behavior itself is code territory — don't Studio it.

## Automation possibilities
Order alerts, welcome/review flows, feed refresh schedules, stockout unpublish nudges.

## Custom development is justified when
- Web product configurators beyond variants/combos.
- B2B punch-out/procurement protocol endpoints.
- Custom checkout logic (validated as truly necessary — each change fights upstream updates).
- Multi-vendor marketplace mechanics.

## External integration is justified when
- PIM owns rich content at scale; search/reco SaaS; additional PSPs; hyperscale/headless front (Odoo stays commerce backend); marketplace networks beyond E connectors.

## What to avoid
- Rebuilding checkout for cosmetic wishes — highest-regret customization in Odoo commerce.
- Catalog copies per channel without a master plan (PIM boundary decision instead).
- Ignoring payment-provider lead times in project plans.
- Promising performance SLAs without hosting architecture review.

## Deloitte recommendation principles
Lead with the integration-free story against best-of-breed stacks; concede hyperscale honestly. Prototype checkout with the client's real tax/delivery matrix in week one. Treat content readiness as a tracked workstream.

## Validation questions
1. Which checkout deviations are legally/brand mandatory vs habit?
2. Traffic/SKU/order volumes vs hosting model?
3. Which channels (marketplaces, feeds) with which data ownership?
4. Returns/refund flows — mapped to credit notes and stock returns?
