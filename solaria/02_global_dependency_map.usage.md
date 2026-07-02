# Usage Instructions — 02_global_dependency_map.yaml

| Field | Value |
|---|---|
| Document name | `02_global_dependency_map.yaml` |
| Document type | Index / Navigation Document (dependency map) |
| Authority level | High for declared dependencies |
| Upload priority | High (Batch 2) |

## Use this document when
Architecture questions: what a module depends on, which Enterprise modules extend a core Community app, dependency hubs, cross-edition structure.

## Do not use this document when
Functional capability questions.

## How to combine with other documents
Catalog 01 for module details; 03 map for the edition narrative.

## Limitations
Direct manifest dependencies only (not transitive); no behaviour.

## Source origin relevance
Shows Enterprise-on-Community layering explicitly (verified: zero unresolved dependencies).

## Confidence / validation note
High — parsed from manifests.

## Recommended Solaria document description (copy-paste)
> Manifest-level dependency map of all 1,422 Odoo 19.0 modules: per-module direct dependencies with edition, top dependency hubs, and which Enterprise modules directly extend each core Community app. Use for architecture and 'what extends what' questions. Direct dependencies only.
