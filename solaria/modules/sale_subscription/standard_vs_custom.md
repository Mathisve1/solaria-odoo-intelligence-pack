# Subscriptions (`sale_subscription`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only, and it depends on Enterprise Accounting (`account_accountant`) — the edition decision is bundled.

## Likely standard (Enterprise)
Recurring plans on sales orders · automated recurring invoicing (cron engine) · renewals/upsell orders · close reasons + churn/retention analytics · MRR logs, breakdown & timeline reports, cohorts · tokenized payment collection · customer portal · online subscription sales (`website_sale_subscription`).

## Configuration possibilities
Plans (period, terms), recurring pricing (pricelist rules), close reasons, portal options, digests/KPIs, follow-up interplay.

## Studio possibilities
Contract metadata (segment, renewal owner). No billing math in Studio.

## Automation possibilities
Renewal-window activities, health-drop playbooks, expansion flags, failed-payment escalations (aligned with follow-ups).

## Custom development is justified when
- Usage/metered billing beyond shipped scope (validate first) — metering adapter + billing mapping.
- Telecom-grade rating, reseller/partner billing hierarchies.
- Complex proration schemes contractually mandated (after live validation of native behavior).

## External integration is justified when
- Payment orchestration/dunning platforms, usage metering sources, IFRS15 revenue engines (scope E deferrals first).

## What to avoid
- Promising proration/usage specifics before a sandbox test.
- Custom recurring engines next to the native crons (double-billing risk).
- Reporting MRR without finance-agreed definitions.
- Scoping subscriptions for a Community-only budget (dependency makes it impossible).

## Deloitte recommendation principles
Treat subscriptions as a finance+CS transformation, not a sales feature: definitions, dunning, revenue treatment first; then automate. Evidence every billing-model claim in a sandbox.

## Validation questions
1. Billing models incl. edge cases (mid-term changes, pauses) — tested live?
2. Collection stack (providers, retries, suspension policy)?
3. Revenue recognition needs (deferrals E vs external)?
4. Migration: how many running contracts, what history must survive?
