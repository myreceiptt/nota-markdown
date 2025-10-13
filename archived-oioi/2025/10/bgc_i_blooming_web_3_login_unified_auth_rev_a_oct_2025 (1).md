# BGC × iBLOOMING — Web3 Login (Unified Auth)
**Revision C — October 13, 2025**  
**Status:** Draft for sign‑off  
**Owners:** Prof. NOTA (Product/Architecture), Yuku (Tech Owner), BGC × iBLOOMING Eng/DevOps

---

## Table of Contents
1. Purpose & Scope  
2. Design Decisions (at a glance)  
3. Non‑Goals & Constraints  
4. System Architecture Overview  
5. User Journeys  
6. Data Model (Unified)  
7. API Specification  
8. Security Model  
9. Thirdweb Integration Guide (Step‑by‑Step)  
10. DevOps & Environments  
11. Migration & Rollout Plan  
12. Testing Strategy  
13. Operations Playbooks (RBAC & Merge)  
14. Acceptance Criteria & Launch Checklist  
15. Change Log  
16. Glossary  
17. Appendix — Reference Snippets

---

## 1) Purpose & Scope
Unify authentication for **BGC** and **iBLOOMING** under a **single credentials database** (same username/password everywhere). After login, users complete a **Wallet Setup** step to either **Create an embedded EOA** (and auto‑provision a Smart Account/AA) or **Connect an existing Web3 wallet** (and auto‑provision AA). This enables consistent on‑chain features (rewards, receipts, payments) across both brands with minimal friction and predictable costs.

**In scope**: identity model, wallet binding, AA provisioning, SIWE, security, DevOps, and a concrete Thirdweb implementation path.  
**Out of scope**: tokenomics rules/ledger logic (PC/SP specifics), business analytics, and non‑auth product features.

---

## 2) Design Decisions (at a glance)
- **Single credentials auth** for BGC × iB (one login surface).  
- **Post‑login** wallet setup: *(A)* **Create EOA (Embedded/MPC)** → **auto AA**, *(B)* **Connect wallet (SIWE)** → **auto AA**.  
- **Deterministic AA** (e.g., CREATE2) per identity/factory/salt.  
- **Identity mapping**: `identity_id ⇄ user_id ⇄ (EOA, AA)`.  
- **Admin Console with RBAC** and auditable merges.  
- **Thirdweb** for SIWE, Embedded/In‑App Wallet, Smart Accounts, and optional Gas Sponsorship.

---

## 3) Non‑Goals & Constraints
**Non‑Goals**  
- No separate user tables per brand.  
- No custom wallet infra or private‑key handling server‑side.

**Constraints**  
- Enforce **unique (address, chain_id)** across `wallets`.  
- SIWE requires **per‑login nonce**, short TTL, domain/URI/chainId checks.  
- Secrets stored in a **vault**; **rotated regularly**.  
- PII minimization and encryption at rest.  
- Production flows must be **observable** (metrics/logs/traces) and **rate‑limited**.

---

## 4) System Architecture Overview
```
[ User ]
  │
  ├─ Credentials Login (Unified) ─────────► [ Auth Service ]
  │                                          │
  │                                          └─ Issues session/JWT { user_id, roles }
  │
  ├─ Post‑Login: Wallet Setup ─────────────► [ Wallet Service ]
  │     ├─ A) Create EOA (Embedded/MPC) ─────► Auto‑create Smart Account (AA)
  │     └─ B) Connect Wallet (SIWE) ─────────► Auto‑create Smart Account (AA)
  │
  └─ BGC / iB apps ───────────────► [ Identity Service ] → { identity_id, eoa, aa }

On‑chain:
[ EOA ] ─(owner/controller)─► [ Smart Account (AA) ] ──(optional)─► Paymaster/Bundler (gas sponsor)
```

---

## 5) User Journeys
### 5.1 New User Sign‑Up
1. User signs up with username/password (MFA optional).  
2. Session starts.  
3. If no wallet bound, show **Wallet Setup**: choose **Create** or **Connect**.  
4. Provision AA; persist identity mapping; done.

### 5.2 Existing User (no wallet yet)
1. Log in with credentials.  
2. Prompt Wallet Setup; complete A or B; AA provisioned; mapping stored.

### 5.3 Existing User (wallet already bound)
1. Log in with credentials.  
2. Skip Wallet Setup; identity already has EOA/AA; continue to app.

---

## 6) Data Model (Unified)
### 6.1 Entities
**`users`** — `user_id` (PK), `email` (unique, nullable), `phone` (unique, nullable), `username` (unique), `password_hash`, `mfa_enabled`, timestamps.  
**`identities`** — `identity_id` (PK), `user_id` (FK→users), timestamps.  
**`wallets`** — `wallet_id` (PK), `identity_id` (FK), `type` (`EOA`|`AA`), `address`, `chain_id`, `salt`, timestamps.  
**`auth_providers`** — `provider_id` (PK), `user_id` (FK), `provider_type` (`credentials`|`siwe`), `provider_ref` (email/phone hash or EOA), timestamps.  
**`audit_logs`** — `log_id` (PK), `identity_id`, `user_id`, `action`, `actor`, `metadata`, timestamps.

### 6.2 Constraints
- `UNIQUE(address, chain_id)` on `wallets`.  
- `type` in (`EOA`, `AA`).  
- FK integrity: `wallets.identity_id` → `identities.identity_id`; `identities.user_id` → `users.user_id`.  
- SIWE nonce table: `nonce` unique, `used` boolean, `expires_at` UTC.

---

## 7) API Specification
**Auth**  
- `POST /auth/credentials/login` → `{ username|email|phone, password }` → `{ session_jwt, user_id }`

**Wallet Setup**  
- `POST /wallet/provision` → uses session → **Create EOA (if missing)** and **deploy AA** → `{ identity_id, eoa, aa }`
- `POST /wallet/connect/siwe` → `{ message, signature }` → verifies SIWE, binds **EOA**, deploys **AA** → `{ identity_id, eoa, aa }`

**Identity**  
- `GET /identity` → uses session → `{ identity_id, eoa, aa }`

**Admin/Audit (internal)**  
- `GET /admin/merge/diff?source&target`  
- `POST /admin/merge/execute` (dual‑control for risky merges)  
- `GET /admin/audit?identity_id|user_id`

---

## 8) Security Model
- **SIWE + per‑login nonce** (3–5 min TTL; nonce consumed upon verify).  
- **Domain/URI/chainId** binding in SIWE messages.  
- **Secrets in vault; rotate regularly** (JWT/JWKS, DB creds, RPC keys, webhook secrets).  
- **RBAC** for Admin Console; two‑person rule for merges affecting balances/affiliates.  
- **PII minimization**; encrypt sensitive fields; strict audit trail.  
- Rate limits for login/OTP/SIWE/merge endpoints; WAF on public APIs.

---

## 9) Thirdweb Integration Guide (Step‑by‑Step)
### 9.1 Map of Capabilities
- **Embedded/In‑App Wallet** → Create EOA for Web2 users.  
- **SIWE (Auth)** → Connect existing EOA securely.  
- **Smart Accounts (AA)** → Deterministic AA per identity; sponsor gas via **Paymaster/Bundler**.  
- **WalletConnect** → UX for mobile/extension wallets.

### 9.2 Client Setup (Web)
1. Install Thirdweb SDK; wrap app with provider (chains, clientId, optional AA/paymaster).  
2. After credentials login, open **Wallet Setup** modal with two buttons: **Create Wallet** (Embedded) or **Connect Wallet** (SIWE).  
3. **Create Wallet**: trigger embedded wallet flow (email/OTP, phone, passkey, social) → get **EOA** → instantiate **Smart Account** (optionally `sponsorGas: true`).  
4. **Connect Wallet**: connect via WalletConnect/extension → request SIWE challenge from server → user signs → server verifies → instantiate **Smart Account** for that EOA.  
5. POST results to backend for persistence (`/wallet/provision` or `/wallet/connect/siwe`).

### 9.3 Server Setup (Auth + Identity)
1. **Credentials login**: issue session/JWT (`user_id`, roles).  
2. **SIWE challenge** endpoint: create cryptographically random `nonce`, store with TTL (`used=false`).  
3. **SIWE verify**: recover address from signature; validate domain/uri/chainId; check nonce unused/unexpired; **consume** nonce; bind EOA→identity; extend session.  
4. **Provision AA**: call AA factory with deterministic salt (e.g., derived from `identity_id`), persist AA address.  
5. **Audit**: log all binds/merges; expose `GET /identity` for apps.

### 9.4 Environment Variables
`THIRDWEB_CLIENT_ID`, `CHAIN_ID`, `RPC_URL`, `AA_FACTORY_ADDRESS`, `PAYMASTER_URL` (optional), `WALLETCONNECT_PROJECT_ID`, `JWT_SECRET`, `AUTH_DOMAIN`, `SIWE_STATEMENT`.

### 9.5 Error Handling & Cost Controls
- Retry‑with‑backoff for AA deploy; fall back to **lazy deploy** on first tx if applicable.  
- Gas sponsorship **scopes** (onboarding only, per‑action caps); budget alerts.  
- Clear UX on wrong network/expired nonce/denied signature.

---

## 10) DevOps & Environments
- **Domains**: `auth.bgcxib.com` (unified), app domains per brand.  
- **CI/CD**: build/lint/typecheck; e2e flows (A & B); smoke tests for JWT issuance, SIWE verify, AA deploy.  
- **Observability**: metrics (login success/error, SIWE failures, AA deploy success), logs, traces; alerting thresholds for gas spend and failure spikes.  
- **Access**: DevOps/Tech Lead manages secrets, env promotion, AA factory; MFA on all admin access.

---

## 11) Migration & Rollout Plan
1. **Inventory** user stores; pick the **source of truth** (`users`).  
2. **Deduplicate** historic BGC/iB accounts into unified `users`; maintain mapping for audits.  
3. **Soft launch** Wallet Setup behind feature flag (only users without wallet see it).  
4. **Monitor** errors/support load; iterate; gradually expand.  
5. Optionally **lazy‑create** AA on first on‑chain action to reduce upfront gas.

---

## 12) Testing Strategy
- **Unit**: SIWE message builder/validator, nonce repository, AA address derivation.  
- **Integration**: `/auth/credentials/login` → `/wallet/provision` and `/wallet/connect/siwe`.  
- **E2E**: full flows A & B, including negative paths (expired nonce, duplicate EOA).  
- **Security**: replay attempts, RBAC route guards, audit immutability.  
- **Load**: login bursts, AA deploy concurrency; paymaster rate behavior.

---

## 13) Operations Playbooks (RBAC & Merge)
- **Roles**: Viewer, Support, Operator, Finance, Admin, SuperAdmin, Auditor.  
- **Permissions**: `users.read`, `wallets.read`, `wallets.link/unlink`, `users.merge_safe`, `users.merge_risky` (dual‑control), `balances.adjust` (thresholded), `audit.read`, `roles.assign`.  
- **Merge SOP**: identity proof (fresh SIWE) → conflict scan → diff page → approvals → execute → immutable audit; revert plan = corrective merge from snapshot.

---

## 14) Acceptance Criteria & Launch Checklist
**Acceptance Criteria**  
- Single credentials login works for both brands.  
- Wallet Setup lets users **Create** or **Connect** and yields a working **AA**.  
- `GET /identity` returns consistent EOA/AA across apps.  
- RBAC enforces permissions; all binds/merges audited.  
- Secrets vaulted and rotation tested.

**Launch Checklist**  
- [ ] Domains & SSL ready  
- [ ] Env vars configured (all environments)  
- [ ] AA factory & (optional) paymaster configured  
- [ ] E2E suite green on staging  
- [ ] Feature flag enabled (soft launch)  
- [ ] Dashboards & alerts active  
- [ ] Runbook shared with Support

---

## 15) Change Log
- **Rev C (2025‑10‑13):** Re‑structured document for clarity and sequence; added detailed Thirdweb guide and improved Testing/Operations sections.  
- Rev B (2025‑10‑13): Unified auth, post‑login wallet setup, slim APIs, security notes.  
- Rev A (2025‑10‑13): First unified draft.

---

## 16) Glossary
- **EOA** — Externally Owned Account (wallet controlled by private key).  
- **AA** — Smart Account (account abstraction) controlled by an EOA; deterministic per factory/salt.  
- **SIWE** — Sign‑In With Ethereum (EIP‑4361) signed challenge.  
- **Embedded/MPC Wallet** — In‑app wallet; no plaintext keys server‑side.  
- **RBAC** — Role‑Based Access Control.  
- **Paymaster/Bundler** — Infra for gasless/sponsored transactions in AA.

---

## 17) Appendix — Reference Snippets (Illustrative)
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
// verify signature ↔ message; check domain/uri/chainId; nonce unused; consume nonce
// bind EOA → identity_id; issue/refresh session JWT; emit audit log
```
# BGC × iBLOOMING — Web3 Login (Unified Auth)
**Revision C — October 13, 2025**  
**Status:** Draft for sign‑off  
**Owners:** Prof. NOTA (Product/Architecture), Yuku (Tech Owner), BGC × iBLOOMING Eng/DevOps

---

## Table of Contents
1. Purpose & Scope  
2. Design Decisions (at a glance)  
3. Non‑Goals & Constraints  
4. System Architecture Overview  
5. User Journeys  
6. Data Model (Unified)  
7. API Specification  
8. Security Model  
9. Thirdweb Integration Guide (Step‑by‑Step)  
10. DevOps & Environments  
11. Migration & Rollout Plan  
12. Testing Strategy  
13. Operations Playbooks (RBAC & Merge)  
14. Acceptance Criteria & Launch Checklist  
15. Change Log  
16. Glossary  
17. Appendix — Reference Snippets

---

## 1) Purpose & Scope
Unify authentication for **BGC** and **iBLOOMING** under a **single credentials database** (same username/password everywhere). After login, users complete a **Wallet Setup** step to either **Create an embedded EOA** (and auto‑provision a Smart Account/AA) or **Connect an existing Web3 wallet** (and auto‑provision AA). This enables consistent on‑chain features (rewards, receipts, payments) across both brands with minimal friction and predictable costs.

**In scope**: identity model, wallet binding, AA provisioning, SIWE, security, DevOps, and a concrete Thirdweb implementation path.  
**Out of scope**: tokenomics rules/ledger logic (PC/SP specifics), business analytics, and non‑auth product features.

---

## 2) Design Decisions (at a glance)
- **Single credentials auth** for BGC × iB (one login surface).  
- **Post‑login** wallet setup: *(A)* **Create EOA (Embedded/MPC)** → **auto AA**, *(B)* **Connect wallet (SIWE)** → **auto AA**.  
- **Deterministic AA** (e.g., CREATE2) per identity/factory/salt.  
- **Identity mapping**: `identity_id ⇄ user_id ⇄ (EOA, AA)`.  
- **Admin Console with RBAC** and auditable merges.  
- **Thirdweb** for SIWE, Embedded/In‑App Wallet, Smart Accounts, and optional Gas Sponsorship.

---

## 3) Non‑Goals & Constraints
**Non‑Goals**  
- No separate user tables per brand.  
- No custom wallet infra or private‑key handling server‑side.

**Constraints**  
- Enforce **unique (address, chain_id)** across `wallets`.  
- SIWE requires **per‑login nonce**, short TTL, domain/URI/chainId checks.  
- Secrets stored in a **vault**; **rotated regularly**.  
- PII minimization and encryption at rest.  
- Production flows must be **observable** (metrics/logs/traces) and **rate‑limited**.

---

## 4) System Architecture Overview
```
[ User ]
  │
  ├─ Credentials Login (Unified) ─────────► [ Auth Service ]
  │                                          │
  │                                          └─ Issues session/JWT { user_id, roles }
  │
  ├─ Post‑Login: Wallet Setup ─────────────► [ Wallet Service ]
  │     ├─ A) Create EOA (Embedded/MPC) ─────► Auto‑create Smart Account (AA)
  │     └─ B) Connect Wallet (SIWE) ─────────► Auto‑create Smart Account (AA)
  │
  └─ BGC / iB apps ───────────────► [ Identity Service ] → { identity_id, eoa, aa }

On‑chain:
[ EOA ] ─(owner/controller)─► [ Smart Account (AA) ] ──(optional)─► Paymaster/Bundler (gas sponsor)
```

---

## 5) User Journeys
### 5.1 New User Sign‑Up
1. User signs up with username/password (MFA optional).  
2. Session starts.  
3. If no wallet bound, show **Wallet Setup**: choose **Create** or **Connect**.  
4. Provision AA; persist identity mapping; done.

### 5.2 Existing User (no wallet yet)
1. Log in with credentials.  
2. Prompt Wallet Setup; complete A or B; AA provisioned; mapping stored.

### 5.3 Existing User (wallet already bound)
1. Log in with credentials.  
2. Skip Wallet Setup; identity already has EOA/AA; continue to app.

---

## 6) Data Model (Unified)
### 6.1 Entities
**`users`** — `user_id` (PK), `email` (unique, nullable), `phone` (unique, nullable), `username` (unique), `password_hash`, `mfa_enabled`, timestamps.  
**`identities`** — `identity_id` (PK), `user_id` (FK→users), timestamps.  
**`wallets`** — `wallet_id` (PK), `identity_id` (FK), `type` (`EOA`|`AA`), `address`, `chain_id`, `salt`, timestamps.  
**`auth_providers`** — `provider_id` (PK), `user_id` (FK), `provider_type` (`credentials`|`siwe`), `provider_ref` (email/phone hash or EOA), timestamps.  
**`audit_logs`** — `log_id` (PK), `identity_id`, `user_id`, `action`, `actor`, `metadata`, timestamps.

### 6.2 Constraints
- `UNIQUE(address, chain_id)` on `wallets`.  
- `type` in (`EOA`, `AA`).  
- FK integrity: `wallets.identity_id` → `identities.identity_id`; `identities.user_id` → `users.user_id`.  
- SIWE nonce table: `nonce` unique, `used` boolean, `expires_at` UTC.

---

## 7) API Specification
**Auth**  
- `POST /auth/credentials/login` → `{ username|email|phone, password }` → `{ session_jwt, user_id }`

**Wallet Setup**  
- `POST /wallet/provision` → uses session → **Create EOA (if missing)** and **deploy AA** → `{ identity_id, eoa, aa }`
- `POST /wallet/connect/siwe` → `{ message, signature }` → verifies SIWE, binds **EOA**, deploys **AA** → `{ identity_id, eoa, aa }`

**Identity**  
- `GET /identity` → uses session → `{ identity_id, eoa, aa }`

**Admin/Audit (internal)**  
- `GET /admin/merge/diff?source&target`  
- `POST /admin/merge/execute` (dual‑control for risky merges)  
- `GET /admin/audit?identity_id|user_id`

---

## 8) Security Model
- **SIWE + per‑login nonce** (3–5 min TTL; nonce consumed upon verify).  
- **Domain/URI/chainId** binding in SIWE messages.  
- **Secrets in vault; rotate regularly** (JWT/JWKS, DB creds, RPC keys, webhook secrets).  
- **RBAC** for Admin Console; two‑person rule for merges affecting balances/affiliates.  
- **PII minimization**; encrypt sensitive fields; strict audit trail.  
- Rate limits for login/OTP/SIWE/merge endpoints; WAF on public APIs.

---

## 9) Thirdweb Integration Guide (Step‑by‑Step)
### 9.1 Map of Capabilities
- **Embedded/In‑App Wallet** → Create EOA for Web2 users.  
- **SIWE (Auth)** → Connect existing EOA securely.  
- **Smart Accounts (AA)** → Deterministic AA per identity; sponsor gas via **Paymaster/Bundler**.  
- **WalletConnect** → UX for mobile/extension wallets.

### 9.2 Client Setup (Web)
1. Install Thirdweb SDK; wrap app with provider (chains, clientId, optional AA/paymaster).  
2. After credentials login, open **Wallet Setup** modal with two buttons: **Create Wallet** (Embedded) or **Connect Wallet** (SIWE).  
3. **Create Wallet**: trigger embedded wallet flow (email/OTP, phone, passkey, social) → get **EOA** → instantiate **Smart Account** (optionally `sponsorGas: true`).  
4. **Connect Wallet**: connect via WalletConnect/extension → request SIWE challenge from server → user signs → server verifies → instantiate **Smart Account** for that EOA.  
5. POST results to backend for persistence (`/wallet/provision` or `/wallet/connect/siwe`).

### 9.3 Server Setup (Auth + Identity)
1. **Credentials login**: issue session/JWT (`user_id`, roles).  
2. **SIWE challenge** endpoint: create cryptographically random `nonce`, store with TTL (`used=false`).  
3. **SIWE verify**: recover address from signature; validate domain/uri/chainId; check nonce unused/unexpired; **consume** nonce; bind EOA→identity; extend session.  
4. **Provision AA**: call AA factory with deterministic salt (e.g., derived from `identity_id`), persist AA address.  
5. **Audit**: log all binds/merges; expose `GET /identity` for apps.

### 9.4 Environment Variables
`THIRDWEB_CLIENT_ID`, `CHAIN_ID`, `RPC_URL`, `AA_FACTORY_ADDRESS`, `PAYMASTER_URL` (optional), `WALLETCONNECT_PROJECT_ID`, `JWT_SECRET`, `AUTH_DOMAIN`, `SIWE_STATEMENT`.

### 9.5 Error Handling & Cost Controls
- Retry‑with‑backoff for AA deploy; fall back to **lazy deploy** on first tx if applicable.  
- Gas sponsorship **scopes** (onboarding only, per‑action caps); budget alerts.  
- Clear UX on wrong network/expired nonce/denied signature.

---

## 10) DevOps & Environments
- **Domains**: `auth.bgcxib.com` (unified), app domains per brand.  
- **CI/CD**: build/lint/typecheck; e2e flows (A & B); smoke tests for JWT issuance, SIWE verify, AA deploy.  
- **Observability**: metrics (login success/error, SIWE failures, AA deploy success), logs, traces; alerting thresholds for gas spend and failure spikes.  
- **Access**: DevOps/Tech Lead manages secrets, env promotion, AA factory; MFA on all admin access.

---

## 11) Migration & Rollout Plan
1. **Inventory** user stores; pick the **source of truth** (`users`).  
2. **Deduplicate** historic BGC/iB accounts into unified `users`; maintain mapping for audits.  
3. **Soft launch** Wallet Setup behind feature flag (only users without wallet see it).  
4. **Monitor** errors/support load; iterate; gradually expand.  
5. Optionally **lazy‑create** AA on first on‑chain action to reduce upfront gas.

---

## 12) Testing Strategy
- **Unit**: SIWE message builder/validator, nonce repository, AA address derivation.  
- **Integration**: `/auth/credentials/login` → `/wallet/provision` and `/wallet/connect/siwe`.  
- **E2E**: full flows A & B, including negative paths (expired nonce, duplicate EOA).  
- **Security**: replay attempts, RBAC route guards, audit immutability.  
- **Load**: login bursts, AA deploy concurrency; paymaster rate behavior.

---

## 13) Operations Playbooks (RBAC & Merge)
- **Roles**: Viewer, Support, Operator, Finance, Admin, SuperAdmin, Auditor.  
- **Permissions**: `users.read`, `wallets.read`, `wallets.link/unlink`, `users.merge_safe`, `users.merge_risky` (dual‑control), `balances.adjust` (thresholded), `audit.read`, `roles.assign`.  
- **Merge SOP**: identity proof (fresh SIWE) → conflict scan → diff page → approvals → execute → immutable audit; revert plan = corrective merge from snapshot.

---

## 14) Acceptance Criteria & Launch Checklist
**Acceptance Criteria**  
- Single credentials login works for both brands.  
- Wallet Setup lets users **Create** or **Connect** and yields a working **AA**.  
- `GET /identity` returns consistent EOA/AA across apps.  
- RBAC enforces permissions; all binds/merges audited.  
- Secrets vaulted and rotation tested.

**Launch Checklist**  
- [ ] Domains & SSL ready  
- [ ] Env vars configured (all environments)  
- [ ] AA factory & (optional) paymaster configured  
- [ ] E2E suite green on staging  
- [ ] Feature flag enabled (soft launch)  
- [ ] Dashboards & alerts active  
- [ ] Runbook shared with Support

---

## 15) Change Log
- **Rev C (2025‑10‑13):** Re‑structured document for clarity and sequence; added detailed Thirdweb guide and improved Testing/Operations sections.  
- Rev B (2025‑10‑13): Unified auth, post‑login wallet setup, slim APIs, security notes.  
- Rev A (2025‑10‑13): First unified draft.

---

## 16) Glossary
- **EOA** — Externally Owned Account (wallet controlled by private key).  
- **AA** — Smart Account (account abstraction) controlled by an EOA; deterministic per factory/salt.  
- **SIWE** — Sign‑In With Ethereum (EIP‑4361) signed challenge.  
- **Embedded/MPC Wallet** — In‑app wallet; no plaintext keys server‑side.  
- **RBAC** — Role‑Based Access Control.  
- **Paymaster/Bundler** — Infra for gasless/sponsored transactions in AA.

---

## 17) Appendix — Reference Snippets (Illustrative)
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
// verify signature ↔ message; check domain/uri/chainId; nonce unused; consume nonce
// bind EOA → identity_id; issue/refresh session JWT; emit audit log
```
