---
description: >-
  Value-flow map of BGC × iBLOOMING from AS-IS to TO-BE on Base—defining PC/SP→ALPHA conversion, an append-only event model (hashed proofs), cash-out windows (KYC), and Pilot v1 parameters aligned with the 5 Strategic Objectives.
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
- **PC** — 100 PC = 1 USD (primary utility: BGC physical products).
- **SP** — meter of reward rights; basis for periodic USD payout.
- **ALPHA** — *settlement layer* converting PC/SP → rights; **ERC-20 interface, non-transferable; mint/burn only via AlphaController** (pre-iBC/iBTC).
- **iBC / iBTC** — on-chain tokens activated post simulation/validation.
- **AA (Smart Account)** — account abstraction wallet mapped via Wallet Registry (post Web3 Login).

# 1. AS-IS (brief)
## 1.1 BGC On-Ramp & PC
- Fiat in → PC increases → spend on physical products → PC decreases.  
  *Pain points:* idle PC; limited utility.

## 1.2 BGC SP & Payout
- SP accrues from activities (LTS/RR/GR/…) → periodic USD payout.  
  *Pain points:* value leaks out of ecosystem; admin dependency.

## 1.3 iBLOOMING Revenue & Rewards
- Periodic fiat intake & distribution; limited real-time transparency.

# 2. TO-BE (conversion via ALPHA)
## 2.1 Unified Conversion (v1 Pilot)
- **PC→ALPHA:** 100 PC : 1 ALPHA; fee **0**; cooldown **0**.  
- **SP→ALPHA:** $1 : 1 ALPHA; fee **0**; cooldown **0**.  
- **Default:** ALPHA is used to **spend / access / stake** (internal).  
- **USD payout** for specific BGC components remains **AS-IS** (see UNDERSTANDING Doc).

### 2.1.1 Cash-Out Windows (v1 Pilot)
- **Frequency:** 4× per year (quarterly).  
- **Window length:** 7 days per window.  
- **Minimum payout:** $50.  
- **Payout fee:** 100 bps (1%).  
- **KYC required.**  
- **Note:** secondary, scheduled path for value to exit the ecosystem.

## 2.2 Partner Loop (phased)
Curated/limited external spending access → keeps value circulating within network.

## 2.3 Demand Engine (iBLOOMING)
Sinks & multipliers (classes, premium features, boosts) to absorb value on-platform.

# 3. Event Model (auditability)
**Event list (minimal final):**  
`JoinAffiliate`, `MintPC`, `SpendPC`, `EarnSP/AccrueLTS`, `CPContribution`, `PoolAccrual`, `ConvertToALPHA`, `Spend/Stake/Access`, `CashoutWindowOpened/Closed`, `PayoutUSD`.

**Minimal columns per event (schema):**
- `actor_id` (string) — internal user/entity id  
- `what` (enum) — event type (as above)  
- `amount` (decimal) — numeric value of the event  
- `unit` (string) — PC | SP | ALPHA | USD | count  
- `timestamp` (iso8601) — event time UTC  
- `ref_id` (string) — invoice/receipt/reference id  
- `channel` (string) — web/app/partner (optional)  
- `data_hash` (hex) — hash anchoring off-chain proof (file/url payload)

> *Append-only*: events are never edited/removed; corrections are appended as new events with `ref_id` linkage.

# 4. Policy & Parameters
**Principle:** behavior-based, non-speculative; policy changes are versioned.

## 4.1 Pilot v1 Values (synced with WHITEPAPER)
**Sponsor Gas & Caps (v1)**
- `sponsor_gas.enabled = true`  
- `actions_covered = [onboarding, convert_to_alpha, spend/access]`  
- `daily_cap_per_user ≈ $0.10`  
- `global_daily_budget ≈ $20`  
- `throttle_global = true` ; `pausable = true`

**Anti-Abuse & Sybil (v1)**
- `referral_cooldown_days = 1` ; `max_tier1_joins_per_actor_per_day = 10`  
- `require_unique_device = true` ; `duplicate_device_limit = 2`  
- `audit_sample_rate_pct = 5`  
- `wash_trade_zeroing = true` ; `penalty_cooling_off_days = 7`

**Settlement Rhythm (v1)**
- `accrual_frequency = daily` ; `points_settlement_frequency = weekly`  
- `pool_distribution = { GPS: semiannual, WEC: quarterly, MC: monthly, GMP: monthly, GEC: monthly }`

## 4.2 Placeholders to be tuned by Tokenomics
- PC/SP→ALPHA adjustment rules (post-pilot), weekly quotas, extended cooling-off.  
- Anti-wash/self-dealing refinements; limited dispute & rollback policy.

# 5. Compliance & Communications Guardrails
- **ALPHA = loyalty/rights**, **non-transferable**; free transfer disabled (controller-governed only).  
- **USD payout (AS-IS)** for specific BGC components continues unchanged.  
- **Cash-out windows = secondary & scheduled; KYC mandatory.**  
- **Legal sign-off is a hard gate** before any public **iBC/iBTC** phase.  
- Public messaging avoids investment language; disclose risks & usage boundaries.

# 6. Alignment Table (Solution ↔ GAP ↔ Objective ↔ KPI)
| Solution/Policy                 | GAP Closed | Objective                     | Primary KPI                  | Notes          |
|---|---|---|---|---|
| PC/SP→ALPHA bridge             | Gap-1      | Revenue↑, Active users↑       | ARPU, MAU/WAU                | (for simulation) |
| Scheduled cash-out windows     | Gap-2      | Cost↓, Tax↓                   | Cost/tx, Tax incidents       | (for simulation) |
| Append-only ledger (events)    | Gap-4      | Cost↓                         | Ops MTTR, Error rate         | (for simulation) |
| Rate-limit + anti-abuse        | Gap-3      | Cost↓, Affiliate↑             | Ops cost, Retention          | (for simulation) |
| Sinks (classes/features/boost) | Gap-6      | Revenue↑                      | On-platform GMV              | (for simulation) |
| **Fairness metric**            | Ops-gap    | Affiliate↑, Active users↑     | **Reward Gini Coefficient**  | (for simulation) |

# 7. Decision Log — v1 (Pilot)
- **Conversion:** `100 PC → 1 ALPHA` ; `$1 SP → 1 ALPHA` ; fee `0` ; cooldown `0`.  
- **Cash-Out Windows:** `4×/year` ; `7 days` ; `min $50` ; `fee 1%` ; `KYC = true`.  
- **Sponsor Gas Caps:** `≈$0.10 / user / day` ; `≈$20 / global / day` ; throttle/pause enabled.  
- **Anti-Abuse:** referral cooldown `1 day` ; `10` tier-1 joins/actor/day ; device rules ; sampling `5%` ; `zeroing + 7-day cooldown`.  
- **Settlement Rhythm:** accrual `daily` ; points settlement `weekly` ; pools as listed in §4.1.

# 8. Open Questions
- Cash-out thresholds/frequency for post-pilot; Q1/Q2 sink priorities; initial/adjusted rate-limit parameters; partner loop expansion gates.

