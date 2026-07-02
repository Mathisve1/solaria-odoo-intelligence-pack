# Point of Sale (`point_of_sale`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: register core + restaurant are Community; IoT hardware layer, preparation displays, settle-due, several terminals and country fiscal certifications are Enterprise.

## Likely standard (Community)
Offline-capable register · sessions with cash control and per-session accounting · payment methods incl. terminal connectors (verify per terminal) · categories, combos/presets · returns/refunds via stock · restaurant floors/kitchen printing · receipts, session reports · customer capture & invoicing from POS.

## Configuration possibilities
Per-store configs, payment methods↔journals, pricelists, receipt layout, cash control, floors/tables, preparation printers, presets, category navigation.

## Studio possibilities (E)
Backoffice fields only (order tags, store attributes). The register is a JS app — no Studio there.

## Automation possibilities
Session-discrepancy alerts, end-of-day digest to managers, stockout flags to purchasing.

## Custom development is justified when
- Register flow changes are genuinely mandated (regulatory prompts, custom tenders) — POS JS development, budget consciously.
- Local payment/fiscal middlewares without connectors.
- Specialized promotion mechanics beyond the loyalty engine (verify loyalty scope first).

## External integration is justified when
- Fiscal middleware mandated by country design; franchise back-ends; external loyalty/CRM; click-and-collect orchestration across systems.

## What to avoid
- Custom register UI for cosmetics — every POS version upgrade becomes a re-test project.
- Committing to a country without checking `l10n_*_pos` certification reality.
- Hardware bought before connector verification.
- Treating POS accounting mapping as an afterthought — finance must sign the journal design.

## Deloitte recommendation principles
Fiscal + hardware feasibility first, features second. Pilot one store with the full hardware matrix before chain rollout. Keep promotions in the loyalty engine; keep custom JS to an absolute minimum with a named owner.

## Validation questions
1. Countries → which fiscal modules/certifications exist (catalog + commercial check)?
2. Exact tender types and terminals per store?
3. Offline requirements — duration, operations allowed?
4. Promotion mechanics inventory vs loyalty engine capabilities (live test)?
