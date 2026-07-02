# Odoo Demo Storyline Playbook — Deloitte

| Attribute | Value |
|---|---|
| Document type | Demo / Storyline Document |
| Authority level | Medium — narrative guidance; every step must be rehearsed in a live 19.0 database |
| Version scope | Odoo 19.0 context pack |

## 1. Principles
1. **Story beats features.** A persona with a problem, a day that gets better — not a menu tour.
2. **Rehearsed truth.** Nothing enters a demo that wasn't executed successfully in the demo DB the day before. Views summaries in the module packs give the real menu paths.
3. **Edition honesty.** Label Enterprise moments as Enterprise. Demoing E to a C budget creates expectation debt that kills projects later.
4. **One continuous thread** across apps (the platform is the product), then depth in the domain that hurts the client.
5. **AI shown responsibly:** native features live and rehearsed with a fallback; concepts as labeled mockups/narrative — never blurred together.

## 2. Executive demo (20–30 min)
Structure: business pain → one continuous flow → control/insight moment → roadmap slide.
- Example thread (trade/services): web lead arrives → CRM kanban → quote with template → customer signs & pays online → delivery order appears → invoice posted → CFO dashboard/report.
- Talk value per step (cycle time, error elimination, audit trail), not clicks.
- End with the standard-first implementation philosophy (why their customization instinct is a cost).

## 3. Functional-team demo (60–90 min per domain)
Structure per domain: their current process replayed in Odoo → configuration moments ("this is a setting, not development") → exception handling → reporting pivots → honest gap notes.
- Use their vocabulary, their product names, 5–10 records of their master data if possible.
- Show the configuration screen for one thing they believe needs custom (stage design, SLA policy, route) — the "it's configuration" reveal is the strongest message.

## 4. Technical-team demo (60 min)
Architecture story: one ORM/data model (show a record's chatter+audit), module/inheritance philosophy, automation rules, API surface, Studio governance (E), upgrade policy. Goal: turn IT from skeptic to guardian of standard-first.

## 5. Storytelling patterns
- **Day-in-the-life:** follow one persona through a morning.
- **Order #1042:** one business object travels through departments.
- **Before/after:** 4 tools + 3 re-entries vs one flow.
- **Exception drama:** things go wrong (stockout, SLA breach) → the system surfaces it → human fixes with context.
- **The invisible accountant:** operations happen, books write themselves (session close, delivery valuation).

## 6. Domain demo seeds (rehearse from module packs' demo angles)
- CRM/Sales: lead→signed quote in minutes; discount control.
- Finance: (E) OCR bill → 3-way match → payment run; live P&L.
- Inventory: barcode receipt→putaway→pick→carrier label (E); serial trace.
- Manufacturing: MTO order→MO→floor tablet→quality gate (E).
- Services: sold hours→project→timesheet→invoice; (E) planning Gantt.
- Helpdesk/FSM (E): ticket→SLA→field visit→signature→invoice on site.
- HR: applicant→CV parse (E)→offer signed (E)→employee onboarding plan.
- eCommerce/POS: webshop order and store sale landing in the same stock/books.
- Subscriptions (E): recurring invoice run + MRR cohort screen.

## 7. Demoing Odoo-native value BEFORE custom AI
Sequence: standard flow → configuration reveal → native AI assist (E, live: OCR, drafting, document sorting) → THEN the Deloitte AI vision (Company Brain/Copilots) as labeled concept slides. This ordering protects credibility and licenses the vision.

## 8. Responsible AI demo rules
- Live AI only after same-day rehearsal; keep a recorded/backup path.
- Show the human validation step every time (the confidence queue is a feature, not a weakness).
- Name data governance (what leaves the environment, IAP credits, pgvector prerequisite) before the client asks.
- Never claim concept features are shipping product.

## 9. What to avoid
- Settings screens in executive demos; menu safaris; lorem-ipsum data.
- Untested "quick" side steps requested mid-demo (park politely).
- Feature-parity duels with incumbent tools ("does it have X?") — return to the thread.
- Promising exact behavior in the client's future setup ("we'll validate in your pilot").

## 10. Preparation checklist
- [ ] Demo DB on 19.0 with client-flavored master data (10 products, 10 partners, their logo)
- [ ] Full run-through executed same week; timings noted
- [ ] Edition labels decided per scene
- [ ] Fallbacks for every live AI/external dependency
- [ ] Gap questions anticipated with honest answers from the fit-gap register
