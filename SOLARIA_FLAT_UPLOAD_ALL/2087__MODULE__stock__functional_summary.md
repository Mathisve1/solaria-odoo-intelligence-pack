# Inventory (`stock`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `stock` |
| Display name | Inventory |
| Source origin | **Community** (Enterprise adds `stock_barcode`, `quality_control`, carrier connectors, `stock_enterprise` reporting) |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `product`, `barcodes_gs1_nomenclature`, `digest` |
| Functional domain | Inventory & Warehouse |
| Confidence | High for structures; reservation/scheduling behavior needs live validation |

## Business purpose
Keep stock true and moving: model warehouses/locations, execute receipts–putaway–picks–deliveries, trace lots/serials, replenish automatically, and feed valuation to finance — with the process itself defined as configuration (routes/rules), not code.

## Main users / personas
Warehouse operators, warehouse managers, supply chain planners, customer service (availability), finance (valuation via `stock_account`).

## Business problems solved
- Inventory inaccuracy (structured operations + adjustments + cycle-count practices).
- Untraceable products (lots/serials `stock.lot`, full move history `stock.move.line`).
- Manual replenishment (reordering rules `stock.warehouse.orderpoint` + scheduler).
- Chaotic flows (picking types per operation; routes generate chained steps).

## Main business processes (source-verified lifecycle)
- `stock.picking`: **draft → waiting → confirmed → assigned (reserved) → done / cancel**; `stock.move` adds `partially_available`. Reservation is the operational heartbeat.
- Receipt → (optional quality/putaway steps via routes) → storage; delivery: pick → (pack) → ship in 1/2/3-step configurations.
- Adjustments via quants (`stock.quant`) counting flows; scrap (`stock.scrap` draft→done).
- Replenishment: orderpoints trigger RFQs (buy route) or MOs (manufacture route) through the scheduler cron.

## Key functional capabilities
- Warehouse topology: `stock.location` hierarchy, multi-warehouse, putaway rules (`stock.putaway.rule`), removal strategies (`product.removal` — FIFO/LIFO/FEFO patterns; validate exact options live).
- Routes & rules (`stock.route`, `stock.rule`): pull/push chains — process design as configuration (group "Manage Push and Pull inventory flows").
- Feature-gating groups (source-verified): multi-locations, multi-warehouse, lots/serials, packages, owners (consignment), signature on delivery, reception report, GS1 barcode printing.
- Packages & package types, picking waves/batch primitives (validate scope), delivery slip/labels reports (21 report actions shipped).
- `stock.package.history`, reference tracking, exception activity flows via chatter.

## Fit with other modules
`sale_stock` (delivery from orders, availability on quotes), `purchase_stock` (receipts, replenish-to-order), `mrp` (component reservation/finished goods), `stock_account` (valuation to `account`), `delivery` (carriers/shipping costs), POS/eCommerce stock visibility; Enterprise: `stock_barcode` (scanner UX), `quality_control` (gates on operations).

## Standard in 19.0 (Community)
All of the above structures: multi-warehouse, routes, lots/serials, putaway, orderpoints, scrap, package handling, valuation hooks. This surprises clients comparing to "basic" competitors — Community inventory is deep.

## Enterprise-specific additions
Barcode operations app, quality checks/alerts embedded in operations, integrated carrier labels/rates (FedEx/UPS/DHL/…), inventory reporting uplift, IoT peripherals. The "paperless warehouse" demo is Enterprise.

## Configuration opportunities
Warehouse steps (1/2/3-step in/out), routes per product/category, reordering min/max, putaway & removal, picking types, lot/serial policies per product, delivery signature, reception report, units & packagings.

## Studio / automation opportunities
Automation: exception alerts (late pickings, negative quants advisory), auto-assign responsible per zone, notifications to CS on delivery done. Studio (E): extra handling fields (dock, temperature flag). Keep allocation/reservation logic native — it's the engine, don't fork it.

## Custom development triggers
True WMS optimization (slotting, wave optimization, labor management) beyond native scope; specialized handling units; deep automation (conveyors/WCS) — usually integration, sometimes custom glue.

## External integration triggers
Automated warehouses (WCS/WMS retained), carrier networks beyond shipped connectors, 3PL EDI, demand-planning suites.

## Common client questions
"Multi-warehouse + transfers?" — native. · "FEFO for expiry?" — with `product_expiry`; validate strategy options live. · "Barcode scanning?" — Enterprise app; Community has data model support (GS1 group) but not the scanner UX. · "Consignment?" — owners group exists; validate the exact flow. · "Real-time accuracy?" — process discipline + counting strategy; the system supports it, adoption delivers it.

## Fit-gap considerations
High fit for mid-market warehousing. Gap hotspots: WMS-grade optimization, complex value-added services, automation integration, 3PL orchestration. Route/rule expressiveness is high — most "gaps" are configuration not yet tried.

## Deloitte demo angles
1. **Flow story:** RFQ→receipt→putaway suggestion→internal transfer→delivery with signature — narrate the route doing the routing.
2. **Traceability story:** serial from receipt to customer in two clicks (lot report).
3. **Self-driving baseline:** orderpoint triggers RFQ overnight (scheduler) — "the system already ordered it".
4. **Enterprise uplift:** same flow with scanner + quality gate + carrier label.

## Implementation watch-outs
- Route complexity creep: start 1-step, add steps for proven reasons.
- Opening stock migration with lots/serials is a project of its own — plan counts.
- Valuation method alignment with finance (standard/FIFO/AVCO via `stock_account`) before go-live.
- Negative stock policy and backorder policy must be explicit decisions.

## Risks and assumptions
Structures verified; reservation nuances, strategy option lists and batch/wave scope are runtime → validate live. Barcode/quality/carriers are Enterprise + hardware dependencies.

## Validation checklist
- [ ] Warehouse topology + steps mapped and tested with real SKUs
- [ ] Lot/serial policy per product family agreed (traceability vs effort)
- [ ] Replenishment parameters simulated on history
- [ ] Valuation method signed off by finance
- [ ] Edition/hardware decisions for barcode & carriers confirmed
