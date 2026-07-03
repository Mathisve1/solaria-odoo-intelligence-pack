# Usage Instructions — modules/spreadsheet_edition/models.json

| Field | Value |
|---|---|
| Document name | `modules/spreadsheet_edition/models.json` |
| Document type | Source-Code-Derived Evidence (data model) |
| Authority level | High for existence of models/fields/relations |
| Upload priority | High-medium (upload Batch 4) |

## Use this document when
Verifying that a business object, field, relation or status value exists in `spreadsheet_edition` in Odoo 19.0; grounding functional claims; data-mapping and migration design.

## Do not use this document when
Inferring business meaning on its own (use the functional summary), judging UX, or estimating computed-field behaviour.

## How to combine with other documents
`functional_summary.md` translates these structures into business meaning; `workflow_summary.md` for lifecycle context.

## Limitations
Curated selection of key fields (not the full schema); no source code included; structure ≠ behaviour.

## Source origin relevance
`spreadsheet_edition` ships in Odoo 19.0 **Enterprise**.

## Confidence / validation note
High that listed structures exist in the 19.0 source; runtime behaviour, UX and performance require validation in a live Odoo 19.0 database.

## Recommended Solaria document description (copy-paste)
> Source-derived data model of the Odoo 19.0 `spreadsheet_edition` module (Enterprise): models defined/extended, key fields with relations and status values, built-in capabilities from mixins. High authority that these structures exist; contains no code and does not prove runtime behaviour.
