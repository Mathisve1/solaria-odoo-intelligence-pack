# Operator Guide: Uploading and Maintaining the Demo Brain

Category: OPERATOR_GUIDE.

## Why the first 20 files matter (read before touching anything)
Solaria weights the first 20 uploaded files as the foundational context; everything later is supporting detail. The 20 foundation files (0000 to 0019) are therefore uploaded FIRST, alone, as Batch 1, in numeric order. Later files must never be uploaded before them.

## Exact upload procedure
1. Paste the FULL contents of `0001__FOUNDATION__global_context_paste_me.txt` into Solaria's global context field ('How you plan to use this context'). Save.
2. Upload BATCH_01 (exactly the 20 foundation files, from `DEMO_BRAIN_UPLOAD_BATCHES_20/BATCH_01/`), in filename order. For each, paste a short description; use the file's `purpose` line from `0019__FOUNDATION__first_20_manifest.json`.
3. STOP. Run the acceptance suite (8000) and the red-team suite (8010) in a fresh session. Gates: 12/14 acceptance, zero critical red-team fails.
4. Only after the gates pass: upload later batches (BATCH_02 onward), one batch at a time, max 20 files each, re-running a 3-question spot check after each (tests 1, 7, 8 of the acceptance suite).
5. The product-knowledge pack (SOLARIA_FLAT_UPLOAD_ALL, the 300+ Odoo files) is a separate corpus: if it is loaded in the same Solaria space, upload the Demo Brain foundation FIRST, product files after, so the constitutional weighting favours behaviour.

## Which files are what
- 0000-0019: constitutional (Batch 1, never diluted).
- 0100-4499: supporting method, intake, challenger, personas, industries, module demo packs, storylines, POC, templates, objection library.
- 8000-8010: testing artifacts (upload optional; if uploaded, their descriptions must say 'testing artifact, not answer content').
- 8500: this guide (operator reference; upload optional).
- 9000+: quality/meta reports (not product evidence; upload optional, late).

## Diagnosing context overload
Symptoms: generic answers return; wrong files cited; storylines quoting test files or meta reports; intake-first behaviour weakening. Actions, in order: (1) verify the global context is still pasted; (2) verify all 20 foundation files are present with descriptions; (3) remove the least-used supporting batches and retest; (4) worst case: fresh space, Batch 1 only, rebuild upward.

## Updating without weakening the foundation
- Supporting files (0100+): replace freely; keep names stable; re-run the 3-question spot check after.
- Foundation files (0000-0019): replace ONE file at a time, keep the same filename and number, update `0019` manifest accordingly, then re-run the FULL acceptance + red-team suites. Never add a 21st foundation file; never renumber.
- Contradiction rule: if a new supporting file contradicts a foundation file, fix the supporting file (foundation wins by design).

## Versioning future releases
Tag releases as DEMO_BRAIN vX.Y in the packaging report (9999); keep a change log of replaced files; re-baseline the red-team transcripts after every foundation change; archive superseded files outside the upload folders (never leave two versions of one number in the flat folder).
