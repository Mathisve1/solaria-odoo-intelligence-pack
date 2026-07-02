# Usage Instructions — modules/industry_fsm/workflow_summary.md

| Field | Value |
|---|---|
| Document name | `modules/industry_fsm/workflow_summary.md` |
| Document type | Source-Code-Derived Evidence (workflows & automation) |
| Authority level | High for shipped states/crons/server actions/templates |
| Upload priority | High-medium (upload Batch 4) |

## Use this document when
Process design, lifecycle/status questions, migration state-mapping, background-automation inventory for `industry_fsm`.

## Do not use this document when
Inferring exact transition conditions or timing behaviour (validate live).

## How to combine with other documents
`functional_summary.md` for the business narrative; `models.json` for the underlying fields.

## Limitations
States and automations as shipped; transition logic details are code-level and not reproduced here.

## Source origin relevance
`industry_fsm` ships in Odoo 19.0 **Enterprise**.

## Confidence / validation note
High that listed structures exist in the 19.0 source; runtime behaviour, UX and performance require validation in a live Odoo 19.0 database.

## Recommended Solaria document description (copy-paste)
> Source-verified lifecycle/status flows, scheduled automations, server actions and mail templates of the Odoo 19.0 `industry_fsm` module (Enterprise). Use for process design, cutover state mapping and automation questions; validate transition details in a live database.
