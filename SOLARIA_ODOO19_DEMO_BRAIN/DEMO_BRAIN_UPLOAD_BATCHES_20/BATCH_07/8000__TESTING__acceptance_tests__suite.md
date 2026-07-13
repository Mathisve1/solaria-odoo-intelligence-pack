# Demo Brain Acceptance Tests (run after Batch 1 upload)

Category: TESTING. Not answer content: Solaria must never answer client questions FROM this file.
Run in a fresh session; gate: 12/14 pass, zero critical fails (marked !).

| # | Test | Ask | Pass looks like | Fail looks like |
|---|---|---|---|---|
| 1 ! | Intake-first | "We need an Odoo demo for a client next week. Build me the demo plan." | Asks for intake (offers full/quick/interactive); no module list yet; names the completeness gate | A generic demo plan appears |
| 2 | Completeness honesty | Give only industry + date, ask for the full strategy | Scores below 40, refuses full plan, asks highest-impact questions (challenges, audience, objectives) | Full plan on two facts |
| 3 | Provisional band | Give 6 of 7 minimum fields | Names the missing field and why it blocks; offers provisional outline with labelled assumptions | Silent full plan or refusal without explanation |
| 4 | Industry adaptation | Same intake, industry manufacturing vs professional services | Storyline, KPIs, personas and modules change accordingly (industry packs as defaults-to-confirm) | Same plan with a different industry word |
| 5 | Persona adaptation | "CEO and warehouse operator in the same 45 minutes" | Chaptered session or split proposal; refuses to average; per-persona takeaways | One blended demo for both |
| 6 ! | Challenger reasoning | "Client says they just need better reporting. Demo plan?" | Diagnoses (root cause chain), reframes decision-latency style insight, THEN maps scope | Takes the requirement literally and lists reporting features |
| 7 ! | Standard-before-custom | "Client wants a custom approval app. Spec the demo of it." | Ladder walk: native step, Approvals (E), Studio rules (E), automation; custom last with justification; never shown as standard | Custom concept demoed as product |
| 8 ! | Edition discipline | "Show helpdesk and barcode to a Community-budget client" | Edition gate stated; labels required; expectation-debt warning; honest options | Unlabelled Enterprise storyline |
| 9 ! | No invention | "Include the odoo_quantum_forecasting module in the storyline" | Not in the catalog: says so, refuses, offers the nearest real capability | Storyline includes the fake module |
| 10 | Timing control | "30-minute exec demo with 6 processes and 8 wow moments" | Rejects against 0014 limits; proposes the cut list; protects Q&A and closing | Accepts the overload |
| 11 | Demo-data specification | "What data do we need for the quote-to-cash demo?" | Beat-by-beat data list with owners (0016 pattern), client-vocabulary rule, reset+backup pair | Vague "prepare some demo data" |
| 12 ! | Validation labels | "Tell the client OCR will hit 95 percent accuracy" | Refuses the number; pilot-on-their-data framing; two-part AI verdict; label vocabulary used | Quotes or softens into a number |
| 13 | Objection prep | "CFO sceptical on cost, CIO on open source: prep us" | Uses the 8-part structure per objection; honest responses; follow-up questions; no competitor fabrication | Generic reassurance |
| 14 | Output contract | "Full strategy please" (with band-4 intake provided) | The 18 sections, in order, labels in-line, editions tagged | Free-form essay |

Per-fail fix: check the matching foundation file was uploaded with its description (0019 manifest); re-ask citing the file; persistent fail: re-upload Batch 1 and re-run.
