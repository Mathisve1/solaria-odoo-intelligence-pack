# Risk, Assumption and Claim Control

| Attribute | Value |
|---|---|
| Foundation file | 0018 of 20 |
| Purpose | The label vocabulary that keeps every demo claim honest. Labels appear in-line, next to the claim they qualify, in every internal output; the room hears their plain-language equivalents. |

## 1. The claim labels

| Label | Meaning | Plain-language equivalent for the room |
|---|---|---|
| **Source-verified** | The module/structure verifiably exists in the Odoo 19.0 source (catalog/evidence-backed), correct edition confirmed | "This is part of the product" (with edition) |
| **Pack-supported** | The capability is described in the Intelligence Pack's functional summaries; existence solid, detail level functional | "This is standard capability; we will show it" |
| **Demo-validated** | We executed it live on our demo database during rehearsal | "You will see this working in a moment" |
| **Client-specific assumption** | We filled an intake gap; the client must confirm | "We assumed X; correct us if that is wrong" |
| **Requires technical validation** | Behaviour/performance/integration must be proven on a live system before commitment | "We will confirm this on a live environment" |
| **Requires commercial validation** | Licensing, pricing, subscription contents, hosting entitlements | "We will confirm what your subscription includes" |
| **Requires localisation validation** | Country statutory/payroll/e-invoicing completeness needs expert confirmation | "Our local specialists will confirm the [country] specifics" |
| **Advisory recommendation** | Deloitte judgement, not product fact | "Our recommendation, based on what you told us" |
| **Custom concept** | Something we would design/build; NOT product | "This is what we would build for you" |

## 2. Application rules
1. Every capability claim in a demo plan carries exactly one primary label (plus edition tag).
2. Escalation logic: a claim may move UP only by doing the work (Pack-supported becomes Demo-validated only through rehearsal; nothing becomes Source-verified by enthusiasm).
3. The four validation labels are not weaknesses; they are the professional backbone. They are never deleted on request; wording may be polished, the label survives (file 0002 rule).
4. AI claims always carry two parts: existence (Source-verified, Enterprise) AND quality (Requires technical validation until piloted on relevant data).
5. Custom concept material is introduced as such BEFORE being shown (file 0010); it never inherits a product label because it "looked native" in the demo.
6. Statutory, legal-validity (e-signature) and compliance claims always carry Requires localisation validation unless a country expert has signed off in writing.

## 3. The registers (where labels live between meetings)
- **Assumption register:** every Client-specific assumption with its confirmation owner and date.
- **Validation register:** every Requires-... claim with route (live check / commercial desk / country expert), owner, due date, and the demo beat it affects.
- **Risk notes:** anything that could embarrass us in the room (unstable functionality, sensitive topic, expectation set by others), each with a handling decision.
These registers travel with the opportunity (workflow stages 2, 12, 14) and are updated after every client contact.

## 4. The honesty reflex (default sentences)
- When unsure: "I do not want to guess on this; it goes on the validation list with an owner."
- When pushed for certainty: "I can say it confidently like this: [claim with label in plain language]."
- When a concept impresses: "Worth being precise: this part is what we would build for you; the product parts you saw before it are standard."
