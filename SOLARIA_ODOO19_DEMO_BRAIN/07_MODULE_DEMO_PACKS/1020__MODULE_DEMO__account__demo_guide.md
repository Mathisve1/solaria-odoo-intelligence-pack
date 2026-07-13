# Module Demo Pack: Invoicing / Accounting (`account`)

| Attribute | Value |
|---|---|
| Edition | Community core; Accounting layers Enterprise |
| Category | MODULE_DEMO (demo guidance only; product truth lives in the Intelligence Pack module docs, routed via foundation 0012) |
| Rule | Every claim keeps its edition tag and claim label (foundation 0018); nothing here is demo-ready until rehearsed (foundation 0017) |

## Demo purpose
Show the financial spine: operations write the books, AP becomes a managed queue, the close gets shorter.

## Best personas
CFO, finance director, accountants

## Prerequisites
- Country chart/taxes configured
- history posted so reports are alive
- Enterprise layers installed only if the conversation is Enterprise (labelled)

## Minimum demo data
- 60+ posted invoices/bills across months
- open AR with overdue items
- bank statement staged for reconciliation (E)
- one credit note case

## Recommended flow
- Invoice born from the operational flow
- AR view and dunning stance
- vendor bill arrives as PDF, OCR fills, human validates (E, labelled)
- bank reco assists (E)
- drill from report to entry

## Wow moments
- PDF bill to validated bill in under a minute (E, labelled)
- drill-down from P&L line to source document
- payment state flipping on reconciliation

## Common mistakes
- Empty ledgers
- demoing as admin with all features unlabelled
- promising country statutory outputs without the country pack check

## Standard vs custom notes
- Taxes, journals, terms: configuration
- statutory outputs: Enterprise account_reports plus country packs, validated
- posting logic: never custom in a demo, ever

## Community vs Enterprise notes
Invoicing is Community; reconciliation workbench, statutory reports, OCR, follow-ups are Enterprise: the sharpest edition line in the product, state it plainly

## Likely objections
- Our statutory needs (localisation validation with named experts)
- migration of open items (approach, not hand-waving)

## Validation checklist
- Country pack coverage per client country
- OCR pilot on their real bills
- close-process mapping to Enterprise features

## Backup flow
Pre-validated bill and pre-matched statement line ready; report screenshots as last resort
