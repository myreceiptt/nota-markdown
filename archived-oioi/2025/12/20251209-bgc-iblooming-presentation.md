---
description: >-
  The goal of this session is to give a clear and structured picture of where the BGC × iBLOOMING integration currently stands — not in terms of document completeness, but in terms of system architecture, alignment, and decision readiness for Phase 1.
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# BGC x iBLOOMING Presentation by Prof. NOTA - 20251209

---

## ✅ I. FULL SLIDE DECK

Here we provide the SLIDE PRESENTATION, 6–8 MINUTE SCRIPT, and CLOSING that is very concrete and not floating, all of which have been integrated with:

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

### Not final (needs founder decisions):

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

### **🟦 Slide 1 — Title**

**BGC × iBLOOMING Integration Progress & Alignment (Phase 1)**

“Thank you, everyone, for your time today.
The goal of this session is to give a clear and structured picture of where the BGC × iBLOOMING integration currently stands —
not in terms of document completeness,
but in terms of **system architecture, alignment, and decision readiness** for Phase 1.”

“We will look at four things today:
(1) the progress across all documents and flows;
(2) the architecture and simulation plan;
(3) the vendor quotation review;
and (4) the specific decisions needed from founders.”

---

### **🟦 Slide 2 — Foundations: Documents Overview**

“All the work so far is grounded in **five core documents** that together form the foundation of Phase 1.”

“The first is the **UNDERSTANDING Doc**, which defines the operational reality of BGC and iBLOOMING today —
how PC is created and consumed, how SP functions,
how USD payouts are calculated,
and the roles of LTS, RR, GR, GPSP, WEC, Miracle Cash, and CP.
These AS-IS rules are essential, because they must remain unchanged.”

“The second is the **Whitepaper draft**, which establishes the conceptual and compliance framework —
including ALPHA as a non-transferable rights unit
and the value-flow principles.”

“The third is the **Tokenflow draft**, which defines the PC/SP → ALPHA conversion logic,
the event model, the append-only flow, and policy parameters.”

“The fourth is the **Web3 Login document**,
which defines how identity, wallet provisioning, and Smart Account mapping must work.”

“And lastly, the **Living Doc**, which contains the strategic objectives and constraints guiding the entire system.”

“These five documents collectively define the architecture for Phase 1.”

---

### **🟦 Slide 3 — What Has Been Completed (High-Level Progress)**

“Here is the work that has already been completed.”

“First, the **UNDERSTANDING Doc** has been fully consolidated.
All structural logic for PC, SP, LTS, RR/GR, GPSP, WEC, and CP flows have been clarified,
and the AS-IS rules that cannot be changed are now clearly identified.”

“Second, the system has been organized into a **three-layer architecture**:
(1) the BGC Core Business Layer,
(2) the iBLOOMING Identity and Demand Engine,
and (3) the On-Chain Layer with ALPHA settlement, EventHub, and Smart Accounts.”

“Third, the **Whitepaper** has a complete structural foundation —
including its executive summary, problem–solution framing, KPIs, compliance narratives,
and fairness metrics such as Reward Gini.
Its core principle remains: PC/SP converts into ALPHA rights,
which are non-transferable and tied to spend/access/stake actions.”

“Fourth, the **Tokenflow skeleton** is established:
conversion rules, cash-out windows, KYC requirements, quarterly schedules,
and an append-only event model.”

“And fifth, the **simulation plan** is ready.
It will use 24 months of historical data to test parameter ranges, validate fairness,
and ensure sustainability.”

---

### **🟦 Slide 4 — Architecture Overview**

“This is the architecture that emerges from the documents.”

“**Layer 1** is the BGC Core —
PC as proof of physical product and compliance for multi-level selling,
and SP as the base for USD payouts through RR, GR, GPSP, and related mechanics.”

“**Layer 2** is the iBLOOMING Demand Engine —
which includes classes, features, boosts as ALPHA sinks,
digital CP products,
and reward multipliers that generate ecosystem utility.”

“**Layer 3** is the On-Chain Layer, in a minimal Phase-1 form —
a controlled ALPHA settlement contract,
non-transferable ERC-20 behavior,
an EventHub that records hashed proofs in an append-only format,
a Wallet Registry mapping users to EOA or Smart Accounts,
and sponsored gas limits that allow smooth UX without over-exposing the system.”

“This combination provides **auditability** without adding unnecessary friction.”

---

### **🟦 Slide 5 — Web3 Login (Implementation View)**

“Next is Web3 Login, which ties the system together at the identity level.”

“The goals are simple:
a unified login that works for all users,
automatic wallet provisioning using either EOA or optional Smart Accounts,
binding user identity to EventHub records,
and enabling ALPHA actions with minimal friction.”

“Technically, the design uses modern providers such as Thirdweb, Privy, or Reown.
This reduces the need for custom contracts,
keeps onboarding simple,
and allows gas sponsorship for key ALPHA actions.”

“We also enforce rate-limits and device rules —
including anti-Sybil protections such as referral cooldowns
and maximum Tier-1 joins per day.”

“This design is fully aligned with the Whitepaper and Tokenflow documents.”

---

### **🟦 Slide 6 — Vendor Quotation Review: Bullnium (USD 52K)**

“We also reviewed the quotation from Bullnium for USD 52,000.”

“They propose a full custom build —
custom Web2/Web3 login,
custom Smart Accounts with Paymaster,
a Smart Contract factory,
identity services,
and telemetry,
with a six-month timeline and optional audit.”

“The price is reasonable for a full custom build,
but the **scope is far larger than what Phase 1 requires**.
Many components overlap with what provider-based solutions already offer.
And a six-month delivery is too slow for our roadmap.”

“So for Phase 1, the modular provider-based approach is **faster** (four to six weeks),
**safer**, and more aligned with the documents we have.”

---

### **🟦 Slide 7 — What Is NOT Final Yet**

“At this point, the structure across all documents is complete.
What is not final are the **parameters and decisions** that must come from founders.”

“These include:
the detailed PC/SP → ALPHA parameters,
cash-out frequency and thresholds after pilot,
governance for the AlphaController,
provider selection for Web3 Login,
simulation parameter acceptance,
the decision between Bullnium or the modular approach,
and the order of deliverables.”

“What is already defined are the flows, the models, the scaffolding,
and the guardrails.
What remains is alignment on the choices.”

---

### **🟦 Slide 8 — Founder Decisions Required (Very Concrete)**

“To move forward efficiently, there are six concrete decisions that founders need to make now for Phase 1.”

“**First**, choose the development approach for Web3 Login:
a modular provider approach — which is faster and recommended —
or the Bullnium custom build, which will take six months.”

“**Second**, set the priority order of deliverables:
Whitepaper v1 first,
Tokenflow v1 first,
or Simulation results first.
These three depend on each other, so the sequence must be fixed.”

“**Third**, approve the Pilot v1 cash-out policy —
quarterly windows, seven-day duration, minimum fifty dollars,
one percent fee, and mandatory KYC —
or adjust it.”

“**Fourth**, select the provider for Web3 Login:
Thirdweb, Privy, or Reown.”

“**Fifth**, assign governance of the AlphaController:
the company, a technical founder, a multisig, or a hybrid model.”

“And **sixth**, give approval to finalize Whitepaper v1, Tokenflow v1, and Simulation v1
after these parameters are aligned.”

“These decisions will allow the drafts to evolve into final documents ready for execution.”

“Once alignment is reached,
Phase-1 implementation can proceed quickly and cleanly.”

“Thank you.”

---

## ✅ III. Q & A

### **Q: Why are documents not final?**

Because parameters require explicit founder decisions.

### **Q: Does Bullnium make sense?**

Price yes; scope no. The scope is too big for Phase 1.

### **Q: Why modular login?**

4–6 weeks vs 6 months. Lower risk, aligned with docs.

### **Q: Is ALPHA a token?**

ALPHA is a non-transferable rights unit; not for trading.

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

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
