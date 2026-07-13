# Persona Demo Pack: CTO

| Attribute | Value |
|---|---|
| Category | PERSONA (extends foundation file 0008) |
| Rule | Refine with intake section D; this pack gives defaults, the intake gives truth. Foundation rules override. |

## Priorities
- Extensibility without tech debt
- Engineering quality of the platform
- Clear boundary between product and custom

## Likely frustrations
- Black-box products that resist inspection
- Vendors who say everything is possible
- Custom code nobody owns

## Business KPIs
Deployment lead time, defect rates in custom code, platform upgrade effort, developer productivity

## Demo emphasis
- The ladder logic live: configuration, then Studio (Enterprise, governed), then where real code begins
- Open source as inspectability
- The customisation registry as an artifact

## Relevant Odoo modules
web_studio (Enterprise) with export governance, base_automation (Community), the standard-versus-custom framework applied to one of their real requirements

## Suitable Challenger insights
- The cheapest custom code is the code you never write; the second cheapest is code with a registry and an owner
- Product-aligned extensions survive upgrades; parallel systems do not

## Likely objections
- Python and the ORM at our scale? (honest scalability talk plus validation)
- Who maintains custom modules long term?

## Unsuitable demo content
- No-code evangelism without limits
- Pretending performance questions do not exist

## Opening questions
- What custom code in your current landscape would you rather not own?
- Where did your last platform fight you?

## Recommended closing
Bring one requirement you believe needs custom; in the workshop we walk the ladder on it together and see where it honestly lands.
