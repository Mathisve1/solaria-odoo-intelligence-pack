# Accounting (`account_accountant`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only. This module IS the edition answer for "real accounting" — the customization question here is almost always "configure reconciliation models properly", not "build".

## Likely standard (Enterprise)
Bank reconciliation workbench · auto-reconcile assistance (cron + wizard) · manual reconciliation tooling · fiscal years (incl. governed non-12-month years) · lock dates with auditable exception flow · clerk-vs-accountant rights split.

## Configuration possibilities
Reconciliation models/matching rules, write-off accounts, lock-date policy per role, fiscal years, bank journals and import formats, close-cadence activities.

## Studio possibilities
Effectively none appropriate — do not reshape reconciliation/close objects with Studio; finance auditability outranks UI wishes.

## Automation possibilities
Advisory only: unreconciled-aging nudges, close-checklist activity plans, digest KPIs. Matching logic stays in reconciliation models; posting stays deterministic and human-validated.

## Custom development is justified when
- Almost never in this layer. Legitimate residuals: import adapters for exotic bank formats (after exhausting shipped + localization formats), fiduciary-workflow integrations.

## External integration is justified when
- Treasury/banking hubs own payments and feeds · group consolidation platforms consume trial balances · external accountant portals exchange files.

## What to avoid
- Promising auto-reconciliation percentages before a pilot on real statements.
- "Technical" reopening of periods bypassing the exception flow — audit finding by design.
- Custom matching scripts next to reconciliation models.
- Scoping this module without `account_reports` when statutory outputs exist (they usually do).

## Deloitte recommendation principles
Present the finance stack as three layers (account → account_accountant → account_reports) and place every client requirement on a layer. Reconciliation tuning is a named workstream with real data. Lock-date governance is a selling point to CFOs/auditors — demo it, don't hide it.

## Validation questions
1. Statement volumes and formats per bank — covered by shipped import paths?
2. Who closes, who may reopen, and what do auditors require as evidence?
3. Which write-off/rounding policies apply (configuration decisions)?
