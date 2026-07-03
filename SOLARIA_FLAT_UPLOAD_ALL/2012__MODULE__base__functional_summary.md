# Base (`base`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `base` |
| Display name | Base |
| Source origin | **Community** (ships inside the server at `odoo/addons/base` — the framework layer) |
| Version scope | Odoo 19.0 |
| Dependencies | none (root of the dependency graph) |
| Functional domain | Technical / Framework |
| Confidence | High (source-verified); this is architect/admin context, not client demo material |

## Business purpose
The platform kernel every module stands on: companies, users and access artifacts, partners (`res.partner` foundation), countries/currencies/languages, and the `ir.*` machinery (models, views, actions, menus, crons, sequences, module lifecycle). When architects ask "how does Odoo actually work", the answer is here.

## Main users / personas
System administrators, solution architects, integration developers; indirectly everyone.

## What it provides (source-verified: 126 defined models, 66 menus, 146 access rules)
- **Identity & org:** `res.company` (multi-company core), `res.users`, groups/rights plumbing, API-key patterns.
- **Master data primitives:** `res.partner`, `res.country(.state)`, `res.currency(.rate)`, `res.lang`, `res.bank`.
- **Application machinery (`ir.*`):** models/fields registry, views, actions, menus, `ir.cron` (2 shipped base crons), `ir.sequence` (numbering), `ir.rule` (record rules engine), `ir.attachment`, `ir.config_parameter`, module install/upgrade lifecycle (`ir.module.module`), server actions engine.
- **Import/export & automation plumbing** used by every app.

## Consulting relevance (why non-developers should care)
- **Multi-company design** lives here: company hierarchy, inter-company visibility via record rules — a project-level architecture decision, not an app setting.
- **Numbering** (`ir.sequence`) is configuration — invoice/PO numbering requirements rarely need code.
- **Scheduled actions** registry = where all background behavior is visible/governable.
- **Users vs employees vs partners**: every user has a partner; employees link to users — identity design across apps starts here.
- **Technical menu** (Settings → Technical) is the admin X-ray of any Odoo instance.

## Standard vs Enterprise
`base` is identical foundation for both; Enterprise adds UI shell (`web_enterprise`) and tooling on top. No Enterprise variant of base exists.

## Configuration opportunities
Companies, users/groups assignment, sequences, languages/currencies (+rate update patterns), system parameters, mail servers (with mail), scheduled action tuning.

## Studio / automation / custom triggers
Automation rules and server actions operate on the machinery defined here. Custom modules = new `ir.*` records by definition — governance means tracking them (module registry, upgrade plan).

## Integration triggers
External APIs authenticate as users (dedicated integration users + API keys, least-privilege groups), master data sync (partners/products) — design system-of-record per object.

## Common questions
"Multi-company: one DB or many?" — architecture workshop; base gives the mechanics (companies + record rules), the answer is per client. · "Can we rename/renumber documents?" — sequences: yes, configuration. · "Who can do what?" — groups + access rights + record rules: design artifacts, demo in Settings.

## Watch-outs
- Admin rights sprawl (Settings user = can do anything) — cap to 2–3 named people.
- `ir.config_parameter` changes are system-wide — change-controlled.
- Timezones/languages set early (retroactive fixes are painful).
- Integration users with admin rights = audit finding; always least-privilege.

## Risks and assumptions
Structures verified. This document intentionally avoids developer detail; use it to reason about architecture, identity and governance questions.

## Validation checklist
- [ ] Multi-company architecture decided (companies, sharing rules)
- [ ] Identity design (users/employees/partners/integration users)
- [ ] Sequence/numbering scheme approved by finance/legal
- [ ] Admin governance (who, how many, change control)
