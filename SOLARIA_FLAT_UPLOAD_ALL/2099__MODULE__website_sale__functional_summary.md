# eCommerce (`website_sale`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `website_sale` |
| Display name | eCommerce |
| Source origin | **Community** (Enterprise adds checkout carrier/tax connectors, subscription/rental commerce, dashboards) |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `website`, `sale`, `website_payment`, `website_mail`, `portal_rating`, `delivery`, `html_builder`, `digest` |
| Functional domain | eCommerce |
| Confidence | High for structures; checkout UX and payment flows must be validated live |

## Business purpose
Sell online on the same platform that manages stock, pricing and invoicing: catalog with variants, cart/checkout with payment providers, customer accounts — every web order is immediately a real `sale.order` with no interface.

## Main users / personas
eCommerce managers, marketers (merchandising/feeds), operations (fulfillment of web orders), finance (payments reconciliation), B2B customers (portal prices), B2C shoppers.

## Business problems solved
- Shop↔ERP sync projects → none needed: one system (the headline).
- Catalog drift → products, prices, stock are the ERP's own (`product.public.category` for web taxonomy, ribbons for merchandising).
- Abandoned revenue → abandoned-cart flows (unpaid orders visible; recovery emails — validate cadence live).
- Channel feeds → `product.feed` (19.0 — product feed structure for channels like Google; validate scope).

## Main business processes (source-verified)
1. Merchandising: public categories, product ribbons (`product.ribbon`), extra media (`product.image`), comparison/UoM price display (groups), base-unit pricing (`website.base.unit`).
2. Shopping: variant selection, pricelists per website/customer group (B2B/B2C), cart = draft sale order.
3. Checkout: configurable steps (`website.checkout.step`, 19.0 — checkout is explicitly modeled), extra fields (`website.sale.extra.field`), delivery choice (carriers), payment via providers/tokens.
4. Post-order: standard sale flow (delivery, invoice, portal account); unpaid/abandoned order menus for ops.

## Key functional capabilities
Multi-website catalogs/prices, B2B mode (login-to-see-prices patterns — validate exact settings), promotions/coupons via loyalty modules (check catalog: `loyalty`, `website_sale_loyalty` — Community family), payment provider ecosystem (Community connectors incl. major PSPs — commercial terms external), SEO on products/categories, digital products via attachments patterns (validate).

## Fit with other modules
`sale` (orders), `stock` (availability display, delivery), `account` (invoices, payment reconciliation), `delivery`+E carrier connectors (live rates/labels), `website` (builder), marketing modules (feeds, mailing), `website_sale_subscription`/`_renting` (E business models), `whatsapp_website_sale` (E notifications).

## Standard in 19.0 (Community)
Full B2C/B2B webshop: catalog, variants, pricelists, checkout steps, payments, customer portal, abandoned carts, feeds structure, ribbons/merchandising.

## Enterprise-specific
Live carrier rates at checkout (FedEx/UPS/etc.), external tax at checkout, subscription/rental selling, sale dashboards, WhatsApp order notifications, AI website content.

## Configuration opportunities
Checkout steps/extra fields, price display (tax incl/excl, UoM price), B2B visibility, payment providers, delivery methods, categories/ribbons, per-website pricelists, cart recovery timing.

## Studio / automation opportunities
Automation: VIP order alerts, first-order welcome flows, review requests post-delivery. Studio (E): product spec fields surfaced on pages (with website Studio patterns). Checkout logic changes = development, not Studio.

## Custom development triggers
Marketplace-grade multi-vendor behavior; complex B2B punch-out; configurator-heavy products on web; deep personalization engines.

## External integration triggers
PIM (large catalogs with rich content), hyperscale/headless commerce fronts, marketplaces (E connectors for Amazon etc. exist — check scope), search/recommendation SaaS, PSPs beyond shipped providers.

## Common client questions
"B2B prices per customer?" — pricelists+login visibility: native; demo it. · "Live shipping rates?" — Enterprise connectors. · "Coupons/loyalty?" — loyalty family in Community catalog; validate mechanics live. · "Performance at X traffic?" — hosting/architecture question: validate honestly, not a module claim. · "Marketplace selling?" — E connectors per marketplace; commercial terms apply.

## Fit-gap considerations
Excellent for SMB/mid-market shops and B2B portals attached to real operations. Gap zone: hyperscale B2C, deep content commerce, multi-vendor marketplaces. The "no integration needed" argument is the fit-gap trump card — use it where operations complexity is the client's pain.

## Deloitte demo angles
1. **The one-platform arc:** order in shop → delivery order appears in Inventory → invoice in Accounting → same customer record everywhere. Rehearsed, this beats feature lists.
2. **B2B moment:** login → customer-specific prices → reorder from portal history.
3. **Ops cockpit:** abandoned carts list → recovery email → recovered order.

## Implementation watch-outs
- Payment provider onboarding (KYC, fees) is a project dependency with lead time.
- Tax display strategy (incl/excl, OSS rules) with finance before catalog build.
- Product content readiness (images, descriptions, variants) is usually the critical path.
- Performance/SEO for existing shops: migration redirect plan mandatory.

## Risks and assumptions
Structures verified (incl. 19.0 checkout-step and feed models). Checkout UX details, cart-recovery cadence, loyalty mechanics and PSP behaviors are runtime/commercial → validate live per project.

## Validation checklist
- [ ] Payment providers + fees + payout reconciliation designed with finance
- [ ] B2B/B2C pricing matrix reproduced in pricelists per website
- [ ] Checkout flow (steps, extra fields, delivery, taxes) prototyped
- [ ] Catalog content migration plan with owners
- [ ] Edition needs (carriers, subscriptions, marketplaces) confirmed
