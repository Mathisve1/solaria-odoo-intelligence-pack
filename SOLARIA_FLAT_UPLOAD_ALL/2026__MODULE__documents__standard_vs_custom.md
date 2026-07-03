# Documents (`documents`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only.

## Likely standard (Enterprise)
Workspaces with hierarchical access · tags, activities, ownership · workflow actions turning files into business records · email-alias intake · document requests · share links · access tracking · bridges (HR, project, accounting, sign, spreadsheet) · AI auto-sorting (`ai_documents`) and documents-as-AI-sources.

## Configuration possibilities
Workspace tree, access per workspace/role, tag taxonomies, workflow actions, aliases, request templates.

## Studio possibilities
Metadata fields on documents for workspace contexts (contract type, expiry date) — pair expiry fields with automation alerts.

## Automation possibilities
Auto-tagging by source/alias, expiry/retention alerts, stale-review activities, routing rules to workspaces.

## Custom development is justified when
- Certified/regulated archiving (WORM, eIDAS-grade preservation) requirements exceed scope — usually integration to archiving services + glue.
- CLM-grade contract lifecycle (clause libraries, negotiation) if contracts are core — challenge vs sign+documents first.
- Bulk migration tooling with mapping rules.

## External integration is justified when
- Collaborative authoring stays in M365/Google (define system-of-record boundary) · certified archives · scanning services/hardware.

## What to avoid
- Importing legacy folder chaos 1:1 — design workspaces first.
- Using Documents as a file dump without workflow actions (that's the whole point).
- Enabling AI agents on documents before access-leakage testing.
- Retention promises without legal sign-off.

## Deloitte recommendation principles
Sell Documents as process infrastructure (AP inbox, HR files, contract flow), not "cheaper SharePoint". Access design is the project. AI features enter with review loops and measured quality.

## Validation questions
1. Which document-driven processes hurt today (AP? HR? contracts?) — start there.
2. Access matrix: who sees/edits what — tested against workspaces live?
3. Retention/archiving obligations per document class?
4. What stays in M365/Drive, and where is the boundary?
