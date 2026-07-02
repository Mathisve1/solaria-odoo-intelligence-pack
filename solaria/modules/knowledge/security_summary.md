# Security & Access Summary — `knowledge` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `knowledge` — Knowledge |
| Source origin | enterprise |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Article-level membership rules (internal permission + invited members) — knowledge sharing defaults deserve an explicit governance decision.

## Access rights (ir.model.access) — 29 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| (no group / global) | — | `knowledge.knowledge_article`, `knowledge.knowledge_article_favorite`, `knowledge.knowledge_article_member`, `knowledge.knowledge_article_stage`, `knowledge.knowledge_article_template_category`, `knowledge.knowledge_article_thread` +2 more | — |
| group_user | `knowledge.knowledge_article_favorite`, `knowledge.knowledge_article_stage`, `knowledge.knowledge_cover` | `knowledge.knowledge_article`, `knowledge.knowledge_article_thread`, `knowledge.knowledge_invite` | `knowledge.knowledge_article_member`, `knowledge.knowledge_article_template_category` |
| group_system | `knowledge.knowledge_article`, `knowledge.knowledge_article_favorite`, `knowledge.knowledge_article_member`, `knowledge.knowledge_article_stage`, `knowledge.knowledge_article_template_category`, `knowledge.knowledge_article_thread` +2 more | — | — |
| group_portal | `knowledge.knowledge_article_favorite`, `knowledge.knowledge_article_stage` | `knowledge.knowledge_article`, `knowledge.knowledge_article_thread` | `knowledge.knowledge_article_member` |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| Articles: System = CRUD on all articles | knowledge.article | `[(1, '=', 1)]` |
| Articles: users/portal: read based on access | knowledge.article | `[('user_has_access', '=', True)]` |
| Articles: users/portal: write based on flag | knowledge.article | `[('user_has_write_access', '=', True)]` |
| Article members: users/portal: read article members | knowledge.article.member | `[('article_id.user_has_access', '=', True)]` |
| Article members: System CRUD all | knowledge.article.member | `[(1,'=',1)]` |
| Article favorite: users/portal: own + readable articles | knowledge.article.favorite | `[('user_id', '=', user.id), ('article_id.user_has_access', '=', True)]` |
| Article favorite: System CRUD all | knowledge.article.favorite | `[(1, '=', 1)]` |
| Item Stages (Read): users/portal: readable articles | knowledge.article.stage | `[('parent_id.user_has_access', '=', True)]` |
| Item Stages (Create/Write/Unlink): users/portal: writable articles | knowledge.article.stage | `[('parent_id.user_has_write_access', '=', True)]` |
| Item Stages: System CRUD all | knowledge.article.stage | `[(1, '=', 1)]` |
| Invite: Users invite members | knowledge.invite | `[('article_id.user_has_write_access', '=', True)]` |
| Invite: System invite members | knowledge.invite | `[(1, '=', 1)]` |
| Articles Threads: portal/users: read based on article access | knowledge.article.thread | `[('article_id.user_has_access', '=', True)]` |
| Article Threads: portal/users: write and create based on article write access | knowledge.article.thread | `[('article_id.user_has_write_access', '=', True)]` |

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
