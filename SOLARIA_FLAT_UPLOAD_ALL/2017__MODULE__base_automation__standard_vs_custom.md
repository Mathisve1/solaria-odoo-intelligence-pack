# Automation Rules (`base_automation`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: **Community** — rung 4 of the ladder is available to every client. Correct anyone who claims automation needs Studio or Enterprise.

## Likely standard (Community)
Trigger→condition→action rules on any model · record-event and time-based triggers (cron-driven, source-verified) · action vocabulary: emails, activities, field updates, record creation, SMS · webhook-style patterns (validate exact scope live).

## Configuration possibilities
The rules are the configuration. Design disciplines: naming conventions, per-rule owner, activation windows, documented intent.

## Studio possibilities (E)
Studio pairs with rules (new field + rule on it) — but neither replaces the other: Studio = shape, rules = behavior.

## Automation possibilities
This IS the automation layer. Enterprise `ai_server_actions` adds AI steps — label the edition when proposing.

## Custom development is justified when
- Logic needs correlation across records/events, transactions across systems, or guarantees a fired-action model can't give.
- A rule would wrap substantial code (code-type server action) — then it's rung 5 wearing a costume: apply full SDLC governance or build it properly.

## External integration is justified when
- Sustained system-to-system flows (contracts, idempotency, monitoring) — rules may *signal*, iPaaS/APIs *integrate*.

## What to avoid
- Hard-blocking business validations via rules (fragile, surprising) — native constraints/approval features first.
- Rule chains emulating workflows (unmaintainable) — if it looks like a state machine, design it as one (stages/native flows).
- Ungoverned rule creation rights.
- Re-implementing shipped behaviors (SLA engines, assignment methods, reminders that exist natively in apps) as rules.

## Deloitte recommendation principles
Every FIT-AUTO verdict names the trigger, condition, action and owner. Rules enter the same customization registry as Studio artifacts and custom modules — one inventory for everything non-vanilla.

## Validation questions
1. Advisory or blocking — per requested behavior?
2. Does a native app feature already do this (checked in the module pack)?
3. Who owns and monitors each rule after go-live?
