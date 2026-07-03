# READ ME FIRST — Solaria Flat All-In Upload Package

## What this is
This folder (`SOLARIA_FLAT_UPLOAD_ALL/`) is a **flattened, all-in-one-folder** copy of the curated Deloitte Solaria Odoo Intelligence Pack. Every file lives directly in this folder with **no subfolders**, because Solaria cannot upload folder trees — only loose files.

Each filename encodes the original structure so nothing is lost:
```
[ORDER]__[CATEGORY]__[ENTITY]__[DOCUMENT_TYPE].[ext]
e.g. 2000__MODULE__sale__functional_summary.md
     5000__MODULE_EVIDENCE__account__models.json
     0600__DECISION_FRAMEWORK__standard_configuration_studio_custom_framework.md
```
Sort this folder by filename and you get the recommended upload order.

## Important context (read before uploading)
- **The authoritative source of truth remains the `solaria/` folder**, not this flat copy. This package is a derived artifact for uploading; edits belong upstream in `solaria/`.
- **You (the user) intentionally chose a FULL upload / stress-test.** This is *not* the safest strategy — the V3 pre-upload gate recommends a staged 29-document upload with acceptance gates (see `solaria/final_upload_package/`). Uploading all 304 files at once risks **retrieval dilution**: with hundreds of similar evidence files competing, Solaria may cite the wrong document or blur narrative vs evidence. Proceed knowingly, and lean on the testing plan.
- If you would rather do the safe staged path, stop here and follow `solaria/final_upload_package/README.md` instead.

## What is and isn't in here
- **In:** behaviour rules, global maps, module catalog, dependency map, Community-vs-Enterprise map, decision framework, AI opportunity map, priority list, every module README/functional_summary/standard_vs_custom, every module evidence file (models/views/security/workflow), the AI native pack, all playbooks, orientation docs, upload guides, testing artifacts, and META/QUALITY reports (clearly marked — **not** product evidence).
- **Out (never uploaded):** `.usage.md` companions (their content is consolidated into the manifest/descriptions here), `index.html` (navigation only, broken links when flat), `_sources/` and any raw Odoo source, zip archives, `.git`, `.claude`, local settings, secrets. See `0007__OPERATOR__do_not_upload_even_in_full_mode.md`.

## Do this, in order
1. **Paste the global context.** Open `0001__OPERATOR__global_context_paste_me.txt`, copy ALL of it into Solaria's global context / custom-instructions field. Save. This is the single most important step — it configures how Solaria reasons.
2. **Set descriptions as you upload.** For each file, paste its description from `0003__OPERATOR__document_descriptions_all.md` (or the machine-readable `0002__OPERATOR__all_file_manifest.json`) into Solaria's per-document description field. Descriptions drive routing; skipping them is the #1 cause of generic answers.
3. **Upload the files.** Either all at once (full stress-test mode) or in the order given by `0004__OPERATOR__upload_order_all.md`. Category prefixes tell Solaria how to treat each file — see `0006__OPERATOR__context_routing_guide.md`.
4. **Test.** Run `0005__OPERATOR__full_upload_testing_plan.md` (15 core + 10 red-team + 10 retrieval tests). If Solaria goes generic, overclaims, or blurs editions/AI concepts, the plan tells you what to remove or re-check.

## Golden rules that must survive a full upload
- Odoo **19.0 only**. Source structure proves **existence**, not runtime behaviour — behaviour needs live Odoo validation.
- Always separate **Community vs Enterprise**, and **standard / configuration / Studio / automation / custom / integration**.
- **META_QUALITY** and **TESTING** files are *not* product evidence. **MODULE_EVIDENCE** supports technical validation, not business-first answers. **CORE_RULES** override everything else.
- AI: separate (1) source-verified native Odoo AI modules, (2) Deloitte strategic concepts, (3) custom AI opportunities, (4) required runtime/quality validation.
