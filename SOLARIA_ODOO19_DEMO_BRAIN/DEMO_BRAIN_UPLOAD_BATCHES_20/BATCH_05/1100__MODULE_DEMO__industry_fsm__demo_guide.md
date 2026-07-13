# Module Demo Pack: Field Service (`industry_fsm`)

| Attribute | Value |
|---|---|
| Edition | Enterprise |
| Category | MODULE_DEMO (demo guidance only; product truth lives in the Intelligence Pack module docs, routed via foundation 0012) |
| Rule | Every claim keeps its edition tag and claim label (foundation 0018); nothing here is demo-ready until rehearsed (foundation 0017) |

## Demo purpose
The technician's whole day on a phone: dispatch, timer, worksheet, signature, invoice on the doorstep.

## Best personas
Service director, dispatchers, technicians, CFO (unbilled work)

## Prerequisites
- Enterprise database
- mobile device that mirrors to the screen
- worksheet template for the intervention type
- products for parts

## Minimum demo data
- Technician users
- staged ticket-to-task
- van stock for parts
- customer for the signature

## Recommended flow
- Ticket escalates to intervention
- map dispatch
- phone: start timer, worksheet, add parts, customer signs
- invoice created on site

## Wow moments
- The phone run end-to-end (rehearse ruthlessly; the best demo in the services portfolio)
- invoice before leaving the driveway
- dispatcher map

## Common mistakes
- Mouse-driven FSM demo (kills it)
- route optimization promises
- ignoring the device/connectivity question

## Standard vs custom notes
- Worksheets, billing types: configuration
- route optimization: integration
- warranty adjudication: design/custom, flagged

## Community vs Enterprise notes
Enterprise-only, and it sits on the Enterprise project/timesheet layer: the edition story is structural

## Likely objections
- Offline in the field (validate on devices, honest)
- our intervention types (worksheet designer shown, validated)

## Validation checklist
- Device pilot in real coverage
- worksheet per top intervention types
- parts logistics with warehouse

## Backup flow
Second staged task; recording of the phone flow as last resort
