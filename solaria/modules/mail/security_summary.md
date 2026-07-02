# Security & Access Summary — `mail` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `mail` — Discuss |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Security & Access Summary |
| Authority | High for shipped groups/rights/rules (Security / Access Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Deloitte advisory notes
- Followers model = per-record visibility amplifier: whoever follows gets notified — govern auto-subscribe templates for sensitive records.

## Security groups defined by this module

| Group | XML id | Implies |
|---|---|---|
| Canned Response Administrator | group_mail_canned_response_admin | — |
| Mail Template Editor | group_mail_template_editor | — |
| — | base.group_system | group_mail_template_editor, group_mail_canned_response_admin |
| Receive notifications in Odoo | group_mail_notification_type_inbox | — |

## Access rights (ir.model.access) — 69 rules

| Group | Full control (rwcd) | Partial (r/w/c mix) | Read-only |
|---|---|---|---|
| group_system | `discuss_channel`, `discuss_channel_rtc_session`, `discuss_voice_metadata`, `fetchmail_server`, `mail.mail_push`, `mail.mail_push_device` +20 more | — | — |
| group_user | `discuss_channel_member`, `discuss_gif_favorite`, `mail_activity`, `mail_canned_response`, `mail_message`, `mail_scheduled_message` +2 more | `discuss_channel`, `mail_activity_schedule`, `mail_activity_schedule_line`, `mail_compose_message`, `mail_followers_edit`, `mail_notification` +1 more | `base.ir_actions_report`, `discuss_call_history`, `mail_activity_plan`, `mail_activity_plan_template`, `mail_activity_type`, `mail_alias` +5 more |
| group_portal | `discuss_channel_member`, `mail_message` | — | `discuss_call_history`, `discuss_channel`, `mail_message_subtype`, `mail_notification` |
| group_public | `discuss_channel_member` | — | `discuss_call_history`, `discuss_channel`, `mail_message`, `mail_message_subtype` |
| group_erp_manager | `mail_alias_domain`, `mail_link_preview`, `mail_message_link_preview`, `res_role` | — | — |
| group_mail_template_editor | `mail_template`, `mail_template_reset` | — | — |

## Record rules (row-level visibility)

| Rule | On object | Visibility logic (domain hint) |
|---|---|---|
| discuss.channel: can access channels (as member or as group allowed) | discuss.channel | `[ "|", "&", ("channel_type", "!=", "channel"), "|", ("is_member", "=", True), ("parent_cha` |
| discuss.channel: admin full access | discuss.channel | `[(1, '=', 1)]` |
| discuss.channel.member: access their own entries | discuss.channel.member | `[ ('is_self', '=', True), "|", ("channel_id.channel_type", "!=", "channel"), "|", ("channe` |
| discuss.channel.member: read members of accessible channels | discuss.channel.member | `[ "|", "&", ("channel_id.channel_type", "!=", "channel"), "|", ("channel_id.is_member", "=` |
| discuss.channel.member: can join group restricted channels when group is matching | discuss.channel.member | `[ ('is_self', '=', True), ('channel_id.channel_type', '=', 'channel'), '|', ('channel_id.g` |
| discuss.channel.member: internal users can invite others in group restricted channels when group is matching | discuss.channel.member | `[ ('is_self', '=', False), ('channel_id.channel_type', '=', 'channel'), '|', ('channel_id.` |
| discuss.channel.member: internal users can invite others in channels they are member of | discuss.channel.member | `[ ('is_self', '=', False), ('channel_id.channel_type', 'not in', ('channel', 'chat')), ('c` |
| discuss.call.history: read call history of accessible channels | discuss.call.history | `[ "|", "&", ("channel_id.channel_type", "!=", "channel"), "|", ("channel_id.is_member", "=` |
| discuss.channel.member: admin can manipulate all entries | discuss.channel.member | `[(1, '=', 1)]` |
| Discuss.gif.favorite: User access | discuss.gif.favorite | `[('create_uid', '=', user.id)]` |
| Discuss.gif.favorite: admin full access | discuss.gif.favorite | `[(1, '=', 1)]` |
| mail.notifications: group_user: write its own entries | mail.notification | `[('res_partner_id', '=', user.partner_id.id)]` |
| mail.notifications: group_portal: own entries | mail.notification | `['|', ('res_partner_id', '=', user.partner_id.id), ('author_id', '=', user.partner_id.id)]` |
| mail.message.subtype: portal/public: read public subtypes | mail.message.subtype | `[('internal', '=', False)]` |
| mail.activity: user: write/unlink only (created or assigned) | mail.activity | `['|', ('user_id', '=', user.id), ('create_uid', '=', user.id)]` |
| Administrators can access all activity plans. | mail.activity.plan | `[(1, '=', 1)]` |
| Administrators can access all activity plan templates. | mail.activity.plan.template | `[(1, '=', 1)]` |
| Mail Compose Message Rule | mail.compose.message | `[('create_uid', '=', user.id)]` |
| Employees can only modify templates they have created or been assigned | mail.template | `['|', ('create_uid', '=', user.id), ('user_id', '=', user.id)]` |
| Mail Template Editors - Edit All Templates | mail.template | `[(1, '=', 1)]` |
| res.users.settings.volumes: access their own entries | res.users.settings.volumes | `[('user_setting_id.user_id', '=', user.id)]` |
| Administrators can access all User Settings volumes. | res.users.settings.volumes | `[(1, '=', 1)]` |
| Canned response: admin has all access on shared canned response | mail.canned.response | `[('is_shared', '=', True)]` |
| Canned response: User read: own or in groups | mail.canned.response | `['|', ('create_uid', '=', user.id), ('group_ids', 'in', user.all_group_ids.ids)]` |
| Canned response: User write/unlink: own only | mail.canned.response | `[('create_uid', '=', user.id)]` |

*…1 more rules omitted.*

## Implementation guidance
- These are **shipped defaults of Odoo 19.0**, not a client's target security model. Role design maps client functions onto these groups first; custom groups only for proven gaps.
- Validation questions for every project: Who may see all records vs own records? Which roles cross companies? Who owns configuration menus? What must auditors see read-only?
- Watch-outs: group proliferation, granting 'Settings/admin' too widely, forgetting portal/public exposure paths, and untested multi-company rules.
