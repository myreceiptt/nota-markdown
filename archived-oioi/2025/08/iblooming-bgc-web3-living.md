---
description: >-
  OiOi, this document serves as the strategic and operational reference for the Web3 Integration of BGC & iBLOOMING, derived from discussions with the founders on July 10–11, 2025.
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# Living Document of Web3 Integration Guidance

---

> **Phase-1 Closure Notice — 5 August 2026**
> This LIVING Doc is closed as the active strategic roadmap for the original BGC × iBLOOMING Web3 and tokenization phase.
> It remains a historical record of the project’s evolution, including assumptions and recommendations that were later revised.
> Future work is governed by the Founder Meeting resolutions of 5 August 2026 and, if approved, the new Product-Led Systems Program.

---

It compiles key insights from these discussions, confirms agreed decisions, and outlines the immediate next steps for execution.

- [📄 Day 1: 10 July 2025](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=u7cWvEAZRNFOnaeRQrvk&only=yes&limit=100)
  - [Prof. NOTA Pitch](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=EpbQmgZXml1WULNEgo9L&only=yes&limit=100),
  - and [Present WEB3 DRAFT](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=DfyK0lgqgs93hvBj4srb&only=yes&limit=100)
- [📄 Day 2: 11 July 2025](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=sdXJQGydvzjLAL8ZtAw0&only=yes&limit=100)
  - [Drafting Living Document](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ParZIhVe9iO8Wm04aZPU&only=yes&limit=100),
  - and [Drafting Understanding BGC X iBLOOMING Rewards](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=dTMAthaQQp8pllUoj0gW&only=yes&limit=100)

This living document is to be read, updated, and agreed upon by all founders, serving as a unified point of reference to keep the integration process synchronized and on track.

> 🔄 **Update Note — Post-Founder Zoom (10 December 2025)**
>
> This Living Doc should now be read together with the
> **BGC × iBLOOMING Working Presentation (Founder Alignment & Phase-1 Roadmap)**,
> which captures the founder Zoom alignment, full slide deck, and the
> Phase-1 Simulation-first roadmap.
>
> Link: [BGC × iBLOOMING Working Presentation](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=LTttfKln1a7ak66MMNUA&only=yes&limit=100)
> 
> ℹ️ **Definition Note**:
>
> * **ALPHA Coin** = *loyalty/rights ledger*; **ERC-20 interface, non-transferable**; **mint/burn only via AlphaController**; formalizes BGC & iBLOOMING’s 2023–2025 reward logic.
> * **iBC/iBTC** = public token layer derived from ALPHA behavior; **launches only after data validation & legal sign-off**.
> * **EventHub** = *append-only* event log for key business events; stores minimal fields plus a **hash** to off-chain proofs.
> * **Simulation** = Business/operational analysis of existing system data, without building new components unless explicitly stated.

---

## 🔍 CORE CONTEXT

Since 2023, **BGC & iBLOOMING** have operated in parallel — iBLOOMING as a digital product platform, and BGC as an affiliate reward engine. This parallel operation forms the foundation of what is now defined as **ALPHA Coin**.

**ALPHA Coin** has already been active through BGC & iBLOOMING’s operational model as a real-world business simulation. (Source → [Day 2 Summary](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=sdXJQGydvzjLAL8ZtAw0&only=yes&limit=100#pdf-page-sdXJQGydvzjLAL8ZtAw0-presentation-bgc-marketing-model-by-kk))

Without explicitly naming it, BGC & iBLOOMING has effectively implemented **ALPHA Coin tokenomics** through the following existing mechanics:

- **Purchase Credit** = Value Token
- **Sales Point** = Activity Token / Reward Token
- **Profit Sharing** = Holding-Based Reward
- **Cross-App Utility** = BGC affiliate integration with iBLOOMING edu-products / gated access to iBLOOMING

This means the integration does not start from scratch — it reframes, extracts insights, and elevates proven value logic that has been active since 2023. All details about the model formulation can be read in this document: [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100).

---

## 🧠 STRATEGIC OBJECTIVES (Reaffirmed)

As reaffirmed during the founder discussions, the **iBC/iBTC token architecture** is designed to directly achieve these five critical business objectives:

1. **Increase Revenue** – Grow overall income streams across the BGC & iBLOOMING ecosystem.
2. **Reduce Operational & Product Cost** – Lower expenses through automated processes and on-chain efficiencies.
3. **Reduce Tax Burden via On-Chain Logic** – Optimize tax exposure by leveraging compliant blockchain-based transaction structures.
4. **Grow Affiliate Network** – Expand the number of active affiliates and strengthen their participation.
5. **Expand Active User Base** – Increase total active users engaging with BGC & iBLOOMING products and services.

Each objective will be simulated, measured, and validated through actual token behavior and tangible utility, ensuring that all execution pillars (see Section 4) are aligned with these targets.

---

## ✅ FOUNDER ZOOM ALIGNMENT — DECEMBER 2025

- Founders accepted the current three-layer architecture and the document stack
  ([UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100), [WHITEPAPER Doc (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100), [TOKENFLOW Doc (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100), [WEB3LOGIN Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=wQewHM8gWWhQ0OPtUe6u&only=yes&limit=100), and this
  [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?limit=100&only=yes&page=ijQlNvGkp9UTE2LR2Tjm)) as the **baseline for Phase 1**.
- Simulation work is acknowledged as a **mandatory first step** before
  finalising any numeric parameters (conversion rates, windows, caps, etc.).
- ALPHA is reaffirmed as an **internal rights/simulation unit**, not a public
  or tradeable token; any public token (e.g. iBC/iBTC) will be handled on a
  separate track, after data validation and legal sign-off.
- Cash-out logic for members may **follow the existing BGC model** unless
  founders explicitly choose a different policy.
- Weekly coordination was requested to keep momentum and prevent drift.

---

## 🧱 EXECUTION PILLARS – PROGRESS

These are the four validated **core execution pillars** agreed upon by all founders, serving as the foundation for the Web3 integration of BGC & iBLOOMING. (Source → [Day 1: 4 Pillars Section](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=u7cWvEAZRNFOnaeRQrvk&only=yes&limit=100#pdf-page-u7cWvEAZRNFOnaeRQrvk-the-4-execution-pillars))

**Progress Legend**: ✅ Live | 🛠 In Progress | 🧪 Planned

| Pillar                             | Description                                                  | Progress      | Notes                                                                                                                                                                                                                                                                  | Owner(s)                    |
| ---------------------------------- | ------------------------------------------------------------ | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------- |
| ALPHA Coin Layer                   | Extract & analyze real existing earning/spending data.       | Running ✅    | Model formulation on the [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100).                                                                                                                | KK (BGC Ops)                |
| Tokenomics + WhitePaper (iBC/iBTC) | Design token economy using ALPHA Coin behavior data.         | In Progress 🛠 | Draft on the [WHITEPAPER Doc (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100) and [TOKENFLOW Doc (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100). | Prof. NOTA                  |
| Web3 Login System                  | Operates on a unified **credentials + Wallet Registry** that maps each user ↔ **Smart Account (AA)** across the ecosystem. | In Progress 🛠 | Implementation details on the [WEB3LOGIN Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=wQewHM8gWWhQ0OPtUe6u&only=yes&limit=100).                                                                                                               | Yuku's Team                 |
| iBC/iBTC Release & Utility         | Launch token with reward, BTC, and governance functions.     | Planned 🧪    | Requires deployment design, roadmap, and founder alignment.                                                                                                                                                                                                            | All Founders + Team Leaders |

✅ Use this table as a coordination grid for stakeholder assignment and responsibility planning.

---

## 📊 EXECUTION MATRIX – CYCLE

> 🧭 **Note – Original Strategy Map (10 July 2025: [Day 1: Simulated Execution Matrix Section](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=u7cWvEAZRNFOnaeRQrvk&only=yes&limit=100#pdf-page-u7cWvEAZRNFOnaeRQrvk-simulated-execution-matrix))**
>
> This matrix captures the original execution cycle and long-term structure
> (ALPHA layer, tokenomics, Web3 Login, iBC/iBTC, cross-app utility, legal).
> It is kept as a strategic reference. For current Phase-1 priorities and
> updated focus, see:
> - “[✅ FOUNDER ZOOM ALIGNMENT — DECEMBER 2025](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?limit=100&only=yes&page=ijQlNvGkp9UTE2LR2Tjm#pdf-page-ijQlNvGkp9UTE2LR2Tjm-founder-zoom-alignment-december-2025)” above, and
> - “[🔜 NEXT STEPS (Our Focus)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?limit=100&only=yes&page=ijQlNvGkp9UTE2LR2Tjm#pdf-page-ijQlNvGkp9UTE2LR2Tjm-next-steps-our-focus)” below.

**How to Read:**

- **Progress** → Combines lifecycle stage (`Live`, `Simulation`, `Planning`, `TBD`, `Post-Sim`) with current execution status (`✅ Running`, `🛠 In Progress`, `🧪 Planned`, `🧭 Pending`, `🧠 Not Started`).
- **Est. Duration** → Estimated completion time.
- **Owner(s)** → Responsible lead(s) and key contributors.
- **Notes** → Key context, dependencies, or constraints.

| Pillar                                     | Objective                                                                              | Progress       | Est. Duration                               | Owner(s)                                        | Notes                                                                                                                                     |
| ------------------------------------------ | -------------------------------------------------------------------------------------- | -------------- | ------------------------------------------- | ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **ALPHA Coin System**                      | Reframe the BGC & iBLOOMING reward system as “ALPHA Coin” behavioral simulation layer. | Running ✅     | ~3 weeks (data extraction & interpretation) | Prof. NOTA, KK                                  | Internal analytical tool, not public; feeds data into iBC/iBTC tokenomics.                                                                |
| **Tokenomics & WhitePaper (iBC/iBTC)**     | Design token economy using ALPHA Coin behavior data.                                   | In Progress 🛠  | 1–2 months                                  | Prof. NOTA (Lead), KK                           | Zero financial risk; NFTs used for behavior modeling.                                                                                     |
| └── **Behavioral Analytics (Pre-Release)** | Validate tokenomics & whitepaper assumptions with detailed user behavior simulation.   | Running ✅     | 2–4 weeks                                   | Prof. NOTA, Ops, Data Analyst                   | Use ALPHA Coin data + simulation to stress-test reward, burn, and staking logic before launch.                                            |
| **Web3 Login & Smart Wallet**              | Operates on a single, unified credentials database for BGC and iBLOOMING.              | Planned 🧪     | 1–2 months                                  | DevOps, Web3 Engineer                           | Details on the [WEB3LOGIN Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=wQewHM8gWWhQ0OPtUe6u&only=yes&limit=100). |
| **Release iBC/iBTC & Utility**             | Launch token with reward, BTC, and governance functions.                               | Planned 🧪     | 2–3 months                                  | All Founders + Team Leaders                     | Requires deployment design, roadmap, and founder alignment.                                                                               |
| └── **Behavioral Analytics (Ongoing)**     | Monitor and adjust tokenomics post-launch.                                             | Not Started 🧠 | Continuous                                  | Prof. NOTA, Ops, Data Analyst                   | Track saving, spending, hoarding, and exchange patterns; detect anomalies; inform iteration of staking, rewards, and burn logic.          |
| **Cross-App Token Utility**                | Enable iBC/iBTC usage across all BGC & iBLOOMING ecosystem.                            | Not Started 🧠 | TBD                                         | Prof. NOTA, Mobile Dev, Web3 Engineer           | Requires dev & UX standardization across platforms.                                                                                       |
| **Legal & Compliance Mapping**             | Define legal path for public/licensed token launch.                                    | Pending 🧭     | TBD                                         | Legal Advisor, Prof. NOTA, External Consultants | Determines eligibility for market release or partnerships. **Legal sign-off is a hard gate before “Release iBC/iBTC & Utility.”**                                                                               |

### 🧾 FINAL NOTES

This matrix is a **living strategy map**, not a finalized execution plan, and will evolve as BGC & iBLOOMING transition from simulation to production.

---

## 🔜 NEXT STEPS (Our Focus)

> 🔁 **Update – Simulation-First Priority (Post Founder Zoom, Dec 2025)**
>
> The immediate execution focus is now:
>
> 1. Complete **[SIMULATION Doc v0.1](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=TJijkNLNT8FUPkncSlJq&only=yes&limit=100)** and run simulations on the 24-month
>    dataset.
> 2. Use simulation outputs to finalise **[WHITEPAPER v1 (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100)** and **[TOKENFLOW v1 (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100)**
>    (parameters, formulas, and guardrails).
> 3. Prepare the **ALPHA Implementation Blueprint** (smart contracts, EventHub,
>    Wallet Registry, governance model) for execution by the engineering team.
>
> The original Next Steps table below remains valid as a structural map, but the
> short-term priority sequence is:  
> **SIMULATION → WHITEPAPER v1 → TOKENFLOW v1 → ALPHA Blueprint.**

The table below is kept as the original step breakdown from 10 July 2025: [Day 1: Next Steps](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=u7cWvEAZRNFOnaeRQrvk&only=yes&limit=100#pdf-page-u7cWvEAZRNFOnaeRQrvk-next-step-suggested-by-prof.-nota). The Simulation-first update above overrides the immediate priority order, but the structural steps here remain valid as a reference checklist.

**Status Legend**: ✅ Done | 🛠 In Progress | 🧪 Planned | 🧭 TBD

| Step   | Description                                                                                                        | Output File / Deliverable                                                                                                  | Status        | Notes                                                                                       |
| ------ | ------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- | ------------- | ------------------------------------------------------------------------------------------- |
| **0**  | Validate the 4 Execution Pillars with all Founders.                                                                | —                                                                                                                          | ✅ DONE       | All founders aligned; serves as base reference for all subsequent steps.                    |
| **1**  | Draft **Tokenomics & WhitePaper** (iBC/iBTC) using ALPHA Coin behavior data.                                       | [WHITEPAPER Doc (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100) | ✅ DONE       | Ongoing drafting based on extracted BGC data.                                               |
| **2**  | Draft **Token Flow** map across BGC & iBLOOMING systems.                                                           | [TOKENFLOW Doc (draft)](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100)  | ✅ DONE       | Requires coordination with both Ops and Dev teams for accuracy.                             |
| **3**  | **Behavioral Analytics (Pre-Release)**: Observe user behavior, process data, validate tokenomics assumptions.      | `Behavioral-Analytics-Report.md`                                                                                           | 🛠 In Progress | Using ALPHA Coin data for stress-testing reward, burn, and staking models.                  |
| **4**  | Assign responsible persons, owners, and execution timelines for each pillar & sub-pillar.                          | -                                                                                                                          | ✅ DONE       | Dependent on completion of steps 1–3 to ensure accurate role allocation.                    |
| **5**  | Prepare **Web3 Login Implementation Plan** (technical, operational, cost estimates).                               | [WEB3LOGIN Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=wQewHM8gWWhQ0OPtUe6u&only=yes&limit=100)  | ✅ DONE       | If a user does not yet have a BGC/iB account, they must first sign up for a BGC/iB account. |
| **6**  | Begin **Web3 Login Implementation**: Implement Web3 Login on BGC & iBLOOMING.                                      | —                                                                                                                          | 🧪 Planned    | Technical kickoff; requires readiness of backend data extraction layer.                     |
| **7**  | Prepare **The Execution Plan** (technical, operational, legal readiness) + confirm ALPHA Coin Layer data pipeline. | -                                                                                                                          | 🧭 TBD        | Needs confirmed owner assignments (Step 4).                                                 |
| **7**  | Circulate token architecture summary to all Founders for feedback.                                                 | Short Message: "This is the token architecture we’ve been running for 2 years — nothing is new, only elevated.             | 🧭 TBD        | Summary to be based on final version WHITEPAPER Doc and TOKENFLOW Doc.                      |
| **8**  | Release iBC/iBTC into the ecosystem with real utility.                                                             | Deployment package + release notes                                                                                         | 🧭 TBD        | **Proceeds only after legal sign-off**, founder consensus, and technical readiness. A single founder sign-off meeting approves the narrative and initial parameters (incl. Legal Gate) before proceeding to deployment.                          |
| **9**  | **Behavioral Analytics (Ongoing)**: Continuous monitoring & iteration of tokenomics post-launch.                   | Continuous log & reports                                                                                                   | 🧭 TBD        | Long-term maintenance and adjustment phase.                                                 |
| **10** | Cross-App Token Utility                                                                                            | —                                                                                                                          | 🧭 TBD        | Requires UX and dev standardization across BGC & iBLOOMING ecosystem.                       |
| **11** | Legal & Compliance Mapping                                                                                         | —                                                                                                                          | 🧭 TBD        | Defines public or licensed launch pathway; must align with jurisdictional requirements.     |

---

**Document Status: Living**  
✍️ Authored by Prof. NOTA v.11.11  
🗓️ Last Updated: 11 December 2025  
📌 For coordination across BGC & iBLOOMING Founders  
🔁 To be updated as dependencies shift or new constraints appear.

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
