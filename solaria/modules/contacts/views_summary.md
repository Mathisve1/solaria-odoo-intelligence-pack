# Views & Navigation Summary — `contacts` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `contacts` — Contacts |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Single partner form with company/person toggle and app-specific tabs appearing as apps are installed — a nice 'one master' demo moment.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Contacts | — | base.group_user,base.group_partner_manager |
| Contacts / Configuration | — | base.group_system |
| Contacts / Configuration / Bank Accounts | — | — |
| Contacts / Configuration / Bank Accounts / menu_action_res_bank_form | action_res_bank_form | — |
| Contacts / Configuration / Bank Accounts / menu_action_res_partner_bank_form | action_res_partner_bank_account_form | — |
| Contacts / Configuration / Contact Tags | action_partner_category_form | — |
| Contacts / Configuration / Industries | res_partner_industry_action | — |
| Contacts / Configuration / Localization | — | — |
| Contacts / Configuration / Localization / Country Group | action_country_group | — |
| Contacts / Configuration / Localization / menu_country_partner | action_country | — |
| Contacts / Configuration / Localization / menu_country_state_partner | action_country_state | — |
| Contacts / Contacts | action_contacts | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Contacts | res.partner | list,kanban,form,activity |

## View inventory

- Primary views defined: 0 (n/a)
- Inheriting views (UI extensions of other modules): 0

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
