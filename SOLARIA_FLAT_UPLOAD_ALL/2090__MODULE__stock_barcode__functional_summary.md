# Barcode (`stock_barcode`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `stock_barcode` |
| Display name | Barcode |
| Source origin | **Enterprise** |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `stock`, `web_tour`, `web_mobile` — the `web_mobile` dependency confirms the mobile-first design intent |
| Functional domain | Inventory & Warehouse (barcode operations) |
| Confidence | High for structures; scanning UX, device behavior and offline envelope must be validated on real hardware |

## Business purpose
The paperless-warehouse app: execute receipts, internal moves, picks, deliveries and inventory counts by **scanning** on a mobile device, on top of the unchanged Community `stock` engine. It is deliberately thin as a data layer (1 defined model — a cancel-operation wizard; 17 extensions of stock models, source-verified): the app changes how operators *touch* the warehouse, not how the warehouse *works* — an architectural point worth making to IT stakeholders.

## Main users / personas
Warehouse operators (scanning flows), inventory controllers (counts/adjustments), warehouse managers (throughput/accuracy), IT (devices, GS1 setup).

## Business problems solved
- Paper pick lists and re-typing → scan location → product/lot → quantity → validate, mirroring the picking flows of `stock`.
- Wrong-product/wrong-lot errors → scan validation against expected moves (behavioral details: validate live).
- Slow counts → barcode-driven inventory counting flows.
- Traceability data entry (lots/serials) → captured by scan at the operation moment — the practical enabler of the lot policies designed in the `stock` pack.

## Main business processes (source-verified structures)
1. Operation execution: pickings by type (receipt/internal/pick/delivery) surfaced in the app; scan-driven line completion; cancel-operation wizard for aborts.
2. Counting: quant-based counts via scanning (the `stock.quant` machinery from core).
3. Parsing: **GS1 nomenclature** (from `stock`'s `barcodes_gs1_nomenclature` dependency + GS1 groups verified in the stock pack) — one scan can carry product+lot+qty; barcode data design is the real project.

## Fit with other modules
Pure overlay on `stock` (routes/rules/reservations unchanged); `mrp_workorder` shares the scanning culture on the production side (`stock_barcode_mrp` bridge exists — see catalog); `quality` checks can appear in scanned flows (bridge modules — verify per combination in catalog); IoT/device layer for dedicated scanners vs phone cameras (validate options live).

## Community fallback
Data model supports barcodes (fields, GS1 nomenclature in core) but there is **no scanning app** in Community 19.0 — operators would use the standard backend UI. For scanning operations, this module is the edition decision.

## Configuration opportunities
Barcode nomenclatures (GS1 application identifiers), location/product/lot label printing (via stock's report actions), picking-type behavior tuning in `stock` (batch/wave decisions are core-side), device policy.

## Studio / automation opportunities
None on the scanning flow (dedicated app). Automation on the surrounding process: exception alerts (short picks), count-cycle scheduling. Label layout tweaks via report tooling — keep GS1 compliance intact.

## Custom development triggers
Custom scan flows (multi-step VAS operations) — POS-app-style JS territory, budget consciously; niche device integrations; voice-picking class requirements (usually external systems).

## External integration triggers
WMS coexistence (if a WMS owns execution, don't deploy this app in parallel — one execution owner), automation hardware (conveyors/PTL), label-print servers where centralization is mandated.

## Common client questions
"Phones or dedicated scanners?" — both patterns exist; device choice = ergonomics + ruggedness + camera-vs-laser — pilot on candidate hardware. · "Offline in cold storage/dead zones?" — validate the current offline envelope honestly on site; never assume. · "GS1 from our suppliers?" — the parser exists (source-verified); supplier label *quality* is the variable — sample real inbound labels early. · "Does it change our flows?" — no: it executes the routes designed in `stock` — flow design stays the prerequisite.

## Fit-gap considerations
The highest-ROI Enterprise add-on for warehouses still on paper: accuracy + speed + traceability with zero process-model change. Gap zones: WMS-grade optimization (slotting/waves at scale), VAS-heavy flows, voice/automation integration — same boundaries as the `stock` pack, unchanged by this app.

## Deloitte demo angles
1. **Receive-to-shelf on a phone:** scan PO receipt → scan lot → putaway suggestion → done; show the same picking in the backend afterwards ("one engine, two faces").
2. **Error prevented:** scan a wrong product → app objects — the accuracy argument in one beep.
3. **Count sprint:** cycle-count a location in 60 seconds.

## Implementation watch-outs
- Hardware pilot (devices, holsters, wifi survey) before rollout promises.
- Label/barcode data readiness (products without barcodes = app without fuel) — barcode enrichment is the critical-path workstream.
- Train flows on the client's real route design (1/2/3-step) — the app mirrors it exactly.

## Risks and assumptions
Structures verified (thin-overlay architecture, GS1 plumbing, cancel wizard). Scanning UX, device matrix, offline behavior → validate on hardware, on site. Enterprise licensing required.

## Validation checklist
- [ ] Device + wifi pilot in the actual warehouse
- [ ] Barcode coverage audit of the product master (and enrichment plan)
- [ ] Inbound supplier label sampling against GS1 parsing
- [ ] Route design (from the `stock` workshop) frozen before app training
