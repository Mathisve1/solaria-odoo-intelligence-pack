# Native AI in Odoo 19.0 — Standard vs Configuration vs Custom (Consolidated)

Edition: entire layer Enterprise-only; pgvector + IAP gates apply. This document places AI requests on the standard solution ladder (05).

## Likely standard (Enterprise, existence source-verified — quality needs pilots)
AI agents suite (`ai_app`) · AI-computed fields (`ai_fields`, incl. via Studio) · AI steps in automation rules (`ai_server_actions`) · lead creation from email/livechat · AI livechat/website agents · document auto-classification · agents grounded on Documents (`ai_documents_source`) · drafting assists (accounting, knowledge) · OCR family (bills, statements, expenses, CVs; bill↔PO matching) · call transcription (`voip_ai`) · sign/ESG/recruitment assists (scope: validate live).

## Configuration possibilities
Agent definitions/prompts and knowledge sources within `ai_app` tooling · AI fields with prompts on chosen models · AI steps in automation rules · OCR validation-queue settings · which workspaces/articles ground which agents. **Prompt/agent definitions are configuration artifacts — register and version them like any customization.**

## Studio possibilities
`web_studio_ai_fields`: create AI-computed fields from Studio — same governance as all Studio artifacts, plus AI-register entry (see governance doc).

## Automation possibilities
AI steps inside deterministic rules — the recommended pattern: deterministic trigger/condition, AI for the fuzzy middle (draft, classify, summarize), human or deterministic check on the way out.

## Custom development is justified when
- External model orchestration (client-mandated LLM platforms, private hosting) beyond native configurability.
- Event-stream/real-time triggers from outside Odoo.
- Cross-system copilots (Odoo + non-Odoo data) — the Company-Brain class of Deloitte builds.
- Bespoke evaluation/guardrail layers for regulated use.

## External integration is justified when
- Enterprise LLM/AI platforms are corporate standard (Odoo consumes/exposes via API) · CDP/data platforms feed segments/features · specialized AI vendors (speech, vision) beyond native scope.

## What to avoid
- AI in deterministic domains: posting, tax determination, reservation, pricing execution — audit findings, not innovation.
- Auto-send/auto-reject flows at go-live — human-in-the-loop is the default until acceptance metrics justify autonomy (and in recruitment: human decision always — EU AI Act high-risk).
- Quoting accuracy/deflection/rate numbers without a pilot on client data.
- Presenting Deloitte concepts as product ("as you saw, Odoo's Company Brain…" — never).
- Ignoring the gates: Community client, no pgvector, or unbudgeted IAP = no native AI story.

## Deloitte recommendation principles
Two-part verdicts (exists natively / quality piloted). Native-first, then configuration (agents/fields/steps), custom AI only with the governance obligations priced in. Every AI artifact — agent, prompt, AI field, AI step — lives in the AI register with an owner (governance doc §3).

## Validation questions
1. Which concrete task, which volume, which error tolerance — and what does the pilot on real data show?
2. Which gate status: edition, pgvector/hosting, IAP budget?
3. Who reviews AI output in-flow, and what happens on low confidence?
4. Is the use case EU-AI-Act-sensitive (recruitment, worker monitoring, credit-like decisions)?
