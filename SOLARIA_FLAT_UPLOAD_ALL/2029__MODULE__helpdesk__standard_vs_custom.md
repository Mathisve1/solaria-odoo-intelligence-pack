# Helpdesk (`helpdesk`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only app. If the client is Community, the honest options are: upgrade edition, project-as-tickets compromise, or external tool — in that order of Deloitte preference when service is core.

## Likely standard (Enterprise)
Multi-team ticket pipelines · email/portal/livechat/form intake · SLA policies with per-ticket status · auto-assignment methods · ratings & satisfaction analytics · canned responses · ticket/SLA analysis · bridges: returns, credit notes, timesheets, field service escalation, knowledge.

## Configuration possibilities
Teams+channels+members, assignment method, stages+templates, SLA matrices, ratings, portal exposure, help-center components, tags/types.

## Studio possibilities
Classification fields (asset, severity, product line), team-specific views. SLA math stays in SLA policies; entitlements need real design.

## Automation possibilities
Escalation chains on SLA warnings, VIP routing, keyword auto-tagging, reopen-handling flows, CSAT follow-ups on bad ratings. AI (E): drafting/livechat with human oversight.

## Custom development is justified when
- Entitlement/contract-based support (support packs with hour decrements beyond timesheet bridge) — design carefully, check timesheet/subscription combinations first.
- Warranty adjudication logic tied to serial/asset data.
- ITSM extensions (CMDB-lite) if the client insists Odoo hosts them — challenge first.

## External integration is justified when
- CCaaS/telephony stacks, IoT/product telemetry ticket creation, corporate ITSM coexistence (clear boundary: customer service in Odoo, IT changes elsewhere).

## What to avoid
- Rebuilding SLA logic in automations next to the native engine.
- One mega-team with 40 stages — team topology is the design lever.
- Deflection promises without a knowledge-content owner.
- Presenting project-as-helpdesk to a service-core client as "the same thing".

## Deloitte recommendation principles
Lead with ERP-connected service (ticket→return→credit in minutes). Design teams/SLAs from measured baselines. Keep AI assistive with human send until quality is evidenced.

## Validation questions
1. Volumes per channel; current SLA baseline (measured, not aspired)?
2. Which resolutions require ERP actions (returns, credits, interventions) — the bridge inventory?
3. Entitlement models in contracts — expressible natively (live test) or design work?
