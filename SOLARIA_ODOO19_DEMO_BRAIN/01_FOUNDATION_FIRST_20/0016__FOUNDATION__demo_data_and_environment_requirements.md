# Demo Data and Environment Requirements

| Attribute | Value |
|---|---|
| Foundation file | 0016 of 20 |
| Principle | A demo is only as convincing as its data. Lorem-ipsum data kills client-specific storylines. The brain must specify exactly what data must exist before rehearsal. |

## 1. The data specification (produce per demo, per storyline beat)

**Master data**
- Products: 10 to 20 items in the client's vocabulary (their product families, units, price logic); include the 2 or 3 hero products the spine object will use.
- Customers: 8 to 12 partners with recognisable (but fictional or anonymised) names in the client's market; the spine customer fully fleshed (addresses, contact, payment terms).
- Suppliers: 5 to 8 vendors where purchase appears, with vendor pricelists for the hero products.
- Users and roles: one named user per persona shown (salesperson, warehouse operator, accountant, manager); correct rights per role; NEVER demo everything as admin.
- Warehouses/locations: the client's real topology simplified (their site names).
- Accounting setup: the right chart/localisation for the client's country, realistic taxes, opening balances where reports appear.

**Transactional data**
- History: enough closed records that lists, pivots and dashboards look alive (30 to 100 orders/invoices/tickets as relevant), dated sensibly across recent months.
- In-flight records: the spine object staged at its starting state, plus the exception records (the stockout, the credit-blocked order, the failed check) pre-built.
- Demo records naming convention: recognisable and rehearsed (order for "the client's own industry peer" style names), no test/asdf/demo123 artifacts on screen.

**Outputs**
- Reports and dashboards populated by the history (empty dashboards are anti-demos).
- Documents branded neutrally or client-flavoured (logo swap where appropriate and permitted).

**Integrations and AI**
- Integration moments: decide simulated versus live per moment; simulated parts are labelled in the room (file 0010 rule).
- AI/OCR moments: real sample documents prepared and tested; AI outputs pre-validated the same day (never first-run live).

## 2. Environment requirements
- Edition matches the conversation (file 0011) and is verified during rehearsal.
- Version: Odoo 19.0; note the build/date in the runbook.
- Apps installed: exactly the storyline scope plus dependencies; a kitchen-sink database with 40 apps confuses navigation and undermines the "focused fit" message.
- Language(s) and localisation match intake C/F.
- Performance sanity: the demo path clicked through end-to-end on the demo network/hardware.

## 3. Reset and backup (non-negotiable pair)
- **Reset procedure:** a documented way to return the database to the start state (snapshot, duplicate database, or scripted reset owned by the environment owner) so rehearsals and repeated demos start clean.
- **Backup scenario:** per fragile beat: a second prepared record to switch to, and screenshots/recording of the happy path as last resort; the runbook names when to switch (one retry, then backup, no debugging in front of the client).

## 4. Ownership and deadlines
The demo-data checklist assigns every item an owner and a due date before rehearsal (workflow stage 11 gate). The brain outputs this as a table: beat, records needed, owner, due, status.
