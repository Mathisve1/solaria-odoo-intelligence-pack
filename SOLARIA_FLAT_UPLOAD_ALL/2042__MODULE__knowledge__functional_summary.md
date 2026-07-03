# Knowledge (`knowledge`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `knowledge` |
| Display name | Knowledge |
| Source origin | **Enterprise** |
| Version scope | Odoo 19.0 |
| Dependencies | `web`, `html_editor`, `mail`, `portal`, `web_hierarchy`, `digest` |
| Functional domain | Knowledge management |
| Confidence | High for structures; editor/embed capabilities evolve — demo live |

## Business purpose
A Notion-style internal knowledge base living inside the ERP: hierarchical articles with a rich editor, embedded live business views, templates, member-based sharing — so procedures, playbooks and reference content sit next to the processes they describe (and can ground AI assistants via `ai_knowledge`/agent sources).

## Main users / personas
All internal teams (SOPs, onboarding), support (answer articles with helpdesk), sales (battlecards), HR (policy hub), knowledge managers (structure/governance).

## Business problems solved
- Knowledge in wikis/drives divorced from work → articles (`knowledge.article`) with hierarchy (`web_hierarchy`), favorites, embedded item views of live records.
- Sharing chaos → member model (`knowledge.article.member` with permissions; internal/private/shared workspaces patterns).
- Blank-page paralysis → templates with categories/stages (`knowledge.article.template.*`).
- Comment-less docs → article threads (`knowledge.article.thread` — discussions on articles).

## Main business processes (source-verified)
1. Create/organize: workspace vs private articles, hierarchy, covers, stages for article boards.
2. Collaborate: members+permissions, threads, chatter; trash/restore lifecycle ("Trashed" menu).
3. Embed: live views (kanban/list) inside articles — dashboards-as-documents patterns.
4. Consume: search, favorites, portal/website sharing (`website_knowledge`), helpdesk answer insertion; AI drafts (`ai_knowledge`).

## Fit with other modules
`helpdesk` (canned knowledge), `ai_app`/`ai_documents_source` patterns (knowledge as AI grounding), `website_knowledge` (public help centers), any app via embedded views.

## Community fallback
None equivalent (chatter notes/attachments only). External wikis remain the alternative — with the integration/AI-grounding downsides.

## Configuration opportunities
Structure/taxonomy design, templates, permissions model, stages for editorial boards, public sharing scope.

## Studio / automation opportunities
Automation: review-cycle activities on stale articles, onboarding article assignments. Article content itself is editorial, not Studio territory.

## Custom development triggers
Rarely justified: heavy CMS-publishing regimes, compliance-controlled documentation (consider documents+sign instead), advanced analytics on knowledge usage.

## External integration triggers
Corporate intranets (SharePoint/Confluence) coexistence — decide the boundary (process knowledge in Odoo, corporate comms elsewhere); LMS platforms (or `website_slides`).

## Common client questions
"Notion/Confluence replacement?" — for process-adjacent knowledge yes; for company-wide intranet/comms, boundary decision. · "Access control?" — member/permission model verified in source; test the matrix live. · "Can AI answer from it?" — the grounding pattern exists (E); validate quality with a pilot; govern article accuracy first.

## Fit-gap considerations
Quick-win app: value = adoption + editorial governance more than features. The AI-grounding story elevates it strategically — Knowledge becomes the curated corpus for assistants; that requires content quality ownership (a Deloitte advisory hook).

## Deloitte demo angles
1. **SOP with live data:** procedure article embedding the actual open-tasks view it governs.
2. **Support flow:** agent inserts article answer into a ticket reply.
3. **AI teaser (E):** assistant answering from a curated article set — labeled, rehearsed.

## Implementation watch-outs
- Name an owner per knowledge domain; orphaned wikis rot in months.
- Migration selectivity: import living documents only.
- Permission defaults reviewed (what's company-visible by default?).

## Risks and assumptions
Structures verified; editor features, embed depth and AI answer quality are runtime → validate. Enterprise licensing required.

## Validation checklist
- [ ] Taxonomy + ownership model per domain
- [ ] Permission matrix tested with real roles
- [ ] Editorial cadence (review cycles) automated
- [ ] AI-grounding pilot criteria defined (if used)
