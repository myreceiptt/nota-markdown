---
description: >-
  We don't belong in your reality, your real life. In your reality, your real
  life, you can merely meet our avatars in any version. So, stay alert and
  beware of scams!
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# PERURI CONNECT × BLOCKCHAIN — Proposal Template (Clean Version)

> Draft date: {{DATE}}  
> Prepared for: **Departemen Pengembangan TI — Perum Percetakan Uang RI (PERURI)**  
> Prepared by: **PT Peruri Digital Security × Voyage**  
> Version: {{VERSION}} (internal)

---

## 0) Cover Summary (Executive Overview)
**Objective.** Build a secure, auditable, and engaging **employee reward system** integrated with **Peruri Connect** using a **permissioned blockchain** (default: Hyperledger Besu + IBFT2).  
**Why now.** Replace manual/centralized reward mechanisms with verifiable records, enable **peer-to-peer recognition**, and unlock interoperable redemption (voucher, merchandise, internal benefits).  
**What you get.** Production-grade chain + contracts + APIs + admin dashboards + documentation + training.  
**Go‑live target.** {{GO_LIVE_DATE}} with pilot scope {{PILOT_SIZE}} users.

---

## 1) Goals & Success Criteria
- **G1 — Verifiable Rewards.** All reward issuance, transfer, and redemption immutably logged on-chain.  
- **G2 — P2P Recognition.** Employees can grant points to peers within policy limits.  
- **G3 — Seamless Integration.** Single sign-on via **Peruri Connect**; consistent UX in mobile app.  
- **G4 — Governance & Controls.** Policy‑enforced quotas, roles, and approval flows.  
- **G5 — Reporting & Audit.** Real‑time dashboards; exportable audit trails.  
- **Success Metrics.** SLA (≥99.5%), issuance/transfer finality (<5s), UAT pass rate (≥95%), user satisfaction (≥80% CSAT).

> **Fill instructions:** Replace or add measurable metrics based on PERURI’s internal KPI (e.g., average time to redeem, weekly MAU).

---

## 2) Scope of Work
**2.1 Analysis & Design**  
- Assess current reward flows; map actors, events, and constraints.  
- Design token model (**non‑transferable from treasury to user; P2P transfers policy‑bounded**).  
- Draft redemption mechanics and partners (internal/external).

**2.2 Blockchain Core & Smart Contracts**  
- Network: **Besu** (permissioned), **IBFT2** (finality), private chain.  
- Contracts: `RewardToken.sol`, `Treasury.sol`, `Redemption.sol`, `PolicyRegistry.sol`.  
- Key features: mint/burn, P2P transfer with limits, redemption workflows, pause/resume, role-based access.

**2.3 Integration Layer (Services/API)**  
- Build **Node.js/TypeScript** service with REST/GraphQL endpoints.  
- Webhooks for redemption partners; JWT/OAuth via Peruri Connect.  
- Documentation: OpenAPI + examples.

**2.4 Treasury & Admin Tools**  
- Admin dashboards (issuer, policy, quotas, reports).  
- On-chain/off-chain reconciliation and alerts.

**2.5 Security & Audit**  
- Contract audits, threat modeling (STRIDE), penetration test for API.  
- Monitoring (Prometheus, Grafana), logs, backups, disaster recovery.

**2.6 Enablement**  
- Training (ops, admin, developer).  
- Handover documentation; runbooks; KT sessions.

**2.7 Support & Maintenance**  
- Hypercare period post‑launch; patches and minor improvements per SLA.

> **Fill instructions:** Trim/expand modules to match budget/timeline. Remove any manufacturing/HMI wording; keep reward-system focus.

---

## 3) Technical Architecture

**3.1 Network Topology (Baseline)**  
- **Validator Nodes:** {{N_VALIDATORS}} (e.g., 2–4 across PERURI IT and PDS).  
- **Transaction Nodes:** {{N_TX_NODES}} (API‑facing).  
- **BAS/Mirror:** Optional indexer/ETL for analytics and search.  
- **Monitoring:** Prometheus + Grafana.  
- **Compute (per node):** 4 vCPU, 8 GB RAM, 200 GB SSD (adjust after load test).

**3.2 Consensus & Rationale**  
- **IBFT2**: Fast finality, permissioned validators, easy governance.

**3.3 Identity & Access**  
- Users authenticated by **Peruri Connect**; chain roles mapped to HR/IT roles.  
- Admin multisig/role control for mint, pause, policy updates.

**3.4 Data & Privacy**  
- On‑chain: events + minimal data (token balances, ids).  
- Off‑chain: PII stays in Peruri Connect DB. Hash/pointer for audits.

**3.5 API Contract (Sketch)**  
- `POST /rewards/issue` — mint to user  
- `POST /rewards/transfer` — P2P within limits  
- `POST /rewards/redeem` — initiate redemption  
- `GET /ledger/tx/:id` — detail; `GET /reports/summary` — aggregates

> **Fill instructions:** Insert current infra (VMs, Kubernetes), networking, firewall rules, domain names, SSL, backup locations, and RPO/RTO.

---

## 4) Functional Requirements

**4.1 Issuance**
- Issuer roles, monthly quotas, mint policies, revocation/burn rules.

**4.2 P2P Recognition**
- Daily/weekly caps, recipient eligibility, cooldowns, abuse prevention.

**4.3 Redemption**
- Catalog (vouchers/merch/internal), settlement flow, fraud checks, refunds.

**4.4 Admin & Reporting**
- Role matrix, audit exports (CSV/BI), anomaly detection.

**4.5 Mobile Integration**
- Peruri Connect app screens, SDK methods, error states, offline handling.

> **Fill instructions:** Describe rules numerically (caps, windows), approval steps, and exception flows.

---

## 5) Non‑Functional Requirements (NFR)
- **Security:** OWASP ASVS L2+, key management SOP, secrets rotation.  
- **Performance:** <2s API p95 in normal load; <5s end‑to‑end transfer finality.  
- **Availability:** ≥99.5% service uptime; graceful degradation.  
- **Compliance:** Logging, retention, auditability; change management.  
- **Observability:** Metrics, centralized logs, alerts with on‑call rota.

---

## 6) Deliverables
1) **Blockchain core & contracts** (source, tests, deployment scripts).  
2) **API services** (containerized), **OpenAPI** docs.  
3) **Admin dashboards** (issuer/treasury/reports).  
4) **Documentation**: BRD, FSD, Architecture, Runbooks, UAT, User Manuals.  
5) **Training & KT** materials; session recordings (if allowed).  
6) **Monthly progress reports**, **Final report**, **Warranty & Support** terms.

> **Fill instructions:** Attach sample screenshots/wireframes if available.

---

## 7) Project Organization & Roles
- **Project Manager** — timeline, risk, stakeholder mgmt.  
- **Blockchain Architect** — network, security, governance.  
- **Smart Contract Dev** — Solidity, reviews, audits.  
- **Backend/API Dev** — services, integrations, monitoring.  
- **QA (Functional)** — test plans, UAT, automation.  
- **QA/Sec** — pen‑test, SAST/DAST, infra hardening.  
- **DevOps** — CI/CD, IaC, envs.  
- **UI/UX** — admin & app UX.

> **Fill instructions:** Insert named resources, CV highlights, and allocated FTE per phase.

---

## 8) Timeline
- **Phase 0 — Discovery (2–3 wks):** BRD/FSD, arch sign‑off.  
- **Phase 1 — Build (6–8 wks):** chain + contracts + APIs + dashboards.  
- **Phase 2 — UAT (2 wks):** scenarios, fixes, acceptance sign‑off.  
- **Phase 3 — Launch (1 wk):** prod deploy, hypercare (4 wks).

> **Fill instructions:** Convert to a dated Gantt; align with PERURI change windows.

---

## 9) Budget (BOQ Skeleton)
**A. Implementation (Man‑Months)**  
| Role | Qty | Duration | Rate | Subtotal |
|---|---:|---:|---:|---:|
| Project Manager | {{Q_PM}} | {{D_PM}} | {{R_PM}} | {{S_PM}} |
| Blockchain Architect | {{Q_ARCH}} | {{D_ARCH}} | {{R_ARCH}} | {{S_ARCH}} |
| Smart Contract Dev | {{Q_SC}} | {{D_SC}} | {{R_SC}} | {{S_SC}} |
| Backend/API Dev | {{Q_BE}} | {{D_BE}} | {{R_BE}} | {{S_BE}} |
| QA (Func) | {{Q_QA}} | {{D_QA}} | {{R_QA}} | {{S_QA}} |
| QA (Sec) | {{Q_SEC}} | {{D_SEC}} | {{R_SEC}} | {{S_SEC}} |
| DevOps | {{Q_DEVOPS}} | {{D_DEVOPS}} | {{R_DEVOPS}} | {{S_DEVOPS}} |

**B. Validator/Node (Annual or Project Term)**  
| Item | Spec | Qty | Term | Rate | Subtotal |
|---|---|---:|---:|---:|---:|
| Validator Node VM | 4 vCPU / 8GB / 200GB SSD | {{Q_VAL}} | {{TERM}} | {{RATE_VAL}} | {{SUB_VAL}} |
| Tx Node VM | 4 vCPU / 8GB / 200GB SSD | {{Q_TX}} | {{TERM}} | {{RATE_TX}} | {{SUB_TX}} |
| BAS/Indexer | 4 vCPU / 8GB / 200GB SSD | {{Q_BAS}} | {{TERM}} | {{RATE_BAS}} | {{SUB_BAS}} |

**C. Documentation & Training**  
| Item | Qty | Subtotal |
|---|---:|---:|
| BRD, FSD, Dev Plan | 1 | {{SUB_DOC}} |
| Source + Config Packages | 1 | {{SUB_SRC}} |
| UAT Docs & Sessions | 1 | {{SUB_UAT}} |
| User/Admin Manuals | 1 | {{SUB_MAN}} |
| Monthly Reports & Final Report | 1 | {{SUB_REP}} |

> **Fill instructions:** Replace placeholders with real numbers; ensure hardware lines map to PERURI’s VM catalogue.

---

## 10) Acceptance & Handover
- **UAT criteria** agreed and signed by IT + HR.  
- **Operational handover**: nodes, keys, runbooks, monitoring dashboards.  
- **Warranty**: {{WARRANTY_TERM}} with defined SLA and response times.

---

## 11) Risks & Mitigations
- Policy abuse → **P2P caps + anomaly alerts + audit**.  
- Key compromise → **HSM/raw key policy, rotation, multisig**.  
- Integration drift → **Contract tests, versioned APIs**.  
- Vendor lock‑in → **Open standards, source delivery, KT**.

---

## 12) Appendices
- A. Detailed API spec (OpenAPI).  
- B. Contract ABIs & events.  
- C. Runbooks (deploy, upgrade, rollback).  
- D. Security test reports.

---

References:
- [Kajian Transformasi Sistem Reward Digital](project-sistem-reward-karyawan-peruri.md#kajian-transformasi-sistem-reward-digital)
- [Ringkasan Eksekutif](project-sistem-reward-karyawan-peruri.md#ringkasan-eksekutif)
- [Narasi Pitch Singkat](project-sistem-reward-karyawan-peruri.md#narasi-pitch-singkat)
- [Proposal Kerja](project-sistem-reward-karyawan-peruri.md#proposal-kerja)
- [Simulasi Tanggapan](project-sistem-reward-karyawan-peruri.md#simulasi-tanggapan)
- [Tanggapan & Jawaban Pertanyaan Follow-Up dari Peruri](respon-follow-up-dari-peruri.md)
- [Rencana Teknis Pengerjaan](peruri_connect_plan.md)
- [Peruri Connect Spec Eksekusi v1](peruri_connect_spec_v1.md)
- [Uraian SDM - Peruri Connect X Blockchain](peruri_connect_sdm.md)
- [Proposal Peruri Connect X Blockchain - ID](proposal_peruri_connect_blockchain_id.md)

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
