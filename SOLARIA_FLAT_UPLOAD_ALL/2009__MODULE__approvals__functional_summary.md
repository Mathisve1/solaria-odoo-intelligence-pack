# Approvals (`approvals`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `approvals` |
| Display name | Approvals |
| Source origin | **Enterprise** |
| Version scope | Odoo 19.0 |
| Dependencies | `mail`, `hr`, `product` |
| Functional domain | Approvals / internal governance |
| Confidence | High for structures; approver-resolution logic needs live validation |

## Business purpose
Generic, configurable approval requests for anything without a native flow: business trips, purchases-to-be, contracts, exceptions. Categories define the form (required fields, documents) and the approver matrix; requests carry a clear status trail — the standard answer to "we need an approval workflow" before anyone says "custom".

## Main users / personas
All employees (requesters), managers/named approvers, process owners (category design), procurement/finance (purchase bridge `approvals_purchase`).

## Business problems solved
- Email-based approvals with no trail → `approval.request` with per-approver records (`approval.approver` status each).
- One-off custom workflows → `approval.category` templates (fields on/off: amount, partner, products via `approval.product.line`, documents required flag).
- Policy drift → categories with fixed approver sets (`approval.category.approver`), manager-based patterns, minimum approvers.

## Main business processes (source-verified)
1. Employee opens category tile ("Dashboard" of `New Request` tiles) → fills category-defined form (+attachments if required).
2. Submit → approvers (from category: specific users/manager patterns) get activities; each approves/refuses (per-approver state).
3. Outcome drives the process (with purchase bridge: approved request → RFQ path); full trace in chatter.
4. Managers oversee via "Approvals to Review"/"All Approvals" menus.

## Key functional capabilities
Category-level required-field configuration, product lines on requests (pre-procurement), document requirements, multi-approver with minimum count, my/manager views, activity-driven notifications.

## Fit with other modules
`approvals_purchase` (E bridge to purchase), `hr` (manager resolution), `documents`/attachments, chatter/activities. Pattern: pre-transaction governance (approve BEFORE the PO/expense exists) complements in-transaction controls (PO approval state, expense approval).

## Community fallback
No generic approvals app in Community 19.0. Options there: native per-app approval states (purchase two-step, expense flows), automation-rule notifications (advisory), or custom — be explicit about the difference between advisory nudges and blocking approvals.

## Configuration opportunities
Categories (fields, documents, approver sets, minimums), tile visibility, templates for common request types (travel, spend, contract, IT access).

## Studio / automation opportunities
Automation: escalate stale requests, route by amount to different categories, post-approval actions (notify, create records). Studio: extra request fields per category (cost center, risk class) — keep the matrix in category config.

## Custom development triggers
Conditional matrices beyond category expressiveness (amount×entity×category tiers with delegation calendars) — verify what category design + several categories can express first; integration-triggered approvals at scale.

## External integration triggers
Corporate workflow platforms (ServiceNow-style) where group IT mandates them; delegation-of-authority systems with legal registries.

## Common client questions
"Amount-based routing?" — via category design (e.g., tiered categories) and/or automation; validate the exact matrix live before promising. · "Delegation/out-of-office?" — validate current behavior live; design fallback approvers. · "Audit trail?" — per-approver statuses + chatter. · "Approve by email/mobile?" — activities support quick actions; validate UX live.

## Fit-gap considerations
Covers the majority of "we need approvals" asks with configuration. Gap zone: DoA-grade conditional matrices, delegation calendars, cross-system approvals. Its very existence is a fit-gap argument: challenge every custom approval request against it (and it's a reason for Enterprise).

## Deloitte demo angles
1. **Tile-to-approved:** spend request → two approvers → approved → (bridge) RFQ created.
2. **Governance story:** categories as policy objects — change policy by changing config, not code.

## Implementation watch-outs
- Map the real approval matrix first; choose category granularity deliberately (too many tiles = confusion).
- Define fallback/delegation process explicitly.
- Don't duplicate native app approvals (expenses, time off have their own flows).

## Risks and assumptions
Structures verified; approver-resolution nuances (manager chains, minimums interplay) and delegation behavior are runtime → validate. Enterprise licensing required.

## Validation checklist
- [ ] Approval matrix inventory mapped to categories (with evidence test)
- [ ] Delegation/absence handling designed
- [ ] Bridges needed (purchase) configured and demoed
- [ ] Overlap with native app approvals resolved (who owns what)
