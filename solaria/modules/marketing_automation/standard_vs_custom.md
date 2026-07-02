# Marketing Automation (`marketing_automation`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only (on Community `mass_mailing`). Community = one-shot mailings; journeys need Enterprise.

## Likely standard (Enterprise)
Visual multi-step campaigns on live record filters · timed/conditional activity trees with branches · per-node traces/KPIs · test mode · server-action nodes (ERP-side actions) · SMS/WhatsApp/CRM bridges · UTM + link tracking · consent/blacklist foundations.

## Configuration possibilities
Audience filters, campaign templates, sending identities, consent policy, UTM conventions, channel bridges.

## Studio possibilities
Segment-driver fields (lifecycle stage, persona) with a governed taxonomy.

## Automation possibilities
Data-hygiene rules feeding segments; journey-adjacent activities (sales handoffs). The journey engine itself covers most needs — don't duplicate it with automation rules.

## Custom development is justified when
- External behavioral events (product telemetry) must trigger journeys — event ingestion adapters.
- Personalization/content logic beyond templates.

## External integration is justified when
- Corporate marketing cloud owns brand campaigns (boundary agreement) · CDP as segment source · specialized deliverability infrastructure.

## What to avoid
- Launching without deliverability + consent groundwork (brand damage risk).
- Journey sprawl with no owner/review cadence.
- Overselling as a full martech suite — its edge is ERP-data journeys.

## Deloitte recommendation principles
Start with two high-value ERP-truth journeys (win-back, lapsing renewals) and measure. Consent and deliverability are phase zero. Use server-action nodes to make marketing operational (create activities, not just emails).

## Validation questions
1. Which journeys create money fastest — and is the data for their filters clean?
2. Consent status of the current database?
3. Channel mix (email/SMS/WhatsApp) and commercial terms?
