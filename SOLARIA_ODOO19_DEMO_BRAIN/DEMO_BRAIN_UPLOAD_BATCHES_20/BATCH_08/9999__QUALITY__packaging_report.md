# Flat Upload Packaging Report (Demo Brain v1.0)

Category: QUALITY (meta artifact; not product evidence, not answer content).

| Metric | Value |
|---|---|
| Flat files (incl. this report) | 146 |
| Foundation files (Batch 1, constitutional) | 20 |
| Upload batches (max 20 files each) | 8 |
| Subfolders in flat folder | 0 (verified) |
| Unsupported extensions | 0 (verified; .md/.txt/.json only in this release) |
| Duplicate filenames | 0 (verified) |
| Em dashes in corpus | 0 (verified) |

## Category counts
| Category | Files |
|---|---|
| CHALLENGER | 13 |
| CLIENT_INTAKE | 11 |
| DEMO_METHOD | 6 |
| FOUNDATION | 20 |
| INDUSTRY | 12 |
| MODULE_DEMO | 24 |
| OBJECTION_LIBRARY | 2 |
| OPERATOR_GUIDE | 1 |
| OUTPUT_TEMPLATE | 13 |
| PERSONA | 16 |
| POC_VALIDATION | 6 |
| QUALITY | 4 |
| STORYLINE | 15 |
| TESTING | 2 |
| QUALITY (this report) | +1 |

## Batches
| Batch | Files | Content |
|---|---|---|
| BATCH_01 | 20 | EXACTLY the 20 foundation files 0000-0019 (upload first, alone, then gate on tests 8000/8010) |
| BATCH_02 | 20 | next numeric range of supporting files |
| BATCH_03 | 20 | next numeric range of supporting files |
| BATCH_04 | 20 | next numeric range of supporting files |
| BATCH_05 | 20 | next numeric range of supporting files |
| BATCH_06 | 20 | next numeric range of supporting files |
| BATCH_07 | 20 | next numeric range of supporting files |
| BATCH_08 | 5 | next numeric range of supporting files |

## Exact first action in Solaria
1. Paste the contents of `0001__FOUNDATION__global_context_paste_me.txt` into 'How you plan to use this context'.
2. Upload only BATCH_01 (the 20 foundation files), in filename order, each with a one-line description from the `purpose` field in `0019__FOUNDATION__first_20_manifest.json`.
3. Run the acceptance suite (8000) and red-team suite (8010) in a fresh session. Gate: 12/14 acceptance, zero critical red-team fails.
4. Only then upload BATCH_02 onward, one batch at a time, spot-checking after each (operator guide 8500).

## Exact first test prompt after Batch 1
"We need to prepare an Odoo demo for a potential client. Before proposing any modules, storyline or demo flow, guide me through the required client intake process and explain which information is still needed."

Expected behaviour: intake-first response offering the mandatory form (full/quick/interactive), the completeness gate explained, no modules or storyline proposed yet.
