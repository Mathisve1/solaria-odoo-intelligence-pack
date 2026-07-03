# Website (`website`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `website` |
| Display name | Website |
| Source origin | **Community** (Enterprise adds `website_studio`, `website_generator`, `ai_website`, push notifications) |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `web`, `html_builder`, `html_editor`, `http_routing`, `portal`, `mail`, `utm`, `social_media`, `auth_signup`, `google_recaptcha`, `digest` |
| Functional domain | Website / front-office platform |
| Confidence | High for structures; builder UX evolves per release — demo live |

## Business purpose
The public web layer of the same platform that runs the ERP: build/edit pages visually, run multiple websites/brands, capture visitors into business flows (forms→CRM, shop→sales, careers→recruitment) — content and transactions on one data model.

## Main users / personas
Marketing/content editors, web designers, digital managers (multi-site), sales/marketing consuming visitor data, IT (domains, SEO governance).

## Business problems solved
- Agency-dependent site changes → in-house visual builder with publish workflow.
- Web/ERP data gap → forms create leads/applicants/tickets directly; visitors tracked (`website.visitor`).
- Multi-brand sprawl → multi-website with shared or separate catalogs/settings, per-site menus/pages.

## Main business processes (source-verified)
1. Site building: pages, menus (`website.menu`), snippets/building blocks; publish lifecycle (draft/published via publishing mixin).
2. Multi-site management (`website` model: domains, languages, themes per site).
3. Visitor capture: `website.visitor` tracking, forms, livechat (`im_livechat` bridge), SEO metadata mixins.
4. Governance: restricted editor vs designer groups; per-site publishing rights.

## Key functional capabilities
Multi-language with translations, SEO tooling (metadata, sitemaps, redirects `website.rewrite`), cookie/consent patterns, blogs/events/slides as sibling apps, robots/controllers for public routes, theming (Community themes + `theme_*`).

## Fit with other modules
`website_sale` (shop), `website_crm` (lead forms), `website_hr_recruitment` (careers), `website_event`, `website_slides` (eLearning), `im_livechat` (+`ai_livechat` E), portal (customer self-service is website-adjacent), Enterprise: `website_studio` (model-driven site apps), `website_generator` (AI site generation), `ai_website`.

## Standard in 19.0 (Community)
Builder, multi-site, multi-language, SEO basics, forms, visitor tracking, blogs/events/eLearning siblings, livechat, themes.

## Enterprise-specific
Studio for website objects, AI website generation/content, push notifications, appointment scheduling pages (`appointment` E family).

## Configuration opportunities
Sites/domains/languages, menus, themes, page templates, form actions (which record they create), SEO defaults, cookie bars, redirects.

## Studio / automation opportunities
Automation: form→routing rules (lead assignment), content-expiry reminders. Website Studio (E): publish custom models as site pages (e.g., a public reference-projects catalog) — powerful, governance needed.

## Custom development triggers
Custom page types/controllers with business logic (dealer locators, calculators), headless/API-first setups, design systems beyond theming.

## External integration triggers
CMS coexistence (corporate WordPress/AEM stays → decide the boundary: Odoo for transactional pages), DAM systems, analytics/consent platforms (beyond built-ins).

## Common client questions
"Can marketing edit without IT?" — yes, builder + rights split. · "Multiple brands/domains?" — multi-website; validate shared-data nuances (products/customers per site) live. · "SEO parity with WordPress?" — solid basics; heavy content-marketing teams may still want their CMS — draw the boundary honestly. · "GDPR/cookies?" — built-in patterns + project-level consent design.

## Fit-gap considerations
Great for SMB/mid-market sites and *transactional* web (shop, portals, forms). For high-end brand/content operations, position coexistence (corporate CMS for storytelling, Odoo for commerce/self-service) rather than fighting it.

## Deloitte demo angles
1. **Form-to-flow:** edit a page live → submit form → lead appears in CRM with source attribution.
2. **Multi-brand:** switch website selector, different theme/menu, same backend.
3. **E uplift:** AI-generate a draft page/site (`website_generator`) — label as Enterprise, rehearse before showing.

## Implementation watch-outs
- Domain/SSL/hosting model decisions early (Odoo Online vs on-prem constraints differ — validate).
- SEO migration (redirect maps) for existing sites — plan like a mini-project.
- Content governance: who may publish; editor vs designer rights enforced.
- Performance/brand expectations vs builder reality — prototype the homepage first.

## Risks and assumptions
Structures verified; builder capabilities/UX and theme flexibility are runtime — always prototype. Multi-site data sharing rules (which products/prices per site) need live validation.

## Validation checklist
- [ ] Site inventory + migration/redirect plan
- [ ] Multi-site/brand matrix (domains, languages, catalogs)
- [ ] Publishing governance roles set and tested
- [ ] Homepage prototype approved by brand owners
- [ ] Boundary decision if a corporate CMS exists
