# Discuss / Mail (`mail`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: fully Community; WhatsApp/VoIP/AI channels are Enterprise add-ons on this backbone.

## Likely standard (Community)
Chatter (messages/followers/email) on every mixin-equipped record · activities + multi-step activity plans · email gateway with per-object aliases · template engine · Discuss channels/DMs incl. portal guests · blacklist/consent primitives · notification digests · queue crons.

## Configuration possibilities
Aliases, templates, activity types/plans, subtypes/notification defaults, digests, mail servers, blacklists.

## Studio possibilities
Rarely relevant — communication shape is configuration.

## Automation possibilities
Automation rules using templates/activities are the standard automation vocabulary; scheduled digests; escalation chains.

## Custom development is justified when
- New communication channels (regional messaging platforms) as channel adapters.
- Compliance journaling/archiving pipelines.

## External integration is justified when
- Corporate mail infrastructure (relays, archiving), Teams/Slack coexistence (define which conversations belong to records — that's the governance line), telephony.

## What to avoid
- Custom notification frameworks next to subtypes/followers.
- Leaving default templates unbranded.
- Email-parsing customizations before testing native aliases.

## Deloitte recommendation principles
Treat mail as infrastructure workstream (deliverability, aliases, templates, notification policy) on every project — invisible when right, project-killing when wrong.

## Validation questions
1. Sending domains and who controls DNS?
2. Which processes need inbound addresses?
3. Record-conversations vs chat-tool culture — where's the boundary?
