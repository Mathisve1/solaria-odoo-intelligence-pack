# Answer Quality Rubric — Scoring Solaria Answers (0–5 per criterion)

**Use:** score acceptance/red-team/benchmark answers and real consultant transcripts. 10 criteria × 0–5 = max 50. Not every criterion applies to every question — score applicable ones, average to a 0–5 overall.
**Release bars:** average ≥4.0 across the Batch-3 suite; no applicable criterion averaging <3.0; criteria C3 and C6 are hard floors (any single answer scoring ≤1 there = treat as critical fail).

## Scale anchors (apply per criterion)
**0** absent/wrong · **1** token mention, unusable · **2** present but vague or partly wrong · **3** correct but shallow — needs consultant rework · **4** correct, specific, usable with light editing · **5** consulting-grade — could go into internal work products as-is.

## Criteria

| # | Criterion | What a 5 looks like | Typical 2 |
|---|---|---|---|
| C1 | **Business interpretation** | Restates the underlying business need; surfaces the implicit process and stakeholder | Jumps straight to features |
| C2 | **Odoo module relevance** | Correct modules by technical name, nothing invented, right granularity (module, not "Odoo can…") | Vague app-level hand-waving |
| C3 | **Community vs Enterprise accuracy** *(hard floor)* | Every capability edition-tagged; commercial caveat where relevant | Missing or wrong edition on a load-bearing claim |
| C4 | **Standard/configuration/Studio/custom separation** | Ladder walked in order; named configuration objects; rejected rungs explained | "Could be configured or customized" without the ladder |
| C5 | **Evidence awareness** | Cites which pack documents ground the answer; grades claims with the evidence vocabulary | No sourcing; uniform confidence |
| C6 | **Uncertainty handling** *(hard floor)* | Existence-vs-behaviour split explicit; validation route named; resists pressure to drop caveats | Runtime details asserted as fact |
| C7 | **Deloitte advisory value** | Opinionated recommendation with risks/assumptions; challenges weak premises | Neutral encyclopedia answer |
| C8 | **Demo usefulness** | Concrete demo angle/storyline with rehearsal caveat where demo-relevant | "You could demo this" without a scene |
| C9 | **Implementation realism** | Effort class, dependencies, migration/adoption watch-outs, phasing awareness | Solution named with zero delivery context |
| C10 | **Concise clarity** | Tight structure, scannable, no filler; a partner could read it in one pass | Rambling or bullet soup that hides the answer |

## Scoring sheet template (copy per answer)
```
Question ID:            Date:            Session: fresh / continued
C1 __  C2 __  C3 __  C4 __  C5 __  C6 __  C7 __  C8 __  C9 __  C10 __
Applicable count: __   Total: __   Average: __
Hard-floor breach (C3/C6 <= 1)? yes/no
Verdict: pass / fail / critical-fail      Notes:
```

## Interpretation guide
- **Avg ≥4.0, no floors breached:** answer quality supports release/expansion.
- **Avg 3.0–3.9:** usable with consultant rework — acceptable early, but investigate the weakest criterion before expanding uploads.
- **Avg <3.0 or any floor breach:** treat as failed test → per-test fix actions in the acceptance suites, then re-score.
- Track criterion averages across runs: a *dropping* C5/C10 after an upload expansion is the classic context-overload signature (see `context_overload_strategy.md`).
