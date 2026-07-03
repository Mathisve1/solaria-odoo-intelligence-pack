# Subscriptions (`sale_subscription`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `sale_subscription` |
| Display name | Subscriptions |
| Source origin | **Enterprise** |
| Version scope | Odoo 19.0 |
| Dependencies | **`account_accountant`** (E), `sale_management`, `portal`, `rating`, `sms`, `web_cohort` |
| Functional domain | Subscriptions & recurring revenue |
| Confidence | High for structures; billing/dunning cadence needs live validation |

## Business purpose
Run recurring business on the sales backbone: subscriptions are sales orders with a recurrence plan — automated recurring invoicing, renewals/upsells, churn tracking and MRR analytics — connected directly to accounting and the customer portal.

## Main users / personas
Subscription/CS managers, finance (recurring billing, revenue), sales (upsell/renewal), executives (MRR/churn/cohorts), customers (portal self-service).

## Business problems solved
- Manual recurring invoicing → plan-driven invoice generation (multiple crons shipped: 4 source-verified — billing/renewal background engine).
- Revenue metric blindness → `sale.order.log` event journal (new/expansion/contraction/churn patterns) + MRR reports (`sale.order.log.report`, `sale.subscription.report`), cohort views, "MRR Breakdown/Timeline" menus.
- Uncontrolled churn → close reasons (`sale.order.close.reason`), close wizard, retention menu.
- Payment friction → tokenized payments (payment.token extensions), portal management, automated charge patterns (validate provider support live).

## Main business processes (source-verified)
1. Sell: quotation with recurring plan (`sale.subscription.plan` — billing period, terms) and recurring products.
2. Run: crons generate invoices per period; payment collection via tokens/providers; dunning intersects Enterprise follow-ups.
3. Change: upsell/renewal orders linked to the subscription; customer-change wizard; logs record MRR movements.
4. End: close with reason → churn analytics; retention reporting.

## Key functional capabilities
Plans with period/pricing rules (pricelist extensions for recurrence), progress/health on subscriptions, portal (view, pay, potentially close/renew — validate options), cohort retention analysis, KPI digests, `website_sale_subscription` (sell online, E).

## Fit with other modules
`account_accountant` (hard E dependency — pulls the finance edition decision), payment providers (tokens), `sale` (orders/upsells), CRM (`crm_sale_subscription` bridge), helpdesk context for CS, spreadsheet dashboards.

## Community fallback
None (no subscription app in Community 19.0). Workarounds (manual recurring invoices, third-party billing) lose MRR analytics and automation — position honestly.

## Configuration opportunities
Plans, recurring products/pricing, close reasons, portal options, dunning interplay with follow-ups, alerts on health (validate the alert feature scope live).

## Studio / automation opportunities
Automation: health-based playbooks (usage drop → CS activity), renewal-window task creation, expansion-opportunity flags. Studio: contract metadata fields. Revenue recognition/deferrals stay in accounting configuration — not Studio.

## Custom development triggers
Usage-based/metered billing beyond shipped patterns (validate what 19.0 supports live first), complex rating engines (telecom-grade), partner/reseller billing hierarchies.

## External integration triggers
Payment orchestration/dunning specialists, usage-metering platforms feeding billing, revenue-recognition suites for IFRS15-heavy contexts (or E deferrals — scope with finance).

## Common client questions
"Proration on upgrades?" — validate behavior live before promising specifics. · "Usage-based billing?" — check shipped scope; often custom/integration. · "MRR/churn out of the box?" — yes structurally (logs+reports); definitions must be validated with finance. · "Self-service portal?" — core exists; exact self-service actions to validate.

## Fit-gap considerations
Great for SaaS-style, service contracts, rentals-adjacent recurring models. Gap zone: telecom-grade rating, heavy usage metering, complex partner billing. The `account_accountant` dependency makes subscriptions an Enterprise-finance conversation by construction.

## Deloitte demo angles
1. **Recurring machine:** subscription order → next-invoice date → run cron (staged) → invoice + payment collected — "billing runs itself".
2. **CFO screen:** MRR breakdown/timeline + cohort retention.
3. **Churn story:** close with reason → retention analysis reflects it.

## Implementation watch-outs
- MRR/churn definitions workshop with finance BEFORE reporting promises (definitions vary wildly).
- Payment-provider token support per market validated early.
- Migration of running contracts (start dates, next-invoice dates, open balances) is delicate — rehearse.
- Dunning path design end-to-end (failed payment → retries → follow-up → suspension policy).

## Risks and assumptions
Structures verified (plans, logs, crons, reports). Proration, usage billing scope, portal self-service depth and dunning specifics are runtime → validate. Enterprise licensing required (incl. accounting).

## Validation checklist
- [ ] Billing models (fixed/seat/usage) mapped to plans with live tests
- [ ] MRR/churn definitions signed by finance
- [ ] Payment collection + dunning flow tested with real provider sandbox
- [ ] Contract migration plan rehearsed
