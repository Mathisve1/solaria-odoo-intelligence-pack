# Point of Sale (`point_of_sale`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `point_of_sale` |
| Display name | Point of Sale |
| Source origin | **Community** (Enterprise adds `pos_enterprise`, `pos_iot`, `pos_settle_due`, extra terminals, country fiscal certifications) |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `stock_account`, `barcodes`, `resource`, `html_editor`, `digest`, `phone_validation`, `partner_autocomplete`, `iot_base`, `google_address_autocomplete` — `stock_account` pulls in `stock` + `account` |
| Functional domain | Point of Sale / retail & hospitality |
| Confidence | High for structures; register UX, offline behavior and fiscal compliance must be validated live per country |

## Business purpose
Sell in-store on a fast, offline-capable register that is not a satellite system: sessions post to the same accounting, deplete the same stock, and share the same customers/loyalty as the rest of the ERP. Restaurant mode (`pos_restaurant`) covers tables/kitchen flows.

## Main users / personas
Cashiers, store managers, F&B staff (restaurant), retail ops (multi-store config), finance (session postings, cash control).

## Business problems solved
- Store↔HQ sync projects → sessions sync natively (`pos.session` lifecycle with cash control and closing wizards).
- Basket/product truth divergence → same product master (`pos.category` for register navigation; combos/presets `pos.preset`, 19.0).
- Payment sprawl → payment methods model incl. terminal integrations (`pos.payment.method`); settle customer dues (E).
- Fiscal exposure → country certification modules (`l10n_*_pos` — largely Enterprise; decisive for regulated markets).

## Main business processes (source-verified)
1. Session open (float/coins config `pos.bill`) → orders (`pos.order`: **draft → paid → done / cancel**) → close with cash control → accounting entries per session.
2. Returns/refunds flowing back through stock; invoicing an order on demand (customer invoice from POS).
3. Restaurant: floors/tables, kitchen/preparation printing (`pos.printer`, preparation display in E), bills split (validate specifics live).
4. Daily ops: session reports (`report_saledetails`, daily sales reports wizard).

## Key functional capabilities
Offline resilience (register works through outages; sync on reconnect — architecture claim: validate scope live), barcode selling, price lists/taxes from ERP, customer capture at register, notes (`pos.note`), preparation printers, multi-config per shop (`pos.config`), loyalty family via `pos_loyalty` (check catalog), self-order/kiosk modules in ecosystem (check catalog per need).

## Fit with other modules
`stock` (real-time depletion per config policy), `account` (session journal entries, payment methods↔journals), `sale`/`crm` (customer continuity), `loyalty` (promotions), `hr` (cashier employees), E: `pos_iot` (scales, printers, payment terminals via IoT box), fiscal `l10n_*_pos`, `whatsapp_pos` receipts.

## Standard in 19.0 (Community)
Full register incl. restaurant mode, sessions/cash control, payment methods (several terminals Community — verify per terminal in catalog), categories/combos, receipts, returns, session accounting.

## Enterprise-specific
Preparation displays/advanced ops (`pos_enterprise`), IoT hardware layer, settle-due, certain terminals (e.g., Tyro), country fiscal certifications (Austria, Germany TSE, France, Italy, Mexico, Kenya OSCU, etc. — check `l10n_*_pos` per country in the catalog).

## Configuration opportunities
Per-store configs (payment methods, pricelists, categories, receipt layout, cash control), presets/combos, restaurant floors, session policies, stock policy (real-time vs at closing — validate options).

## Studio / automation opportunities
Backend automations (alerts on session discrepancies, VIP customer flags). The register UI itself is a dedicated JS app — customizing it = development, not Studio.

## Custom development triggers
Register UX changes (custom buttons/flows), niche hardware, local payment schemes without connectors, specialized promotions beyond loyalty engine.

## External integration triggers
Retail ERPs/legacy POS coexistence during rollouts, e-commerce marketplaces' click-and-collect orchestration, external loyalty/CRM platforms, fiscal middleware where mandated.

## Common client questions
"Does it work offline?" — designed for it; validate the exact offline envelope (what works without server) live. · "Fiscal compliance in country X?" — check `l10n_x_pos` module + certification status commercially; never hand-wave. · "Which payment terminals?" — per-country connector check in catalog + provider contracts. · "Multi-store?" — configs per store, consolidated backend: native.

## Fit-gap considerations
Strong for retail SMB/mid-market chains and hospitality. Gap zones: enterprise retail (advanced promotions engines, retail-specific merchandising), hardware certification matrices, franchise models (multi-company design). Fiscal certification availability can single-handedly decide feasibility per country.

## Deloitte demo angles
1. **Speed:** open register → barcode scan → pay → receipt in seconds; then show the sale order/accounting trace in backoffice.
2. **Store-to-HQ:** close session → journal entry + stock moves — "the store books itself".
3. **Hospitality:** table order → kitchen printer → split bill (rehearse!).

## Implementation watch-outs
- Hardware matrix (printers, drawers, scanners, terminals, scales) certified early — longest lead item.
- Country fiscal rules first conversation in regulated markets.
- Store network resilience assumptions tested (offline envelope).
- Cash-control discipline training; discrepancy handling process.

## Risks and assumptions
Structures verified. Offline scope, terminal behavior, restaurant specifics and certification statuses are runtime/commercial → validate per deployment. Franchise/multi-company retail needs dedicated architecture design.

## Validation checklist
- [ ] Country fiscal module + certification confirmed (per store country)
- [ ] Payment terminal connectors + acquirer contracts aligned
- [ ] Hardware matrix tested (incl. IoT/E decision)
- [ ] Stock posting policy agreed with finance
- [ ] Offline behavior tested in store-like conditions
