# Views & Navigation Summary — `knowledge` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `knowledge` — Knowledge |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Article tree + editor is the whole UX; embedded item views (kanban/list inside articles) make it feel alive.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Knowledge | — | — |
| Knowledge | — | — |
| Knowledge / Articles | knowledge_article_action | — |
| Knowledge / Configuration | — | base.group_no_one |
| Knowledge / Configuration / Favorites | knowledge_article_favorite_action | base.group_system |
| Knowledge / Configuration / Members | knowledge_article_member_action | base.group_system |
| Knowledge / Configuration / Stages | knowledge_article_stage_action | — |
| Knowledge / Configuration / Trashed | knowledge_article_action_trashed | base.group_system |
| Knowledge / Home | ir_actions_server_knowledge_home_page | — |
| Knowledge / Template Categories | knowledge_article_template_category_action | base.group_system |
| Knowledge / Template Stages | knowledge_article_template_stage_action | base.group_system |
| Knowledge / Templates | knowledge_article_template_action | base.group_system |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| Favorites | knowledge.article.favorite | list,form |
| Members | knowledge.article.member | list,form |
| Stages | knowledge.article.stage | list,form |
| Template Stages | knowledge.article.stage | list,form |
| Template Categories | knowledge.article.template.category | list,form |
| Trash | knowledge.article | list,form,kanban |
| Articles | knowledge.article | list,kanban,hierarchy,form |
| Articles | knowledge.article | form |
| Articles | knowledge.article | form |
| Article Items | knowledge.article | list,kanban,form |
| Article Items | knowledge.article | calendar |
| Article Items | knowledge.article | kanban,list,form |
| Article Templates | knowledge.article | list,form |
| Invite people | knowledge.invite | form |

## View inventory

- Primary views defined: 26 (form: 8, list: 8, search: 6, kanban: 2, hierarchy: 1, calendar: 1)
- Inheriting views (UI extensions of other modules): 2
- Richest UI objects: `knowledge.article` (calendar, form, hierarchy, kanban, list, search); `knowledge.article.favorite` (form, list, search); `knowledge.article.member` (form, list, search); `knowledge.article.stage` (form, list, search); `knowledge.article.template.category` (form, list); `knowledge.invite` (form)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
