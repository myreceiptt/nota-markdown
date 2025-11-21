---
description: >-
  Peta alur nilai BGC × iBLOOMING dari AS-IS ke TO-BE di Base—menetapkan konversi PC/SP→ALPHA, model peristiwa append-only (bukti ter-hash), cash-out windows (KYC), serta parameter Pilot v1 yang selaras dengan 5 Sasaran Strategis.
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# BGC × iBLOOMING — Alignment Call (Preparation Sprint v0.1)

> Related docs:  
> - [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100)  
> - [WHITEPAPER Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100)  
> - [TOKENFLOW Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100)  
> - [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100)  
> - [WEB3LOGIN Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=wQewHM8gWWhQ0OPtUe6u&only=yes&limit=100)

## 1. Call Objectives

- Confirm a shared understanding of the current status:
  - AS-IS BGC rewards and existing (Web2) system (see also [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100)).
  - TO-BE vision with ALPHA on Base and Web3 Login by Yuku (see also [WHITEPAPER Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100) and [TOKENFLOW Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100)).
- Agree on the scope and priorities of a short “Preparation Sprint” while Web3 Login is being implemented (see also [WEB3LOGIN Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=wQewHM8gWWhQ0OPtUe6u&only=yes&limit=100)).
- Decide on immediate next steps, owners, and a rough timeline (see also [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100)).

---

## 2. Context (Short)

- Web3 Login implementation is in progress (see also [WEB3LOGIN Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=wQewHM8gWWhQ0OPtUe6u&only=yes&limit=100)).
- Last month, KK already shared **~2 years of raw BGC data** for analysis (see also [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100)).
- The raw data has not yet been fully cleaned or mapped, because we still need a joint session to:
  - confirm which columns/fields are “source of truth”, and  
  - translate the existing format into the **target structure** we need for simulation.
- Instead of waiting passively, we use this time to:
  - Stabilize the **story & tokenflow model** (see also [WHITEPAPER Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100) and [TOKENFLOW Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100)).
  - Finish the **data mapping** and run a first simulation.
  - Define a realistic and limited **Pilot v1**.

---

## 3. Topics to Cover

### 3.1 Narrative & Tokenflow Basics

- Short value proposition of BGC × iBLOOMING (why it exists and for whom).
- AS-IS → TO-BE:
  - How PC/SP (or equivalent points) map into ALPHA.
  - Append-only event model and hashed evidence.
  - Cash-out windows and KYC boundaries (high-level, non-technical).

> See also:  
> - [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100)  
> - [WHITEPAPER Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100)  
> - [TOKENFLOW Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100)

### 3.2 Data & Simulation

- Acknowledge that KK has already sent **2 years of raw BGC data**.
- Clarify together:
  - Which parts of the data are complete and reliable enough for a first simulation.
  - Which columns/fields map to our target event structure (earn, redeem, referral, etc.).
- Agree on a simple **target schema** for simulation:
  - Minimal fields needed (member ID, timestamp, event type, amount, etc.).
  - How to derive ALPHA balances from the existing records.
- Define a practical plan:
  - Who helps with data translation/mapping (KK + Prof. NOTA).
  - What is the smallest “slice” of data we use for the first simulation (e.g. 6–12 months).
- Decide what **outputs** KK needs from the simulation:
  - Member-level summary (examples).
  - Total liabilities / reward exposure.
  - Edge cases (top earners, very inactive members, etc.).

> See also:  
> - [TOKENFLOW Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100)  
> - [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100)

### 3.3 Pilot v1 Shape

- Target profile and approximate number of participants.
- Pilot duration.
- What participants can earn/redeem and under what conditions.
- Operational roles:
  - Who handles support and questions.
  - Who reviews KYC/cash-out issues.
  - Who is allowed to adjust parameters during the pilot.

> See also:  
> - [WHITEPAPER Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100)  
> - [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100)

### 3.4 Governance, Legal & Risk (High-Level)

- KK’s view on:
  - ToS and disclaimers (non-investment, no guaranteed returns, etc.).
  - Basic privacy/data statement.
  - Handling suspicious or abusive behavior (freeze, block, etc.).

> See also:  
> - [WHITEPAPER Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100)  
> - [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100)

---

## 4. Expected Outcomes

By the end of the call, we aim to have:

- Agreement on the **Preparation Sprint** structure and workstreams.
- A list of **data requests** and a person responsible for gathering them.
- Clarity on:
  - What we can already move forward with (before Web3 Login is ready).
  - When and how to involve Yuku in a focused tech session.

> See also:  
> - [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100)

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
