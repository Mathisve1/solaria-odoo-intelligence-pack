# Security & Access Summary — `product` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `product` — Products & Pricelists |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Pricing rights (pricelist edit) should be tighter than product-data rights in most orgs — split via groups, not custom code.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| Basic Pricelists | group_product_pricelist | — |
| Manage Product Variants | group_product_variant | — |
| Create | group_product_manager | — |

## Access rights (ir.model.access) — 38 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_product_manager | `product_attribute`, `product_attribute_custom_value`, `product_attribute_value`, `product_category`, `product_combo`, `product_combo_item` +12 more | `update_product_attribute_value` | — |
| group_user | `product_label_layout` | — | `product_attribute`, `product_attribute_custom_value`, `product_attribute_value`, `product_category`, `product_combo`, `product_combo_item` +11 more |
| group_partner_manager | — | — | `product_pricelist` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Product multi-company | product.template | `['|', ('company_id', 'parent_of', company_ids), ('company_id', '=', False)]` |
| Product multi-company | product.document | `['|', ('company_id', 'parent_of', company_ids), ('company_id', '=', False)]` |
| product pricelist company rule | product.pricelist | `['|', ('company_id', 'parent_of', company_ids), ('company_id', '=', False)]` |
| product pricelist item company rule | product.pricelist.item | `['|', ('company_id', 'parent_of', company_ids), ('company_id', '=', False)]` |
| product supplierinfo company rule | product.supplierinfo | `['|', ('company_id', '=', False), ('company_id', 'parent_of', company_ids)]` |
| Product combo multi-company rule | product.combo | `['|', ('company_id', '=', False), ('company_id', 'parent_of', company_ids)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
