# Security & Access Summary — `account_accountant` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `account_accountant` — Invoicing |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- 'Invoicing & Banks' vs full accountant rights split day-to-day clerks from closers; lock-date exception rights deserve explicit assignment.
- Fiscal-year flexibility group ('more or less than a year') is a controlled setting — involve auditors before enabling.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| Invoicing & Banks | account.group_account_basic | group_account_readonly |
| Allow to define fiscal years of more or less than a year | group_fiscal_year | — |

## Existing groups this module modifies

These records extend groups owned by other modules (typically adding implied rights) — they do not create new roles:

| Existing group (reference) | Rights/groups implied by this module |
|---|---|
| account.group_account_manager | group_account_basic |

## Access rights (ir.model.access) — 7 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_account_user | — | `account.account_secure_entries_wizard`, `account_auto_reconcile_wizard`, `account_reconcile_wizard` | — |
| group_account_manager | `account_fiscal_year` | `account_change_lock_date` | — |
| group_account_readonly | — | — | `account_fiscal_year` |
| group_account_basic | — | — | `account_fiscal_year` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
