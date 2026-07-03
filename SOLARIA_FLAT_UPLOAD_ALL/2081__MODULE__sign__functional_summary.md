# Sign (`sign`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `sign` |
| Display name | Sign |
| Source origin | **Enterprise** |
| Version scope | Odoo 19.0 |
| Dependencies | `mail`, `portal`, `sms`, `attachment_indexation`, `certificate` |
| Functional domain | e-Signature |
| Confidence | High for structures; legal validity levels are jurisdiction questions — always validate with legal |

## Business purpose
Electronic signing embedded in business flows: prepare reusable templates with drag-and-drop fields per signer role, send requests, track progress, and keep an audit log — so offers, contracts and HR documents get signed without leaving the platform (or adding a DocuSign subscription).

## Main users / personas
Sales (quotes/contracts), HR (contracts/policies — `hr_contract_salary` bridge), legal/admin (templates governance), signers (portal, no login needed), management (status tracking).

## Business problems solved
- External e-sign tool costs/integration → native `sign.template` + `sign.request` flows.
- Chasing signatures → states (**sent → signed / canceled / expired**, per-signer `sign.request.item` states), reminders/expiry crons.
- Evidence needs → `sign.log` audit trail, completed documents (`sign.completed.document`), certificate module dependency for signing infrastructure (source-verified).
- Role confusion → `sign.item.role` (customer, employee, company rep) mapped to template fields (`sign.item`, typed fields incl. radio sets/options).

## Main business processes (source-verified)
1. Template prep: upload PDF → place typed fields per role (text, signature, checkbox, radio, selection).
2. Request: choose signers per role → send (mail/SMS patterns) → portal signing without account.
3. Track: My/All Documents menus, per-signer status, reminders, expiry; shared/public sign links (`shared` state — validate scope).
4. Complete: signed PDF + log stored; bridges file it (documents) or advance flows (HR contract, rental).

## Key functional capabilities
Reusable templates with tags, roles, field types incl. radio sets; batch-ish sending via share; "green savings" report (paper-saved storytelling — demo garnish); template access rights ("Manage template access" group); `sign_ai` (E AI assist — validate what it does live before claiming).

## Fit with other modules
`hr_recruitment_sign`/`hr_contract_salary` (offers/contracts), `documents_sign` (filing), `sale_renting_sign`, website/portal, `certificate` infrastructure. Pattern: any record with a PDF artifact can grow a sign step.

## Community fallback
Quote acceptance by portal "sign" (simple acceptance signature on sale orders) exists in Community sales — but it is not a general e-signature product. Be precise about this distinction.

## Configuration opportunities
Templates+roles+tags, reminder/expiry settings, terms text, template access groups, branding of request emails.

## Studio / automation opportunities
Automation: auto-create sign requests on record events (contract stage reached), escalate unsigned after N days, file signed docs to workspaces. Studio: request metadata fields.

## Custom development triggers
Qualified signature (QES) flows with national identity providers (check availability/validate — often external providers), bulk-personalized generation+signing pipelines, complex countersigning matrices.

## External integration triggers
QES/eIDAS trust service providers where law requires, notarization services, CLM suites (if negotiation is core), archival services.

## Common client questions
"Legally valid?" — signature levels (SES/AES/QES) are jurisdiction- and use-case-dependent: Odoo covers standard electronic signing with audit trail; regulated cases need legal review — never answer with a blanket yes. · "Signers need accounts?" — no, portal links. · "Templates with auto-filled data?" — field mapping patterns; validate depth live. · "Replace DocuSign?" — for common business signing yes, for regulated QES flows validate.

## Fit-gap considerations
High-fit quick win for sales/HR flows already in Odoo (zero-integration argument). Gap zone: QES-regulated documents, high-volume personalized packs, negotiation workflows. Often the easiest Enterprise-value demo in a deal.

## Deloitte demo angles
1. **Two-minute close:** offer PDF → fields → send → sign on phone → status flips, signed doc archived.
2. **HR pack:** new-hire contract from salary configurator → sign → filed in employee documents.
3. Green-savings report as a light ESG note.

## Implementation watch-outs
- Legal review of signature-level needs per document class (one workshop, saves lawsuits).
- Template governance (who edits templates — group exists, use it).
- Retention/access of signed documents (with documents app design).
- Brand the signer experience; it's customer-facing.

## Risks and assumptions
Structures verified. Legal validity, identity-verification options, `sign_ai` scope are runtime/legal → validate. Enterprise licensing required.

## Validation checklist
- [ ] Document classes mapped to required signature levels with legal
- [ ] Template set built for top 5 documents with role design
- [ ] Signer UX tested externally (real phone, real email)
- [ ] Filing/retention path defined (documents bridge)
