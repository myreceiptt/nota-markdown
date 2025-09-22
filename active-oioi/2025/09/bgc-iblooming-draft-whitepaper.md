## 🧩 Problem

Since 2023 the reward setup has worked in practice, but six flow-level gaps still block scale and value realization across BGC & iBLOOMING:

1) **No Unified Conversion Path (PC/SP → User Outcomes)**  
   Value units (**PC**) and reward rights (**SP**) exist, but there is no settlement bridge that turns them into flexible user outcomes (spend across apps, stake, or trade) without leaving the ecosystem.

2) **Interoperability Gap → Value Leakage**  
   PC tends to sit idle (BGC-only utility) while SP typically exits as fiat payouts. Value leaves the system instead of recirculating across BGC, iBLOOMING, and partners—weakening compounding utility.

3) **Admin-Dependent Operations (Low User Agency)**  
   Conversions and redemptions depend on scheduled, admin-driven processes. Users often “ask for updates” instead of acting via self-service, raising overhead and slowing decisions.

4) **Transparency Deficit (Real-Time & Provable)**  
   Users lack a real-time, provable view of balances and entitlements. Without a trustworthy, append-only ledger, confidence and initiative are constrained.

5) **Fiat-First Tax Drag**  
   Early routing to fiat increases taxable events between parties. Keeping flows inside tokenized rights and internal settlement could reduce exposure (subject to jurisdictional compliance).

6) **Growth Imbalance (BGC > iBLOOMING)**  
   Capital enters via BGC but does not consistently convert into demand for iBLOOMING’s digital products. Without strong on-platform sinks/multipliers and creator-aligned incentives, affiliate gains risk stagnation and user growth remains shallow.

**In short:** the system is viable yet held back by the absence of a conversion bridge, cross-app utility gaps, admin-dependent flows, low real-time transparency, fiat-first tax drag, and an imbalance between where capital enters (BGC) and where digital demand should grow (iBLOOMING).

---

## 💡 Solution

We do not invent a new economy from scratch. We **reframe and elevate** the existing **Purchase Credit (PC)** and **Sales Point (SP)** into a unified analytical framework — **ALPHA Coin Simulation** — and upgrade it to an on-chain, user-driven system (**iBC/iBTC**) that closes the six flow-level gaps.

1) **Unified Conversion Bridge (PC/SP → Outcomes)**
   - Introduce an internal **conversion/settlement bridge** that maps PC (value) and SP (rights) into clear user outcomes: **spend across apps**, **stake for yield/tiers**, or **convert within the ecosystem**.
   - Bridge rules are codified (rates, limits, cooldowns) and enforced by smart contracts.

2) **Interoperability That Recirculates Value**
   - Enable **cross-app utility** (BGC ↔ iBLOOMING ↔ partners) so PC/SP value **recirculates** instead of leaking to fiat prematurely.
   - Standardize earn/spend primitives so rewards naturally find on-platform sinks (courses, services, access passes).

3) **Self-Service over Admin-Dependent Flows**
   - Replace scheduled, admin-driven conversions with **user-initiated self-service** via **Web3 Login / Smart Wallet** (account abstraction).
   - Users act instantly within policy bounds; ops focuses on exceptions, not routine execution.

4) **Real-Time, Provable Ledger**
   - Move entitlements and balances to an **append-only, on-chain (or L2/rollup) ledger** for **real-time and auditable** visibility.
   - Provide explorer-style views and in-app receipts; align incentives with transparent rules.

5) **Fiat-Efficient, Compliant Routing**
   - Keep flows **inside tokenized rights and internal settlement** for as long as possible; define clear conversion points to fiat.
   - Design with **jurisdiction-aware compliance** to reduce unnecessary taxable events while remaining audit-ready.

6) **Growth Rebalance toward iBLOOMING Demand**
   - Add **on-platform sinks/multipliers** (bundles, gated content, tiered access, creator revenue-share) to pull capital from BGC into iBLOOMING usage.
   - Align creator/affiliate incentives so user gains compound within the product ecosystem, not exit immediately.

---

**Unifying Principle.**  
**ALPHA Coin Simulation** keeps **PC** (value) and **SP** (reward rights) functionally distinct yet governed by one policy plane; **iBC/iBTC** operationalizes this with a conversion bridge, cross-app utility, self-service wallets, and a provable ledger — solving fragmentation, leakage, admin overhead, opacity, fiat-first drag, and growth imbalance.

---

## 🔧 Tokenomics

> This section translates the proven **PC/SP mechanics** into a clear issuance and utility model for **iBC/iBTC**.  
> PC (Purchase Credit) and SP (Sales Point) remain as **internal data & rights**, acting as weights to “mine/distribute” iBC/iBTC to users.

### 1) Token Definition & Roles
- **Token Name/Symbol**: **iBC/iBTC** *(final naming TBD)*  
- **Nature**: Single ecosystem token for **access, spend, and staking** across **BGC** & **iBLOOMING**.  
- **Internal Rights**:  
  - **PC (Purchase Credit)** = value contribution measure.  
  - **SP (Sales Point)** = activity/reward rights measure.  
- **Principle**: Users **do not convert** PC/SP into iBC/iBTC 1:1. Instead, **PC/SP act as mining weights** used to calculate **periodic iBC/iBTC emissions**.

### 2) Supply & Emissions
- **Initial Supply**: **[TBD]** (e.g., genesis allocation for ops/team/community with vesting).  
- **Emission Epoch**: **[TBD cadence]** (e.g., weekly).  
- **Total Emission per Epoch**: \(E(t)\) with **[TBD decay]** (e.g., linear decay/halving).  
- **User Emission Formula**:
  \[
  \text{iBC}_{\text{user},t}
  = E(t)\times \Big(
      w_{PC}\cdot \frac{PC_{\text{user},t}}{\sum PC_t}
    + w_{SP}\cdot \frac{SP_{\text{user},t}}{\sum SP_t}
    \Big)
  \]
  - **Weights**: \(w_{PC}, w_{SP}\) **[TBD split]** (e.g., 60/40).  
  - **Normalization**: \(\sum PC_t, \sum SP_t\) dihitung per-epoch (snapshot dengan aturan anti-manipulasi).  
  - **Guards**: per-user cap **[TBD]**, **cooldown [TBD]**, **exclusion/slashing** untuk fraud/abuse.

### 3) Distribution Pools (High-Level)
- **User Distribution (Emissions)**: **[TBD]%** — mengikuti formula PC/SP di atas.  
- **Growth & Campaigns**: **[TBD]%** — referral boosts, creator incentive, seasonal quests.  
- **Ops/Community Reserve**: **[TBD]%** — reliquidity for sinks, promo, contingency.  
- **Team/Foundation (Vested)**: **[TBD]%** — vesting **[TBD schedule]**, cliff **[TBD]**.  

> Catatan: porsi & vesting diputuskan di Level Founder; perubahan dicatat di changelog parameter.

### 4) Utilities & Sinks (On-Platform)
- **Access / Gated Features**: premium courses, tools, content passes.  
- **Spend**: discounts, bundles, subscriptions, service fees.  
- **Stake (Tiered Benefits)**:  
  - **Tiers [TBD]** → fee rebates, redemption priority, referral multipliers, exclusive access.  
  - **Unstake rules [TBD]** → cooldown/penalty.  
- **Sinks**: **[TBD mix]** antara **burn**, **sink-to-treasury**, atau **recycle-to-rewards**.  
  - Contoh: **burn_rate [TBD]%** pada setiap spend; atau **_**
