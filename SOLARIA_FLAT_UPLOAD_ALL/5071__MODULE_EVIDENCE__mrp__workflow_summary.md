# Workflow & Automation Summary — `mrp` (Odoo 19.0)

| Attribute | Value |
|---|---|
| Module | `mrp` — Manufacturing |
| Source origin | community |
| Version scope | 19.0 |
| Document type | Workflow & Automation Summary |
| Authority | High for shipped states/crons/actions (Source-Code-Derived Evidence) |
| Confidence | High for existence of listed items; runtime behaviour needs live validation |


## Main business flow (consultant narrative)
- MO lifecycle: draft -> confirmed -> progress -> to_close/done, with component reservation like pickings.
- BoM changes do not alter running MOs — plan engineering-change conversations (PLM is Enterprise).
- Scrap/unbuild flows exist standard — quality gates come with Enterprise quality modules.

## Lifecycle / status fields (source-verified)

| Business object | Field | States / mechanism |
|---|---|---|
| mrp.production | state | draft → confirmed → progress → to_close → done → cancel |
| mrp.production | reservation_state | confirmed → assigned → waiting |
| mrp.production | components_availability_state | available → expected → late → unavailable |
| mrp.unbuild | state | draft → done |
| mrp.workcenter | working_state | normal → blocked → done |
| mrp.workorder | state | blocked → ready → progress → done → cancel |

## Server actions shipped (incl. contextual actions)

| Action | On object | Kind |
|---|---|---|
| Split | mrp.production | code |
| Labels | mrp.production | code |
| Lock/Unlock | mrp.production | code |
| Scrap | mrp.production | code |
| Print Labels | mrp.production | code |
| Plan based on Components Availability | mrp.production | code |
| Merge | mrp.production | code |
| Mark as Done | mrp.production | code |
| Unreserve | mrp.production | code |
| Start | mrp.workorder | code |
| Pause | mrp.workorder | code |

## Integration surface
- Direct dependencies: `product`, `stock`, `resource`
- Sequences configured: 0 — numbering is configuration, not code.

## Implementation implications (generic)
- Status flows above are the checkpoints for data migration (records must land in a valid state).
- Crons imply background behaviour after go-live — include in cutover runbooks and monitoring.
- Mail templates are white-label surfaces: rebrand before UAT.
