# Batch 3 — Exact Document Titles & Descriptions (paste sheet)

18 files, functional summaries only + the AI pack unit (items 17–18 require the AI risk/legal checkbox from the go/no-go list). Common rules: authority = high for functional questions about that module; never use for runtime-behaviour proof — validate live in Odoo 19.0.

---

**1. `modules/sale/functional_summary.md`** · Title: `Odoo 19.0 — Sales Functional Summary (Community)`
> Primary business reference for the Odoo 19.0 sale module (Community): quote-to-order capabilities, pricelists, portal signature/payment, invoicing policies, fit-gap and demo angles. Use for functional Sales questions. Do not use for runtime behaviour proof — validate live.

**2. `modules/account/functional_summary.md`** · Title: `Odoo 19.0 — Invoicing/Finance Functional Summary (Community core)`
> Primary business reference for the Odoo 19.0 account module (Community "Invoicing"): AR/AP, payments, taxes, and the edition line to Enterprise Accounting (account_accountant, account_reports). Use for functional finance questions and the finance edition decision. Do not use for statutory completeness — country packs + expert validation.

**3. `modules/crm/functional_summary.md`** · Title: `Odoo 19.0 — CRM Functional Summary (Community)`
> Primary business reference for the Odoo 19.0 crm module (Community): pipeline, stages, activities, predictive scoring, lead assignment, and Enterprise extensions (AI leads, VoIP). Use for functional CRM questions. Do not use for runtime scoring behaviour — validate live.

**4. `modules/stock/functional_summary.md`** · Title: `Odoo 19.0 — Inventory Functional Summary (Community)`
> Primary business reference for the Odoo 19.0 stock module (Community): warehouses, routes, lots/serials, replenishment, valuation hooks; Enterprise adds barcode/quality/carriers. Use for functional inventory questions. Do not use for WMS-optimization promises.

**5. `modules/purchase/functional_summary.md`** · Title: `Odoo 19.0 — Purchase Functional Summary (Community)`
> Primary business reference for the Odoo 19.0 purchase module (Community): RFQ→PO lifecycle with native approval step, vendor pricing, bill↔PO matching structures; Enterprise adds 3-way match, Approvals, OCR. Use for functional procurement questions. Do not use for approval-matrix promises beyond the native step without the Enterprise/custom distinction.

**6. `modules/mrp/functional_summary.md`** · Title: `Odoo 19.0 — Manufacturing Functional Summary (Community)`
> Primary business reference for the Odoo 19.0 mrp module (Community): BoMs, manufacturing orders, work centers, subcontracting; Enterprise adds Shop Floor, MPS, PLM, quality. Use for functional manufacturing questions. Do not use to promise APS-grade finite scheduling — it is not.

**7. `modules/project/functional_summary.md`** · Title: `Odoo 19.0 — Project Functional Summary (Community)`
> Primary business reference for the Odoo 19.0 project module (Community): task pipelines, milestones, portal collaboration, profitability plumbing; Enterprise adds Gantt/forecast. Use for functional project/services questions. Do not use for billing promises without the sale/timesheet configuration context.

**8. `modules/hr_recruitment/functional_summary.md`** · Title: `Odoo 19.0 — Recruitment Functional Summary (Community, AI = high-risk domain)`
> Primary business reference for the Odoo 19.0 hr_recruitment module (Community): jobs, applicant pipeline, talent pools, refusal flows; Enterprise adds CV OCR and AI assist (EU AI Act high-risk domain — human decision always). Use for functional recruitment questions with governance framing. Do not use to promise screening accuracy.

**9. `modules/helpdesk/functional_summary.md`** · Title: `Odoo 19.0 — Helpdesk Functional Summary (Enterprise-only)`
> Primary business reference for the Odoo 19.0 helpdesk module (Enterprise-only): teams, SLA policies, ratings, ERP bridges (returns, credit notes, timesheets, field service). Use for functional customer-service questions. Do not use for Community clients without stating the edition gate and honest fallbacks.

**10. `modules/documents/functional_summary.md`** · Title: `Odoo 19.0 — Documents/DMS Functional Summary (Enterprise-only)`
> Primary business reference for the Odoo 19.0 documents module (Enterprise-only): workspaces, tags, workflow actions turning files into business records, AI sorting. Use for functional DMS questions and the SharePoint-coexistence boundary. Do not use for retention/legal compliance promises — design work.

**11. `modules/sign/functional_summary.md`** · Title: `Odoo 19.0 — Sign/e-Signature Functional Summary (Enterprise-only)`
> Primary business reference for the Odoo 19.0 sign module (Enterprise-only): templates with roles, portal signing, audit log, HR/sales bridges. Use for functional e-signature questions. Do not use for legal-validity claims — signature levels (SES/AES/QES) are jurisdiction questions for legal review.

**12. `modules/sale_subscription/functional_summary.md`** · Title: `Odoo 19.0 — Subscriptions Functional Summary (Enterprise-only)`
> Primary business reference for the Odoo 19.0 sale_subscription module (Enterprise-only; depends on Enterprise accounting): plans, recurring invoicing crons, renewals, MRR/churn analytics. Use for functional subscription questions. Do not use for proration/usage-billing promises without live validation.

**13. `modules/industry_fsm/functional_summary.md`** · Title: `Odoo 19.0 — Field Service Functional Summary (Enterprise-only)`
> Primary business reference for the Odoo 19.0 industry_fsm module (Enterprise-only, built on the Enterprise project/timesheet layer): mobile work orders with timers, worksheets, signatures, on-site invoicing. Use for functional field-service questions. Do not use for offline/route-optimization promises — validate on devices; optimization is integration territory.

**14. `modules/website_sale/functional_summary.md`** · Title: `Odoo 19.0 — eCommerce Functional Summary (Community)`
> Primary business reference for the Odoo 19.0 website_sale module (Community): catalog, checkout steps, payments, B2B pricing visibility, abandoned carts — natively wired to stock and invoicing. Use for functional eCommerce questions. Do not use for hyperscale/performance promises — hosting architecture questions.

**15. `modules/web_studio/functional_summary.md`** · Title: `Odoo 19.0 — Studio Functional Summary (Enterprise-only)`
> Primary business reference for the Odoo 19.0 web_studio module (Enterprise-only): no-code fields/views/apps, report editing, Studio approval rules on actions, Studio export governance. Use for Studio-vs-custom scoping and no-code approval questions. Do not use for Community clients except to state the edition gate; never place algorithms in Studio.

**16. `modules/base_automation/functional_summary.md`** · Title: `Odoo 19.0 — Automation Rules Functional Summary (Community)`
> Primary business reference for the Odoo 19.0 base_automation module (Community): trigger→condition→action rules on any model, time-based cron, action vocabulary. Use for automation questions on any edition. Do not use for hard-blocking validations or workflow-engine emulation — native features first.

**17. `modules/ai_native_odoo_19/functional_summary.md`** · Title: `Odoo 19.0 — Native AI Layer Functional Summary (Enterprise-only)` *(requires AI review checkbox)*
> Business-level explanation of the native AI layer of Odoo 19.0 Enterprise, grouped by capability (platform, front-office assists, drafting, document intelligence/OCR, specialized assists), with edition/pgvector/IAP gates and what does NOT exist natively. Use for any "what can Odoo's AI do" question with the two-part verdict (exists / quality-piloted). Do not use for accuracy claims — pilot on client data.

**18. `modules/ai_native_odoo_19/governance_and_validation.md`** · Title: `AI in Odoo — Governance, Validation & Safe Phrasing (Deloitte rules)` *(requires AI review checkbox)*
> Governance and phrasing rules for AI in Odoo engagements: risk table, AI register, validation protocol (pilot, leakage test), EU AI Act mapping, demo-safe rules and client-safe wording with explicit never-promise examples. Use for every AI risk, compliance or phrasing question. Do not use as a capability inventory — that is the AI pack's inventory/summary.
