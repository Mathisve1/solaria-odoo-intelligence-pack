# Sign (`sign`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only. Community has only simple quote-acceptance signing in the sales portal — not a general e-sign product.

## Likely standard (Enterprise)
Reusable PDF templates with typed fields per role · send/track requests with per-signer states · portal signing without accounts · reminders & expiry · audit log + completed document storage · template access governance · HR/sales/documents bridges · SMS patterns.

## Configuration possibilities
Templates, roles, tags, reminder/expiry, terms, email branding, template access groups.

## Studio possibilities
Request metadata (contract class, counterparty type) for reporting/routing.

## Automation possibilities
Trigger requests from record events, unsigned-escalations, auto-filing signed PDFs, notify owners on completion.

## Custom development is justified when
- Mass-personalized document generation + signing pipelines (hundreds of variants).
- Countersigning matrices with conditional roles beyond template roles.
- Integrations to identity/QES providers where mandated.

## External integration is justified when
- QES/eIDAS trust services or notarization are legally required · CLM owns negotiation · certified archiving.

## What to avoid
- Blanket "legally binding" claims — signature levels are a legal analysis, per document class and jurisdiction.
- Unmanaged template sprawl (use the template-access group and an owner).
- Custom signing UIs — the portal flow is the product.

## Deloitte recommendation principles
Position Sign as the zero-integration e-sign inside existing flows; bring legal into the first workshop; keep regulated documents on a validated path (possibly external QES) while everyday signing moves to Odoo.

## Validation questions
1. Document classes and their legal signature requirements?
2. Volumes and personalization needs per class?
3. Where must signed originals live, and for how long?
