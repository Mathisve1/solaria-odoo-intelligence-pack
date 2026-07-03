# AI in Odoo 19.0 — Consolidated Native-AI Evidence Pack (`ai_native_odoo_19`)

> One pack for the entire native AI layer of Odoo 19.0 (28 modules: AI platform, domain assists, OCR digitization) — consolidated because the individual AI modules are small, but the questions about them are big.

| Attribute | Value |
|---|---|
| Pack type | Consolidated evidence + advisory pack (not a single technical module) |
| Source origin | **Enterprise only** — verified: the Community 19.0 tree contains no `ai*` modules |
| Version scope | Odoo 19.0 (Enterprise snapshot 2026-07-02) |
| Infrastructure gates | `ai_auto_install` requires PostgreSQL **pgvector**; OCR extract family runs on **IAP** (metered pay-per-use) |
| Confidence | Module existence: high (source-verified). Runtime output quality: **unverified — always pilot before promising** |
| Recommended upload priority | High-medium (with Batch 2/3 — it answers the fastest-growing question category) |

## Contents and how Solaria should use them

| File | What it is | Use it for |
|---|---|---|
| `ai_module_inventory.json` | Source-verified list of all 28 native AI/OCR modules with edition, dependencies, manifest summaries | THE authority on "does a native AI module exist for X" |
| `functional_summary.md` | Business meaning of the native AI layer, grouped by capability | Explaining what Odoo 19 AI actually does for a client |
| `standard_vs_custom.md` | Where native AI ends and Deloitte-built AI begins | Scoping AI requests on the solution ladder |
| `governance_and_validation.md` | Risks, EU AI Act mapping, validation protocol, demo-safe and client-safe phrasing | Keeping every AI conversation credible and compliant |

## Reading order
Existence question → inventory JSON. Value question → functional_summary. Build question → standard_vs_custom. Risk/phrasing question → governance_and_validation. Strategy/concepts (Company Brain, Copilots) → `06_odoo_ai_opportunity_map.md` + the AI strategy playbook — **those are Deloitte concepts, never product features.**

## The three sentences that must survive every AI answer
1. Native AI in Odoo 19.0 is **Enterprise-only** (and pgvector/IAP-gated).
2. The source proves these modules **exist** — output quality must be **validated live** per use case.
3. Deloitte concepts (Company Brain, Operations Copilot, Alerts Center, Role Assistants) are **not** Odoo features.
