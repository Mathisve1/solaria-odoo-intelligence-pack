# Contacts (`contacts`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `contacts` |
| Display name | Contacts |
| Source origin | **Community** (thin app UI over `res.partner` from `base`) |
| Version scope | Odoo 19.0 |
| Dependencies | `base_setup`, `mail` |
| Functional domain | Partner master data |
| Confidence | High (source-verified; app = menus/views over the base partner model) |

## Business purpose
The single directory of everyone the company deals with: companies and persons, customers and vendors, addresses and roles — one `res.partner` record reused by sales, purchasing, accounting, projects, helpdesk and portal access. `contacts` itself is the app skin (12 menus, source-verified); the model lives in `base`.

## Main users / personas
Everyone touching counterparties; data stewards (dedup/merge); compliance (GDPR); finance (payment/fiscal data on partners).

## What it provides
- Company/person hierarchy (parent/child: HQ, branches, contacts of a company), address types (invoice/delivery patterns).
- One partner = customer AND vendor AND portal user as roles, not copies — the anti-silo argument in demos.
- Tags/industries, banks accounts on partners, multiple addresses, localization-driven fiscal fields (VAT etc. via l10n).
- Merge/dedup tooling (base partner merge; `data_cleaning`/`data_merge_*` E enhance it).

## Consulting relevance
- Customer/vendor dedup BEFORE migration — merging later is corrective surgery.
- Partner hierarchy design (group structures, invoice-to/ship-to) drives billing correctness.
- GDPR anchor object: retention, consent (with marketing), access design.
- Every portal user is a partner — external access design starts here.

## Standard vs Enterprise
Community fully. Enterprise adds data-cleaning/merge automation, enrichment contexts, WhatsApp/VoIP touchpoints.

## Configuration opportunities
Tags/industries taxonomy, address type usage, bank data policy, localization fields, duplicate-handling process.

## Studio / automation opportunities
Automation: completeness/quality nudges, ownership assignment. Studio (E): segmentation fields (governed). Avoid parallel "customer" objects — extend the partner.

## Custom / integration triggers
MDM platforms (partner as golden record or consumer — decide), enrichment providers, KYC/sanction screening services (regulated industries).

## Common questions
"One record for customer & supplier?" — yes, roles on one partner: the model's core idea. · "Branch/HQ invoicing?" — hierarchy + address types; validate the specific billing scenario live. · "Dedup?" — merge tooling + (E) data cleaning apps; process matters more than tool.

## Watch-outs
- Uncontrolled partner creation rights → duplicate factory; steward + merge cadence.
- Deletion is usually wrong (history!) — archive instead; GDPR via anonymization procedures.
- Address-type misuse breaks delivery/invoice routing — train order entry teams.

## Validation checklist
- [ ] Dedup/cleansing done before migration (measured duplicate rate)
- [ ] Hierarchy & address-type conventions documented
- [ ] GDPR retention/anonymization procedure defined
- [ ] Partner creation/edit rights matrix set
