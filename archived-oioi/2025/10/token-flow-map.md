---
description: >-
  Value-flow map of BGC × iBLOOMING from AS-IS to TO-BE on Base blockchain—defining PC/SP→ALPHA conversion, an append-only event model (hashed proofs), cash-out windows (KYC), and Pilot parameters aligned with the 5 Strategic Objectives.
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

---
title: "iBLOOMING × BGC — TOKENFLOW v1 (AS-IS → TO-BE)"  
version: "v1.0.0-draft"  
date: "2025-10-28"  
language: "EN"  
ties_to:  
  - [WHITEPAPER Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100) (Outline)
  - [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100) (PC/SP definitions)
  - [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100) (Strategic Objectives)
---

# 0. Glossary (aligned with UNDERSTANDING)
- **PC**: 100 PC = 1 USD (primary utility: BGC physical products).
- **SP**: meter of reward rights; basis for periodic USD payout.
- **ALPHA**: *settlement layer* converting PC/SP → rights; **ERC-20 interface, non-transferable; mint/burn only via AlphaController** (pre-iBC/iBTC).
- **iBC/iBTC**: on-chain tokens activated post simulation/validation.

# 1. AS-IS (brief)
## 1.1 BGC On-Ramp & PC
- Fiat in → PC increases → spend on physical products → PC decreases.
- Pain points: idle PC; limited utility.

## 1.2 BGC SP & Payout
- SP accrues from activities (LTS/RR/GR/…) → USD payout.
- Pain points: value leaks out of ecosystem; admin dependency.

## 1.3 iBLOOMING Revenue & Rewards
- Periodic fiat intake & distribution; limited real-time transparency.

# 2. TO-BE (conversion via ALPHA)
## 2.1 Unified Conversion
- PC→ALPHA: **100 PC : 1 ALPHA**; fee **0**; cooldown **0**.
- SP→ALPHA: **$1 : 1 ALPHA**; fee **0**; cooldown **0**.
- Default: ALPHA is used to **spend / access / stake** (internal).
- USD payout for specific BGC components remains **AS-IS** (see [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100)).

### 2.1.1 Cash-Out Windows (Pilot v1)
- Frequency: **4× per year** (quarterly).
- Window duration: **7 days** per window.
- Minimum payout: **$50**.
- Payout fee: **100 bps (1%)**.
- **KYC required**.
- Note: secondary, scheduled path for value to exit the ecosystem.

## 2.2 Partner Loop (phased)
- Curated/limited external spending access → keeps value circulating.

## 2.3 Demand Engine (iBLOOMING)
- Sinks & multipliers (classes, premium features, boosts) to absorb value.

# 3. Event Model (auditability)
Key event definitions + minimal fields:
- `JoinAffiliate`, `MintPC`, `SpendPC`, `EarnSP/AccrueLTS`, `CPContribution`, `PoolAccrual`, `ConvertToALPHA`, `Spend/Stake/Access`, `CashoutWindowOpened/Closed`, `PayoutUSD`.

# 4. Policy Placeholders (filled by Tokenomics)
- PC/SP → ALPHA ratios, conversion fees, weekly quotas, cooling-off.
- Anti-wash & anti-self-dealing rules; limited dispute & rollback policy.

# 5. Alignment Table (Solution ↔ GAP ↔ Objective ↔ KPI)
| Solution/Policy                 | GAP Closed | Objective                         | Primary KPI                 | Notes |
|---|---|---|---|---|
| PC/SP→ALPHA bridge             | Gap-1      | Revenue↑, Active users↑           | ARPU, MAU/WAU               | [fill] |
| Scheduled cash-out windows     | Gap-2      | Cost↓, Tax↓                       | Cost/tx, Tax incidents      | [fill] |
| Append-only ledger (events)    | Gap-4      | Cost↓                             | Ops MTTR, error rate        | [fill] |
| Rate-limit + anti-abuse        | Gap-3      | Cost↓, Affiliate↑                 | Ops cost, Retention         | [fill] |
| Sinks (classes/features/boost) | Gap-6      | Revenue↑                           | On-platform GMV             | [fill] |
| **Fairness metric**            | Gap-(ops)  | Affiliate↑, Active users↑         | **Reward Gini Coefficient** | [fill] |

# 6. Open Questions
- Cash-out thresholds & frequency? Q1 priority sinks? Initial rate-limit parameters?
