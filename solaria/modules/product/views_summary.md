# Views & Navigation Summary — `product` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `product` — Products & Pricelists |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Product template form (variants, attributes tabs) is shared across apps; configuration menus live under each consuming app.

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Attributes | product.attribute | list,form |
| Categories | product.category | — |
| Combo Choices | product.combo | list,form |
| Pricelists | product.pricelist | list,kanban,form |
| Price Rules | product.pricelist.item | list,form |
| Vendor Pricelists | product.supplierinfo | list,form,kanban |
| Product Tags | product.tag | list,form |
| Products | product.template | kanban,list,form |
| Products | product.template | kanban,list,form |
| Product Variants | product.product | list,form,kanban,activity |
| Product Variants | product.product | — |
| Product Variants | product.product | kanban,list,form,activity |
| Print Labels | product.label.layout | — |

## View inventory

- Primary views defined: 49 (list: 17, form: 15, search: 9, kanban: 6, activity: 2)
- Inheriting views (UI extensions of other modules): 11
- Richest UI objects: `product.template` (activity, form, kanban, list, search); `product.product` (activity, form, kanban, list, search); `product.document` (form, kanban, list, search); `product.pricelist` (form, kanban, list, search); `product.supplierinfo` (form, kanban, list, search); `product.attribute` (form, list, search); `product.template.attribute.value` (form, list, search); `product.category` (form, list, search); `product.pricelist.item` (form, list, search); `product.template.attribute.line` (form, list); `product.combo` (form, list); `product.tag` (form, list)

## Printable reports (PDF/actions)

| Report | On object | Type |
|---|---|---|
| Product Label 2x7 (PDF) | product.template | qweb-pdf |
| Product Label 4x7 (PDF) | product.template | qweb-pdf |
| Product Label 4x12 (PDF) | product.template | qweb-pdf |
| Product Label 4x12 No Price (PDF) | product.template | qweb-pdf |
| Packaging Barcodes (PDF) | product.uom | qweb-pdf |
| Pricelist | product.product | qweb-pdf |
| Product Label (PDF) | product.template | qweb-pdf |

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
