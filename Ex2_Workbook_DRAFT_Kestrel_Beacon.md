# Exercise 2 Answer Workbook (DRAFT for review): Kestrel Health Network, "Beacon"

**Status date used throughout: Tuesday 8 December 2026** (the case's "today").
**Candidate ID:** [U48680]
**AI tool used:** [Claude]
**Date / attempt:** [30/10/2026] / Attempt 1

> Draft note: every finding, owner and status below is built only from the case pack. Before submitting, check each line against the source named in brackets, rewrite anything in your own words, and make sure you can defend every status to an evaluator.

---

## Part 1 · Cover

As above.

---

## Part 2 · Findings Log

Each finding is a weakness in Beacon Release Readiness v0.9 that would stop a careful stranger trusting it. Sources are in brackets.

| # | Finding | Evidence | v0.9 item affected |
|---|---|---|---|
| F1 | Auto-route threshold was lowered from 0.80 to 0.72 on 25 Nov to reduce nurse queue. The only validated figure (ev-118) is at 0.80. No re-evaluation or CSO approval followed. AIP-2 requires both for any threshold change. | triage-config.yaml (a41f); E1; AIP-2 | 10 |
| F2 | The threshold was changed for workload reasons ("to manage nurse workload"), which is an operational motive, not a clinical one. | Appendix note; #beacon-delivery, 26 Nov (Imran Qureshi) | 10 |
| F3 | The clinical safety case was signed by Neha Sharma, the delivery lead, not by Kestrel's CSO. CSS-1 requires a Kestrel-owned case signed by the CSO. | v0.9 item 11; CSS-1; E7 | 11 |
| F4 | The "hazard log" relied on is Corvid AI's hazard log v2, written for CorvidBench deployments. It has no hazards for automated replies, mixed-language messages or nurse queue capacity. CSO Dr. Mathews has not reviewed it. | E7 | 11 |
| F5 | Under-triage in mixed-language messages is 6.8%, and the team logged it as risk R-17. No production measure of under-triage exists, and no clinician sampling is scheduled. | E1; E5 | 18 |
| F6 | R-17 was accepted by Neha Sharma on delivery's behalf on 5 Dec, and recorded by Owen Fletcher on 7 Dec. AIP-2 says clinical risk may be accepted only by the CMO or CSO, in writing, with a review date. | E4 (5 and 7 Dec); AIP-2 | 18 |
| F7 | The model is called through the floating alias "corvid-med-latest", which Corvid can change with 14 days' notice. A move to corvid-med-3.3 is scheduled for 15 Dec. Any model change needs re-evaluation and CSO approval before use under AIP-2. | E3; E4 (30 Nov); E8 (contract clause 9.4) | 9, 27 |
| F8 | The "96% accuracy" in v0.9 item 9 is Corvid's CorvidBench figure (96.2%), not Kestrel's data. Kestrel's own accuracy is 93%. The owner of item 9 (Jonas Weber) left Kestrel on 16 Oct. | v0.9 item 9; E1; E2; A3 | 9 |
| F9 | Vendor change process is marked agreed, but contract clause 9.4 lets Corvid update the alias on 14 days' notice, and pinned versions cost extra. No Kestrel decision was recorded. | v0.9 item 27; E8 | 27 |
| F10 | The rollback rehearsal covers only the application container (1.4.2 to 1.3.9). It does not cover model version, prompt version, or switching Beacon off so that all messages go to nurses. | E6 | 23 |
| F11 | The regression suite is green but does not include the model evaluation set. Its owner, Jonas Weber, has left Kestrel. | E4 (Victor Osei, 27 Nov); v0.9 item 8 | 8 |
| F12 | Night-shift capacity is 2 triage nurses covering both pilot sites plus the ward phone line. The urgent peak needs about 75 minutes of work against a 30-minute response target. | E4 (Priyanka Das, 1 Dec); v0.9 item 17 | 17 |
| F13 | The patient AI disclosure is still a draft, English only, and with Legal. PCS-3 requires patients to be told when a message was drafted by an automated system, and to be offered Hindi and Marathi. | E8; PCS-3; v0.9 item 26 | 26 |
| F14 | Automated self-care replies are at about grade 11 reading level. PCS-3 requires grade 8 or below. | E1 | 12 |
| F15 | Data retention is set to 365 days. RP-1 requires patient communications and decision records to be kept for 8 years. | triage-config.yaml; RP-1; v0.9 item 22 | 22 |
| F16 | The DPIA (v1, August) covers referral letters only. Portal messages were added in October, and the DPO has asked for an addendum before patient messages are processed. | E4 (Grace Liu, 2 Dec); v0.9 item 14 | 14 |
| F17 | Only 11 of 29 pilot-site triage nurses (38%) have completed the Beacon module, against a "trained" tick. | E8 | 24 |
| F18 | No call-centre scripts exist, and there is no route for a patient who replies to a self-care message saying "it's getting worse". Those replies land in the general inbox, answered within 48 hours. | E4 (Sunil Bhat, 3 Dec); E8 | 25 |
| F19 | The "Beacon Drift" dashboard has no Kestrel baseline. It measures category distribution and confidence only, not under-triage. Alerts go to a 14-member chat channel, not to an on-call rota. | E5 | 19, 20 |
| F20 | Accessibility review is marked N/A because Beacon is a "backend service". Beacon sends patient-facing messages in several languages, so the review is not optional. | v0.9 item 16; PCS-3 | 16 |
| F21 | ADR-009 (21 Sept) predates the 9 Oct scope change to portal messages and automated replies. No later architecture review exists. intent.md was not updated after the 9 Oct decision. | E8; A5 | 4, 1 |
| F22 | Stage-gate approvals for Intent, Spec, Plan, Build and Review were all signed by Neha Sharma on 2 Dec. She also wrote the checklist. The same person writes, approves and signs the gates, with no independent review. | v0.9 appendix | 1–4, 6–8, 11 |
| F23 | Code review is mostly by coding agents. Imran Qureshi approved 12 PRs and also wrote the prompts the agents use. About 70% of code was written by agents. | A5 | 12 |
| F24 | Two of 11 features have no plan: "Automated reply drafting" and "threshold tuning", which are the two riskiest. | A5 | 6 |
| F25 | Technical ownership sits with Tobias Grant until handover, but his contract ends on 18 Dec, and no handover is recorded. Operational ownership is "joint" with no named accountable person. | v0.9 appendix; A3 | 23, 30 |
| F26 | Human review for urgent cases (item 17) is ticked, but the staffing evidence shows the 30-minute response cannot be met. | E4; F12 | 17 |

---

## Part 3 · Governance Frame

### 3a. Five dimensions, one Accountable owner each

Accountable owners are taken only from A3.

| Dimension | What it covers | Accountable owner | Approver / second line |
|---|---|---|---|
| D1 · Clinical safety and risk acceptance | Clinical safety case, hazard log, risk acceptance, clinical sign-off | Dr. Helen Mathews (CSO) | Dr. Anjali Rao (sponsor), for the go decision |
| D2 · Model, evaluation and drift | Model version, confidence threshold, evaluation evidence, drift monitoring | Dr. Farah Siddiqui (Head of Data & AI) | Dr. Helen Mathews (CSO) |
| D3 · Data protection and records | DPIA and addenda, retention, audit logging | Grace Liu (DPO) | Owen Fletcher (Head of Risk & Compliance) |
| D4 · Security, platform and operational resilience | Security sign-off, rollback, monitoring, alerting, on-call | Kavya Nair (Platform & SRE Lead) | Rahul Menon (CISO) for security |
| D5 · Patient communication and human oversight | AI disclosure, reading level, language, nurse review, call-centre routes | Priyanka Das (Head of Nursing) | Marcus Bell (Chief Digital Officer), for disclosure |

Owen Fletcher holds the AI Use Policy and the risk register, so he is the second line for risk recording across all five dimensions.

### 3b. Stage-gate map

Stages: Intent, Spec, Plan, Build, Review, Release. Phases: **Pilot gate** (Go/No-Go 10 Dec; go-live 14 Dec, two sites) and **Network gate** (rollout 11 Jan 2027, nine sites).

| Stage | What must be true at the pilot gate (14 Dec) | What must be true at the network gate (11 Jan) |
|---|---|---|
| Intent | intent.md updated to include portal messages and automated replies | Scope confirmed for all nine sites |
| Spec | spec.md v4 covers the 9 Oct scope; clinical safety section is Kestrel-owned | Spec re-approved with pilot results |
| Plan | Plans exist for automated reply drafting and threshold tuning | Plans for all network-specific changes |
| Build | Model pinned to a version Kestrel evaluated; threshold set with re-evaluation | Build re-validated on Kestrel data at all nine sites |
| Review | Independent (non-author) review of safety-critical changes; CSO clinical safety case signed | Pilot review findings closed |
| Release | Human oversight, rollback covering model and prompt, monitoring with Kestrel baseline, DPIA addendum, retention fixed | Pilot evidence on under-triage, nurse capacity and patient outcomes reviewed |

### 3c. What must be true, pilot versus network

Pilot (14 Dec, two sites): this is a narrower decision because it limits exposure. Every message that Beacon would auto-route or auto-reply to should be nurse-reviewed, or those features should be switched off for the pilot.

Network (11 Jan): all the pilot conditions must be evidenced by data from the pilot, including a measured under-triage rate for mixed-language messages, real nurse-capacity data, and a clinical sample review.

---

## Part 4 · Release-Readiness Checklist v1

Status is as of 8 Dec. Met means the evidence in the pack shows it. Not met means the evidence shows it is absent or failing. Partial means part is evidenced.

Gate column: P = pilot gate (14 Dec), N = network gate (11 Jan), P+N = both.

| # | Stage | Gate | Dimension | Checkable question | Evidence and where logged | Owner | Approver | Status 8 Dec |
|---|---|---|---|---|---|---|---|---|
| 1 | Intent | P+N | D5 | Does intent.md include portal messages and automated replies? | intent.md not updated after 9 Oct (A5) | Neha Sharma | Dr. Anjali Rao | Not met |
| 2 | Intent | P | D1 | Is the pilot scope signed off by the sponsor? | Sponsor has not made the Go/No-Go decision (v0.9 item 30) | Dr. Anjali Rao | Marcus Bell | Not met |
| 3 | Intent | P | D1 | Is the business case approved? | Board paper, August (v0.9 item 1) | Marcus Bell | Board | Met |
| 4 | Spec | P+N | D1 | Does spec.md v3 cover portal messages and automated replies? | Spec v3 updated in October; clinical section copied from Corvid hazard log (A5) | Neha Sharma | Dr. Helen Mathews | Partial |
| 5 | Spec | P+N | D1 | Is the clinical safety section Kestrel-owned and CSO-signed? | Corvid hazard log v2 only; CSO has not reviewed (E7); CSS-1 | Dr. Helen Mathews | Dr. Anjali Rao | Not met |
| 6 | Spec | P | D4 | Is the architecture reviewed after the 9 Oct scope change? | ADR-009 dated 21 Sept; no later review (E8) | Tobias Grant | Dr. Farah Siddiqui | Not met |
| 7 | Plan | P | D2 | Do all features that affect patients have plans? | Plans missing for automated reply drafting and threshold tuning (A5) | Imran Qureshi | Neha Sharma | Not met |
| 8 | Plan | P+N | D3 | Are vendor contracts and data-processing agreements signed? | CTR-311 and CTR-312 signed; DPA includes India residency (v0.9 item 5) | Neha Sharma | Owen Fletcher | Partial |
| 9 | Plan | P+N | D2 | Is the model version pinned and evaluated by Kestrel? | Alias "corvid-med-latest"; Corvid moves to 3.3 on 15 Dec (E3, E4) | Dr. Farah Siddiqui | Dr. Helen Mathews | Not met |
| 10 | Build | P | D2 | Is the confidence threshold set by re-evaluation on Kestrel data? | Threshold changed to 0.72 on 25 Nov without re-evaluation (E3); AIP-2 | Dr. Farah Siddiqui | Dr. Helen Mathews | Not met |
| 11 | Build | P | D2 | Is the validated accuracy from Kestrel's own data? | Kestrel accuracy 93%, under-triage 2.1% (E1). Item 9's 96% is Corvid's | Dr. Farah Siddiqui | Dr. Helen Mathews | Partial |
| 12 | Build | P+N | D4 | Does the regression suite include the model evaluation set? | Regression green on 1.4.2, but the model evaluation set is excluded (E4, Victor Osei) | Kavya Nair | Victor Osei | Not met |
| 13 | Build | P | D2 | Is under-triage measured for mixed-language messages? | 6.8% under-triage flagged as R-17; no production measure (E1, E5) | Dr. Farah Siddiqui | Dr. Helen Mathews | Not met |
| 14 | Review | P | D1 | Is the clinical safety case signed by the Kestrel CSO? | Signed by Neha Sharma, not CSO (v0.9 item 11; F3) | Dr. Helen Mathews | Dr. Anjali Rao | Not met |
| 15 | Review | P | D3 | Is the DPIA current for all message types? | DPIA v1 covers referral letters only; addendum requested 2 Dec (E4) | Grace Liu | Owen Fletcher | Not met |
| 16 | Review | P | D1 | Is every safety-critical change reviewed by someone other than its author? | Imran approved 12 PRs he helped write; agents wrote about 70% of code (A5) | Imran Qureshi | Dr. Helen Mathews | Partial |
| 17 | Review | P | D4 | Is the penetration test passed with critical findings closed? | PT-2026-77: 1 critical, fixed; retest passed 30 Nov, signed R. Menon (v0.9 item 13) | Rahul Menon | Rahul Menon | Met |
| 18 | Review | P | D3 | Is the load test passed at 3× expected volume? | LT-1.4.2, p95 1.8 s at 3× pilot volume, 1 Dec (v0.9 item 15) | Tobias Grant | Kavya Nair | Met |
| 19 | Review | P | D5 | Is the accessibility review completed for patient-facing output? | Marked N/A as "backend service" (v0.9 item 16; F20) | Neha Sharma | Priyanka Das | Not met |
| 20 | Release | P | D5 | Is a human reviews every urgent case within the response target? | Urgent queue peaks at 25 cases between 7 and 10 pm; 2 nurses; about 75 min of work vs 30 min target (E4) | Priyanka Das | Dr. Helen Mathews | Not met |
| 21 | Release | P | D5 | Are triage nurses trained? | 11 of 29 (38%) completed the Beacon module (E8) | Priyanka Das | Priyanka Das | Not met |
| 22 | Release | P | D5 | Is the patient AI disclosure approved in English, Hindi and Marathi? | Draft, English only, with Legal (E8; PCS-3) | Marcus Bell | Owen Fletcher | Not met |
| 23 | Release | P | D5 | Do automated self-care replies meet grade 8 reading level? | Grade 11 on 200-message sample (E1; PCS-3) | Priyanka Das | Dr. Helen Mathews | Not met |
| 24 | Release | P | D5 | Is there a call-centre route for patients whose symptoms get worse after a self-care reply? | No scripts; reply lands in general inbox, 48 h response (E4, E8) | Sunil Bhat | Priyanka Das | Not met |
| 25 | Release | P | D3 | Is patient data retained for 8 years per RP-1? | triage-config.yaml sets retention to 365 days (E3; RP-1) | Grace Liu | Owen Fletcher | Not met |
| 26 | Release | P | D3 | Is audit logging enabled with the fields the DPO requires? | log_fields: message_id, category, confidence (E3). Whether this meets the DPO's requirement is not evidenced in the pack | Kavya Nair | Grace Liu | Partial |
| 27 | Release | P | D4 | Is the rollback runbook covering the model version, prompt version and manual triage? | Rehearsed for app container only, 20 Nov (E6) | Kavya Nair | Tobias Grant | Partial |
| 28 | Release | P | D4 | Do alerts reach people who can act out of hours? | Alerts post to #beacon-alerts (14 members); not on-call rota (E5) | Kavya Nair | Dr. Farah Siddiqui | Not met |
| 29 | Release | P | D2 | Does the drift monitor have a Kestrel baseline and an under-triage measure? | Baseline is Corvid's benchmark; no under-triage measure (E5) | Dr. Farah Siddiqui | Dr. Helen Mathews | Not met |
| 30 | Release | P | D1 | Is R-17 accepted in writing by the CMO or CSO with a review date? | Accepted by Neha Sharma, 5 Dec, recorded by Owen Fletcher 7 Dec (E4; AIP-2) | Dr. Helen Mathews | Dr. Anjali Rao | Not met |
| 31 | Release | P | D1 | Has the sponsor made a documented pilot decision? | Go/No-Go on 10 Dec, item 30 unticked | Dr. Anjali Rao | Board | Not met |
| 32 | Release | N | D4 | Is technical ownership handed over from Tobias Grant before his contract ends? | Contract ends 18 Dec; no handover recorded (v0.9 appendix) | Kavya Nair | Dr. Farah Siddiqui | Not met |
| 33 | Release | N | D5 | Is the network rollout plan current for nine sites on 11 Jan? | Rollout plan v2 exists (v0.9 item 28); not yet re-based on pilot evidence | Neha Sharma | Dr. Anjali Rao | Partial |
| 34 | Release | N | D1 | Is the board informed with accurate status? | Annual report p.14 announces 14 Dec pilot (v0.9 item 29; E4) | Marcus Bell | Dr. Anjali Rao | Partial |

---

## Part 5 · Readiness Statement

**To:** Dr. Anjali Rao, Chief Medical Officer and Programme Sponsor
**From:** [Ashwin], AI Technical Program Manager, Beacon
**Date:** 8 December 2026
**Re:** Beacon pilot decision for 14 December

**Decision: No-go for the pilot as currently configured. A reduced-scope go on 14 December is possible if the conditions below are met and evidenced by 12 December.**

The current v0.9 checklist is not a reliable basis for a go. It records 29 of 30 items as complete, but the evidence shows that several of those ticks are not supported. The most serious issues are that the clinical safety case was not signed by Kestrel's CSO, the confidence threshold was lowered from the validated 0.80 to 0.72 without re-evaluation, the model is on a floating alias that Corvid can change on 15 December, and the risk R-17 (mixed-language under-triage at 6.8%) was accepted by delivery rather than by the CMO or CSO as AIP-2 requires.

**What would make it a yes (reduced scope, pilot only):**
1. Revert the threshold to 0.80, or re-evaluate 0.72 on Kestrel data with CSO approval in writing.
2. Pin the model to corvid-med-3.2 and block the 15 Dec move until re-evaluated.
3. Switch automated replies off for the pilot, so that every message is nurse-reviewed.
4. Dr. Helen Mathews signs a Kestrel clinical safety case and hazard log that cover portal messages, mixed-language messages and nurse capacity.
5. The CMO or CSO re-accepts R-17 in writing, with a review date and a mixed-language sampling plan.
6. The DPO issues the DPIA addendum for portal messages.
7. Retention is changed to 8 years, per RP-1.
8. Rollback is rehearsed covering the model and prompt versions, and switch-off to manual triage.
9. Nurse capacity is confirmed for the urgent queue, and at least 90% of pilot triage nurses are trained.
10. The call-centre route for "getting worse" replies is in place.

**What must be true before 11 January (network rollout):** pilot data showing measured under-triage for mixed-language messages within an agreed bound; a Kestrel-baselined drift dashboard with an on-call alert route; reading level at grade 8 or below with Hindi and Marathi offered; the patient AI disclosure approved; a documented handover from Tobias Grant; and a sign-off from the CSO on the pilot evidence.

I recommend that you make the decision on 10 December at the Go/No-Go, and that the conditions above are tracked as named items with owners and dates.

---

## Part 6 · Assumptions

1. The five governance dimensions are my own choice, since the case pack does not define them. Check that your workbook template does not specify them.
2. Status is as of 8 December, as the case instructs, and I have not treated Corvid's 15 December change as having happened.
3. Owner assignments use only people listed in A3. Where a person's role is not an obvious fit, I used the closest accountable role.
4. I assumed that a reduced-scope pilot (auto-routing and auto-replies off) is a valid option for the sponsor. The case does not confirm that this is technically possible without a configuration change.
5. I assumed that the patient AI disclosure counts as an AIP-2 or PCS-3 requirement, and treated it as a release-gate item.
6. I have not verified the DPA's India data-residency claim, so it is marked Partial.
