# Base (`base`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Framework layer — the question here is rarely "customize base?" (never modify it) but "which mechanism do we use?".

## Likely standard
Multi-company mechanics · users/groups/record rules · partners, countries, currencies, languages · sequences/numbering · scheduled actions · attachments · module lifecycle · import/export.

## Configuration possibilities
Companies, groups assignment, sequences, currencies/rates, languages, system parameters, cron schedules, mail servers.

## Studio possibilities (E)
Studio creates new models/fields ON this machinery — every Studio artifact is an `ir.*` record; inventory them per release.

## Automation possibilities
Server actions/automation rules on any model; scheduled actions for periodic logic — all governed via the Technical menu.

## Custom development is justified when
- New business objects/logic are needed (by definition custom modules) — with inheritance, never core edits.
- Integration adapters (REST endpoints, auth flows).

## External integration is justified when
- Identity (SSO/IdP), master-data hubs, ESB/iPaaS landscapes — base provides the API surface.

## What to avoid
- ANY modification of base/source code — the cardinal rule; inheritance only.
- Admin-rights sprawl; integration users with admin.
- Unmanaged `ir.config_parameter` tweaks.
- Sequence hacks in code when configuration does it.

## Deloitte recommendation principles
Treat base as the constitution: architecture decisions (multi-company, identity, numbering, background jobs) are made consciously, documented, and change-controlled. Every custom artifact is inventoried against upgrades.

## Validation questions
1. Multi-company now and in 3 years (acquisitions?) — one DB or several?
2. Who administers, with what change control?
3. Which integrations authenticate how, with which rights?
