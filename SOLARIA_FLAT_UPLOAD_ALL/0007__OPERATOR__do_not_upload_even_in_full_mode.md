# Do NOT Upload — Even in Full Stress-Test Mode

Full-upload mode means "upload all the curated knowledge files". It does **not** mean "upload everything on disk". The following must never reach Solaria, regardless of mode. None of these are present in this flat folder — this list is your guard against re-adding them by hand or pointing Solaria at the wider repo.

| Never upload | Why |
|---|---|
| `_sources/` and any raw Odoo source (Community/Enterprise trees, `.py`/`.xml`/`.js` source, `odoo-bin`) | Raw source code — out of scope, licensing-sensitive, huge, and not what Solaria should reason from. The whole pack exists to avoid this. |
| Original zip archives (`odoo-19.0.zip`, `enterprise-19.0.zip`, any `*.zip`) | Raw source bundles; unsupported type; irrelevant to advisory reasoning. |
| `.git/` and any Git internals | Version-control plumbing; not knowledge. |
| `.claude/`, `settings*.json`, `settings.local.json` | Local tool config; potential leakage; not knowledge. |
| `*.usage.md` companion files | Human uploader notes. Their content is already consolidated into `0002__OPERATOR__all_file_manifest.json` and `0003__OPERATOR__document_descriptions_all.md`. Uploading them duplicates every description and **poisons retrieval**. |
| `index.html` | Navigation helper with relative links that break when flattened; zero product value. |
| Shell artifacts / stray zero-byte files | Accidental redirect outputs (the repo root had a few once — they were cleaned). Not knowledge. |
| Any unsupported file type (`.csv .xlsx .py .sql .db .sqlite .zip .log .ini .toml .ipynb .parquet .pkl`) | Solaria does not accept them and they are not part of the curated pack. |
| Secrets, tokens, passwords, API keys, database URLs, `.env` files | Never upload credentials anywhere. None exist in the pack; keep it that way. |

## If you accidentally uploaded one
Remove it from Solaria, then re-run at least the first three tests in `0005__OPERATOR__full_upload_testing_plan.md` (retrieval sanity) — a stray `.usage.md` or source file is the most likely cause of sudden generic or confused answers.

## Reminder
Even in full mode, **TESTING** and **META_QUALITY** files ARE uploaded (they are curated pack content) but must be treated by Solaria as non-product-evidence — see `0006__OPERATOR__context_routing_guide.md`. That is different from the items above, which are never uploaded at all.
