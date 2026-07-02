# Usage Instructions — 01_global_module_catalog.json

| Field | Value |
|---|---|
| Document name | `01_global_module_catalog.json` |
| Document type | Index / Navigation Document (source-derived catalog) |
| Authority level | High for module existence/edition/dependencies |
| Upload priority | High (Batch 2) |

## Use this document when
Confirming whether a module exists in Odoo 19.0, which edition ships it, what it depends on, its category/domain and manifest summary — for ALL 1,422 modules.

## Do not use this document when
Judging detailed runtime behaviour or feature depth (use module packs / live validation).

## How to combine with other documents
Domain map 04 for business framing; module packs for depth; 02 for dependency structure.

## Limitations
Manifest-level truth; interpretations for modules without summaries carry per-entry confidence markers; data-file lists truncated to samples.

## Source origin relevance
Every entry carries source_origin (community/enterprise) from the actual tree it ships in.

## Confidence / validation note
High for existence/edition; per-entry confidence field for interpretations.

## Recommended Solaria document description (copy-paste)
> Source-derived catalog of ALL 1,422 Odoo 19.0 modules (650 Community + 772 Enterprise): edition, dependencies, category, functional domain, summary, per-entry confidence. THE authority on whether a module exists and which edition ships it. Never cite a module absent from this catalog. Not proof of runtime behaviour.
