---
description: >-
  It replaces the Founder’s Reading Guide as the current interpretation authority. It does not replace the original reports. The original reports remain preserved as first-version outputs.
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# SIMALPHA Findings, Evidence Limits, and Decision Framework

**Version:** 1.0  
**Prepared for:** BGC × iBLOOMING Founders and Core Team  
**Prepared by:** Prof. NOTA  
**Simulator owner and principal implementer:** Fabio Kalandra (“Uncle Kal”)  
**Date:** 5 August 2026  
**Status:** Active decision-support reference

---

## 1. Purpose

This document explains:

- what SIMALPHA is;
- what it successfully does;
- what its current data and reports support;
- what they do not support;
- how founders should read the first simulation results;
- what must be corrected before future policy approval.

It replaces the Founder’s Reading Guide as the current interpretation authority.

It does not replace the original reports. The original reports remain preserved as first-version outputs.

---

## 2. What SIMALPHA Is

SIMALPHA is an internal decision-support web application.

Its workflow allows a permitted user to:

1. upload or select a versioned business-data snapshot;
2. define or select a policy scenario;
3. run a deterministic simulation;
4. review money, ALPHA, distribution, and risk outputs;
5. compare completed runs;
6. export reports for founder discussion.

SIMALPHA is not:

- a public token;
- a smart-contract deployment;
- a wallet;
- a cash-out system;
- a treasury;
- an exchange;
- a legal or tax engine;
- an audited accounting system.

---

## 3. What Has Been Successfully Built

The working MVP includes:

- data-snapshot versioning;
- import and validation;
- scenario storage;
- deterministic execution;
- result references;
- duplicate-run governance;
- comparison;
- data-versus-assumption separation;
- report generation;
- PDF export;
- founder-oriented summaries.

This is a substantial technical deliverable.

The application is suitable for structured internal policy exploration.

---

## 4. Current Dataset

### 4.1 Profile

The current compiled dataset contains:

- 236 records;
- 25 monthly periods;
- April 2024–April 2026;
- BGC and iBLOOMING records;
- monthly-tier aggregation.

Examples of synthetic record keys include combinations such as:

- BGC + month + membership tier;
- iBLOOMING + month + membership tier.

These are not persistent individual member identities.

### 4.2 Consequence

The dataset can support:

- monthly aggregate analysis;
- source-system comparison;
- tier comparison;
- issuance and cash-release sensitivity;
- cashflow-proxy discussion.

It cannot validly support:

- real active-user count;
- new-user count;
- retained-user count;
- churn;
- member-level Gini;
- real top earners;
- P95 or P99 by person;
- member-level referral behaviour;
- individual cash-out behaviour;
- longitudinal cross-application activity.

Any metric derived by treating each aggregate record as a person must be removed or relabeled.

---

## 5. Aggregate Data Snapshot

| Metric | BGC | iBLOOMING | Combined |
|---|---:|---:|---:|
| Cash in | $4,034,038.00 | $21,117.00 | $4,055,155.00 |
| Recognized-revenue field | $4,034,038.00 | $6,335.10 | $4,040,373.10 |
| Gross-margin field | $4,034,038.00 | $6,335.10 | $4,040,373.10 |
| Internal credit or sink spend | $567,234.00 | $0.00 | $567,234.00 |
| PC volume | 403,403,617 | 0 | 403,403,617 |
| SP reward basis | 2,823,835 | 0 | 2,823,835 |
| Global/direct reward | $411,385.60 | $1,429.46 | $412,815.06 |
| Pool reward | $508,288.57 | $950.52 | $509,239.09 |
| Historical cash-out | $546,506.11 | $25,715.08 | $572,221.19 |

### 5.1 Important Interpretation

The dataset labels BGC cash-in as:

- cash in;
- recognized revenue;
- gross margin.

These labels must not be interpreted as audited revenue, gross margin, profit, or free cash.

The available data does not deduct:

- physical-product cost;
- inventory;
- shipping;
- fulfillment;
- operating expense;
- outstanding PC;
- reward liability;
- pool liability;
- reserve restrictions.

---

## 6. First Scenario Results

| Scenario | ALPHA Issued | ALPHA Used | Modeled ALPHA Cash Release | ALPHA Held | Reported Net Cash Proxy | Reported Pressure |
|---|---:|---:|---:|---:|---:|---:|
| Baseline | 253,462.58 | 47,250.55 | 70,138.55 | 136,073.48 | $3,970,234.55 | 0.25× |
| Conservative | 185,770.06 | 35,690.04 | 37,558.99 | 112,521.03 | $4,002,814.11 | 0.24× |
| Growth | 304,155.10 | 56,173.06 | 85,512.27 | 162,469.77 | $3,954,860.83 | 0.25× |
| Stress | 128,168.01 | 24,016.75 | 29,569.66 | 74,581.59 | $4,010,803.44 | 0.24× |

---

## 7. Correct Scenario Interpretation

### 7.1 Baseline

An initial policy reference using the current model assumptions.

It is not a validated reproduction of the complete historical economy.

### 7.2 Conservative

A lower-issuance and lower-cash-release policy.

It demonstrates sensitivity to tighter parameters.

### 7.3 Growth

A higher-issuance and higher-cash-release policy.

It does not demonstrate real revenue or user growth because no independent future-growth evidence is included.

### 7.4 Stress

The name is misleading.

The scenario:

- uses the same imported historical business data;
- has no meaningful future shock;
- mainly lowers issuance;
- tightens caps;
- restricts cash-out frequency;
- raises cash-out friction.

Correct interpretation:

> **Treasury Preservation / Restrictive Policy Scenario**

It retains the most modeled cash because the model releases the least cash.

That is a parameter consequence, not an independent finding that the policy is best.

---

## 8. Report Corrections

### 8.1 Verdict Labels

Replace:

- Ready;
- Needs Review;
- Do Not Use.

With:

| New Label | Meaning |
|---|---|
| Preliminary Pass | Run completed and did not cross current model thresholds |
| Material Review Required | One or more model or evidence risks require review |
| Model-Detected Risk | Current assumptions create a model threshold breach |
| Insufficient Evidence | No responsible implementation conclusion can be made |

All four current scenarios should carry:

> **Preliminary Pass — Insufficient Evidence for Implementation Approval**

### 8.2 ALPHA Definition

Replace:

> ALPHA is the practice version of iBC/iBTC.

With:

> **ALPHA is a neutral simulation unit used to test alternative representations of rights, rewards, access, or internal value. It does not imply that a public token will be launched.**

### 8.3 Cash-Out Label

Replace:

> Actual Payout Out

With:

> **Modeled ALPHA Cash Release**

Historical cash-out is a different data field and must be shown separately.

### 8.4 “PC and SP Go In, ALPHA Comes Out”

This statement must be removed.

PC and SP represent different rights.

Any future conversion must define:

- which original right is extinguished;
- whether conversion is reversible;
- whether product or payout rights remain;
- whether the conversion creates a new liability.

### 8.5 Net Cash

Replace:

> Net Cash

With:

> **Incomplete Net Cash Proxy**

Until the model includes:

- rewards payable;
- pools;
- fulfillment;
- COGS;
- OpEx;
- reserve;
- PC liability;
- intercompany movements.

### 8.6 User and Fairness Metrics

Remove or relabel:

- Active User Count;
- New Active User Count;
- Retained Active User Count;
- Affiliate Retention;
- Top 10% Member Share;
- member-level Gini;
- member-level P95/P99.

Suggested label where retained:

> **Aggregate Segment Concentration**

---

## 9. Reconciliation Gaps

The current source data contains:

- pool reward fields;
- historical cash-out fields;
- internal credit spend.

The first reports show:

- pool funding owed = zero;
- much lower modeled ALPHA cash release;
- fulfillment cost = zero.

This does not automatically prove a software bug.

It proves that field mapping, liability treatment, or policy treatment is incomplete or undocumented.

The next technical review should trace:

```text
source field
→ import mapping
→ model variable
→ formula
→ report line
→ founder interpretation
```

---

## 10. What SIMALPHA Can Support Today

SIMALPHA can support decisions such as:

- whether a scenario issues more or less ALPHA;
- whether cash-release restrictions retain more modeled cash;
- whether report outputs change consistently;
- whether assumptions are visible;
- whether a proposed rule should be studied further.

It can support the conclusion:

> **Do not approve current tokenization.**

It cannot support the conclusion:

> **This system is economically safe and ready for token implementation.**

---

## 11. Evidence Gates

### Gate 0 — Data and Model Integrity

Required:

- versioned input;
- documented mapping;
- reproducible results;
- no unsupported member-level metrics.

### Gate 1 — Historical Replay

Required:

- reproduce historical observed totals;
- separate actual from modeled values;
- explain every material difference.

### Gate 2 — Economic and Accounting Reconstruction

Required:

- PC obligations;
- reward obligations;
- pool obligations;
- COGS;
- fulfillment;
- OpEx;
- reserve;
- intercompany transfers.

### Gate 3 — Product-Demand Evidence

Required:

- independent product buyers;
- repeat purchases;
- product usage;
- margin;
- retention;
- product-market evidence.

### Gate 4 — Policy Simulation

Only after Gates 0–3:

- caps;
- fees;
- internal access;
- entitlement policy;
- cash-release rules.

### Gate 5 — Tokenization Comparison

Compare:

- conventional database;
- EventHub or evidence anchoring;
- non-transferable credential;
- internal rights;
- public token.

### Gate 6 — Legal, Tax, Technical, and Founder Approval

No token implementation before written approval.

---

## 12. Founder Use Guide

### Step 1 — Read the Evidence Status

Before reading numbers, confirm whether the report says:

- actual;
- modeled;
- assumed;
- missing;
- preliminary.

### Step 2 — Ask What Changed

A scenario is useful only when the changed rules are clear.

### Step 3 — Ask What the Output Excludes

Always check:

- obligations;
- costs;
- reserve;
- rights;
- user impact.

### Step 4 — Compare With a No-Token Control

Every future token-related simulation must include:

> **No-token / conventional-system control**

### Step 5 — Record a Decision

A simulator result should lead to one of:

- reject;
- study further;
- request evidence;
- approve limited pilot;
- approve implementation.

“Green” is not automatically approval.

---

## 13. Operator Workflow

1. Select a versioned dataset.
2. Confirm source and mapping notes.
3. Select a scenario.
4. review changed parameters;
5. confirm actual-versus-modeled flags;
6. run the model;
7. review warnings and missing evidence;
8. compare with a no-token control;
9. export the result;
10. attach a Decision Note;
11. obtain named approval before changing any live system.

---

## 14. Remediation Backlog

### Priority 0 — Before Further Founder Reliance

- change verdict labels;
- add Insufficient Evidence;
- relabel cash release;
- relabel net cash;
- remove invalid user metrics;
- separate historical cash-out from modeled release;
- document aggregate-data limitations;
- rename Stress interpretation.

### Priority 1 — Model Integrity

- reconcile pool fields;
- reconcile partner payouts;
- reconcile fulfillment;
- trace internal credit;
- document formula mapping;
- add no-token control.

### Priority 2 — Historical Replay

- calibrate against observed totals;
- show differences;
- explain opening and closing balances.

### Priority 3 — Product-Led Simulation

Add support for:

- independent product demand;
- direct product sale;
- repeat purchase;
- product margin;
- digital access usage;
- product-passport adoption;
- conventional-versus-Web3 cost.

### Priority 4 — True Stress Tests

Apply:

- new-join decline;
- product-revenue decline;
- cash-out increase;
- PC redemption increase;
- COGS increase;
- OpEx increase;
- reserve limitation.

---

## 15. Final Status

> **SIMALPHA is a working internal decision-support MVP with preliminary policy-sensitivity outputs. It is not yet a calibrated historical economic replay, a validated sustainability model, or a basis for final token parameters.**

This is not a failure.

It is the correct status for a first serious simulation product.

The next value of SIMALPHA is to support Product-Led evidence, no-token controls, and disciplined founder decisions.

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
