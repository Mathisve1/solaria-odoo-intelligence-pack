# Security & Access Summary — `website_sale` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `website_sale` — eCommerce |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Storefront runs as public/portal user — test what anonymous visitors can see (prices, stock) as a data-exposure review.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| UOM Price Display for eCommerce | group_show_uom_price | — |
| Comparison Price | group_product_price_comparison | — |
| Product Feed | group_product_feed | — |

## Existing groups this module modifies

These records extend groups owned by other modules (typically adding implied rights) — they do not create new roles:

| Existing group (reference) | Rights/groups implied by this module |
|---|---|
| base.group_user | group_delivery_invoice_address |
| sales_team.group_sale_manager | group_website_restricted_editor |

## Access rights (ir.model.access) — 66 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_portal | — | — | `account.account_fiscal_position`, `account.account_payment_term`, `product.product_attribute`, `product.product_attribute_value`, `product.product_category`, `product.product_pricelist` +14 more |
| group_public | — | — | `account.account_tax`, `product.product_attribute`, `product.product_attribute_value`, `product.product_category`, `product.product_pricelist`, `product.product_pricelist_item` +13 more |
| group_user | — | — | `product.product_attribute`, `product.product_attribute_value`, `product.product_category`, `product.product_pricelist`, `product.product_pricelist_item`, `product.product_product` +11 more |
| group_sale_manager | `product_image`, `product_public_category`, `website_base_unit`, `website_sale.product_ribbon` | — | — |
| group_website_designer | `product_feed`, `website_checkout_step` | `product_public_category` | — |
| group_website_restricted_editor | `product_image`, `website_sale_extra_field` | — | — |
| group_system | `product_feed` | — | — |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Public product template | product.template | `[('website_published', '=', True), ('sale_ok', '=', True)]` |
| product.product_pricelist_comp_rule | — | `` |
| product.product_pricelist_item_comp_rule | — | `` |
| product pricelist company rule | product.pricelist | `['|', ('company_id', 'in', [False, website.company_id.id]), ('company_id', 'in', company_i` |
| product pricelist item company rule | product.pricelist.item | `['|', ('company_id', 'in', [False, website.company_id.id]), ('company_id', 'in', company_i` |
| Hide empty eCommerce categories to public/portal users | product.public.category | `[('has_published_products', '=', True)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
