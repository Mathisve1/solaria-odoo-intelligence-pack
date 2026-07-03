# Studio (`web_studio`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `web_studio` |
| Display name | Studio |
| Source origin | **Enterprise** |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `base_automation`, `base_import_module`, `mail`, `web`, `web_enterprise`, `html_editor`, `web_map`, `web_gantt`, `web_cohort`, `sms` |
| Functional domain | Studio / no-code customization |
| Confidence | High for structures (incl. approval-rule models); editor capabilities evolve per release — demo live |

## Business purpose
Odoo's governed no-code customization layer: add fields, tailor views, create apps/menus, edit reports — graphically, without a developer. In 19.0 it also carries **Studio Approval Rules** (source-verified models `studio.approval.rule/entry/request` with approvers and delegation): no-code approval requirements on actions/buttons. Studio is rung 3 of the Deloitte solution ladder — the sanctioned middle ground between configuration and custom code.

## Main users / personas
Key users/citizen developers (fields, views), functional consultants (fit-gap execution without dev queue), IT/governance owners (registry, export), process owners (approval rules).

## Business problems solved
- Dev-queue bottleneck for small data/UI changes → key users add fields/views under governance.
- "We need approval on this button" → **Studio approval rules** (with entries log and delegation, source-verified) — check BEFORE proposing the Approvals app or custom code for action-level gates.
- Environment drift of no-code changes → **Studio Export** (`studio.export.*` models/wizard) packages customizations as a module — the migration/governance artifact between staging and production.
- Report layout changes → report editor (validate current editor scope live).

## Main capabilities (source-verified structures)
- 9 defined models: approval rules/entries/requests/delegation, export model/wizard, `studio.mixin`; 26 model extensions (the editor overlays much of the platform).
- Backend menus: Studio Approval Entries / Approval Rules / Studio Export — the governance surface (the editor itself is a UI overlay, not a menu tree).
- Via its dependencies, Studio brings the Enterprise view toolkit (map/gantt/cohort) into reach of customized apps.

## Fit with other modules
Built on `base_automation` (automation rules pair naturally with Studio artifacts) and `base_import_module` (export/import of customizations). `web_studio_ai_fields` (E) adds AI-computed fields creation from Studio. Website Studio is a sibling for site objects.

## Standard vs edition
Enterprise-only. On Community, rung 3 of the ladder is unavailable: equivalent needs become small custom modules — a material edition argument for clients expecting key-user autonomy.

## Configuration vs Studio boundary (keep it sharp)
Configuration = options the apps already offer (stages, routes, settings). Studio = new shape (fields, views, models, menus, approval rules on actions). If a shipped setting exists, Studio is the wrong tool.

## Custom development triggers (when Studio must NOT be used)
Business algorithms, computed logic beyond simple cases, performance-sensitive screens, anything needing tests/versioned review — rung 5 with SDLC. Studio is for shape, not brains (the pack's standing rule).

## External integration triggers
None inherent — but exported Studio modules participate in environment/deployment tooling like any module.

## Common client questions
"Can key users add fields safely?" — yes, WITH governance: named Studio users, change registry, staging-first, export-based promotion (the models for this exist — demo the export). · "Do Studio changes survive upgrades?" — they are data/module artifacts; they must be tested at each upgrade like any customization — never say "automatic". · "Approvals without code?" — action-level: Studio approval rules; request-object approvals: Approvals app; document both options with their fit. · "Is Studio available on our hosting?" — Enterprise + hosting policy — validate.

## Fit-gap considerations
Studio converts many would-be GAP-CUSTOM verdicts into FIT-STUDIO — but each conversion adds a governed artifact, not zero cost. In fit-gap registers, FIT-STUDIO entries need an owner and registry reference. The approval-rules capability changes several classic verdicts (button-level gates) — revisit old assumptions.

## Deloitte demo angles
1. **60-second field:** open any form → Studio → drag a field → save → it's live (staging!). The autonomy story for functional leadership.
2. **Governance counter-story (for IT):** Studio Export screen + approval entries log — "no-code, not no-governance".
3. **Approval rule:** add an approval requirement on a confirm button → second user approves → entries log shows the trail.

## Implementation watch-outs
- Ungoverned Studio = field sprawl and upgrade debt — enforce the pack's Studio governance rules (05 §5) contractually.
- Studio work happens on staging and promotes via export — never live-edit production.
- Inventory Studio artifacts per release; test them in upgrade rehearsals.

## Risks and assumptions
Structures verified (approval + export models, menus). Editor feature scope (which view types, report editor depth, AI-field creation via `web_studio_ai_fields`) is runtime → demo live. Enterprise licensing required.

## Validation checklist
- [ ] Studio governance policy agreed (named users, registry, staging-first, export promotion)
- [ ] Approval-rule expressiveness tested against the client's gate list
- [ ] Upgrade-rehearsal procedure includes Studio artifacts
- [ ] Hosting policy for Studio confirmed
