# Module Demo Pack: Inventory (`stock`)

| Attribute | Value |
|---|---|
| Edition | Community |
| Category | MODULE_DEMO (demo guidance only; product truth lives in the Intelligence Pack module docs, routed via foundation 0012) |
| Rule | Every claim keeps its edition tag and claim label (foundation 0018); nothing here is demo-ready until rehearsed (foundation 0017) |

## Demo purpose
The warehouse that runs on rules: receipts, putaway, picking, delivery and replenishment as configuration, traceability as a by-product.

## Best personas
Warehouse manager, COO, quality-minded stakeholders

## Prerequisites
- Client-like location tree
- routes for their in/out steps
- lots enabled where their traceability lives

## Minimum demo data
- Hero SKUs with barcodes and lots
- one staged receipt, one delivery
- an engineered stockout
- history for the forecast view

## Recommended flow
- Receive with lot capture
- putaway suggests the shelf
- pick for the spine order
- engineered exception surfaces
- deliver
- trace the lot both directions

## Wow moments
- The two-minute recall drill (lot traced to customers)
- route change live: process design as a setting
- replenishment firing from min/max

## Common mistakes
- Explaining routes theoretically instead of showing one change
- no exception beat
- promising WMS optimisation

## Standard vs custom notes
- Steps, routes, strategies: configuration
- scanning UX: Enterprise barcode app, labelled
- wave/slotting optimisation: WMS boundary, integration

## Community vs Enterprise notes
Deep Community core; barcode app, quality gates, carrier labels are Enterprise

## Likely objections
- Real-time accuracy (process discipline honesty)
- our volumes (validation, reference)
- multi-site (groups and config shown)

## Validation checklist
- Route workshop on their real flows
- lot policy per product family
- opening stock migration approach

## Backup flow
Every picking staged in duplicate; trace report pre-opened in a tab
