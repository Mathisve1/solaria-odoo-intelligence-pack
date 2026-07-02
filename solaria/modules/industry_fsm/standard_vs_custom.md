# Field Service (`industry_fsm`) — Standard vs Configuration vs Studio vs Custom — Odoo 19.0

Edition: Enterprise-only (siblings: worksheets, sale, stock bridges).

## Likely standard (Enterprise)
Mobile field tasks with travel/work timers · dispatch queues, map & planning views · digital worksheets with customer signature · parts consumption / van-stock flows (sibling) · quotes & invoices from the task · helpdesk/sales intake · ratings · recurrence for periodic visits.

## Configuration possibilities
FSM projects (billing types, worksheets), worksheet templates, stages/tags, planning defaults, rating cadence.

## Studio possibilities
Intervention-type fields, safety checklist fields (paired with worksheet design). Not for dispatch logic.

## Automation possibilities
Dispatch SLA alerts, follow-up visit creation on outcomes, replenishment nudges, post-visit review requests.

## Custom development is justified when
- Entitlement/warranty adjudication tied to contracts/serials.
- Deep asset registries with hierarchy/history beyond available modeling (design first).
- Specialized compliance documents beyond worksheet scope.

## External integration is justified when
- Route optimization engines · IoT alarm-to-intervention feeds · subcontractor platforms.

## What to avoid
- Selling route optimization as native.
- Designing worksheets in a conference room (do it with technicians).
- Custom mobile apps replacing the native flow before piloting it.
- Ignoring device/connectivity reality in scoping.

## Deloitte recommendation principles
Pilot-first (real devices, real jobs), worksheet co-design with the field, one-platform arc as the value story. Optimization ambitions → integration architecture, honestly priced.

## Validation questions
1. Intervention types + volumes + current proof-of-service pains?
2. Device/connectivity landscape?
3. Parts logistics model (van stock? central issue?)
4. Which optimization level is truly needed — assignment help or algorithmic routing?
