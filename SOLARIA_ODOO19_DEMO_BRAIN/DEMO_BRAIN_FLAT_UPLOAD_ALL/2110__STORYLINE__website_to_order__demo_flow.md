# Demo Storyline: Website-to-Order

| Attribute | Value |
|---|---|
| Category | STORYLINE (instantiates the 12-beat framework, foundation 0009) |
| Rules | Timing limits per format apply (0014); every beat needs data (0016) and rehearsal (0017); editions and claim labels always (0011, 0018) |

## Client problem
The webshop and the ERP are separate worlds; every order pays an integration tax.

## Audience
eCommerce manager, COO, CFO; 30 to 45 minutes

## Prerequisites
- website_sale staged with client-flavoured catalog
- payment sandbox
- B2B login if relevant

## Modules (edition)
- website_sale (C)
- stock + account behind it (C)
- carriers at checkout labelled (E) if shown

## Start state
Anonymous visitor on the shop

## End state
The web order picked in the warehouse and booked in finance, untouched by human re-typing

## Step-by-step demo flow
1. Shop as the customer
2. B2B login changes the prices (if relevant)
3. checkout with payment
4. THE FLIP: backoffice already has the delivery order and draft invoice
5. pick and ship
6. abandoned-cart recovery beat as the growth close

## Wow moments
- The flip (order already in the warehouse queue)
- login-price change
- recovered cart

## Challenger insight
Every connector between shop and ERP is a toll booth: zero-interface commerce changes the cost of every single order.

## Likely questions
- Performance and SEO? (hosting/architecture validation)
- our PSP?
- content management scale?

## Risks
Skipping the backoffice flip (it IS the argument)

## Validation points
- Checkout with real tax/delivery matrix
- PSP sandbox e2e
- catalog readiness

## Short version (15 min)
Order placed, the flip, done

## Executive version (30 min)
Integration-tax framing, one order run, cost-curve close
