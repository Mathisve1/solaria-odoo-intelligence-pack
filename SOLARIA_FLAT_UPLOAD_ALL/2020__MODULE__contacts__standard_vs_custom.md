# Contacts (`contacts`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Community (app UI over the base partner model).

## Likely standard
One partner for customer/vendor/portal roles · company-person hierarchy · multiple typed addresses · tags/industries · bank accounts · merge/dedup tooling · localization fiscal fields.

## Configuration possibilities
Taxonomies, address conventions, creation rights, localization fields, portal invitation policy.

## Studio possibilities (E)
Segmentation fields (governed); never a parallel customer object.

## Automation possibilities
Quality nudges, steward assignment, enrichment triggers, anonymization schedules (GDPR).

## Custom development is justified when
- KYC/sanction screening or MDM adapters are required (regulated/group contexts).

## External integration is justified when
- Corporate MDM owns the golden record (declare direction of truth per field) · enrichment/KYC providers.

## What to avoid
- Custom "customer" models — the platform's unity is the value.
- Open creation rights without stewardship.
- Physical deletion habits (archive/anonymize instead).

## Deloitte recommendation principles
Partner data = governance program: steward, quality KPIs, merge cadence, GDPR procedures. Migration gate: no uncleansed partner imports.

## Validation questions
1. Current duplicate rate (measured) and cleansing owner?
2. Group/billing hierarchies to model — tested against a live scenario?
3. MDM landscape: who is master for which fields?
