# Inventory (`stock`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: `stock` is Community; barcode UX, quality gates, carrier connectors are Enterprise.

## Likely standard (Community)
Multi-warehouse, location hierarchies · 1/2/3-step receipts & deliveries · routes with pull/push rules · lots/serials + full traceability · putaway rules, removal strategies · reordering rules + scheduler replenishment · packages & package types · scrap, adjustments via quants · delivery slips/labels reports · valuation hooks (with `stock_account`) · feature toggles as groups (multi-location, owners, signature on delivery, reception report).

## Configuration possibilities
Warehouse steps, picking types, routes per product/category/warehouse, orderpoint min/max/lead times, putaway/removal, lot policies, packagings & UoM, delivery signature, reception report, barcode nomenclatures (GS1 group), scheduler frequency.

## Studio possibilities (E)
Operational annotation fields (dock door, seal number, temperature check flag), tailored operator list views. Not for allocation, reservation or valuation logic.

## Automation possibilities
Late-picking escalations, exception dashboards feeds, notify sales on delivery done, auto-set responsible by zone, data-quality nudges (missing weight/dimensions). Scheduled actions for KPI snapshots.

## Custom development is justified when
- Genuine WMS algorithms (slotting optimization, wave/labor optimization) are core to the client's margin — after honestly assessing whether a WMS integration serves better.
- Specialized industry flows (e.g., catch-weight economics) not expressible via UoM/packaging/routes — verify with a route-design workshop first.
- Custom label/handling-unit standards beyond shipped reports.

## External integration is justified when
- Warehouse automation (WCS, conveyors, AS/RS) or a retained best-of-breed WMS.
- 3PL EDI messaging.
- Carrier networks beyond Enterprise connectors.
- Demand planning/S&OP suites (Odoo orderpoints stay execution-level).

## What to avoid
- Custom reservation/allocation forks — the single most upgrade-hostile customization in Odoo logistics.
- Reproducing route behavior in server actions because a workshop skipped route design.
- Turning every wish into a new picking step — each step costs operator time forever.
- Promising scanner workflows on Community.

## Deloitte recommendation principles
Design flows as routes in a workshop with real SKUs before any gap verdict. Treat inventory accuracy as adoption discipline, not software. Keep valuation decisions co-owned with finance. Position Enterprise barcode+quality as the operational payoff bundle.

## Validation questions
1. Which concrete flow fails in a configured demo warehouse? (Route workshop evidence.)
2. Is the gap optimization (WMS-class) or execution (Odoo-class)?
3. Volumes: lines/day, SKUs, operators — do they fit the interaction model?
4. What hardware/carrier landscape must be certified, and on which edition/hosting?
