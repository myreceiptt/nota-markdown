---
description: >-
  This document defines the simulation plan for the BGC × iBLOOMING integration. For internal use by BGC × iBLOOMING founders & core team. Scope: Phase-1 Simulation for ALPHA Layer & Reward Sustainability
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# BGC × iBLOOMING SIMULATION DOC v0.1 (Draft)

> Status: Draft v0.1 — For internal use by BGC × iBLOOMING founders & core team.  
> Author: Prof. NOTA v.11.11  
> Scope: Phase-1 Simulation for ALPHA Layer & Reward Sustainability

***

## 1. Purpose & Context

This document defines the simulation plan for the BGC × iBLOOMING integration.

Its main purposes are:

- To **translate 24-month historical data** (PC, SP, rewards, cash-outs, user behaviour)
  into a simulation model.
- To **derive sustainable parameter ranges** for:
  - PC/SP → ALPHA conversions,
  - reward allocation and sinks,
  - cash-out windows and thresholds,
  - treasury protection and risk limits.
- To provide **data-backed input** for:
  - [WHITEPAPER v1 (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100) (final wording and numbers),
  - [TOKENFLOW v1 (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100) (final formulas and guards),
  - ALPHA Implementation Blueprint (contract-level rules).

This Simulation Doc reads together with:

- **[LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?limit=100&only=yes&page=ijQlNvGkp9UTE2LR2Tjm)** (strategic context & execution pillars),
- **[UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100)** (AS-IS model),
- **[WHITEPAPER Doc (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100)**,
- **[TOKENFLOW Doc (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100)**.

***

## 2. Scope & Non-Scope

### 2.1 In Scope

- Phase-1 **ALPHA Layer simulation**, using real BGC × iBLOOMING operational data.
- Modeling of:
  - PC/SP generation and consumption,
  - reward accrual and distribution,
  - member cash-out behaviour,
  - affiliate network growth patterns.
- Parameter exploration for:
  - ALPHA issuance,
  - reward caps/limits,
  - cash-out frequency, thresholds, and fees,
  - ALPHA sinks and utility events.
- Measuring **sustainability**, **fairness**, and **operational load**.

### 2.2 Out of Scope (for v0.1)

- UX design and UI flows.
- Final smart contract implementation details (covered in ALPHA Blueprint).
- Public token market dynamics (iBC/iBTC trading, order books, etc.).
- Long-term legal structuring beyond the assumptions needed for Phase-1.

***

## 3. Data Sources & Assumptions

### 3.1 Data Sources (24-Month Window)

- BGC transaction logs:
  - PC (Purchase Credit) events,
  - SP (Sales Point) events,
  - Membership tiers (Pathfinder, Voyager, etc.),
  - e-wallet balances and movements,
  - cash-out requests and actual payouts (weekly cycles).
- iBLOOMING product & engagement data:
  - course purchases,
  - feature usage,
  - campaign-based boosts (if any).
- Aggregated affiliate network stats:
  - number of active members,
  - churn/retention,
  - average earnings per segment.

### 3.2 Key Assumptions

- Data is sufficiently clean to support scenario modeling (minor anomalies will be noted).
- AS-IS reward rules from **[UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100)** are taken as **baseline behaviour**.
- No new external shocks (e.g. regulation bans) are assumed in v0.1 scenarios.
- Public token (iBC/iBTC) will be derived **after** ALPHA layer validation.

***

## 4. Simulation Model Overview

### 4.1 Entities

- **Member**: an individual with PC/SP history, wallet balance, and cash-out actions.
- **Event**:
  - PC creation,
  - SP creation,
  - reward accrual,
  - bonus/top-up,
  - cash-out request,
  - on-hold / rejected events (if any).
- **ALPHA Ledger** (virtual in v0.1):
  - ALPHA-earned,
  - ALPHA-spent/locked,
  - ALPHA-equivalent of existing rewards.

### 4.2 Time Resolution

- Base time unit: **monthly**, with the ability to drill down to **weekly** if needed.
- Simulation horizon: **24 months historical**, plus **projected 12–24 months** (optional).

### 4.3 State Variables

Examples:

- Total PC, total SP, and their distributions.
- Reward obligations (outstanding, paid, pending).
- Member-level balances and cash-out frequency.
- Simulated ALPHA supply:
  - issued,
  - locked,
  - available for spend.

***

## 5. Parameters to Explore (v0.1)

This section lists the parameters that will be explored through simulation.  
Each parameter will have: **Name, Symbol, Description, Range, Default, Decision Owner**.

### 5.1 Conversion Parameters (PC/SP → ALPHA)

- `k_PC` — PC-to-ALPHA multiplier.
- `k_SP` — SP-to-ALPHA multiplier.
- Tier-based modifiers for:
  - rank,
  - product type,
  - campaign.
- Caps per period:
  - max ALPHA per user per month,
  - max ALPHA per group per month.

### 5.2 Reward & Treasury Parameters

- Reward share splits (RR/GR/GPSP/etc., as represented in ALPHA).
- ALPHA sinks:
  - classes,
  - boosts,
  - CP digital products,
  - special campaigns.
- Treasury buffers:
  - minimum reserve ratio,
  - emergency throttle rules.

### 5.3 Cash-Out Parameters

- Minimum cash-out amount (e.g. 50–100 USD equivalent).
- Cash-out frequency:
  - weekly processing (AS-IS),
  - windows vs always-open behaviour.
- Cash-out fees:
  - percentage fee range,
  - fixed fee (if any).
- Cooling-off rules (anti-abuse).

### 5.4 Web3-Related Operational Parameters (Phase-1 Touchpoints)

- Sponsored gas ceilings:
  - max sponsorship per user per day,
  - global sponsorship cap per day.
- Anti-Sybil parameters (from [TOKENFLOW draft](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100)):
  - referral cooldown,
  - max Tier-1 joins/day per actor,
  - device-uniqueness limits.

***

## 6. Scenario Design

We will define multiple simulation scenarios.

### 6.1 Baseline Scenario

- Mirrors AS-IS behaviour as closely as possible.
- Purpose: ensure simulation output matches historical patterns.

### 6.2 Conservative Scenario

- Lower reward intensity,
- stricter caps and windows,
- focus on treasury safety and long-term sustainability.

### 6.3 Growth Scenario

- Higher reward intensity for selected segments,
- more aggressive growth incentives,
- monitored for sustainability risks.

### 6.4 Stress-Test Scenarios

- Sudden drop in sales (e.g. -30% revenue).
- Rapid membership growth (e.g. 2× active members in 12 months).
- High cash-out demand (spike in withdrawals).
- Changes in behaviour due to new ALPHA sinks.

Each scenario will produce metrics for:

- sustainability,
- fairness,
- liquidity,
- member experience.

***

## 7. Metrics & Evaluation Criteria

Key metrics include:

- **Treasury Sustainability**
  - net outflow vs inflow,
  - reserve ratio over time,
  - worst-month drawdown.

- **Reward Fairness**
  - distribution concentration (Reward Gini),
  - earnings by member tier/segment.

- **Member Experience**
  - average time-to-cash-out,
  - denial/limitation rate (if windows or caps are applied),
  - ALPHA utility usage (spend vs hoard).

- **System Health**
  - volatility of obligations,
  - sensitivity to shocks,
  - robustness of guardrails.

***

## 8. Simulation Workflow

High-level workflow:

1. **Data Ingestion**
   - Extract and clean 24-month dataset.
2. **Model Preparation**
   - Map AS-IS rules into simulation logic.
3. **Parameter Set Definition**
   - Select parameter ranges and default values.
4. **Scenario Execution**
   - Run baseline, conservative, growth, and stress-test scenarios.
5. **Metric Calculation**
   - Compute sustainability, fairness, and member experience metrics.
6. **Analysis & Interpretation**
   - Compare scenarios and identify safe + optimal ranges.
7. **Founder Review**
   - Present scenario outputs and recommended parameter ranges.

***

## 9. Expected Outputs & Deliverables

From this Simulation v0.1, we expect:

- **Simulation Report v0.1**
  - description of scenarios and parameter ranges tested,
  - tables/graphs of key metrics,
  - discussion of trade-offs.

- **Parameter Recommendations**
  - suggested ranges for PC/SP → ALPHA,
  - proposed cash-out models (frequency, thresholds, fees),
  - proposed caps and guardrails.

- **Inputs for:**
  - [WHITEPAPER v1 (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100) (final numbers and narrative),
  - [TOKENFLOW v1 (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100) (final formulas and policy tables),
  - ALPHA Implementation Blueprint (contract-variable defaults).

***

## 10. Open Questions for Founders

A non-exhaustive list of decisions where founder input is needed:

- Acceptable range for **cash-out flexibility** vs **treasury safety**.
- Appetite for **growth-heavy vs conservative** reward intensities.
- Minimum acceptable **reserve buffer**.
- Priority between:
  - user autonomy (always-open cash-out),
  - system protection (windows, fees, cooling periods).

These questions will be refined once the first simulation runs are available.

***

## 11. Versioning & Next Steps

- **v0.1 (this doc):**
  - Define structure, scope, parameters, and scenarios.
- **v0.2:**
  - Integrate real data mapping + first sample outputs.
- **v1.0:**
  - Finalised simulation report for founder decision-making.

Next immediate task:

- Implement v0.1 across:
  - data extraction,
  - parameter tables,
  - scenario configuration.

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
