# Workflow & Automation Summary — `purchase` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `purchase` — Purchase |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- RFQ draft -> sent -> purchase order (confirmed) -> receipt(s) -> vendor bill; billing control policy (ordered vs received) governs the bill moment.
- Reception/billing status fields on the PO are the manager's control panel — demo exception filters (to bill, late receipts).

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| purchase.order | state | draft → sent → to approve → purchase → cancel |
| purchase.order | invoice_status | no → to invoice → invoiced |
| purchase.report | state | draft → sent → to approve → purchase → cancel |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Purchase reminder | purchase.order | 1 days |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Share | purchase.order | code |
| Send Reminder | purchase.order | code |
| Merge RFQs | purchase.order | code |
| Confirm RFQ | purchase.order | code |

## Mail templates shipped: 3

*Purchase: Request For Quotation*, *Purchase: Purchase Order*, *Purchase: Vendor Reminder*

## Integration surface
- Direct dependencies: `account`
- Sequences configured: 1 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
