# Website (`website`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: builder/multi-site are Community; website Studio, AI generation, push notifications are Enterprise.

## Likely standard (Community)
Visual builder with snippets · multi-website, multi-language · publish workflow + rights split (editor/designer) · forms creating business records · visitor tracking · SEO metadata/redirects/sitemap · blogs/events/eLearning/livechat siblings · theming.

## Configuration possibilities
Domains/languages per site, menus, themes, form target objects, SEO defaults, cookie bar, redirects, per-site company/pricing links (with commerce).

## Studio possibilities (E)
Website Studio: publish records of custom/standard models as pages (catalogs, references) — governed; content editors shouldn't own data models.

## Automation possibilities
Form-routing rules, stale-content review activities, UTM hygiene checks.

## Custom development is justified when
- Interactive tools with business logic (configurators, calculators, locators) as controllers/OWL widgets.
- Headless patterns or specific design systems beyond themes (accept the maintenance cost consciously).

## External integration is justified when
- Corporate CMS/DAM remains for brand content — set the boundary (transactional = Odoo).
- Advanced analytics/consent/personalization stacks.

## What to avoid
- Pixel-perfect brand promises before a homepage prototype.
- Theme forks for wishes CSS/settings can meet.
- Splitting forms from flows (external form tools posting to email) — the integration IS the value.
- Letting everyone publish (governance first).

## Deloitte recommendation principles
Sell the platform effect (form→lead, shop→order, careers→applicant) over CMS feature wars. Prototype early; brand stakeholders decide on evidence. Draw the CMS-coexistence boundary explicitly in multi-site corporates.

## Validation questions
1. Which pages are transactional vs brand-storytelling — and who owns each?
2. Hosting model and its constraints (custom modules on Odoo Online are restricted — validate current policy)?
3. SEO baseline to preserve (traffic pages, redirect map)?
