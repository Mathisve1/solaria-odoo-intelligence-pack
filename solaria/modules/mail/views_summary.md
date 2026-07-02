# Views & Navigation Summary — `mail` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `mail` — Discuss |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Views & Navigation Summary |
| Authority | High for menus/actions/views existence (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Consultant interpretation
- Discuss app UI plus the chatter widget embedded in every form view — demo it inside a business record, not standalone.

## Menu structure (as shipped)

| Menu path | Opens action | Restricted to groups |
|---|---|---|
| Activities | — | — |
| Activities / menu_mail_activities | mail_activity_action | — |
| Activities / menu_mail_activity_plan | mail_activity_plan_action | — |
| Activities / menu_mail_activity_type | mail_activity_type_action | — |
| Canned Responses | mail_canned_response_action | — |
| Channels | discuss_channel_action | — |
| Channels | discuss_channel_action_view | base.group_no_one |
| Channels/Members | discuss_channel_member_action | base.group_no_one |
| Configuration | — | — |
| Discuss | action_discuss | base.group_user |
| Discuss | action_discuss | — |
| Discuss | — | — |
| Discuss / Email Blacklist | mail_blacklist_action | — |
| Discuss / Followers | action_view_followers | base.group_no_one |
| Discuss / GIF favorite | discuss_gif_favorite_action | — |
| Discuss / Guests | mail_guest_action | — |
| Discuss / ICE Servers | action_ice_servers | — |
| Discuss / Link Previews | mail_link_preview_action | — |
| Discuss / Message Reactions | mail_message_reaction_action | — |
| Discuss / Messages | action_view_mail_message | — |
| Discuss / Notifications | mail_notification_action | base.group_no_one |
| Discuss / RTC sessions | discuss_channel_rtc_session_action | — |
| Discuss / Scheduled Messages | mail_message_schedule_action | — |
| Discuss / Subtypes | action_view_message_subtype | — |
| Discuss / Tracking Values | action_view_mail_tracking_value | — |
| Discuss / User Settings | res_users_settings_action | — |
| Emails | action_view_mail_mail | — |
| Incoming Mail Servers | action_email_server_tree | base.group_no_one |
| Notifications | discuss_notification_settings_action | — |
| Roles | res_role_action | — |
| Technical | — | base.group_no_one |
| Technical / Call History | discuss_call_history_action | — |
| Voice & Video | discuss_call_settings_action | — |
| mail_alias_domain_menu | mail_alias_domain_action | base.group_no_one |
| mail_alias_menu | mail_alias_action | base.group_no_one |
| mail_gateway_allowed_menu | mail_gateway_allowed_action | base.group_no_one |
| menu_email_templates | action_email_template_tree_all | — |

## Window actions (what users can open)

| Action | On business object | View modes |
|---|---|---|
| base.ir_cron_act | — | — |
| Channels/Members | discuss.channel.member | list,form |
| RTC sessions | discuss.channel.rtc.session | list,form |
| Join a group | discuss.channel | kanban,list,form |
| Channels | discuss.channel | kanban,form |
| Incoming Mail Servers | fetchmail.server | list,form |
| Activity Plans | mail.activity.plan | list,kanban,form |
| Activity Types | mail.activity.type | list,kanban,form |
| Activity Overview | mail.activity | list,form |
| Other activities | mail.activity | list,form |
| My Activities | mail.activity | list,kanban,calendar |
| Alias Domains | mail.alias.domain | list,form |
| Aliases | mail.alias | — |
| Blacklisted Email Addresses | mail.blacklist | — |
| Canned Responses | mail.canned.response | list,form,kanban |
| Followers | mail.followers | list,form |
| Mail Gateway Allowed | mail.gateway.allowed | list |
| Guests | mail.guest | list,form |
| ICE Servers | mail.ice.server | list,form,kanban |
| Link Previews | mail.link.preview | list,form |
| Emails | mail.mail | list,form |
| Messages | mail.mail | — |
| Message Reactions | mail.message.reaction | list,form |
| Scheduled Messages | mail.message.schedule | list,form |
| Subtypes | mail.message.subtype | list,form |
| Messages | mail.message | list,form |
| base.action_attachment | — | kanban,list,form |
| Notifications | mail.notification | list,form |
| Email Templates | mail.template | form,list |
| Tracking Values | mail.tracking.value | list,form |
| base.action_partner_form | — | list,kanban,form,activity |
| base.action_partner_customer_form | — | list,kanban,form,activity |
| base.action_partner_supplier_form | — | list,kanban,form,activity |
| Send email | mail.compose.message | form |
| Roles | res.role | list,form |
| User Settings | res.users.settings | list,form |
| Change My Preferences | res.users | form |
| Call History | discuss.call.history | list,form |
| GIF favorite | discuss.gif.favorite | list,form |
| Compose Email | mail.compose.message | form |
| Template Preview | mail.template.preview | form |
| Reset Mail Template | mail.template.reset | form |

## View inventory

- Primary views defined: 95 (form: 37, list: 31, search: 18, kanban: 7, calendar: 1, activity: 1)
- Inheriting views (UI extensions of other modules): 22
- Richest UI objects: `mail.activity` (calendar, form, kanban, list, search); `discuss.channel` (form, kanban, list, search); `mail.activity.plan` (form, kanban, list, search); `mail.activity.type` (form, kanban, list, search); `mail.canned.response` (form, kanban, list, search); `mail.ice.server` (form, kanban, list, search); `discuss.channel.rtc.session` (form, list, search); `fetchmail.server` (form, list, search); `mail.alias.domain` (form, list, search); `mail.alias` (form, list, search); `mail.blacklist` (form, list, search); `mail.mail` (form, list, search)

## UX/demo observations (generic)
- Menus above are the exact navigation surface for demo scripts.
- Kanban-first objects indicate process/stage thinking; list-first objects indicate registers.
- Search filters/group-bys ship with defaults; demo them instead of building reports.
