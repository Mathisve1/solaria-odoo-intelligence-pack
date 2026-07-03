# Automation Rules (`base_automation`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `base_automation` |
| Display name | Automation Rules |
| Source origin | **Community** — automation does NOT require Enterprise/Studio (a frequent misconception worth correcting in every relevant answer) |
| Version scope | Odoo 19.0 |
| Dependencies (manifest, direct) | `base`, `digest`, `resource`, `mail`, `sms` |
| Functional domain | Automation (platform) |
| Confidence | High for the engine's existence and cron; exact trigger-type list and UI must be validated live in 19.0 |

## Business purpose
The platform's rule engine: **when X happens on any record, check condition Y, do Z** — without code. It is rung 4 of the Deloitte ladder and the standard answer to escalations, notifications, auto-assignment, data-quality nudges and lightweight process glue, on Community and Enterprise alike.

## Main users / personas
Functional consultants (process glue during implementation), admins (governed rule management), process owners (requesting behaviors), Enterprise AI users (`ai_server_actions` extends this pattern with AI steps).

## Business problems solved
- "The system should warn/remind/assign automatically" → rules firing server actions (emails, activities, field updates, record creation).
- Time-based discipline → the shipped cron **"Automation Rules: check and execute"** (source-verified) drives time-triggered rules (e.g., N days after a date).
- Small workflow gaps that would otherwise become custom modules → configured triggers instead of code.

## Main capabilities (source-verified structures)
- One core model: `base.automation` (3 models total incl. plumbing; 1 access rule — admin-managed by design).
- Trigger families: record events (create/update/delete), time-based via the cron, and webhook/external patterns (validate the exact 19.0 trigger list live — it evolves per release).
- Actions delegate to the server-action vocabulary (mail templates, activities, field writes, Python-free options first; code-type server actions exist but move the item toward rung 5 governance).
- SMS/mail integration through direct dependencies.

## Fit with other modules
Universal — rules attach to any model. `web_studio` depends on it (Studio fields + automation rules = the classic no-code pair). Enterprise `ai_server_actions`/`ai_fields` extend the same pattern with AI steps. Every module pack's "Automation possibilities" section in this knowledge pack resolves to this engine.

## Standard vs edition
Community. This is strategically important: **deterministic automation is available to every Odoo client**; only AI-flavored automation and Studio-built shape are Enterprise. Never gate an automation recommendation on Enterprise by mistake.

## Configuration opportunities
The rules themselves ARE configuration: trigger, filter/condition, action chain, timing. Plus digest/notification channels.

## Studio / custom boundaries
- A rule with a simple action chain = rung 4, fine.
- A rule wrapping a code-type server action with business logic = rung 5 in disguise — apply custom-development governance (review, tests, registry).
- Blocking validations via rules (hard stops) are fragile — prefer native constraints/approval features; rules are best advisory/reactive.

## Custom development triggers
Complex event processing (multi-record correlation, external event streams), transactional guarantees across systems, performance-sensitive hooks — real modules, not rule chains.

## External integration triggers
Webhook-style triggers can notify external systems; sustained integrations belong to API/iPaaS patterns with contracts, not rule sprawl.

## Common client questions
"Do we need Studio for automation?" — **No: automation rules are Community.** Studio adds shape; rules add behavior. · "Can it block a save?" — validate the specific case live; prefer native constraints for hard gates and say why. · "Who maintains rules?" — a named owner + registry; rules are process changes with an off switch. · "Can AI be a step?" — Enterprise `ai_server_actions`; label the edition.

## Fit-gap considerations
In fit-gap registers, FIT-AUTO verdicts cite this engine. Its existence kills a large class of "small custom module" proposals — challenge accordingly. Its limits (correlation, hard guarantees) mark where GAP-CUSTOM verdicts genuinely begin.

## Deloitte demo angles
1. **Two-minute rule:** build "opportunity idle 5 days → activity for manager" live — the audience realizes process glue is configuration.
2. **Governance beat:** show the rules list as a registry — "every behavior is visible, owned, and switchable."

## Implementation watch-outs
- Rule sprawl = invisible process drift: registry + owner + review cadence (same governance as Studio artifacts).
- Failing rules can fail silently — include rule monitoring in the run book.
- Beware rule-on-rule cascades (loops, side effects) — design review for chains.

## Risks and assumptions
Engine + cron verified in source. Exact trigger list, UI and webhook specifics per 19.0 build → validate live. Everything here is Community; no licensing caveat beyond hosting policy.

## Validation checklist
- [ ] Candidate rule list from fit-gap classified (advisory vs blocking vs code-type)
- [ ] Rule governance (owner, registry, monitoring) agreed
- [ ] Trigger types needed vs live 19.0 trigger list verified
