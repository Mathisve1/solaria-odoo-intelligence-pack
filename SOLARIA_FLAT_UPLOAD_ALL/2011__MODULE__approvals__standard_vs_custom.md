# Approvals (`approvals`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only. This app is the designated first stop for any "approval workflow" request.

## Likely standard (Enterprise)
Category-defined request forms (fields, products, documents required) · approver sets incl. manager patterns and minimum count · per-approver statuses with full trail · my/manager dashboards · purchase bridge.

## Configuration possibilities
Categories as policy objects, tiered categories for amount bands, required documents, approver sets, tile visibility.

## Studio possibilities
Request context fields (cost center, risk class, project ref). Keep routing logic in category design/automation, not field hacks.

## Automation possibilities
Stale-request escalation, amount-based routing helpers, post-approval record creation/notifications.

## Custom development is justified when
- A true delegation-of-authority engine (conditional matrices, delegation calendars, legal registries) is mandated — after a serious category-design attempt and a DoA workshop.
- Approvals must span external systems.

## External integration is justified when
- Corporate workflow platforms are mandated by group IT — Odoo raises/receives statuses via API.

## What to avoid
- Custom approval modules before an Approvals design attempt (the classic unnecessary build).
- Recreating native app approvals (expense, time off, purchase two-step) here — overlap confusion.
- Advisory automation dressed up as blocking control — say which one it is.

## Deloitte recommendation principles
Approval requirements get a matrix workshop; every line maps to native app flow / Approvals category / (rare) custom. Categories = policy configuration is the governance sell.

## Validation questions
1. The full matrix: types × amounts × entities × approvers × delegation rules?
2. Advisory or blocking — per line?
3. What happens after approval (records to create, systems to inform)?
