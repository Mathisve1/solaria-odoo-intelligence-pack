# Workflow & Automation Summary — `website_sale` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `website_sale` — eCommerce |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Cart (draft SO) -> checkout -> payment transaction -> confirmed order -> standard sale flow takes over — one continuous process, no interface.
- Abandoned-cart recovery email is a shipped cron/flow — a free quick win in demos.

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| eCommerce: send email to customers about their abandoned cart | website | 1 hours |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Recently Sold Products | product.product | code |
| Recently Viewed Products (per user) | product.product | code |
| Product Accessories | product.product | code |
| Products Recently Sold With | product.product | code |
| Alternative Products | product.product | code |
| Category List | product.public.category | code |
| Reset Cache | product.feed | code |

## Mail templates shipped: 1

*Ecommerce: Cart Recovery*

## Integration surface
- Direct dependencies: `website`, `sale`, `website_payment`, `website_mail`, `portal_rating`, `digest`, `delivery`, `html_builder`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
