# Documents (`documents`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `documents` |
| Display name | Documents |
| Source origin | **Enterprise** |
| Version scope | Odoo 19.0 |
| Dependencies | `mail`, `portal`, `web_enterprise`, `attachment_indexation`, `digest` |
| Functional domain | Documents / DMS |
| Confidence | High for structures; workflow-action behavior and AI sorting need live validation |

## Business purpose
A DMS inside the ERP: organize files in workspaces with tags and fine-grained access, and — the differentiator — turn documents into business records through workflow actions (PDF → vendor bill, CV → applicant, contract → sign request), making the document inbox part of operations.

## Main users / personas
Finance (bill inbox), HR (employee files via `documents_hr`), legal/admin (contracts), project teams (`documents_project`), management (spreadsheets in `documents_spreadsheet`), external parties (sharing links/portals).

## Business problems solved
- Files trapped in shares/mailboxes → workspaces with tags, activities, ownership (`documents.document` wraps `ir.attachment` with process metadata).
- Manual re-typing from documents → workflow actions + (E AI) `ai_documents` auto-sorting + OCR bridges (`documents_account` patterns with extract family).
- Uncontrolled sharing → `documents.access`/`documents.sharing` models (access tracking source-verified: `documents.access.tracking`).
- Document requests chasing → request flow (`documents.request_wizard`) with activities.

## Main business processes (source-verified)
1. Intake: upload, email alias per workspace, request-from-someone flow.
2. Organize: workspaces (hierarchy), tags, ownership; spreadsheet documents live here too.
3. Act: workflow/server actions per workspace (create bill/task/sign request, move/tag) — `documents.operation`, link-to-record wizard.
4. Share: internal rights per workspace/role; external share links with scope/expiry (validate exact options live).

## Key functional capabilities
Versioning-ish attachment handling (validate depth), previews, chatter/activities on documents, deletion protection patterns (`documents.unlink.mixin`), KPI/digest integration, bridges: `documents_hr`, `documents_project`, `documents_account`(+fiscal), `documents_sign`, `documents_spreadsheet`, `website_documents`; AI: `ai_documents` (auto-classification), `ai_documents_source` (ground AI agents on documents).

## Community fallback
Plain attachments/chatter on records — no workspaces, workflow actions, or governance layer. For DMS needs on Community: external DMS integration or edition upgrade.

## Configuration opportunities
Workspace tree + access design (THE core design task), tags taxonomy, workflow actions per workspace, email aliases, retention conventions (process + automation).

## Studio / automation opportunities
Automation: auto-tag by source, escalation on stale documents-with-activities, retention sweeps (careful, legal sign-off). AI (E): auto-sorting with review loop. Studio: document metadata fields per workspace context.

## Custom development triggers
Regulated records management (certified archiving, WORM) beyond scope; complex approval-with-versioning regimes (contract lifecycle beyond sign bridge); mass migration tooling.

## External integration triggers
SharePoint/Drive coexistence (collaboration-heavy authoring stays there — define the system-of-record boundary), certified archiving services, scanning hardware/services, CLM suites if contracts are the core business.

## Common client questions
"Replace SharePoint?" — for process documents yes, for collaborative authoring no — draw the line. · "OCR bills from here?" — with account extract bridges (E) — the flagship flow. · "Access control depth?" — workspace/role model is real (source-verified); validate against the client's matrix live. · "Retention/GDPR?" — design + automation; not an out-of-box compliance engine.

## Fit-gap considerations
Strongest when documents *drive processes* (AP inbox, HR files, contracts). Weakest as a pure collaboration/authoring platform. The AI auto-sorting + agents-grounded-on-documents combo (E) is an emerging differentiator — validate quality before promising.

## Deloitte demo angles
1. **The inbox that works:** drag 3 PDFs → one becomes a vendor bill (OCR), one a task, one a sign request — audience sees the DMS acting.
2. **HR files:** employee workspace auto-filed docs with access rules.
3. **AI moment (E):** unsorted pile → auto-classified into workspaces — label as AI, show the review step.

## Implementation watch-outs
- Workspace/access design workshops before migration; folder chaos imported = chaos certified.
- Migration scope pragmatism (active documents first, archive stays archived).
- Legal involvement for retention rules and external sharing policies.
- Test access inheritance into AI features (leakage check) before enabling agents on documents.

## Risks and assumptions
Structures verified. Versioning depth, share-link options, AI sorting quality are runtime → validate. Enterprise licensing required.

## Validation checklist
- [ ] Workspace + access matrix designed and tested with real roles
- [ ] Priority workflow actions configured (bill, task, sign) and demoed
- [ ] Migration scope agreed (what moves, what stays)
- [ ] Retention/sharing policy signed by legal
- [ ] AI sorting/agent scope piloted with leakage tests
