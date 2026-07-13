# File Type Compliance Report

Category: QUALITY (meta artifact; not product evidence).

Allowed extensions: .md, .txt, .json, .yaml, .yml. Forbidden: raw source, .py, zips, configs, databases.

| Metric | Value |
|---|---|
| Content files across the 12 source folders (incl. this report) | 145 |
| `.md` files | 142 |
| `.json` files | 2 |
| `.txt` files | 1 |
| Unsupported files | 0 |

**Result: PASS.** Every file uses an allowed extension. No raw Odoo source, no Python files, no archives, no local configuration, no Git or Claude artifacts anywhere in the brain. Generation tooling lives outside this folder tree. The flat upload folder and the batch folders are derived copies of these files plus the packaging report, and inherit compliance.

Verified also: zero em dashes in the corpus (style rule); zero duplicate flat filenames; foundation numbering 0000-0019 complete.
