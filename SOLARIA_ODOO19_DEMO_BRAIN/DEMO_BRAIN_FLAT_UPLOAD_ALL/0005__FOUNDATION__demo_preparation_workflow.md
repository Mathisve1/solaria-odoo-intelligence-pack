# Demo Preparation Workflow (end to end)

| Attribute | Value |
|---|---|
| Foundation file | 0005 of 20 |
| Purpose | The 14-stage pipeline every serious demo preparation follows. The brain states which stage it is serving in any given answer. |

For every stage: objective, inputs, actions, expected output, quality gate, failure condition.

## 1. Intake
- **Objective:** know the client, the audience, the challenges, the objective.
- **Inputs:** anything the account team has; the form (file 0003).
- **Actions:** administer the form (full/quick/interactive); restate; score.
- **Output:** completed intake block + completeness score.
- **Gate:** score band determines what may be produced (file 0004).
- **Failure:** proceeding on guesses; counting defaults as facts.

## 2. Intake validation
- **Objective:** separate facts from assumptions and rumours.
- **Inputs:** intake block; account-team claims.
- **Actions:** label every statement (client fact / assumption / default); flag contradictions; list unknowns by impact.
- **Output:** validated intake with assumption register.
- **Gate:** seven minimum fields present before a full plan.
- **Failure:** unsupported account-team folklore entering the plan unlabelled.

## 3. Challenge diagnosis
- **Objective:** find the real problems behind stated requirements.
- **Inputs:** section E; industry pack defaults.
- **Actions:** run the diagnosis chain of file 0006 per challenge.
- **Output:** challenge table: statement → pain → root cause → impact → insight → Odoo capability → demo moment → validation question.
- **Gate:** at least the top two challenges diagnosed to root-cause level.
- **Failure:** treating every requested feature as the real problem.

## 4. Audience analysis
- **Objective:** know who must be convinced of what.
- **Inputs:** section D; persona packs.
- **Actions:** per attendee: objective, concern, likely objection, wow moment, language level; identify the decision maker and the sceptic.
- **Output:** audience strategy map.
- **Gate:** every key attendee has an intended takeaway.
- **Failure:** one demo aimed at everyone (which convinces no one).

## 5. Odoo scope mapping
- **Objective:** map challenges to Odoo 19.0 capability, honestly.
- **Inputs:** challenge table; the existing Intelligence Pack via routing (file 0012).
- **Actions:** name modules with editions; verify existence in the catalog; pull demo angles from functional summaries.
- **Output:** scope list: challenge → modules (edition) → capability claim with label.
- **Gate:** no module outside the catalog; every capability edition-tagged.
- **Failure:** invented functionality; edition ambiguity.

## 6. Standard-versus-custom analysis
- **Objective:** classify every planned demo element on the ladder (file 0010).
- **Inputs:** scope list.
- **Actions:** per element: standard / configuration / Studio / automation / custom / integration / validation required.
- **Output:** classified scope; list of anything that must NOT be shown as standard.
- **Gate:** zero custom concepts disguised as standard.
- **Failure:** demoing a prototype as product.

## 7. Storyline design
- **Objective:** one process-led narrative that carries the challenges (file 0009).
- **Inputs:** challenge table, audience map, classified scope.
- **Actions:** choose the business object to follow; place wow moments at challenge points; plan the reframe.
- **Output:** storyline (12-beat structure).
- **Gate:** process-led, not menu-led; wow moments map to stated challenges.
- **Failure:** app tour; wow moments nobody asked for.

## 8. Demo flow design
- **Objective:** the minute-by-minute execution plan.
- **Inputs:** storyline; timing limits (file 0014).
- **Actions:** allocate minutes; assign presenters; define screens per beat; plan transitions and Q&A slots.
- **Output:** minute-by-minute runbook.
- **Gate:** within the format's process and wow-moment maximums.
- **Failure:** overloading; no Q&A budget.

## 9. Challenger preparation
- **Objective:** the insight that reframes the client's thinking (file 0007).
- **Inputs:** challenge table; industry pack.
- **Actions:** per key challenge: conventional view, hidden cost, insight, reframe, story, demo moment, advancing question.
- **Output:** Challenger sheet.
- **Gate:** insight is client-relevant and non-generic; tone is helpful.
- **Failure:** generic provocation; attacking the client's current choices.

## 10. Objection preparation
- **Objective:** never be surprised in the room (file 0015).
- **Inputs:** audience map (likely objections), competitive context.
- **Actions:** per expected objection: underlying concern, what not to say, response, proof, demo action, follow-up question.
- **Output:** objection sheet.
- **Gate:** top five objections covered incl. one edition/licensing and one AI objection if relevant.
- **Failure:** improvising answers to predictable objections.

## 11. Demo-data preparation
- **Objective:** data that tells the client's story (file 0016).
- **Inputs:** storyline; scope.
- **Actions:** specify master data, transactions, users/roles, reports, dashboards per demo beat; define reset and backup.
- **Output:** demo-data checklist.
- **Gate:** every beat has named records that exist before rehearsal.
- **Failure:** demoing on lorem-ipsum data.

## 12. Validation and rehearsal
- **Objective:** convert claims into demo-validated moments (file 0017).
- **Inputs:** runbook; environment.
- **Actions:** execute every beat live; check editions, rights, reports, AI outputs; time it; prepare backups.
- **Output:** rehearsal log; demo-ready confirmation per beat.
- **Gate:** ALL beats demo-validated or removed/replaced.
- **Failure:** first live execution happens in front of the client.

## 13. Delivery
- **Objective:** run the session to the plan, adapt without losing control.
- **Inputs:** runbook, backup flows, objection sheet.
- **Actions:** follow the storyline; park off-scope requests explicitly; capture questions.
- **Output:** delivered demo + captured questions/commitments.
- **Gate:** no unrehearsed improvisation on product claims.
- **Failure:** unplanned deep-dives; promises made live without labels.

## 14. Follow-up and next steps
- **Objective:** convert the demo into movement.
- **Inputs:** captured questions, commitments, audience reactions.
- **Actions:** follow-up email (template), open-question register with validation owners, POC recommendation if warranted.
- **Output:** follow-up pack; updated opportunity view.
- **Gate:** every open claim has an owner and a validation route.
- **Failure:** the demo ends and nothing happens.
