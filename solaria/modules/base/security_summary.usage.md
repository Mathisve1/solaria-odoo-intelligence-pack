# Usage Instructions — modules/base/security_summary.md

| Field | Value |
|---|---|
| Document name | `modules/base/security_summary.md` |
| Document type | Security / Access Evidence |
| Authority level | High for shipped groups/access rights/record rules |
| Upload priority | Medium (upload Batch 4) |

## Use this document when
Role design baselines, permission questions, segregation-of-duties discussions involving `base`.

## Do not use this document when
As the client's target security model (that is a project design task) or for org-specific role advice without client context.

## How to combine with other documents
Client role requirements; roadmap playbook security phase; other modules' security summaries for cross-app roles.

## Limitations
Shipped 19.0 defaults only; domain hints are abbreviated; client configuration and custom groups are out of scope.

## Source origin relevance
`base` ships in Odoo 19.0 **Community** (Enterprise modules may extend it — see 03 map).

## Confidence / validation note
High that listed structures exist in the 19.0 source; runtime behaviour, UX and performance require validation in a live Odoo 19.0 database.

## Recommended Solaria document description (copy-paste)
> Security baseline of the Odoo 19.0 `base` module (Community): shipped groups, access rights and record rules with Deloitte advisory notes. Use as the starting point for role design; the client's actual security model must be designed and tested per project.
