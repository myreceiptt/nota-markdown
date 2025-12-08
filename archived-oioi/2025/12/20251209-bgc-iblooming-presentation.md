# BGC x iBLOOMING Prentation by Prof. NOTA - 20251209

---

## ✅ I. FULL SLIDE DECK

Here we provide the SLIDE PRESENTATION, 6–8 MINUTE SCRIPT, CHEAT SHEET, and CLOSING that is very concrete and not floating, all of which have been integrated with:

- [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100) ✔️
- [WHITEPAPER Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100) ✔️
- [TOKENFLOW Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100) ✔️
- [WEB3LOGIN Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=wQewHM8gWWhQ0OPtUe6u&only=yes&limit=100) ✔️
- [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100) ✔️
- And the Bullnium (USD 52K) quotation analysis that was requested.

---

## **Slide 1 — Title**

### BGC × iBLOOMING Integration Progress & Alignment (Phase 1)

**Objective Today:**

- Clarify system progress (documents, architecture, simulation plan)
- Align Phase-1 scope
- Review vendor quotation (Bullnium)
- Request explicit founder decisions

---

## **Slide 2 — Foundations: Documents Overview**

### System groundwork comes from 5 documents:

1. **[UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100)** — Source of truth for:

   - Affiliate system, PC/SP definitions, SP-based payout, pools, reward mechanics
   - Business rules that must remain AS-IS

2. **[WHITEPAPER Doc v1 (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100)** — Value-flow principles & ALPHA settlement layer

3. **[TOKENFLOW Doc v1 (draf)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100)** — PC/SP → ALPHA conversion, event model, policy parameters

4. **[WEB3LOGIN Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=wQewHM8gWWhQ0OPtUe6u&only=yes&limit=100)** — Unified identity, wallet provisioning, AA (Smart Account) mapping

5. **[LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100)** — Strategic Objectives & constraints

**Together, these form the system architecture for Phase 1.**

---

## **Slide 3 — What Has Been Completed (High-Level Progress)**

### **1. UNDERSTANDING Doc Consolidation**

- Cleaned structural logic for PC, SP, LTS, RR/GR, MC, GPSP, WEC, and CP flows.
- Identified AS-IS rules that cannot change.

### **2. System Architecture (Three-Layer Model)**

- Layer 1: BGC Core Business (PC, SP, payouts)
- Layer 2: iBLOOMING Identity & Demand Engine
- Layer 3: On-Chain Layer (ALPHA, EventHub, AA-based wallet registry)

### **3. Whitepaper Structure**

- Executive summary, problem–solution map, KPIs, compliance frames, fairness metric (Reward Gini).
- Core concept: PC/SP → ALPHA rights → spend/access/stake (non-transferable).

### **4. Tokenflow Skeleton**

- Conversion rules
- Cash-out windows (KYC, quarterly, 7 days, min $50)
- Append-only event model

### **5. Simulation Plan**

- 24-month data
- Conversion stress-test
- Parameter selection (fairness, sustainability)

---

## **Slide 4 — Architecture Overview**

### **Layer 1: BGC Core (AS-IS)**

- PC = proof of physical product / multi-level selling compliance
- SP = base for USD payouts (RR/GR/GPSP/etc.)

### **Layer 2: iBLOOMING Demand Engine**

- Classes, features, boosts (ALPHA sinks)
- CP digital products
- Reward multipliers & ecosystem utility

### **Layer 3: On-Chain Layer (Phase 1 Minimal)**

- ALPHA settlement layer
- Non-transferable ERC-20 interface; mint/burn controlled
- EventHub: append-only ledger (hashed proofs)
- Wallet Registry: maps user → EOA/AA
- Sponsored gas limits
  (≈$0.10/user/day; ≈$20 global/day)

This allows **auditability + low friction** without over-complicating the system.

---

## **Slide 5 — Web3 Login (Implementation View)**

(From WEB3LOGIN Doc)

### **Goals**

- Unified login for all users (Web2 → Web3)
- Automatic wallet provisioning (EOA + optional AA)
- Binding identity to EventHub records
- Reduce friction for ALPHA usage

### **Technical Design**

- Choose from modern providers (Thirdweb / Privy / Reown)
- Minimize custom smart contracts
- Use sponsored gas for onboarding and key ALPHA actions
- Enforce rate-limits + device rules (anti-Sybil)
  (Referral cooldown 1 day; max 10 Tier-1 joins/day)

This matches the WHITEPAPER and TOKENFLOW documents.

---

## **Slide 6 — Vendor Quotation Review: Bullnium (USD 52K)**

### **What Bullnium Proposes**

- Custom Web2/Web3 login
- Custom Smart Accounts + Paymaster
- Smart Contract factory
- Identity service
- Telemetry system
- 6-month timeline
- Optional audit +12K
  📄 (Based on Bullnium Quotation PDF)

### **Assessment**

- Price is reasonable **for full custom build**.
- **But scope is too heavy** for Phase-1.
- Many components duplicate provider features.
- 6-month delivery = too slow for our roadmap.
- Higher long-term maintenance burden.

### **Conclusion for Phase-1**

Use **modular provider-based integration** → faster (4–6 weeks), safer, lower risk, better aligned with documents.

---

## **Slide 7 — What Is NOT Final Yet**

### ❗Not final (needs founder decisions):

1. PC/SP → ALPHA detailed parameters (beyond v1 defaults)
2. Cash-out frequency & thresholds post-pilot
3. Governance: who controls AlphaController
4. Web3 Login provider choice
5. Simulation parameter acceptance
6. Bullnium vs modular vendor decision
7. Priority order of deliverables

### ✔️ Already defined structurally

- All flows
- All event models
- All policy scaffolding
- All compliance guardrails
- All architecture layers
- All document frameworks

---

## **Slide 8 — Founder Decisions Required (Very Concrete)**

### **Founders must decide now (Phase-1 commitments):**

#### **Decision 1 — Select Development Approach**

- **A: Modular (recommended)** → 4–6 weeks
- **B: Bullnium custom build** → 6 months

#### **Decision 2 — Prioritize Deliverable Order**

Choose **one**:

- Whitepaper v1 first
- Tokenflow v1 first
- Simulation output first

(These three depend on each other — sequence must be fixed.)

#### **Decision 3 — Cash-Out Policy (Pilot v1)**

Approve or adjust:

- 4× per year
- 7-day window
- Min $50
- Fee 1%
- Mandatory KYC

#### **Decision 4 — Web3 Login Provider**

- Thirdweb / Privy / Reown
  (Fully custom implementation only if founders insist.)

#### **Decision 5 — Governance Holder for AlphaController**

- Company?
- Technical founder?
- Multi-sig?
- Hybrid?

#### **Decision 6 — Approval to Move to Document Finalization**

Whitepaper v1 + Tokenflow v1 + Simulation v1.

---

## ✅ II. FULL SCRIPT (6–8 MINUTES)

### **Opening**

“Thank you, everyone, for your time.
Today’s goal is to give a clear picture of where the integration stands —
not from the perspective of document completeness,
but from the perspective of _system architecture and alignment_.”

“All the work so far has been grounded in five documents:
the UNDERSTANDING Doc, the Whitepaper draft, the Tokenflow draft,
the Web3 Login plan, and the Living Doc.
Together, they establish a consistent foundation for Phase-1.”

---

### **UNDERSTANDING Doc (Source of Truth)**

“The UNDERSTANDING Doc defines the reality of BGC & iBLOOMING today:
how PC is created and consumed, how SP functions,
how USD payouts are calculated,
the roles of LTS, RR, GR, GPSP, WEC, Miracle Cash, CP, and so on.”

“This document is essential because these AS-IS rules
cannot be changed by tokenomics — they must be respected.”

---

### **The Completed Work: Architecture & Structure**

“From this, I have consolidated the flows into a three-layer architecture:

1. BGC Core Business Layer
2. iBLOOMING Identity & Demand Engine
3. On-Chain Settlement Layer for ALPHA
   with EventHub, append-only logs, and controlled Smart Accounts.”

“The Whitepaper establishes the conceptual and compliance frame —
ALPHA as a non-transferable rights unit,
cash-out windows as a controlled exit,
and KPIs tied to the five Strategic Objectives.”

“The Tokenflow draft defines the conversion rules,
the event model, and the operational parameters such as rate-limits,
gas sponsorship caps, anti-Sybil policies, and settlement frequency.”

“The simulation plan is ready to test the 24-month data
to validate fairness, sustainability, and parameter selection.”

---

### **Web3 Login Integration**

“The Web3 Login design integrates smoothly with this architecture:
user signs in → wallet provisioned → identity anchored →
events recorded → ALPHA actions permitted with safeguards.”

“This allows us to keep UX simple
while still retaining auditability and control.”

---

### **Vendor Quotation Review**

“We also reviewed Bullnium’s quotation of USD 52K.”

“The price is reasonable for a full custom build,
but the scope is significantly larger than what Phase-1 requires.
Many of the components — Smart Accounts, Paymaster, identity layers —
are already available via modern providers
and do not need to be developed from scratch.”

“The custom approach would take six months;
the modular approach would take four to six weeks.”

“So for Phase-1, the modular approach is safer, faster, and fully compatible
with all our documents.”

---

### **What Is Not Final Yet**

“What remains open is not the structure —
that is already consistent across all documents —
but the decisions needed from founders
to move the documents into final form.”

“Whitepaper v1, Tokenflow v1, and Simulation v1
depend on explicit parameter approval,
provider choice for Web3 Login,
and policy decisions such as cash-out rules,
sinks priorities, and governance of the AlphaController.”

---

### **Closing — What We Need From Founders (Very Concrete)**

“To proceed efficiently, we need six concrete decisions from founders:”

1. **Choose the development approach for Web3 Login:**
   modular provider vs custom build.

2. **Fix the priority order of deliverables:**
   Whitepaper first, Tokenflow first, or Simulation first.

3. **Approve the cash-out window policy for Pilot v1:**
   quarterly windows, 7-day duration, minimum $50, 1% fee, KYC.

4. **Choose the provider for Web3 Login:**
   Thirdweb, Privy, or Reown.

5. **Decide governance for the AlphaController:**
   who holds authority (company, technical founder, multisig).

6. **Give approval to finalize Whitepaper v1 + Tokenflow v1 + Simulation v1
   after alignment on these parameters.**

“These decisions will allow the documents to move from structured drafts
into final versions ready for implementation.”

“Once alignment is complete,
execution for Phase-1 can proceed quickly and cleanly.”

“Thank you.”

---

## ✅ III. FOUNDER Q&A CHEAT SHEET (SUPER SINGKAT)

### **Q: Why are documents not final?**

Because parameters require explicit founder decisions.

### **Q: Does Bullnium make sense?**

Price yes; scope no. Scope is too big for Phase-1.

### **Q: Why modular login?**

4–6 weeks vs 6 months. Lower risk, aligned with docs.

### **Q: Is ALPHA a token?**

ALPHA is non-transferable rights unit; not for trading.

### **Q: Does this change BGC’s USD payouts?**

No — AS-IS rules remain exactly the same. (UNDERSTANDING Doc)

### **Q: What’s the biggest blocker now?**

Missing founder decisions on parameters & priority order.

---

## ✅ IV. FALLBACK LINES

**Option 1:**
“I have structured and synchronized all system documents —
UNDERSTANDING, Whitepaper, Tokenflow, Web3 Login, and the simulation plan —
so they no longer contradict each other.”

**Option 2:**
“My work has been architectural and integrative:
consolidating logic, designing flows, defining parameters
so implementation can proceed without rework.”

**Option 3:**
“I coordinated cross-document consistency so that any provider
— internal or external — can implement without ambiguity.”

---
