# Workflow & Automation Summary — `mail` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `mail` — Discuss |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- Not a business flow itself: chatter+activities define the universal follow-up pattern (schedule activity -> done -> next) used by every app; mail gateway turns emails into records.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| fetchmail.server | state | draft → done |
| mail.activity | state | overdue → today → planned → done |
| mail.activity.mixin | activity_state | overdue → today → planned |
| mail.alias | alias_status | not_tested → valid → invalid |
| mail.mail | state | outgoing → sent → received → exception → cancel |
| mail.notification | notification_status | ready → process → pending → sent → bounce → exception → canceled |
| mail.presence | status | online → away → offline |
| res.users | manual_im_status | away → busy → offline |

## Scheduled automations (crons)

| Automation | Runs on | Interval |
|---|---|---|
| Mail: Email Queue Manager | mail.mail | 1 hours |
| Publisher: Update Notification | publisher.warranty.contract | 1 weeks |
| Notification: Delete Notifications older than 6 Months | mail.notification | 1 months |
| Mail: Fetchmail Service | fetchmail.server | 5 minutes |
| Mail: Post scheduled messages | mail.scheduled.message | 1 days |
| Notification: Notify scheduled messages | mail.message.schedule | 1 hours |
| Mail: send web push notification | mail.push | 1 days |
| Discuss: channel member unmute | discuss.channel.member | 1 days |

## Integration surface
- Direct dependencies: `base`, `base_setup`, `bus`, `web_tour`, `html_editor`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
