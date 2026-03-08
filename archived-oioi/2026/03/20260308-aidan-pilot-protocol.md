---
description: >-
  This pilot is designed to test whether AI& can safely and practically support physicians in selected non-autonomous clinical assistance tasks.
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# AI& Pilot Protocol

## 2–4 Week Controlled Pilot for a Physician-Controlled Clinical Assistance System

Version 0.1

- March 2026

---

## 1. Purpose of the Pilot

This pilot is designed to test whether AI& can safely and practically support physicians in selected non-autonomous clinical assistance tasks.

The pilot does not aim to prove that AI can replace physicians.

The pilot aims to answer a simpler and more useful question:

**Can AI& reduce documentation and communication friction while keeping physicians fully in control?**

---

## 2. Pilot Objectives

The pilot has four primary objectives:

### 2.1 Efficiency

Evaluate whether AI& reduces time spent on repetitive documentation and communication drafting.

### 2.2 Quality

Evaluate whether AI& improves consistency, clarity, and structure of outputs.

### 2.3 Safety

Evaluate whether AI& can operate without introducing unacceptable risk, misleading outputs, privacy concerns, or workflow disruption.

### 2.4 Trust and Adoption

Evaluate whether participating physicians find AI& useful, acceptable, and worth continuing after the pilot.

---

## 3. Pilot Duration

Recommended duration:

- minimum: 2 weeks
- ideal: 3 to 4 weeks

This duration is long enough to observe patterns, but short enough to remain controlled and easy to review.

---

## 4. Pilot Scope

The pilot must remain narrow and highly controlled.

### Recommended First Use Cases

Choose only 1 to 2 use cases for the pilot.

Preferred options:

1. SOAP note draft generation
2. Structured visit summary drafting
3. Patient education draft generation
4. Follow-up reminder drafting
5. Evidence summary for physician review

### Not Included in the Pilot

The pilot must not include:

- autonomous diagnosis
- autonomous triage
- medication recommendation
- emergency guidance
- unsupervised patient messaging
- direct patient-facing AI interaction
- unrestricted sharing of patient-linked data across physicians

---

## 5. Pilot Participants

### 5.1 Physician Participants

Recommended:

- 1 primary physician
- optional: 1 to 3 additional physicians after initial validation

### 5.2 Operational Participants

May include:

- project coordinator
- technical support person
- compliance or quality reviewer
- note-taker for feedback sessions

### 5.3 Patients

Patients are not system operators in this pilot.

If patient-linked data is involved, all handling must follow the defined data governance rules.

---

## 6. Entry Criteria Before Pilot Starts

The pilot may begin only if the following conditions are met:

### 6.1 Use Case Is Defined

One or two pilot tasks are selected clearly.

### 6.2 Workflow Is Agreed

All participants understand:

- when AI& may be used
- who reviews outputs
- what happens if outputs are poor
- what is logged

### 6.3 Safety Boundaries Are Agreed

All participants agree that:

- physicians remain the final decision-makers
- no AI output is final without physician review
- no autonomous patient communication is allowed

### 6.4 Templates Are Ready

At least basic templates exist for the selected use cases.

### 6.5 Logging Is Ready

The team can record:

- AI usage events
- review outcomes
- corrections
- incidents
- feedback

---

## 7. Pilot Workflow

### Step 1 – Select Eligible Case

A participating physician identifies a case appropriate for pilot use.

Examples:

- routine documentation case
- follow-up case
- patient education need
- non-emergency outpatient interaction

### Step 2 – Enter Structured Input

The physician provides structured input into AI&.

Possible inputs:

- chief complaint
- relevant history
- findings
- assessment points
- plan points
- communication goals

### Step 3 – Generate Draft

AI& generates a draft according to the selected workflow.

Examples:

- SOAP note draft
- education message draft
- follow-up summary draft

### Step 4 – Physician Review

The physician must review the draft before any use.

The physician may:

- approve
- edit
- reject
- regenerate

### Step 5 – Final Use

Only physician-approved output may be used in real workflow.

### Step 6 – Logging

The system or team records:

- type of task
- time used
- degree of correction needed
- whether output was useful
- whether any issue occurred

---

## 8. Case Selection Rules

The pilot should begin with cases that are relatively stable and low-risk.

### Good Early Cases

- routine follow-up visits
- straightforward documentation tasks
- patient education messages for familiar conditions
- structured note conversion tasks

### Poor Early Cases

- emergencies
- highly ambiguous complex cases
- medico-legal conflict situations
- emotionally sensitive or crisis communication
- cases requiring urgent escalation

The pilot should begin in calm water, not in the storm.

---

## 9. Review Rules

The pilot must define clear review rules.

### Mandatory Review Rule

Every AI-generated output must be reviewed by the responsible physician before use.

### Minimum Review Actions

The physician must check:

- factual alignment with the encounter
- clarity of wording
- completeness
- safety of advice or explanation
- appropriateness of tone

### Rejection Rule

If the output is misleading, incomplete, or confusing, it must not be used.

### Escalation Rule

If the output raises a safety concern, the incident must be logged and reviewed.

---

## 10. Logging Requirements

The pilot should collect both quantitative and qualitative data.

### 10.1 Quantitative Log

For each AI-assisted case, record:

- date
- physician name or identifier
- use case type
- draft generation time
- review time
- whether output was approved, edited, or rejected
- approximate level of correction required
- whether output was ultimately used

### 10.2 Qualitative Log

Record:

- physician comments
- moments of trust or distrust
- unclear phrasing
- missing information
- useful outputs
- workflow friction points

### 10.3 Incident Log

Record separately:

- misleading clinical wording
- privacy concern
- wrong context carryover
- source issue in evidence summary
- unauthorized access concern
- output that could have caused a near-miss

---

## 11. Success Metrics

The pilot should define success before it begins.

### 11.1 Efficiency Metrics

- average time saved per task
- reduction in repetitive writing effort
- faster preparation of communication drafts

### 11.2 Quality Metrics

- physician rating of clarity
- physician rating of usefulness
- consistency of structure
- completeness of documentation draft

### 11.3 Safety Metrics

- number of rejected outputs
- number of significant corrections
- number of incidents or near-misses
- number of privacy concerns

### 11.4 Adoption Metrics

- percentage of eligible cases where AI& was used
- repeat voluntary use by physicians
- willingness to continue after pilot

---

## 12. Simple Scoring Framework

A lightweight scoring framework may be used after each AI-assisted case.

### Per Case Score (1–5)

Physician rates:

1. usefulness
2. clarity
3. time saved
4. trustworthiness
5. amount of editing needed

Optional note:

- “Would I use this again for a similar case?”

---

## 13. Weekly Review Structure

### End of Week 1

Review:

- whether the chosen use case was correct
- whether outputs are generally usable
- whether templates need adjustment
- whether workflow is too heavy or too light

### End of Week 2

Review:

- patterns in editing
- trust levels
- repeated weaknesses
- safety observations

### End of Week 3–4

Review:

- whether to continue
- whether to revise scope
- whether to add one additional use case
- whether technical deeper build should proceed

---

## 14. Stop / Pause Criteria

The pilot must pause immediately if any of the following occurs:

- repeated misleading outputs
- privacy or confidentiality breach
- unauthorized access issue
- physician cannot review efficiently
- workflow becomes more burdensome than manual work
- team confidence drops due to unresolved safety concern

The goal of the pilot is not to force success.  
The goal is to learn safely.

---

## 15. Fallback Workflow

At any point, the physician must be able to continue manually.

Fallback rule:

**If AI& is unavailable, poor, uncertain, or unsafe, normal physician workflow continues without dependence on AI&.**

No clinical process should become blocked because AI& failed.

---

## 16. Pilot Deliverables

At the end of the pilot, the team should produce:

### 16.1 Pilot Summary

A short narrative of what was tested.

### 16.2 Metrics Summary

A simple report of:

- number of cases
- use case types
- efficiency observations
- quality observations
- safety observations

### 16.3 Template Revision Notes

A record of what should be improved.

### 16.4 Go / Revise / Stop Recommendation

A final recommendation:

- Go forward to next phase
- Revise and repeat pilot
- Stop due to risk or lack of value

---

## 17. Suggested Pilot Timeline

### Week 0 – Preparation

- choose use case
- define workflow
- finalize review rules
- prepare templates
- align pilot participants

### Week 1 – Controlled Initial Use

- first 5 to 10 cases
- close observation
- collect correction patterns

### Week 2 – Adjustment

- revise templates
- refine prompts
- improve review process

### Week 3 – Broader Controlled Use

- continue with improved workflow
- observe stability
- track repeat behavior

### Week 4 – Evaluation

- summarize findings
- assess trust, usefulness, and safety
- decide next step

---

## 18. Recommended First Decision After Pilot

At the end of the pilot, the team should answer one central question:

**Did AI& make physician work clearer and lighter without weakening safety, privacy, or control?**

If the answer is yes, the team may proceed to:

- technical architecture detail
- security architecture detail
- product requirement specification
- mock-up / UI-UX design
- second pilot design

If the answer is partially yes, the team should revise the pilot design and repeat.

If the answer is no, the project should pause and reconsider scope.

---

## 19. Final Principle

The pilot is successful not when AI looks impressive,  
but when physicians remain confident, careful, and more present with patients.

That is the standard.
