---
description: >-
  How BGC × iBLOOMING mirrors value flows to Base blockchain with an EventHub (append-only, hashed proofs) and structures rights/loyalty with ALPHA (non‑transferable, via AlphaController).
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# iBLOOMING × BGC — Whitepaper

_Integrating Loyalty, Value, and On‑Chain Transparency_

---

{% hint style="success" %}

- title: Whitepaper v1 • Executive 1‑Pager  
- version: v1.0.0-draft  
- date: 2025-10-28  
- language: EN  

{% endhint %}

---

## Impact on the 5 Strategic Objectives ([LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100#pdf-page-ijQlNvGkp9UTE2LR2Tjm-strategic-objectives-reaffirmed))
- **Revenue ↑**: on‑platform utility drives GMV & ARPU.
- **Cost ↓**: automated event ledger & rate limiting reduce operational/transaction costs.
- **Tax burden ↓**: compliant internal settlement lowers taxable events.
- **Affiliate ↑**: clear incentives & utilities improve activation/retention.
- **Active users ↑**: unified utility + Web3 Login reduces friction.

## Tokenomics (at a glance)
- **Principle**: behavior‑based (ALPHA simulation outcomes), not speculation.
- **Utilities & Sinks**: purchase products/classes/features, premium access, staking for boost; value absorption through usage fees & event‑based burn.
- **Conversion Policy**: PC/SP → **ALPHA rights** (default: spend/access/stake); scheduled **cash‑out windows**, with quotas and anti‑abuse.
- **Governance & Compliance**: staged governance; jurisdictional compliance notes (separate memo).

## Concise Roadmap
- 1a) ALPHA simulation → 2a) **Whitepaper v1** → 3a) **Tokenflow Map v1** → 4) Single Founder Sign‑Off (incl. Legal Gate) → 5) Pilot utilities iBC/iBTC → 6) Cross‑app expansion.
- 1b) **Web3 Login** plan → 2b) **Web3 Login** implementation → 3b) **Web3 Login** launch → 4) Single Founder Sign‑Off (incl. Legal Gate) → 5) Pilot utilities iBC/iBTC → 6) Cross‑app expansion.

## Decisions Requested (Founders)
**Approve Whitepaper v1** with three open parameters to be finalized at **Single Founder Sign‑Off (incl. Legal Gate)**: initial PC/SP→ALPHA conversion ratios, **cash‑out windows** policy, and **Q1 sinks** priorities.

---

{% hint style="success" %}

- title: WHITEPAPER v1 (Outline)  
- version: v1.0.0-draft  
- date: 2025-10-28  
- language: EN  
- single_language_rule: true  
- sources_of_truth:  
  - [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100) (business/marketing model)  
  - [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100#pdf-page-ijQlNvGkp9UTE2LR2Tjm-strategic-objectives-reaffirmed) (Strategic Objectives & guardrails)  

{% endhint %}

## 1. Executive Summary

BGC × iBLOOMING mirrors value flows operating since 2023 to Base via an **EventHub** (append‑only) that records key events with **hashed** off‑chain proofs. Rights/loyalty are structured with **ALPHA**—an ERC‑20 interface that is **non‑transferable**; **mint/burn** occur only via an **AlphaController**—so value by **default** circulates inside the ecosystem (spend/access/stake). **USD payouts** for specific BGC components **remain AS‑IS** per the [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100), while **cash‑out windows** schedule and throttle value flowing outward. The **Web3 Login + Wallet Registry → Smart Account (AA)** architecture sustains low‑friction UX with high auditability. After **24‑month data validation** and **legal sign‑off (hard gate)**, the public phase **iBC/iBTC** expands utilities across applications. This three‑act strategy targets **5 Strategic Objectives** (Revenue↑, Cost↓, Tax↓, Affiliate↑, Active Users↑) with measurable KPIs, including **Reward Gini Coefficient** for distributional fairness. Launches are gated by a **Single Founder Sign‑Off (incl. Legal Gate)** prior to deployment.

- Core problem set (six value‑flow gaps) → Solution (ALPHA → iBC/iBTC) mapped directly to the **5 Strategic Objectives**.

## 2. Problem Statement (Brief)
- Gap‑1: Limited outcome from PC/SP conversion bridge.
- Gap‑2: Interoperability & value leakage (out of ecosystem).
- Gap‑3: Admin dependency (manual operations).
- Gap‑4: Low real‑time transparency (limited audit trail).
- Gap‑5: High tax burden from fiat‑first processes.
- Gap‑6: BGC growth > iBLOOMING (imbalance).

Note: gap list refers to [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100) + [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100#pdf-page-ijQlNvGkp9UTE2LR2Tjm-strategic-objectives-reaffirmed); details are condensed in the [TOKENFLOW Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100).

## 3. Solution Overview (C → A → B)
### 3.1 Concept
- Reframe PC/SP as **tokenized rights** via the **ALPHA** settlement layer.
- Target: default utility inside the ecosystem; cash‑out as a secondary, controlled path.

### 3.2 Analogy
- An internal “conversion bridge”: PC/SP → **ALPHA rights** → spend/access/stake across apps.
- Value circulates longer inside; leakage outward decreases.

### 3.3 Design (High‑Level Implementation)
- Settlement Layer (ALPHA): conversion rules, event model, rate‑limit, and audit trail.  
  * **ALPHA** uses an ERC‑20 interface, is **non‑transferable**, and **mint/burn only via AlphaController**; free transfer is disabled (except *system‑governed flows*).  
  * **EventHub** acts as an *append‑only ledger* with **hashed proofs** anchoring off‑chain documents.
- Utility map: spend (products/services), access (features/classes), stake (commitment).
- Transparent dashboard (*append‑only ledger*) for claims/entitlements.
- Sponsor gas (active – Pilot v1): onboarding, convert_to_alpha, spend/access; per‑account daily cap ≈ **$0.10**; global daily cap ≈ **$20**; throttle/pause enabled.

## 4. Tokenomics (Framework)
### 4.1 Objectives ↔ KPIs
- Revenue↑ → KPI: ARPU/GMV on‑platform.
- Cost↓ → KPI: operational cost per 1,000 transactions.
- Tax burden↓ → KPI: fewer taxable events via compliant internal settlement.
- Affiliate↑ → KPI: number of active affiliates; 30/90‑day retention.
- Active users↑ → KPI: MAU/WAU across applications.
- Fairness → KPI: **Reward Gini Coefficient** (distribution inequality).

*Note: baselines & targets will be populated after the 24‑month data session.*

### 4.2 Supply & Emission
- Principle: behavior‑based (ALPHA simulation results), not speculative.
- Parameters: [PLACEHOLDER initial figures + periodic adjustment method].

### 4.3 Distribution
- Utility pools (spend/access/stake), affiliate incentives, ecosystem reserves.

### 4.4 Utilities & Sinks
- Utilities: product purchases, feature/class access, staking for boost.
- Sinks: usage fees, event‑based burn, premium fees.

### 4.5 Conversion Policy (PC/SP → ALPHA → iBC/iBTC)
- PC → ALPHA: **100 PC (= $1)** → **1 ALPHA**; fee **0 bps**; cooldown **0 days**.
- SP → ALPHA: **$1 SP** → **1 ALPHA**; fee **0 bps**; cooldown **0 days**.
- Default use of ALPHA: spend / access / stake inside the ecosystem.
- USD payout for certain BGC components remains **AS‑IS** (see UNDERSTANDING Doc).

#### 4.5.1 Cash‑Out Windows (Pilot v1)
- Frequency: **4× per year** (quarterly).
- Window duration: **7 days** per window.
- Minimum payout: **$50**.
- Payout fee: **100 bps (1%)**.
- **KYC required** for every payout.
- Note: cash‑out windows are the **secondary, scheduled** path for value leaving the ecosystem.

### 4.6 Governance & Risk
- Staged governance; rate‑limit; policy orchestration.
- Risk map: operational; market; compliance; reputation.
- **Anti‑Abuse & Sybil (Pilot v1)**: referral cooldown **1 day**; max **10** Tier‑1 joins per actor/day; `require_unique_device = true`; `duplicate_device_limit = 2`; audit sampling **5%**; penalties: `wash_trade_zeroing = true`, cooling_off **7 days**.

### 4.7 Compliance Notes
- **PC** is the proof of physical‑product transactions (MLM legal requirement).
- **Affiliate membership can only be purchased with fiat** (not with PC nor with tokens).
- **Legal sign‑off** is required before the public iBC/iBTC launch.
- **KYC is enforced** for payouts executed via cash‑out windows (Pilot v1).

## 5. Roadmap (High‑Level)
- ALPHA simulation → Whitepaper v1 → Tokenflow Map v1 → **Single Founder Sign‑Off (incl. Legal Gate)** → Pilot utilities iBC/iBTC → Cross‑app expansion.
- Web3 Login Plan → Web3 Login Implementation → Web3 Login Launch → **Single Founder Sign‑Off (incl. Legal Gate)** → Pilot utilities iBC/iBTC → Cross‑app expansion.

## 6. Data & Methodology
- 24‑month data sources; metric definitions; cleaning rules; reproducibility.
- Privacy standard: PII anonymization and dataset *manifest* for reproducibility.

## 7. Open Questions
- Cash‑out thresholds, initial conversion ratios, Q1 sinks priorities, prioritized use cases.

## Appendices
- Glossary; event table; compact architecture diagram.

### Initial Parameter List (v1 Pilot)
**Convert to ALPHA (v1)**
- `pc_to_alpha.ratio = 100 PC : 1 ALPHA; fee = 0 bps; cooldown = 0 days.`
- `sp_to_alpha.ratio = $1 : 1 ALPHA; fee = 0 bps; cooldown = 0 days.`

**Cash‑Out Windows (v1)**
- `windows_per_year = 4; window_length_days = 7; min_payout_usd = 50; payout_fee_bps = 100; kyc_required = true.`

**Sponsor Gas & Caps (v1)**
- `sponsor_gas.enabled = true; actions_covered = [onboarding, convert_to_alpha, spend/access];`
- `daily_cap_per_user ≈ $0.10; global_daily_budget ≈ $20; throttle_global = true; pausable = true.`

**Anti‑Abuse & Sybil (v1)**
- `referral_cooldown_days = 1; max_tier1_joins_per_actor_per_day = 10;`
- `require_unique_device = true; duplicate_device_limit = 2;`
- `audit_sample_rate_pct = 5; wash_trade_zeroing = true; penalty_cooling_off_days = 7.`

**Settlement Rhythm (v1)**
- `accrual_frequency = daily; points_settlement_frequency = weekly;`
- `pool_distribution: GPS = semiannual; WEC = quarterly; MC = monthly; GMP = monthly; GEC = monthly.`

### Event Model (Minimal Final)

**Event list (audit trail):**  
`JoinAffiliate`, `MintPC`, `SpendPC`, `EarnSP`/`AccrueLTS`, `CPContribution`, `PoolAccrual` (GPS/GMP/WEC/MC/GEC), `ConvertToALPHA`, `SpendAccess` / `Stake` / `Vote`, `CashoutWindowOpened`, `CashoutWindowClosed`, `PayoutUSD`.

**Minimal columns per event:**  
`actor`, `what`, `amount`, `unit`, `timestamp`, `refId`, `dataHash` (anchor to off‑chain proof).

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re‑tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
