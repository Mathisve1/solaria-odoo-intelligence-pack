# Demo Storyline: Order-to-Cash (B2B trade)

| Attribute | Value |
|---|---|
| Category | STORYLINE (instantiates the 12-beat framework, foundation 0009) |
| Rules | Timing limits per format apply (0014); every beat needs data (0016) and rehearsal (0017); editions and claim labels always (0011, 0018) |

## Client problem
B2B orders arrive by email and phone, prices are tribal knowledge, delivery promises are guesses.

## Audience
COO, sales director, warehouse manager; 45 to 60 minutes

## Prerequisites
- sale + stock + account rehearsed
- customer pricelists
- availability data staged

## Modules (edition)
- sale (C)
- stock (C)
- account (C)
- barcode pick labelled (E) if shown

## Start state
B2B portal order lands at customer-specific prices

## End state
Delivered, invoiced, paid; margin per order visible

## Step-by-step demo flow
1. Portal order at their price appears as a real order
2. availability answers the promise-date question
3. warehouse picks (scanner beat if E, labelled)
4. engineered stockout on line two surfaces and resolves
5. delivery, invoice per policy
6. margin per customer pivot

## Wow moments
- Customer-specific price after login
- the stockout caught early
- order-to-invoice with zero re-typing

## Challenger insight
Delivery reliability is bought at order intake: a promise made against live availability is the cheapest service-level upgrade there is.

## Likely questions
- EDI-like intake?
- backorders policy?
- customer portals for order history?

## Risks
Availability data unstaged makes the promise beat fall flat

## Validation points
- Pricing agreements in pricelists
- route design
- portal scope for B2B customers

## Short version (15 min)
Portal order to pick to invoice

## Executive version (30 min)
OTIF framing, one continuous run, margin-per-customer close
