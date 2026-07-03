# Purchase (`purchase`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `purchase` |
| Display name | Purchase |
| Source origin | **Community** (Enterprise adds `account_3way_match`, `approvals_purchase`, bill OCR + PO matching, intrastat) |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `account` only — product comes transitively; `purchase_stock` (auto-installed bridge) connects it to inventory |
| Functional domain | Purchase / procure-to-pay |
| Confidence | High for structures; approval/matching nuances need live validation |

## Business purpose
Structure procure-to-pay: request quotations, confirm purchase orders, manage vendor pricing, control receipts and vendor bills, and give managers an exception view (what's late, what's to bill, what deviates).

## Main users / personas
Buyers, procurement managers, warehouse (receipts), AP accountants (bills), budget owners (with E approvals/budgets).

## Business problems solved
- Maverick buying → structured RFQ→PO flow with rights and (E) approvals.
- Vendor price opacity → `product.supplierinfo` price grids, agreements (`purchase_requisition` sibling module).
- Bill/receipt mismatches → billing control policies; Enterprise 3-way match.
- Replenishment latency → orderpoints auto-generate RFQs (with stock).

## Main business processes (source-verified lifecycle)
`purchase.order`: **draft (RFQ) → sent → to approve → purchase (confirmed) → done / cancel** — an approval state exists natively (two-step confirm via settings; amount-based manager approval — validate thresholds live). Receipt status and invoice status fields drive the exception worklists ("to bill", late receipts). `purchase.bill.line.match` (19.0) supports bill↔PO line matching; `bill.to.po.wizard` creates POs from bills.

1. RFQ creation (manual, from orderpoint, from sale with MTO) → send → vendor answer → confirm.
2. Receipt via linked pickings (with `purchase_stock`); reminder mails to vendors (group-gated auto-reminder is shipped).
3. Vendor bill creation under billing policy (ordered vs received) + matching.
4. Analysis: purchase reporting pivots (spend by vendor/category/period).

## Key functional capabilities (source-verified structures)
- `purchase.order` with native approval state (`draft → sent → to approve → purchase`), receipt/invoice status fields driving exception worklists, and order locking.
- Vendor pricing via `product.supplierinfo`: multi-vendor per product, price breaks, vendor lead times, vendor product codes — the data spine of buyer productivity.
- **Bill↔PO matching tooling is first-class in 19.0**: `purchase.bill.line.match` (line-level matching model) and `bill.to.po.wizard` (create/link a PO from a received bill) — the Community foundation the Enterprise 3-way match and OCR build on.
- Agreements/blanket orders via `purchase_requisition` (Community sibling — confirm fit per client in a demo); alternative RFQs comparison patterns (validate exact 19.0 UX live).
- Auto-replenishment: orderpoints generate RFQs grouped per vendor (with `purchase_stock`); vendor confirmation reminder mails (group-gated, source-verified).
- Currencies, incoterms, vendor/product warnings, dropshipping (with `stock_dropshipping`), purchase analytics (`purchase.report`: spend by vendor/category/period).

## Fit with other modules
`stock` (receipts, MTO/dropship routes), `account` (bills, 3-way in E), `mrp` (subcontracting purchases), `sale` (inter-company patterns in E), `approvals` (E, PO approvals), `hr_expense` (employee spend separate).

## Standard in 19.0 (Community)
RFQ/PO lifecycle incl. basic approval step, vendor pricing, receipt/billing control policies, reporting, vendor reminders, bill-to-PO tooling.

## Enterprise-specific additions
Formal approval workflows (Approvals app bridge), 3-way match on bills, OCR vendor bills with PO auto-matching, intrastat declarations, budget control (`account_budget`).

## Configuration opportunities
Billing policy (ordered/received), two-step approval + amount threshold, vendor reminder days, warnings, agreements types, dropship routes, lock confirmed orders.

## Studio / automation opportunities
Automation: PO > threshold → notify controller; late receipt chaser activities; vendor scorecard field updates. Studio (E): requisition reference fields, cost-center tags. Approval *matrices* (multi-level, category-based) → prefer Approvals app (E) over Studio hacks.

## Custom development triggers
Complex sourcing (multi-round tenders, weighted vendor scoring) beyond requisitions; supplier portals beyond shipped portal scope; punch-out catalogs (OCI/cXML) — usually integration plus glue.

## External integration triggers
E-procurement suites (Ariba/Coupa) where corporate mandates them; supplier EDI networks; spend-analytics platforms.

## Common client questions
"Multi-level approvals by amount/category?" — one approval step is native; matrices → Approvals (E) or custom; be precise. · "Vendor price lists with breaks?" — native. · "3-way match?" — Enterprise. · "Auto-POs from min/max?" — native with stock. · "Blanket orders?" — `purchase_requisition` (check catalog; Community).

## Fit-gap considerations
Strong fit for direct procurement tied to stock/manufacturing. Indirect procurement with heavy approval governance leans Enterprise (Approvals + budgets). Tender-style sourcing is the most common genuine gap.

## Deloitte demo angles
1. **Self-driving replenishment:** orderpoint → RFQ appears → confirm → receipt → bill matched. 
2. **Control story:** billing policy + "to approve" state + (E) 3-way match — procurement compliance in one arc.
3. **AP productivity (E):** emailed vendor bill → OCR → PO matched → scheduled payment.

## Implementation watch-outs
- Approval expectations vs native single-step: clarify in week one; it decides edition/scope.
- Vendor master + price data cleanliness drives everything; plan data work.
- Billing policy misalignment with finance causes accrual noise — decide jointly.

## Risks and assumptions
Lifecycle and matching structures verified; exact threshold behavior, reminder logic and OCR quality are runtime → validate. Requisition/tender features live in sibling modules — confirm in catalog per need.

## Validation checklist
- [ ] Approval matrix documented and mapped to native/E/custom explicitly
- [ ] Billing policies per category agreed with finance
- [ ] Vendor pricelist data migration plan
- [ ] Replenishment simulation for top SKUs
- [ ] Edition decision for 3-way/OCR/budgets confirmed
