---
description: >-
  We don't belong in your reality, your real life. In your reality, your real
  life, you can merely meet our avatars in any version. So, stay alert and
  beware of scams!
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# BGC × iBLOOMING — Web3 Login (Unified Auth)

**Revision D — October 13, 2025**  
**First Version**: [Web3 Login Identity Bridge](archived-oioi/2025/09/bgc-iblooming-web3-login-implementation-plan-oct-2025.md)  
**Status:** Draft for sign‑off (clean, single‑source)  
**Owners:** Prof. NOTA (Product/Architecture), Yuku (Tech Owner), BGC × iBLOOMING Eng/DevOps

---

## Table of Contents

1. Purpose & Scope
2. Key Decisions
3. Constraints & Non‑Goals
4. Architecture Overview
5. User Journeys
6. Data Model (Unified)
7. API Specification
8. Security Model
9. Thirdweb Integration — Step‑by‑Step
10. DevOps & Environments
11. Migration & Rollout
12. Testing Strategy
13. Operations (RBAC & Merge)
14. Acceptance Criteria & Launch Checklist
15. Change Log
    Appendix: Reference Snippets

---

## 1) Purpose & Scope

We operate on a **single, unified credentials database (existing)** for BGC and iBLOOMING. Users can sign up and log in to any app (BGC Web, iBLOOMING Web, iBLOOMING Mobile) with the **same username/password** and, in the near future, also authenticate with a **Passkey** as a first‑class method.

After login, users complete **Wallet Setup** by either:

* **Create EOA (Embedded/In‑App)** → **auto‑provision a Smart Account (AA)**; or
* **Connect existing wallet (SIWE)** → **auto‑provision a Smart Account (AA)**.

This standardizes on‑chain identity to **one EOA and one Smart Account (AA) per user per chain**, enabling consistent features (rewards, receipts, payments) across the BGC/iB ecosystem with minimal friction and predictable costs.

**Bridging Web2 ↔ Web3.** If a user does not yet have a BGC/iB account, they must first **sign up** for a BGC/iB account and then **log in** (via username/password or **Passkey**). Only **after** a successful login is **Wallet Setup** available: either **Create an embedded EOA → auto‑provision AA** or **Connect an existing Web3 wallet → auto‑provision AA**. Web3‑native users who already have a BGC/iB account simply log in and proceed to Wallet Setup.

**Analytics & simulations.** The unified mapping `user_id ⇄ identity_id ⇄ (EOA, AA)` enables reliable, on‑chain‑addressed telemetry for behavioral simulations (Alpha Coin → future iBC/iBTC).

**Partner signal.** A single, **passkey‑enabled** login and **post‑login Smart Account bootstrap** operating across apps demonstrates concrete momentum while tokenomics is finalized.

**In scope:** identity model, wallet binding, AA provisioning, SIWE, **Passkey support**, security, DevOps, and Thirdweb implementation.

**Out of scope:** tokenomics/ledger rules, analytics dashboards, and non‑auth product features.

## 2) Key Decisions

* **Single credentials auth** for the BGC/iB ecosystem.
* **Post‑login Wallet Setup** (Create or Connect), not pre‑login.
* **Deterministic AA** per identity (factory + salt).
* **Identity mapping:** `identity_id ⇄ user_id ⇄ (EOA, AA)`.
* **Admin Console with RBAC** and full audit for binds/merges.
* **Thirdweb** supplies SIWE, Embedded/In‑App Wallet, Smart Accounts, and optional gas sponsorship.

---

## 3) Constraints & Non‑Goals

**Constraints**

* `UNIQUE(address, chain_id)` across `wallets`.
* SIWE uses **per‑login nonce** (TTL 3–5 min); check **domain/uri/chainId**; nonce consumed upon verify.
* Secrets in **vault**; **regular rotation**.
* PII minimization; encryption at rest; observability + rate‑limits.

**Non‑Goals**

* No separate user tables per app in the BGC/iB ecosystem.
* No server‑side plaintext key handling for wallets.

---

## 4) Architecture Overview

```
[ User ]
  │
  ├─ Credentials Login (Unified) ───────► [ Auth Service ] → session/JWT { user_id, roles }
  │
  ├─ Post‑Login: Wallet Setup ──────────► [ Wallet Service ]
  │     ├─ A) Create EOA (Embedded/MPC) ───► Auto‑create Smart Account (AA)
  │     └─ B) Connect Wallet (SIWE) ───────► Auto‑create Smart Account (AA)
  │
  └─ BGC / iB Apps ───────────────► [ Identity Service ] → { identity_id, eoa, aa }

On‑chain:
[ EOA ] ─(owner/controller)─► [ Smart Account (AA) ] ──(optional)─► Paymaster/Bundler
```

---

## 5) User Journeys

**5.1 New User**  
Sign up (username/password/passkey, MFA optional) → Session starts → **Wallet Setup** (Create or Connect) → AA provisioned → Done.

**5.2 Existing User (no wallet yet)**  
Login (username/password/passkey, MFA optional) → **Wallet Setup** (Create or Connect) → AA provisioned → Done.

**5.3 Existing User (wallet bound)**  
Login (username/password/passkey, MFA optional) → **Skip Wallet Setup** → Proceed.

---

## 6) Data Model (Unified)

**users**  
- `user_id` (PK), `email` (unique, nullable), `phone` (unique, nullable), `username` (unique), `password_hash`, `mfa_enabled`, timestamps.

**identities**  
- `identity_id` (PK), `user_id` (FK→users), timestamps. *(Keeps future merge/link options without breaking unification.)*  

**wallets**
- `wallet_id` (PK), `identity_id` (FK), `type` (`EOA`|`AA`), `address`, `chain_id`, `salt`, timestamps.  

**auth_providers**
- `provider_id` (PK), `user_id` (FK), `provider_type` (`credentials`|`siwe`), `provider_ref` (email/phone hash or EOA), timestamps.  

**audit_logs**
- `log_id` (PK), `identity_id`, `user_id`, `action` (`bind`|`merge`|`unlink`), `actor`, `metadata`, timestamps.  

**Constraints**
- `UNIQUE(address, chain_id)` on `wallets`; `type ∈ {EOA, AA}`; FK integrity enforced.
- SIWE nonces: unique, `used` boolean, `expires_at` UTC.

---

## 7) API Specification

**Auth**

* `POST /auth/credentials/login` → `{ username|email|phone, password }` → `{ session_jwt, user_id }`

**Wallet Setup**

* `POST /wallet/provision` → uses session → Create **EOA** (if missing) + deploy **AA** → `{ identity_id, eoa, aa }`
* `POST /wallet/connect/siwe` → `{ message, signature }` → verify SIWE, bind **EOA**, deploy **AA** → `{ identity_id, eoa, aa }`

**Identity**

* `GET /identity` → session → `{ identity_id, eoa, aa }`

**Admin/Audit**

* `GET /admin/merge/diff?source&target`
* `POST /admin/merge/execute` (dual‑control for risky merges)
* `GET /admin/audit?identity_id|user_id`

---

## 8) Security Model

* **SIWE + per‑login nonce** (short TTL; consumed on verify).
* Bind SIWE to **domain/uri/chainId**.
* **Secrets in vault; rotate regularly** (JWT/JWKS, DB creds, RPC keys, webhook secrets).
* **RBAC** for Admin Console; two‑person rule for risky merges.
* PII minimization; encryption at rest; immutable audit.
* Rate‑limit login/OTP/SIWE/merge; WAF on public APIs.

---

## 9) Thirdweb Integration — Step‑by‑Step

**9.1 Capabilities used**

* Embedded/In‑App Wallet (Create EOA).
* SIWE (Auth) for existing wallets.
* Smart Accounts (AA) with deterministic deployment (factory + salt).
* WalletConnect for UX.
* Optional Paymaster/Bundler for gas sponsorship.

**9.2 Client (Web)**

1. Install Thirdweb; wrap app with provider (chains, `clientId`, AA/paymaster config).
2. After credentials login, open **Wallet Setup** modal: **Create Wallet** or **Connect Wallet**.
3. **Create Wallet** (Embedded): trigger embedded flow (email/OTP/phone/passkey/social) → get **EOA** → instantiate **AA** on top (`sponsorGas: true` if needed).
4. **Connect Wallet** (SIWE): connect via WalletConnect/extension → request SIWE challenge → user signs → server verifies → instantiate **AA** for that EOA.
5. Persist `{ eoa, aa }` to backend via the Wallet Setup endpoints.

**9.3 Server (Auth + Identity)**

* **Credentials login**: issue session/JWT (`user_id`, roles).
* **SIWE challenge**: generate cryptographic `nonce`, store (`used=false`, TTL 3–5 min).
* **SIWE verify**: recover address, validate domain/uri/chainId, check nonce unused/unexpired → **consume** nonce → bind EOA→identity → issue/refresh session.
* **Provision AA**: call factory with deterministic salt (e.g., derived from `identity_id`); persist AA address.
* **Audit**: log every bind/merge; expose `GET /identity`.

**9.4 Environment Variables**  
- `THIRDWEB_CLIENT_ID`,
- `CHAIN_ID`,
- `RPC_URL`,
- `AA_FACTORY_ADDRESS`,
- `PAYMASTER_URL` (optional),
- `WALLETCONNECT_PROJECT_ID`,
- `JWT_SECRET`,
- `AUTH_DOMAIN`,
- `SIWE_STATEMENT`.

**9.5 Error Handling & Cost Controls**

* Retry with backoff for AA deploy; allow **lazy deploy** on first tx if applicable.
* Scope gas sponsorship (onboarding only, per‑action caps); alerts on budget.
* Clear UX for wrong network/expired nonce/denied signature.

---

## 10) DevOps & Environments

* **Domains**: `auth.bgcxib.com` (unified), brand app domains.
* **CI/CD**: build/lint/typecheck; E2E flows (Create & Connect); smoke tests for JWT issuance, SIWE verify, AA deploy.
* **Observability**: metrics (login success/error, SIWE failures, AA deployment), logs, traces; alerts for gas spend and failure spikes.
* **Access**: DevOps/Tech Lead manages secrets, env promotion, AA factory; MFA enforced.

---

## 11) Migration & Rollout

1. **Inventory** current user stores; pick the **source of truth** (`users`).
2. **Deduplicate** historic BGC/iB accounts to unified `users`; preserve audit mapping.
3. **Soft‑launch** Wallet Setup behind feature flag (only users w/o wallet see it).
4. **Monitor** errors & support load; iterate; expand.
5. Optionally **lazy‑create** AA on first on‑chain action to reduce upfront gas.

---

## 12) Testing Strategy

* **Unit**: SIWE builder/validator, nonce repo, AA address derivation.
* **Integration**: credentials login → `/wallet/provision` and `/wallet/connect/siwe`.
* **E2E**: full flows A & B; negatives (expired nonce, duplicate EOA).
* **Security**: replay attempts, RBAC guards, audit immutability.
* **Load**: login bursts, concurrent AA deploys; paymaster behavior.

---

## 13) Operations (RBAC & Merge)

* **Roles**: Viewer, Support, Operator, Finance, Admin, SuperAdmin, Auditor.
* **Permissions**: `users.read`, `wallets.read`, `wallets.link/unlink`, `users.merge_safe`, `users.merge_risky` (dual‑control), `balances.adjust` (thresholded), `audit.read`, `roles.assign`.
* **Merge SOP**: identity proof (fresh SIWE) → conflict scan → diff page → approvals → execute → immutable audit; revert = corrective merge from snapshot.

---

## 14) Acceptance Criteria & Launch Checklist

**Acceptance Criteria**

* Single credentials login works for the BGC/iB ecosystem.
* Wallet Setup (Create/Connect) yields a working **AA**.
* `GET /identity` returns consistent EOA/AA across apps.
* RBAC enforces permissions; all binds/merges are audited.
* Secrets vaulted; rotation tested.

**Launch Checklist**

* [ ] Domains & SSL ready
* [ ] Env vars configured (all envs)
* [ ] AA factory & (optional) paymaster configured
* [ ] E2E suite green on staging
* [ ] Feature flag enabled (soft launch)
* [ ] Dashboards & alerts active
* [ ] Support runbook shared

---

## 15) Change Log

* **Rev D (2025‑10‑13):** Clean rewrite, removed all duplication; stable single‑source structure.
* Rev C (2025‑10‑13): Re‑structured sequence; added detailed Thirdweb guide, Testing/Operations.
* Rev B (2025‑10‑13): Introduced unified auth + post‑login Wallet Setup.
* Rev A (2025‑10‑13): First unified draft.

---

## Appendix — Reference Snippets (Illustrative)

**Client — Create (Embedded) → AA**

```ts
const embedded = await connectEmbeddedWallet({ email }); // returns EOA
const aa = await connectSmartAccount({ personalWallet: embedded, chainId, sponsorGas: true });
await fetch("/api/wallet/provision", { method: "POST", body: JSON.stringify({ eoa: embedded.address, aa: aa.address }) });
```

**Client — Connect (SIWE) → AA**

```ts
const eoa = await connectExternalWallet();
const { message } = await (await fetch("/api/auth/siwe/challenge")).json();
const signature = await eoa.signMessage(message);
await fetch("/api/auth/siwe/verify", { method: "POST", body: JSON.stringify({ message, signature }) });
const aa = await connectSmartAccount({ personalWallet: eoa, chainId, sponsorGas: true });
await fetch("/api/wallet/connect/siwe", { method: "POST", body: JSON.stringify({ eoa: eoa.address, aa: aa.address }) });
```

**Server — SIWE verify (sketch)**

```ts
// verify signature against message + nonce
// check domain/uri/chainId; ensure nonce unused + unexpired; then consume nonce
// bind EOA → identity_id; issue/refresh session; emit audit log
```

---

**End of document.**

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
