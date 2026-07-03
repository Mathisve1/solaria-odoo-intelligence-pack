# Studio (`web_studio`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only. This module IS rung 3 of the ladder — this document is about using the rung correctly.

## Likely standard (Enterprise)
Graphical field/view/menu/app creation · report layout editing (scope: validate live) · **approval rules on actions with entries log and delegation** · Studio export of customizations as a module · access to Enterprise view types for customized apps · AI-computed field creation via `web_studio_ai_fields` sibling.

## Configuration possibilities (before Studio)
Always check shipped settings first — a Studio artifact for something a setting does is governance debt. The configuration-vs-Studio boundary: settings change behavior of existing shape; Studio adds shape.

## Studio possibilities (the sanctioned scope)
Additive fields (classification, references), view tailoring per role, simple new models for peripheral registers (visitor log class of problems), action-level approval rules, report cosmetics.

## Automation possibilities
Pair Studio fields with `base_automation` rules (Studio depends on it) — shape + trigger without code. Registry both.

## Custom development is justified when
- Logic: computations beyond trivial, validations with business rules, performance-sensitive paths, anything requiring tests/review — rung 5.
- Core-flow modifications (never Studio-hack posting/reservation/pricing behavior).

## External integration is justified when
Not applicable at this layer (Studio artifacts deploy like modules; integration questions live elsewhere).

## What to avoid
- Studio on production directly — staging + export promotion only.
- Algorithms in Studio (automated fields with business math, chained server-action logic dressed as no-code).
- Unregistered artifacts — every Studio change enters the customization registry with an owner.
- Selling Studio to Community clients (edition gate) or as "free changes" (governance cost is real).

## Deloitte recommendation principles
Position Studio as *governed autonomy*: the client gets speed, Deloitte installs the guardrails (policy, registry, staging, upgrade rehearsal). Re-examine legacy "needs custom" verdicts against 19.0 Studio approval rules — several classic gaps closed.

## Validation questions
1. Which pending change requests are shape (Studio) vs brains (custom) — classified list?
2. Who are the named Studio users and who owns the registry?
3. Which approval gates are action-level (Studio rules) vs request-level (Approvals app)?
