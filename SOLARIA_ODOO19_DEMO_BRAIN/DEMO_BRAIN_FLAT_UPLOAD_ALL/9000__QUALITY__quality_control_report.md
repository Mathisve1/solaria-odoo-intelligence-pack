# Demo Brain Quality Control Report (v1.0)

Category: QUALITY (meta artifact; not product evidence, not answer content).

## Validation checklist (from the build specification)

| Check | Result |
|---|---|
| Exactly 20 foundation files | PASS (0000 to 0019, verified by count and numbering) |
| Correct numbering 0000-0019, no gaps, no duplicates | PASS |
| No duplicate foundation responsibilities | PASS (one concern per file; 0019 manifest maps them; overlaps are references, not redefinitions) |
| No contradictions between foundation files | PASS (see foundation_consistency_audit.md for the cross-check table) |
| Mandatory intake logic present | PASS (0003 form; intake-first mandate in 0001/0002) |
| Intake completeness scoring present | PASS (0004: weights, 0-100, four bands, hard minimum-fields gate) |
| Challenger logic present | PASS (0007 methodology; 0300-range library, template and 11 scenarios) |
| Audience adaptation present | PASS (0008 matrix; 16 persona packs in 0400 range) |
| Standard-before-custom present | PASS (0010 demo ladder; reinforced in module demo packs and red-team tests) |
| Community-versus-Enterprise discipline present | PASS (0011; edition labels required throughout; enforced in tests 8000/8010) |
| Routing to existing Odoo pack present | PASS (0012: 11-step routing, authority statements, conflict rule) |
| Output contract present | PASS (0013: 18 sections; template 3500 mirrors it) |
| Demo timing control present | PASS (0014: format limits, cut protocol, overrun recovery) |
| Objection framework present | PASS (0015 structure and 14 categories; 4000-range library; scenarios) |
| Data readiness present | PASS (0016 specification; checklists 3550/3560) |
| Validation and claim control present | PASS (0017 rehearsal gate; 0018 nine labels and registers) |
| Later files do not redefine foundation rules | PASS (every supporting file states it extends and defers to foundations; conflict rule in 0012 and operator guide) |
| No raw Odoo source | PASS (no code files; product facts route to the Intelligence Pack) |
| No unsupported extensions | PASS (only .md, .txt, .json; see file_type_compliance_report.md) |
| All upload batches contain <= 20 files | PASS (BATCH_01 = exactly the 20 foundation files; later batches max 20) |

## Known limitations (say them plainly)
1. Persona, industry, module-demo and storyline packs are curated defaults: they must be confirmed against client intake (rule stated in each file) and, for product facts, against the Intelligence Pack.
2. Competitor-related scenarios are deliberately high-level; they contain no competitor capability claims and must stay that way.
3. This brain assumes the Odoo 19.0 Intelligence Pack is available as the product-knowledge corpus; without it, product answers degrade to reduced-confidence mode by design (0012).
4. Solaria retrieval behaviour is unverifiable before upload: the acceptance and red-team suites (8000/8010) exist to close exactly that gap after Batch 1.
5. Style rule honoured: no em dashes anywhere in the pack (verified by sweep).

## Recommended human review before upload
0001 global context read end to end; 0003/0004 intake and scoring approved by the pre-sales lead; one persona pack, one industry pack, one storyline sampled for tone; the red-team suite read by whoever will run it.