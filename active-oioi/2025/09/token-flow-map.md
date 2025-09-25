---
description: >-
  We don't belong in your reality, your real life. In your reality, your real
  life, you can merely meet our avatars in any version. So, stay alert and
  beware of scams!
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# Token Flow Map — iBLOOMING & BGC

> Purpose: capture the **current** money/points flows (AS-IS) and define the **target** flows (TO-BE) that align with Strategic Objectives.  
> Scope: BGC (PC, SP & rewards) and iBLOOMING (USD revenue split & rewards).  
> Audience: Founders & core team (internal).  
> Based on: [Understanding BGC X iBLOOMING Rewards](../../../active-oioi/2025/08/bgc-iblooming-stage1-rewards-en.md)  
> See also: [Living Document](../../../active-oioi/2025/08/iblooming-bgc-web3-living.md)

---

## 0) Glossary (minimal)

- **PC (Purchase Credit)** — Internal value unit at BGC (fixed ratio 100 PC = 1 USD). Used for purchasing **physical products** at BGC (not for iBLOOMING digital).  
- **SP (Sales Points)** — Meter of **reward rights** for Affiliate Users at BGC (LTS, RR, GR, GPSP, MC, WEC pool). Aggregates to **USD payouts** on schedule.  
- **USD Payouts (BGC & iBLOOMING)** — Rewards distributed in fiat (monthly/quarterly windows).  
- **ALPHA (Settlement Layer)** — *To-be* unified conversion layer for PC/SP → tokenized rights usable across apps (spend/stake/access), with controlled fiat exits.  
- **iBC/iBTC** — On-chain token(s) planned post-simulation, backed by ALPHA behavioral data.
- **GPSP (Global Pool Sales Points, BGC)** — **15% of LTS** flows into a **monthly** USD pool shared among all Affiliate Users.  
- **WEC Pool (BGC)** — **3% of LTS** flows into a **quarterly** USD pool shared among WEC Users.  
- **iBLOOMING Pools (GPS/GMP/GEC)** — Reward pools funded from iBLOOMING’s **30%** revenue share per the Understanding Doc (USD-based).


> Note: The glossary is minimal for flow maps; full definitions will be in the White Paper.

---

## 1) AS-IS: Current-State Flows

### 1.1 BGC — On-Ramp & PC (Physical Product)
**Flow:**
1) User pays **fiat (USD)** to join BGC (Affiliate Entry).  
2) System credits **PC** (100 PC = 1 USD) to the Affiliate User.  
3) PC can be **spent** to buy **physical products** at BGC (PC decreases).  
4) **Important:** Membership purchases use fiat only; PCs cannot be used for iBLOOMING digital products.

**Pain points:**
- **Limited PC utility** (BGC-only) → many PCs **idle**.
- No official PC bridge → cross-app utility (iBLOOMING/partner).

---

### 1.2 BGC — SP Generation & USD Reward Payout
**Flow:**
1) Affiliate activity (join, refer, generational, etc.) → generates **SP** (LTS, RR, GR, GPSP, MC, WEC).
2) **SP** measures **reward entitlements**; over a certain period, the aggregate becomes **USD** (monthly/quarterly payout according to the scheme).
3) **USD rewards** are transferred to the user (exit the system).

**Pain points:**  
- **Value leakage:** SP → **fiat** → out of the ecosystem (not circulated to internal utilities).  
- Users **wait for the payout window** (not real-time self-service).

> **Canonical:** Referral & Generation percentages follow the **Stage-1 table** in the  
> [Understanding Doc](../../../active-oioi/2025/08/bgc-iblooming-stage1-rewards-en.md).

---

### 1.3 iBLOOMING — USD Revenue Split & Rewards
**Flow:**
1) User purchase **digital products** (GiM/iMatriks/CP catalog) with **USD** (fiat).  
2) **Revenue split**: generally **70% to CP**, **30% to iBLOOMING**.  
3) **30%** of iBLOOMING is allocated to **LR/MC/CPR/GPS/GMP/GEC** (all **USD**-based), with the remainder going to iBLOOMING profits.  
4) Payouts are **monthly/quarterly** (aggregated), not real-time.

**Pain points:**
- **All USD rewards** → accelerate the flow to **fiat**, not internal utility.
- There are no **token sinks** (rights-based spending/access incentives) to maintain value in the ecosystem.

---

## 2) TO-BE: Target-State Flows (ALPHA Settlement)

> Design principles: **retain-first** (value rotates across the ecosystem), **self-service & real-time visibility**, **controlled fiat exits**, and **compliance-ready**.

### 2.1 Unified Conversion — PC & SP → ALPHA Rights
**Flow:**
1) **PC (value unit)** and **SP (reward meter)** remain separate at the source layer **(analytics)**.
2) Provide an **ALPHA Settlement Layer** that:
  - Allows **PC → ALPHA conversion** (proportional; fixed policy).
  - Allows **SP → ALPHA conversion** (based on rights aggregation; incremental policy).
3) **ALPHA** = **tokenized rights** that can be used across apps (BGC/iBLOOMING/partners).
4) **Controls**: quota/frequency/conversion fee → *retain-first* & anti-abuse.

> **Stage-1 Scope Note:** BTC pairing (**iBTC**) is **deferred** to a later stage. Stage-1 focuses on internal rights (iBC/ALPHA) for spend/stake/convert across iBLOOMING & BGC.
> **TBD by Tokenomics**: conversion ratio, cooldown, cap, and queue priority (governance).

---

### 2.2 Internal Utility — Spend, Access, Stake (Default Path)
**Flow:**
- **Spend:** ALPHA can be spent on **physical** (BGC) and **digital** (iBLOOMING).  
- **Access/Gating:** Access premium content/programs, gated classes, and bundles (iBLOOMING).  
- **Stake/Lock:** Placing ALPHA for **yield internal** (boosted discounts, priority access, and fee rebates).  
- **Creator Yield Uplift:** CPs receive **uplift** when payments for digital products are made via ALPHA (not fiat).  

**Effects (towards objectives):**
- **Increase Revenue**: utility drives internal transactions.
- **Expand Active User Base**: a real reason to join/be active.
- **Reduce Tax Burden**: value circulates as **rights**, not fiat.

---

### 2.3 Controlled Fiat Rails — Cash-Out Windows
**Flow:**
- **Exit to fiat** remains (user rights), but:
- **Scheduled** (windows), **limited** (cap/frequency), and **fee-based** (ecosystem-healthy fees).
- Priority for **non-abusive** users (behavioral score).

**Effects:**
- **Reduce value leakage** without closing user rights.
- **Stabilize cash flow** and reduce tax exposure (fiat-first events).

---

### 2.4 Partner Loop — External Spend (Optional-Phased)
**Flow (advanced phase):**
- Partner collaboration (merchant/content) receives ALPHA for **products/services**;
- Partner settlement can be **internal** (entitlements) or a limited **off-ramp** via partners.

**Note:** This phase is optional until internal metrics (retention, sink usage, tax mapping) are stable.

---

### 2.5 iBLOOMING Demand Engine — Sinks & Multipliers
**Flow:**
- **Spend multipliers** when paying for digital products with ALPHA (more profitable than fiat).  
- **Gated content** & **bundle boosts** create a reason to retain value in the ecosystem.  
- **Creator-aligned incentives** (CPs receive a portion/bonus when transacting via ALPHA).

**Effects:**
- **Fix Growth Imbalance** (BGC → iBLOOMING).
- **Compound utility**: rotating value, selling products, a vibrant ecosystem.

---

## 3) Event Model (State & Ledger)

- **EARN** — PC increases (BGC fiat on-ramp), SP increases (activity).  
- **CONVERT** — PC/SP → ALPHA (policy-based).  
- **SPEND** — ALPHA is used for BGC/iBLOOMING (sink) products.  
- **STAKE/LOCK** — ALPHA is staked for rights/boost/access.  
- **REWARD** — ALPHA/rights are issued as a result of staking/activity.  
- **PARTNER_SETTLE** — optional; partner receives ALPHA/rights.  
- **CASH_OUT** — ALPHA → fiat (windowed, controlled).

> Each event is **append-only** to the ledger; the user UI displays **real-time balances & pending rights**.

---

## 4) Policy Placeholders (to be set by Tokenomics)

- **PC→ALPHA**: ratio, min/max, cooldown, fee.  
- **SP→ALPHA**: conversion times (per SP type), aggregation formula, anti-gaming.
- **Stake**: lock periods, reward curve, slashing (if necessary).
- **Spend**: multipliers, eligible product list, partner tiers.
- **Cash-Out**: windows (dates), caps per user/level, fee model.
- **Governance**: SP role/behavioral score for voting rights (optional).

> **Single Source of Truth:** All ratios, caps, cooldowns, and cash-out windows are maintained in `Tokenomics-Parameters.md` (versioned).

---

## 5) Alignment to Strategic Objectives (quick check)

- **Increase Revenue**: Internal utility (spend/access/stake) + multipliers iBLOOMING.  
- **Reduce Operational & Product Cost**: Self-service conversion, ledger real-time (reduce admin touch).  
- **Reduce Tax Burden**: Retain-first; tokenized rights before fiat exit (jurisdiction mapping on legal track).  
- **Grow Affiliate Network**: Clear control and liquidity for affiliate rights.  
- **Expand Active User Base**: Real value for non-affiliate users (access, discounts, bundles, creator economy).

---

## 6) Open Questions (for Tokenomics Session)

1) Ratio **PC→ALPHA** and **SP→ALPHA** per category (LTS/RR/GR/GPSP/MC/WEC).  
2) Design of **stake/lock** & reward curve (without the promise of returns that pose regulatory risks).  
3) **Spend multipliers** in iBLOOMING (how much and for what products).  
4) **Cash-out rails**: window dates, caps, and base fees.  
5) Data and signals of **behavioral analytics** used for policy (e.g. hoarding vs spending score).

---

