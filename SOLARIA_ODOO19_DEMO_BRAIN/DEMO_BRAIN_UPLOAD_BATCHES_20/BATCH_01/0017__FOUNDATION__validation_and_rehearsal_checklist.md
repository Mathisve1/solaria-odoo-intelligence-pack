# Validation and Rehearsal Checklist

| Attribute | Value |
|---|---|
| Foundation file | 0017 of 20 |
| Rule | No beat is demo-ready until rehearsed live (file 0002 definition). This checklist is executed at workflow stage 12; ALL items pass or the beat is cut, replaced or backed up. |

## 1. Environment checks
- [ ] **Module installed:** every module the storyline touches is installed and loads (verified by clicking, not by assumption).
- [ ] **Edition confirmed:** the database edition matches the conversation (file 0011); Enterprise-only beats verified as actually present.
- [ ] **Version confirmed:** Odoo 19.0; build date noted in the runbook.
- [ ] **Localisation/language:** demo language and country setup match intake C/F.

## 2. Functional checks (per storyline beat)
- [ ] **User rights tested:** each beat executed as its persona user (not admin); role-based screens verified to show what the storyline claims.
- [ ] **Workflow tested:** the full click-path executed end to end, including the exception beats (the stockout, the block, the failed check fire as planned).
- [ ] **Demo records prepared:** the named records of the data checklist (file 0016) exist, staged at the right states.
- [ ] **Reports populated:** every report/dashboard shown displays real history; drill-downs land where the script says.
- [ ] **Integrations available:** live integration moments tested on the demo network; simulated moments have their labelling sentence in the script.
- [ ] **AI output validated:** every AI/OCR moment executed the same day with the actual demo documents; outputs reviewed; fallback prepared. AI is never first-run in front of a client.

## 3. Resilience checks
- [ ] **Backup records prepared:** each fragile beat has its plan-B record and the switch rule (one retry, then backup).
- [ ] **Demo database reset:** reset procedure executed once successfully; a clean start state exists for the real session.
- [ ] **Offline/latency contingency:** remote demos: screen-share fallback, second presenter can take over; on-site: local fallback or recording for network-dependent beats.

## 4. Delivery checks
- [ ] **Timing rehearsed:** full run-through against the runbook clock; accordions (file 0014) identified; overrun recovery agreed.
- [ ] **Browser tabs prepared:** tab set in runbook order, logged in per persona, zoom level readable from the back of the room; notifications silenced.
- [ ] **Handovers rehearsed:** multi-presenter transitions practised with one-line handoffs.
- [ ] **Client-specific claims reviewed:** every claim in the script re-checked against its label (file 0018); anything "Requires validation" either resolved, rephrased, or explicitly framed as to-be-validated in the room.

## 5. Sign-off
The rehearsal log records: date, environment, who rehearsed, per-beat pass/fail, cuts and backups decided. A beat without a pass does not appear in the client session. The sign-off line: "every minute of this demo has run successfully on this database within the last N days" should be true with N no greater than 7 (same-day for AI moments).
