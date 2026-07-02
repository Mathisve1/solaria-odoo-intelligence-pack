# Sales (`sale`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: `sale`/`sale_management` are Community. Subscriptions, rental, marketplaces, commissions, external tax = Enterprise.

## Likely standard (Community)
Quotation→order lifecycle · quotation templates with optional products · pricelists (qty/date/currency rules, formulas) · discounts (rights-gated) · online portal signature & payment auto-confirmation · down payments · ordered/delivered invoicing policies · delivery & invoice status tracking · margins & sales analysis pivots · pro-forma invoices · order locking.

## Configuration possibilities
Payment terms, validity, templates, pricelist strategy & rounding, discount groups, portal toggles, teams/targets, T&C, product invoicing policy, unit-of-measure & packaging, warning messages on customer/product ("A warning can be set…" groups are shipped).

## Studio possibilities (E)
Order/line custom fields (contract no., cost center), simplified rep-facing form views, report layout tweaks (with report editor). Not for pricing logic, not for approval logic.

## Automation possibilities
Automation rules: discount>X% → notify manager (advisory gate), quote idle N days → activity, auto-set analytic tags. Scheduled actions for pipeline hygiene. Hard blocking approvals are NOT a shipped sale feature in Community — say so honestly; options: Approvals app (E) via bridge patterns, automation-based blocking (careful), or custom.

## Custom development is justified when
- Constraint-based CPQ (compatibility matrices, engineering rules) — native configurator/combos won't carry it; consider custom module or external CPQ.
- Rebate/royalty/commission engines with retro calculations (check `partner_commission` E first).
- EDI order intake for specific retail networks (check localization/EDI modules first).
- High-volume order APIs with custom validation.

## External integration is justified when
- Marketplace/EDI networks beyond shipped connectors.
- Corporate CPQ or e-procurement platforms (Ariba/Coupa order intake).
- External tax engines (pattern exists natively in E — prefer it).

## What to avoid
- Custom order states (breaks every downstream module and report).
- Pricing logic in Studio fields or server-action hacks — it belongs in pricelists or a reviewed module.
- Bypassing the portal with a custom "quote acceptance" page before testing the native one.
- Promising hard multi-level order approval as standard — it isn't in Community.

## Deloitte recommendation principles
Reproduce the client's pricing in pricelists during fit-gap (evidence beats debate). Decide invoicing policies with finance, not sales alone. Sell the portal moment early — it resets "ERP is backend" perceptions. Keep the order object clean; push exotic needs to well-bounded satellites.

## Validation questions
1. Which pricing scenario fails in a live pricelist test? (Show, don't assume.)
2. Is the approval need advisory (alerts fine) or blocking (edition/custom decision)?
3. Which channels create orders (reps/portal/webshop/EDI) and at what volumes?
4. What must sync to CRM stages, and is that automation or process discipline?
