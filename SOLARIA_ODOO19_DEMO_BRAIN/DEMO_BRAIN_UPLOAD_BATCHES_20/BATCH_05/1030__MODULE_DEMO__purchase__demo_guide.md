# Module Demo Pack: Purchase (`purchase`)

| Attribute | Value |
|---|---|
| Edition | Community |
| Category | MODULE_DEMO (demo guidance only; product truth lives in the Intelligence Pack module docs, routed via foundation 0012) |
| Rule | Every claim keeps its edition tag and claim label (foundation 0018); nothing here is demo-ready until rehearsed (foundation 0017) |

## Demo purpose
Procure-to-pay under control: from need to RFQ to receipt to matched bill, with the approval story told honestly.

## Best personas
Procurement lead, CFO (control), COO

## Prerequisites
- Vendors with pricelists
- reordering rules on hero SKUs
- receipt flow configured

## Minimum demo data
- 2 vendors per hero product with different prices
- one auto-generated RFQ from stock rules
- receipt and bill staged for matching

## Recommended flow
- Stock rule creates RFQ overnight (tell it, show the result)
- compare vendor prices
- confirm PO
- receive
- bill arrives and matches

## Wow moments
- The self-ordered RFQ ('the system already ordered it')
- native approval state appearing above threshold
- bill-to-PO match

## Common mistakes
- Claiming matrix approvals are native Community (one step is; matrices are Enterprise Approvals/Studio rules or custom)
- skipping the receipt step

## Standard vs custom notes
- Thresholds, policies: configuration
- 3-way match and OCR-with-PO-match: Enterprise, labelled
- tender flows: purchase_requisition checked per case

## Community vs Enterprise notes
Core P2P Community; formal approvals, 3-way match, touchless AP are Enterprise

## Likely objections
- Our approval matrix (map it line by line to native step / Approvals E / custom, in the follow-up)
- vendor price agreements (supplierinfo demo)

## Validation checklist
- Approval matrix mapped explicitly
- billing policy agreed with finance
- reordering parameters on real history

## Backup flow
Pre-confirmed PO chain staged at each state
