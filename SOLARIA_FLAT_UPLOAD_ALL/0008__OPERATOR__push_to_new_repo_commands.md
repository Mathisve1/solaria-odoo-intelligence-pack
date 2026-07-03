# Push This Flat Folder to a New Private GitHub Repo

**Do not run these automatically.** They are provided for when you explicitly want the flat upload package in its own private repository, separate from the main pack repo.

Target repo name: **`solaria-odoo-flat-upload-all`** (private).

The commands copy **only** `SOLARIA_FLAT_UPLOAD_ALL/` into a fresh folder outside the current repo, so the new repo contains just the flat files — no `_sources/`, no `.git` history, no source code.

---

## Option A — GitHub CLI (`gh`), recommended
Run from a normal shell (paths are Windows examples; adjust as needed).

```bash
# 1. Create a clean staging folder OUTSIDE the current repo
mkdir "C:/Users/mathi/Desktop/solaria-odoo-flat-upload-all"

# 2. Copy ONLY the flat files (no subfolders exist, so a flat copy is exact)
cp "C:/Users/mathi/Desktop/Solaria/SOLARIA_FLAT_UPLOAD_ALL/"* "C:/Users/mathi/Desktop/solaria-odoo-flat-upload-all/"

# 3. Initialise git there
cd "C:/Users/mathi/Desktop/solaria-odoo-flat-upload-all"
git init
git branch -M main

# 4. Safe .gitignore (belt-and-braces; nothing sensitive should be here anyway)
printf "%s\n" "_sources/" "*.zip" "*.7z" "*.tar" "*.gz" ".env" "*.env" "*.key" "*.pem" "*.pfx" "*.p12" "*.db" "*.sqlite" "settings.local.json" ".claude/" "__pycache__/" > .gitignore

# 5. Commit
git add .
git commit -m "Solaria Odoo intelligence pack — flat all-in upload package (304 curated files)"

# 6. Create the PRIVATE repo and push in one step
gh repo create solaria-odoo-flat-upload-all --private --source=. --remote=origin --push
```

Verify afterward:
```bash
gh repo view solaria-odoo-flat-upload-all --json visibility,name
git remote -v
```

---

## Option B — Manual remote (no `gh`)
1. On github.com, create a new **private** repo named `solaria-odoo-flat-upload-all` (do not initialise with README).
2. Then:
```bash
mkdir "C:/Users/mathi/Desktop/solaria-odoo-flat-upload-all"
cp "C:/Users/mathi/Desktop/Solaria/SOLARIA_FLAT_UPLOAD_ALL/"* "C:/Users/mathi/Desktop/solaria-odoo-flat-upload-all/"
cd "C:/Users/mathi/Desktop/solaria-odoo-flat-upload-all"
git init
git branch -M main
printf "%s\n" "_sources/" "*.zip" ".env" "*.key" "*.pem" ".claude/" "settings.local.json" > .gitignore
git add .
git commit -m "Solaria Odoo intelligence pack — flat all-in upload package (304 curated files)"
git remote add origin https://github.com/<YOUR_USERNAME>/solaria-odoo-flat-upload-all.git
git push -u origin main
```

---

## Safety checks before pushing
- [ ] Confirm the new repo is **private** (checkbox in the GitHub UI, or `--private` flag / `gh repo view … --json visibility`).
- [ ] Confirm the staging folder contains **only** the flat files (no `_sources`, no `.git` from the old repo, no zips): `ls` should show ~314 files, all starting with a 4-digit order prefix.
- [ ] Confirm no secrets: none exist in the pack, but a quick scan never hurts.

## Note
This is a **copy**, so the original `SOLARIA_FLAT_UPLOAD_ALL/` stays inside the main `Solaria` repo. If you would rather keep the flat folder only in the new repo, delete it from the main repo after pushing — but the authoritative source (`solaria/`) always stays in the main repo regardless.
