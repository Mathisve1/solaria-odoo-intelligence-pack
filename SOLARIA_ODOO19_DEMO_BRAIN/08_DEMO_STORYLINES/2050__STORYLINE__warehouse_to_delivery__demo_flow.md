# Demo Storyline: Warehouse-to-Delivery

| Attribute | Value |
|---|---|
| Category | STORYLINE (instantiates the 12-beat framework, foundation 0009) |
| Rules | Timing limits per format apply (0014); every beat needs data (0016) and rehearsal (0017); editions and claim labels always (0011, 0018) |

## Client problem
Picking errors, paper everywhere, carrier chaos at the packing bench.

## Audience
Warehouse manager, COO; 45 minutes

## Prerequisites
- stock rehearsed with client-like locations
- barcodes printed
- scanner device (E, labelled)
- carrier setup or labelled simulation

## Modules (edition)
- stock (C)
- stock_barcode (E)
- carrier connectors (E), labelled or simulated with the label said

## Start state
Morning queue: two receipts, three deliveries

## End state
Shipped with labels; stock truth intact; one cycle count done

## Step-by-step demo flow
1. Receive with scan, putaway suggested
2. wrong-item scan objection beat
3. pick the spine order by scan
4. pack and carrier label (labelled if simulated)
5. sixty-second cycle count
6. the manager view: accuracy and throughput

## Wow moments
- The wrong-item beep
- putaway suggestion
- the sixty-second count

## Challenger insight
Accuracy is made at the scanning moment, not at the annual count: catch the error at the shelf and the year-end weekend disappears.

## Likely questions
- Devices and wifi?
- our location scheme?
- returns flow?

## Risks
Scanner connectivity in the demo room (test on site or mirror a phone)

## Validation points
- Barcode coverage of the product master
- device pilot
- route design frozen

## Short version (15 min)
Scan-receive and scan-pick only

## Executive version (30 min)
Error-cost framing, one pick run, accuracy economics close
