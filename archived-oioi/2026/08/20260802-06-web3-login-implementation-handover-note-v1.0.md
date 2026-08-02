---
description: >-
  This note transfers the Web3 Login project from completed architecture specification into controlled engineering implementation.
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# Web3 Login Implementation Handover Note

**Version:** 1.0  
**Date:** 5 August 2026  
**Specification:** BGC × iBLOOMING WEB3 LOGIN IMPLEMENTATION — Revision D  
**Specification status:** Final and founder-approved, as confirmed by Prof. NOTA  
**Implementation status:** Pending  
**Product and architecture owner:** Prof. NOTA  
**Technical implementation owner:** Yuku  
**Execution team:** BGC × iBLOOMING Engineering and DevOps

---

# 1. Purpose

This note transfers the Web3 Login project from completed architecture specification into controlled engineering implementation.

It clarifies:

- what has been approved;
- who owns implementation;
- what must be verified before development;
- what is in scope;
- what is not in scope;
- how changes are controlled;
- how the infrastructure supports the Product-Led direction.

---

# 2. Approved Architecture Intent

Users first authenticate through the existing BGC × iBLOOMING account system.

After successful login, Wallet Setup provides one of two paths:

1. create an embedded or in-app EOA;
2. connect an existing wallet through SIWE.

The system then provisions or maps a Smart Account for cross-application use.

The intended identity relationship is:

```text
BGC/iBLOOMING identity
↔ canonical identity ID
↔ EOA
↔ Smart Account
↔ application-specific user references
```

---

# 3. Current Status

| Area | Status |
|---|---|
| Architecture specification | Final |
| Founder approval | Confirmed by Prof. NOTA |
| Product ownership | Prof. NOTA |
| Technical ownership | Yuku |
| Engineering implementation | Pending |
| Production deployment | Not started or not evidenced |
| Token dependency | None |
| Product-Led relevance | High |

---

# 4. Why Web3 Login Proceeds Independently

Web3 Login remains valuable even if:

- ALPHA is not implemented;
- PC and SP are never tokenized;
- iBC/iBTC is never launched;
- public-token research is stopped.

It can support:

- unified identity;
- wallet-ready product experiences;
- product passports;
- access credentials;
- proof of purchase;
- digital receipts;
- retailer or distributor verification;
- creator entitlements;
- ownership and warranty records.

Its continuation is justified by independent infrastructure and product value.

---

# 5. Preconditions Before Engineering Kickoff

## 5.1 Confirm Actual Authentication Topology

The ability to use the same username and password across applications does not, by itself, prove a single physical credentials database.

Yuku and the engineering team must confirm whether the production architecture uses:

- one database;
- shared authentication service;
- federation;
- replication;
- synchronization;
- another topology.

## 5.2 Confirm Canonical Identity

Define:

- canonical user ID;
- BGC user ID;
- iBLOOMING user ID;
- duplicate-account rules;
- account-merge rules;
- suspended-account behaviour;
- deleted-account behaviour.

## 5.3 Confirm Wallet Provider and Custody Model

Decide:

- embedded wallet provider;
- Smart Account provider;
- key custody;
- recovery;
- Passkey;
- OTP;
- wallet replacement;
- compromised-wallet process.

## 5.4 Confirm Chain and Environment

Define:

- development chain;
- testnet;
- production chain;
- RPC provider;
- bundler;
- paymaster;
- indexer;
- monitoring.

No public-token contract is required for Web3 Login.

## 5.5 Confirm Privacy and Security

Define:

- personal-data boundaries;
- wallet-address storage;
- audit log;
- RBAC;
- merge permissions;
- recovery permissions;
- incident response;
- secrets management.

---

# 6. Implementation Scope

## In Scope

- login through existing account;
- Passkey support, if approved;
- Wallet Setup after login;
- embedded EOA creation;
- existing-wallet connection;
- SIWE verification;
- Smart Account provisioning;
- identity-wallet registry;
- session mapping;
- audit log;
- admin and merge workflow;
- development, testing, staging, and production environments;
- migration and rollout;
- acceptance testing.

## Out of Scope

- ALPHA issuance;
- PC or SP conversion;
- public iBC/iBTC;
- token trading;
- DEX/CEX integration;
- cash-out;
- financial rewards;
- final KYC/AML system;
- Product-Led pilot business rules;
- public-token treasury.

---

# 7. Recommended Delivery Stages

## Stage 0 — Technical Verification

Deliverables:

- current auth diagram;
- identity-source-of-truth decision;
- wallet-provider decision;
- security assumptions;
- implementation estimate.

## Stage 1 — Development Proof

Deliverables:

- test user login;
- embedded wallet creation;
- existing wallet connection;
- Smart Account provisioning;
- registry entry;
- basic audit event.

## Stage 2 — Cross-Application Test

Deliverables:

- same identity in BGC and iBLOOMING;
- same expected wallet mapping;
- session consistency;
- duplicate-account handling.

## Stage 3 — Security and Operations

Deliverables:

- recovery;
- merge;
- RBAC;
- logs;
- monitoring;
- incident flow.

## Stage 4 — Controlled Production Pilot

Deliverables:

- limited user cohort;
- support process;
- failure metrics;
- rollback;
- acceptance report.

## Stage 5 — Product-Led Enablement

After infrastructure acceptance:

- product passport;
- digital access credential;
- receipt;
- retailer credential.

---

# 8. Roles and Responsibilities

| Role | Responsibility |
|---|---|
| Founders | Budget, mandate, risk acceptance |
| Yuku | Technical owner and implementation accountability |
| Engineering | Build, integrate, test, deploy |
| DevOps | Environment, security, monitoring, release |
| Prof. NOTA | Architecture guidance, cross-project consistency, Product-Led use-case alignment |
| Product owner | User journey and adoption |
| Legal/privacy | Data and user-consent review |
| QA | Acceptance and regression testing |

Prof. NOTA does not become the default engineer, DevOps owner, project manager, or support owner merely because he authored the architecture.

---

# 9. Acceptance Criteria

The implementation is accepted only when:

- one canonical identity is resolved correctly;
- embedded EOA creation works;
- existing wallet connection works;
- Smart Account provisioning is deterministic or follows an approved replacement design;
- the same identity maps correctly across applications;
- secrets are not exposed;
- recovery is tested;
- merge and duplicate handling are tested;
- RBAC and audit logs are operational;
- monitoring is active;
- rollback exists;
- security review is complete;
- production owner signs acceptance.

---

# 10. Change Control

A design change is classified as:

## Minor

- provider-specific API adjustment;
- UI copy;
- logging;
- non-breaking schema extension.

## Material

- custody-model change;
- canonical-identity change;
- wallet-per-user policy change;
- recovery-model change;
- Smart Account architecture change;
- chain change;
- security-boundary change.

Material changes require:

- written change request;
- impact analysis;
- Prof. NOTA architecture review;
- Yuku technical approval;
- founder approval where business risk changes.

---

# 11. Product-Led Guardrail

Web3 Login must not silently become a reason to:

- issue ALPHA;
- tokenize PC/SP;
- launch a public token;
- create financial returns;
- build a DeFi product.

Wallet readiness is infrastructure.

Every product use case requires a separate approved Pilot Brief or System Design.

---

# 12. Kickoff Decision Record

| Decision | Entry |
|---|---|
| Engineering owner |  |
| Product owner |  |
| Provider |  |
| Chain |  |
| Development start |  |
| Pilot target |  |
| Budget |  |
| Security reviewer |  |
| Acceptance owner |  |
| Prof. NOTA checkpoint |  |

---

# 13. Handover Statement

> The WEB3LOGIN Doc is complete as an architecture specification and approved for implementation.
>
> Implementation, testing, security, rollout, and production operations belong to Yuku and the BGC × iBLOOMING engineering and DevOps teams.
>
> Prof. NOTA will support architectural consistency and Product-Led integration, but implementation ownership must not return to him by default.

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
