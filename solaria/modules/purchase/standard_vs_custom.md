# Purchase (`purchase`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: `purchase` is Community; 3-way match, formal approvals, bill OCR, budgets are Enterprise.

## Likely standard (Community)
RFQ→PO lifecycle with a native "to approve" step · vendor pricelists with breaks/lead times · receipt & billing control policies · auto-RFQ from reordering rules (with stock) · vendor reminders · bill↔PO matching tooling (`purchase.bill.line.match`, bill-to-PO wizard) · purchase analytics · warnings, incoterms, currencies · agreements/blanket orders via `purchase_requisition` (Community — verify fit).

## Configuration possibilities
Two-step confirmation + amount threshold, billing policy, reminder days, lock confirmed POs, dropship/MTO routes, agreement types, vendor warning messages.

## Studio possibilities (E)
Cost-center/requisition reference fields, buyer-facing simplified views. Not for approval logic beyond simple field additions.

## Automation possibilities
Threshold notifications, late-receipt chasers, vendor performance field updates, budget-owner FYI pings. Blocking multi-level approvals via automation = fragile — prefer Approvals app (E).

## Custom development is justified when
- Tender/sourcing events (multi-round, weighted scoring, sealed bids) are core — beyond requisitions.
- Supplier collaboration portals with structured data exchange beyond portal scope.
- Punch-out/e-catalog protocols (OCI/cXML) — integration adapters.

## External integration is justified when
- Corporate e-procurement (Ariba/Coupa) is mandated — Odoo executes, they source/approve (or vice versa; draw the line once).
- Supplier EDI networks, invoice networks (Peppol AP flows — check localization modules first).

## What to avoid
- Custom PO states/parallel approval fields — breaks matching, reporting, localizations.
- Simulating approval matrices with chains of automation rules — unauditable; use Approvals (E) or a reviewed module.
- Free-text vendor pricing in descriptions instead of supplierinfo data.

## Deloitte recommendation principles
Get the approval matrix on paper in week one and map every line to native step / Approvals (E) / custom — this single artifact prevents the most common purchase-scope conflict. Keep sourcing (strategic) vs purchasing (execution) explicitly split when e-procurement suites are in play.

## Validation questions
1. Approval matrix: levels, amounts, categories, delegations — which lines exceed native+E capability?
2. Which spend is PO-backed vs expense-backed (different modules)?
3. What must vendors receive/see (docs, portals, EDI)?
4. Billing policy per category — finance-agreed?
