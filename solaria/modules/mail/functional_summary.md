# Discuss / Mail (`mail`) — Functional Summary — Odoo 19.0

| Attribute | Value |
|---|---|
| Technical name | `mail` |
| Display name | Discuss |
| Source origin | **Community** (Enterprise `mail_enterprise` adds mobile/UI polish) |
| Version scope | Odoo 19.0 |
| Dependencies | `base`, `base_setup`, `bus`, `web_tour` |
| Functional domain | Communication & activity backbone |
| Confidence | High (source-verified: 83 models incl. mixins used platform-wide) |

## Business purpose
The communication nervous system: chatter on every business record (messages, followers, email in/out), activities (structured to-dos with types and plans), Discuss chat/channels, and the template engine — the reason Odoo processes feel "alive" and auditable.

## Main users / personas
Everyone. Specifically: process owners (activity plans), admins (aliases, templates, gateways), integrators (email infrastructure).

## What it provides (source-verified)
- **Chatter pattern:** `mail.thread` mixin → any model gains messages/followers/email; `mail.activity.mixin` → scheduled activities. (These mixins are why "can we log/follow/remind on X?" is almost always "yes, standard".)
- **Activities:** `mail.activity(.type)`, **activity plans** (`mail.activity.plan(.template)`) — multi-step playbooks (onboarding, follow-up cadences) as configuration.
- **Email integration:** inbound gateway + aliases (`mail.alias` — email-to-record per object), outbound servers, `mail.template` engine, blacklist (`mail.blacklist`), 8 shipped crons (queue sending, notifications digest, etc.).
- **Discuss:** channels/DMs (`discuss.channel`), presence, guests (portal chat participants), integrations surface for livechat.
- **Followers & subtypes:** per-record subscription model — notification governance.

## Consulting relevance
- Email deliverability/domain setup is an infrastructure workstream on every project (SPF/DKIM, aliases).
- Activity plans are an underused configuration gem: standardized process cadences without code.
- Follower auto-subscribe rules determine who gets notified — privacy/noise design.
- The chatter IS the audit narrative in most disputes ("who said/changed what, when").

## Standard vs Enterprise
All core is Community. `mail_enterprise` = UX polish; WhatsApp (`whatsapp`, E) and VoIP (E) are separate channels built on this backbone; AI base module (`ai`, E) also depends on mail.

## Configuration opportunities
Aliases per object/team, templates (rebrand!), activity types/plans, notification preferences, digests, blacklists, gateways/servers.

## Studio / automation opportunities
Automation rules commonly send templates/schedule activities — the mail layer is their action vocabulary. Studio rarely needed here.

## Custom development / integration triggers
Custom channels (SMS providers beyond shipped, messaging platforms), CRM-grade email sync depth (check existing plugins/modules first), archiving/journaling requirements (compliance) → integration.

## Common questions
"Does Odoo send/receive email natively?" — yes; the project task is domain/deliverability setup. · "Can each team have its own address?" — aliases: yes. · "Internal chat replacing Teams/Slack?" — Discuss exists; coexistence boundary is a client-culture decision, don't force it. · "Notification overload?" — subtype/follower design + user training.

## Watch-outs
- Untouched default templates leak "Odoo" branding to customers — rebrand before UAT.
- Alias domain misconfiguration = silent lead/ticket loss — test inbound early.
- Follower auto-subscribe on sensitive models (HR!) — review before go-live.
- Mail queue monitoring belongs in ops runbooks (crons verified in source).

## Validation checklist
- [ ] Sending domain (SPF/DKIM/DMARC) configured and tested
- [ ] Inbound aliases per process tested end-to-end
- [ ] Templates rebranded and legally reviewed (footers/consent)
- [ ] Notification/follower policy for sensitive objects reviewed
