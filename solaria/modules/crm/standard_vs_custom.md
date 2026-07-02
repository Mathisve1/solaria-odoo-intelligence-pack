# CRM (`crm`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Apply with the global framework `05_standard_vs_configuration_vs_custom_framework.md`. Edition: `crm` is Community; AI/VoIP/journey extensions are Enterprise.

## Likely standard (Community, source-verified structures)
Pipeline with configurable stages · lead/opportunity lifecycle · activities & activity plans · predictive lead scoring · rule-based lead assignment (daily cron) · lost reasons & win/loss analysis · UTM source attribution · email-to-lead gateway · merge/dedup support · recurring revenue plans · pipeline/activity reporting pivots.

## Configuration possibilities (no code)
Stages per team, probability defaults, lost reasons, tags, scoring field selection, assignment rules and team quotas, activity types/plans, mail aliases, lead enrichment settings, menus visibility (leads on/off), templates for emails.

## Studio possibilities (Enterprise, governed)
Extra qualification fields (segment, compliance flags), tailored form layouts per industry, list/kanban tweaks, simple related fields. Keep algorithms out of Studio.

## Automation possibilities (Community `base_automation`)
Escalation alerts (stale opportunities), auto-assignment beyond native rules, stage-entry notifications/emails, data-quality nudges (missing phone/email), webhook pings to external systems. Enterprise adds AI server actions/fields (drafts, summaries).

## Custom development is justified when
- A proprietary scoring/routing algorithm is genuinely differentiating and must run in-flow.
- High-volume ingestion from proprietary sources needs a robust adapter (API-level work).
- Complex commission/territory engines beyond `partner_commission` (E) — after challenging the requirement.

## External integration is justified when
- Corporate marketing cloud remains system of engagement (journeys stay there; leads sync in).
- Telephony/contact-center platforms outside Odoo VoIP scope.
- Third-party enrichment/data providers replacing IAP.

## What to avoid
- Rebuilding stages as custom states (kills standard reporting).
- Custom duplicate logic before testing native dedup on real data.
- Hard-coding routing matrices that assignment rules can express.
- Promising AI lead features to Community-edition clients.

## Deloitte recommendation principles
Standard pipeline first, configuration for routing/scoring, automation rules for discipline nudges, Studio only for data shape, custom only for provable differentiation. Any CRM customization request during discovery is a smell — park it until users have run the standard pipeline for two weeks.

## Validation questions before recommending customization
1. Which exact routing/scoring case fails in a live configuration test?
2. Is the gap volume-driven (integration) or logic-driven (algorithm)?
3. Does the Enterprise layer (AI, journeys, VoIP) already close it — and is the edition available?
4. Who owns the custom logic through upgrades?
