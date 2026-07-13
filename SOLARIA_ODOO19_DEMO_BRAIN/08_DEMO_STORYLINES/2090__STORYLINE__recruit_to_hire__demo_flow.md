# Demo Storyline: Recruit-to-Hire

| Attribute | Value |
|---|---|
| Category | STORYLINE (instantiates the 12-beat framework, foundation 0009) |
| Rules | Timing limits per format apply (0014); every beat needs data (0016) and rehearsal (0017); editions and claim labels always (0011, 0018) |

## Client problem
Slow candidate response loses hires; CVs live in inboxes; compliance anxiety everywhere.

## Audience
HR director, recruiters, compliance owner; 45 minutes

## Prerequisites
- hr_recruitment staged
- CV samples parsed same-day if E parsing shown
- offer template for e-sign (E)

## Modules (edition)
- hr_recruitment (C)
- CV OCR + AI assist (E, human-decision governance stated)
- sign (E)
- hr (C) for the hire

## Start state
Application arriving from the careers page

## End state
Signed offer; applicant became employee with onboarding plan firing

## Step-by-step demo flow
1. Application lands in the pipeline
2. CV parsed into the form, human reviews (E, labelled)
3. interview loop via activities
4. respectful refusal beat with template (the other candidate)
5. offer sent, signed on a phone (E)
6. create employee, onboarding checklist fires

## Wow moments
- CV-to-form with visible human check
- phone-signed offer
- the onboarding plan firing

## Challenger insight
Speed wins talent: the first respectful, fast response frames the candidate's decision as much as the salary does.

## Likely questions
- GDPR retention?
- job boards?
- AI fairness? (human decides, said plainly)

## Risks
Parsing shown first-run (never: same-day rehearsal on the actual CVs)

## Validation points
- Parsing pilot on their CV sample
- retention automation configured
- works-council notes

## Short version (15 min)
Application to parsed to offer signed

## Executive version (30 min)
Time-to-hire framing, the pipeline run, compliance-confidence close
