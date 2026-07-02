# Workflow & Automation Summary — `website` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `website` — Website |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Publishing lifecycle (draft/published) per page/content object; visitor tracking feeds CRM/marketing — the site is a data source, not a brochure.

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Disable unused snippets assets | website | 1 weeks |
| Website Visitor : clean inactive visitors | website.visitor | 1 days |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Website: Dashboard | website | code |
| Website: Analytics | website | code |

## Integration surface
- Direct dependencies: `digest`, `web`, `html_editor`, `http_routing`, `portal`, `social_media`, `auth_signup`, `mail`, `google_recaptcha`, `utm`, `html_builder`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
