# Barcode (`stock_barcode`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only. Architecturally a thin mobile execution overlay on Community `stock` — flows stay where they were designed.

## Likely standard (Enterprise)
Scan-driven receipts/internal moves/picks/deliveries · barcode inventory counts · lot/serial capture by scan · GS1 parsing (product+lot+qty in one scan) · wrong-item objection at scan time · cancel-operation handling · mobile-first UI (`web_mobile` dependency).

## Configuration possibilities
GS1 nomenclature rules, label printing (core report actions), picking-type behavior (core), device policy, per-operation scanning strictness (validate options live).

## Studio possibilities
None on the app. Backend metadata only if truly needed.

## Automation possibilities
Exception alerts (short picks, count variances), count-cycle scheduling, replenishment nudges — all beside the app, not inside it.

## Custom development is justified when
- Genuine custom scan flows (multi-step VAS, kitting stations) — JS app work; scope like POS customization (consciously, minimally).
- Niche device/peripheral integrations.

## External integration is justified when
- A WMS owns execution (then don't run both) · conveyor/PTL automation · voice picking systems · central label-print infrastructure.

## What to avoid
- Deploying alongside a WMS "temporarily" — two execution owners, permanent reconciliation pain.
- Rollout before barcode-coverage and wifi reality checks.
- Custom scan screens before piloting native flows on real hardware.
- Treating it as a WMS — optimization boundaries are unchanged from the `stock` pack.

## Deloitte recommendation principles
Sequence: route design (stock workshop) → barcode data readiness → device pilot → app training. Sell accuracy/traceability ROI, not "a WMS". Keep the one-execution-owner rule absolute.

## Validation questions
1. Barcode coverage of the product master today (measured %)?
2. Device and connectivity reality (site survey done?)
3. Which flows first (receipts usually), and what accuracy baseline do we measure against?
