# Sales (`sale`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `sale` (app packaging: `sale_management`) |
| Display name | Sales |
| Source origin | **Community** (Enterprise extends via `sale_enterprise`, `sale_subscription`, `sale_renting`, marketplace connectors, `partner_commission`, external tax engines) |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `sales_team`, `account_payment`, `utm` — `account_payment` pulls in `account` + `payment`; `sale_management` packages the app UI |
| Functional domain | Sales / quote-to-order |
| Confidence | High for structures; pricing/portal behavior details need demo validation |

## Business purpose
Run quote-to-order: price and compose quotations, get them approved/accepted (incl. online signature & payment on the customer portal), confirm orders, and hand off cleanly to fulfillment (`stock`) and invoicing (`account`) under explicit policies.

## Main users / personas
Sales reps, sales admins/back office, sales managers (margins, discounts), finance (invoicing policy), customers (portal).

## Business problems solved
- Slow, error-prone quoting (templates, optional products, pricelists).
- Unmanaged discounts and margin leakage (discount groups, approval-style controls via config/automation).
- Quote acceptance friction (portal: view, sign, pay online — standard Community).
- Disconnect between sales, delivery and invoice (state-driven handoffs, one data model).

## Main business processes (source-verified lifecycle)
`sale.order`: **draft (quotation) → sent → sale (confirmed) → done/locked or cancel**. Confirmation triggers downstream: deliveries (with `sale_stock`), invoiceable lines per **invoicing policy** (ordered vs delivered quantities), or tasks/projects (with `sale_project`).

1. Quotation creation (products, pricelists, discounts, optional products, quotation templates).
2. Sending & customer interaction (email + portal link; online signature/payment settings).
3. Confirmation → order documents (delivery/invoice status fields track fulfillment).
4. Invoicing (regular, down payment via `sale.advance.payment.inv` wizard).
5. Margin/analysis (`sale.report` pivots; salesperson/team dimensions).

## Key functional capabilities
- Pricelists (rules per product/category/quantity/date, multi-currency), discounts (group-gated "Discount on lines"), Pro-forma invoices (group-gated).
- Quotation templates with optional products & sections; combo/configurable choices (`sale.product_configurator` ecosystem).
- Portal confirmation: online signature and/or online payment can auto-confirm (configuration).
- Locking confirmed orders (group "Lock Confirmed Sales") for audit discipline.
- Mass cancel wizard, discount wizard — operational tooling is standard.

## Fit with other modules
`crm` (opportunity → quote), `stock` (delivery, availability), `account` (invoice, taxes, terms), `project`/`hr_timesheet` (service delivery & T&M billing), `website_sale` (webshop orders land as sale orders), `sale_subscription` (E, recurrence), `sale_renting` (E). Sales teams shared with CRM.

## Standard in 19.0 (Community)
Everything above. Notably: online quote signature + payment, quotation templates, pricelists, down payments, delivered/ordered invoicing policies, margins (via costing), portal.

## Enterprise-specific additions
Reporting/dashboard uplift (`sale_enterprise`), subscriptions/rental business models, Amazon/Shopee/Lazada connectors, commissions (`partner_commission`), Avatax/external tax engines, intrastat, WhatsApp quote delivery. Approval workflows beyond simple config → `approvals` (E) or automation.

## Configuration opportunities
Invoicing policy per product, quotation validity, payment terms, pricelist strategy, discount rights, templates, portal signature/payment toggles, sales teams & targets, product catalog behavior, terms & conditions, shipping policy (with stock).

## Studio / automation opportunities
- Automation rules: discount threshold alerts, stale-quote chasers, auto-archive lost quotes, CRM-stage sync behaviors.
- Studio (E): client-specific order fields (project codes, contract refs), tailored quote form layout. Never re-implement pricing logic in Studio.

## Custom development triggers
True CPQ (deep constraint-based configuration) beyond native configurator/combos; complex rebate/bonus schemes; margin engines with external cost feeds; EDI order intake beyond available connectors.

## External integration triggers
CPQ suites, marketplace/EDI networks not covered by connectors, external tax engines (natively supported pattern in E via Avatax), CPFR/forecast collaboration platforms.

## Common client questions
"Can customers sign and pay quotes online?" — yes, Community, configuration. · "Discount control?" — rights + automation alerts; hard approval gates → Approvals (E)/custom. · "Multiple price lists per market/customer?" — native pricelists. · "Down payments?" — native wizard. · "Blanket orders on the sales side?" — no dedicated sales blanket-order app in the official 19.0 catalog (purchase side has `purchase_requisition`, Community); the native patterns are long-validity quotations/templates or recurring plans — validate the client's exact need in a demo before proposing anything custom.

## Fit-gap considerations
High fit for standard B2B/B2C order flows. Gap hotspots: CPQ depth, rebates/commissions, multi-level order approvals, exotic pricing (formula pricing exists — validate expressiveness live).

## Deloitte demo angles
1. **The signature moment:** build quote with template → send → customer signs & pays in portal → order auto-confirms → delivery appears. One flow, zero interfaces.
2. **Manager control:** discount rights, locked orders, margin pivot.
3. **Policy story:** ordered-vs-delivered invoicing on two products — shows ERP thinking, not just CRM thinking.

## Implementation watch-outs
- Pricelist design explodes if unmanaged — cap rule types, document precedence.
- Invoicing policy per product must be decided with finance before go-live.
- Portal payment requires payment provider setup + finance reconciliation design.
- Quote templates need content ownership (sales ops), or they rot.

## Risks and assumptions
Order lifecycle and wizards verified in source. Exact portal UX, configurator depth and pricing edge cases are runtime → demo validation. Marketplace connectors are Enterprise + per-marketplace commercial terms.

## Validation checklist
- [ ] Pricing model reproduced in pricelists on real examples
- [ ] Invoicing policies per product family agreed with finance
- [ ] Portal sign/pay flow tested end-to-end incl. payment provider
- [ ] Discount governance (groups + alerts) matches sales policy
- [ ] Edition check for subscriptions/rental/commissions/marketplaces
