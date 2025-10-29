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
**First Version**: [Web3 Login Identity Bridge](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=UuIVClWGsW8J9R2NdfWZ&only=yes&limit=100)  
**Status:** Draft for sign-off (clean, single-source)  
**Owners:** Prof. NOTA (Product/Architecture), Yuku (Tech Owner), BGC × iBLOOMING Eng/DevOps

---

## Table of Contents

1. [Purpose & Scope](#id-1-purpose-and-scope)  
2. [Key Decisions](#id-2-key-decisions)  
3. [Constraints & Non-Goals](#id-3-constraints-and-non-goals)  
4. [Architecture Overview](#id-4-architecture-overview)  
5. [User Journeys](#id-5-user-journeys)  
6. [Data Model (Unified)](#id-6-data-model-unified)  
7. [API Specification](#id-7-api-specification)  
8. [Security Model](#id-8-security-model)  
9. [Thirdweb Integration — Step-by-Step](#id-9-thirdweb-integration-step-by-step)  
10. [DevOps & Environments](#id-10-devops-and-environments)  
11. [Migration & Rollout](#id-11-migration-and-rollout)  
12. [Testing Strategy](#id-12-testing-strategy)  
13. [Operations (RBAC & Merge)](#id-13-operations-rbac-and-merge)  
14. [Acceptance Criteria & Launch Checklist](#id-14-acceptance-criteria-and-launch-checklist)  
15. [Appendix — Reference Snippets](#appendix-reference-snippets-illustrative)
16. [Appendix — Cost Estimates (Non-HR)](#appendix-cost-estimates-non-hr)

---

## 1) Purpose & Scope

We operate on a **single, unified credentials database (already in production)** for BGC and iBLOOMING. Users can sign up and log in to any app (BGC Web, iBLOOMING Web, iBLOOMING Mobile) with the **same username/password** and, during rollout, may also authenticate with a **Passkey (WebAuthn)** as a first-class method.

After login, users complete **Wallet Setup** by either:

- **Create EOA (Embedded/In-App)** → **auto-provision a Smart Account (AA)**; or  
- **Connect existing wallet (SIWE)** → **auto-provision a Smart Account (AA)**.

This standardizes on-chain identity to **one EOA and one Smart Account (AA) per user per chain**, enabling consistent features (rewards, receipts, payments) across the BGC/iB ecosystem with minimal friction and predictable costs.

**Bridging Web2 ↔ Web3.** If a user does not yet have a BGC/iB account, they must first **sign up** for a BGC/iB account and then **log in** (via username/password or **Passkey**). Only **after** a successful login is **Wallet Setup** available: either **Create an embedded EOA → auto-provision AA** or **Connect an existing Web3 wallet → auto-provision AA**. Web3-native users who already have a BGC/iB account simply log in and proceed to Wallet Setup.

**Analytics & simulations.** The unified mapping `user_id ⇄ identity_id ⇄ (EOA, AA)` enables reliable, on-chain-addressed telemetry for behavioral simulations (Alpha Coin → future iBC/iBTC).

**Partner signal.** A single, **passkey-enabled** login and **post-login Smart Account bootstrap** operating across apps demonstrates concrete momentum while tokenomics is finalized.

**In scope:** identity model, wallet binding, AA provisioning, SIWE, **Passkey support**, security, DevOps, and Thirdweb implementation.  
**Out of scope:** tokenomics/ledger rules, analytics dashboards, and non-auth product features.

## 2) Key Decisions

- **Single credentials auth** for the BGC/iB ecosystem.  
- **Passkey (WebAuthn)** as a first-class login method (rolling out), with username/password fallback.  
- **Post-login Wallet Setup** (Create or Connect), not pre-login.  
- **Deterministic AA** per identity (factory + salt).  
- **Identity mapping:** `identity_id ⇄ user_id ⇄ (EOA, AA)`.  
- **Admin Console with RBAC** and full audit for binds/merges.  
- **Thirdweb** supplies SIWE, Embedded/In-App Wallet, Smart Accounts, and optional gas sponsorship.

---

## 3) Constraints & Non-Goals

**Constraints**

- **Unified DB & identity**
  - Single credentials store across BGC/iB; no per-app user tables.
  - One on-chain identity per user per chain: **exactly 1 EOA + 1 AA**.
  - DB integrity:
    - `wallets`: `UNIQUE(address, chain_id)` and `CHECK (type IN ('EOA','AA'))`
    - Enforce **one-per-chain** with `UNIQUE(identity_id, type, chain_id)`  (so a user can’t end up with multiple EOAs/AAs on the same chain).

- **SIWE (existing wallets)**
  - **Per-login nonce** (TTL 3–5 minutes); nonce **consumed** on successful verify.
  - Validate **domain / origin URI / chainId**; reject cross-site replay.
  - All SIWE traffic over TLS; audit message + `address` + `nonce` usage.

- **Passkey (WebAuthn)**
  - RP config pinned: **`rpId` = auth domain**, allowed **origins** explicit.
  - **userVerification = required**; **resident/discoverable keys** enabled.
  - Attestation policy defined (e.g., `none`); store `credential_id` (unique), `public_key`, `sign_count` (monotonic), transports, backup flags.
  - Device lifecycle supported: list & revoke passkeys per user.

- **Smart Accounts (AA)**
  - Deterministic deployment (factory + salt); one factory **per chain** per environment.
  - Optional gas sponsorship via paymaster/bundler with **budget caps** and alerting.

- **Secrets & privacy**
  - Secrets in **vault**; **regular rotation** (JWT/JWKS, DB, RPC, webhooks).
  - PII minimization; sensitive fields encrypted at rest.
  - Observability + rate-limits for login/OTP/SIWE/AA endpoints; immutable audits for binds/merges.

- **In-App Wallet (Starter plan)** uses Thirdweb’s built-in OTP (Email/Phone) for **Create Wallet**; **no BYO-Auth/JWT** for wallet creation in this phase.

**Non-Goals**

- No separate user tables per app within the BGC/iB ecosystem.
- No server-side plaintext key handling for wallets (embedded/MPC only).

---

## 4) Architecture Overview

```text
[ User ]
   │
   ├─ If new: Sign up BGC/iB account
   │
   ├─ Login (Credentials or Passkey/WebAuthn)
   │         └─ [ Auth Service ] — issues session/JWT { user_id, roles }
   │
   ├─ Post‑Login: Wallet Setup
   │      ├─ A) Create EOA (Embedded/In‑App) ─────────────► [ Wallet Service ]
   │      │                                                 │
   │      │                                                 └─► [ AA Factory ] — deploy **Smart Account (AA)**
   │      │                                                        (deterministic per chain: factory + salt)
   │      └─ B) Connect Existing Wallet (SIWE) ───────────► [ SIWE Verify ] ─────┘
   │
   ├─ Persist mapping ────────────────────────────────────► [ Identity Service ] → { identity_id, eoa, aa }
   │                                                       └─► [ Audit Log ] (immutable)
   │
   └─ Apps (BGC Web, iB Web/Mobile) ─────────────────────► consume identity & roles

On‑chain:
[ EOA ] (owner/controller) ─────────► [ Smart Account (AA) ] ─────────► (optional) [ Paymaster / Bundler ]
```

---

## 5) User Journeys

**5.1 New User (no BGC/iB account yet)**  
1) **Sign up** a BGC/iB account (username/password; offer **Passkey** registration during or after signup).  
2) **Log in** using credentials or **Passkey** (MFA optional per policy).  
3) **Wallet Setup** (post-login): choose **Create** or **Connect**.  
4) **AA provisioned** deterministically → Done.

**5.2 Existing User (no wallet yet)**  
1) **Log in** (credentials or **Passkey**).  
2) **Wallet Setup** (Create or Connect).  
3) **AA provisioned** → Done.

**5.3 Existing User (wallet already bound)**  
1) **Log in** (credentials or **Passkey**).  
2) **Skip Wallet Setup**; identity already has EOA/AA.  
3) Proceed to app.

---

## 6) Data Model (Unified)

**users**  
- `user_id` (PK), `email` (unique, nullable), `phone` (unique, nullable), `username` (unique), `password_hash`, `mfa_enabled`, timestamps.

**webauthn_credentials**  
- `credential_id` (PK, b64url), `user_id` (FK→users), `public_key`, `sign_count`, `transports`, `backup_eligible`, `backed_up`, timestamps.

**identities**  
- `identity_id` (PK), `user_id` (FK→users), timestamps. *(Keeps future merge/link options without breaking unification.)*  

**wallets**  
- `wallet_id` (PK), `identity_id` (FK), `type` (`EOA`|`AA`), `address`, `chain_id`, `salt`, timestamps.  

**auth_providers**  
- `provider_id` (PK), `user_id` (FK), `provider_type` (`credentials`|`siwe`), `provider_ref` (email/phone hash or EOA), timestamps.  

**siwe_nonces**  
- `nonce` (PK), `used` (boolean), `expires_at` (UTC), `issued_for_domain`, `issued_for_uri`, timestamps.

**audit_logs**  
- `log_id` (PK), `identity_id`, `user_id`, `action` (`bind`|`merge`|`unlink`|`passkey.register`|`passkey.login`), `actor`, `metadata`, timestamps.  

**Constraints**  
- `wallets`: `UNIQUE(address, chain_id)`; `CHECK (type IN ('EOA','AA'))`; `UNIQUE(identity_id, type, chain_id)` ensures **one EOA and one AA per chain**.  
- `webauthn_credentials.credential_id` unique; `sign_count` monotonic (reject regressions).  
- `siwe_nonces.nonce` unique; must be **unused** and **unexpired** at verify time.  
- FK integrity enforced across all relations.

---

## 7) API Specification

**Auth**  
- `POST /auth/credentials/login` → `{ username|email|phone, password }` → `{ session_jwt, user_id }`  
- `POST /auth/passkey/register/options` → server generates WebAuthn **attestation options**  
- `POST /auth/passkey/register/verify` → verify attestation; persist credential; return `{ session_jwt? }`  
- `POST /auth/passkey/login/options` → server generates WebAuthn **assertion options**  
- `POST /auth/passkey/login/verify` → verify assertion; start session → `{ session_jwt, user_id }`  
- *(optional)* `GET /auth/passkey/devices` & `DELETE /auth/passkey/devices/:credential_id`

**Wallet Setup**  
- `POST /wallet/provision` → uses session → Create **EOA** (if missing) + deploy **AA** → `{ identity_id, eoa, aa }`  
- `POST /wallet/connect/siwe` → `{ message, signature }` → verify SIWE (domain/uri/chainId + nonce), bind **EOA**, deploy **AA** → `{ identity_id, eoa, aa }`

**Identity**  
- `GET /identity` → session → `{ identity_id, eoa, aa }`

**Admin/Audit**  
- `GET /admin/merge/diff?source&target`  
- `POST /admin/merge/execute` (dual-control for risky merges)  
- `GET /admin/audit?identity_id|user_id`

---

## 8) Security Model

- **Passkey (WebAuthn)**  
  - `rpId` = auth domain; **allowed origins** explicitly listed.  
  - `userVerification = required`; **resident/discoverable** credentials enabled.  
  - Attestation policy defined (e.g., `none`); store `credential_id`, `public_key`, **monotonic `sign_count`**.  
  - Device lifecycle: list/revoke passkeys; backup codes for account recovery.

- **Credentials**  
  - Password hashing with **Argon2id** (memory-hard), strong parameters; lockout + step-up on anomalies.

- **SIWE (existing wallets)**  
  - **Per-login nonce** (TTL 3–5 min); consume on success; reject reused/expired.  
  - Validate **domain / URI / chainId**; enforce TLS; audit `address` + message + nonce usage.

- **Smart Accounts (AA)**  
  - Deterministic deployment (factory + salt) per chain; monitor deploy success rate; optional **paymaster/bundler** with budget caps and alerts.

- **Sessions & secrets**  
  - Short-lived JWT; **HttpOnly + Secure** cookies; rotation on refresh; CSRF protection on state-changing routes.  
  - Secrets in **vault**; **regular rotation** (JWT/JWKS, DB creds, RPC, webhooks).

- **Privacy, observability & abuse prevention**  
  - PII minimization; encryption at rest.  
  - Rate-limit login/OTP/SIWE/merge; WAF on public APIs.  
  - Immutable audits for binds/merges/passkey events; anomaly detection dashboards.

---

## 9) Thirdweb Integration — Step-by-Step

**9.1 Capabilities used**
- **In-App (Embedded) Wallet — built-in auth via Email OTP or Phone OTP** (Starter plan; no Thirdweb Passkey/Social for wallet creation).
- **SIWE (Auth)** for existing wallets (Connect Wallet).
- **Smart Accounts (AA)** with deterministic deployment (factory + salt).
- **WalletConnect** for UX.
- Optional **Paymaster/Bundler** for gas sponsorship.

**9.2 Client (Web)**
1) After a successful BGC/iB login (credentials/Passkey handled by our system), open a **custom modal with exactly two buttons**:
   - **Create Wallet** (In-App Wallet, built-in)
   - **Connect Wallet** (External + SIWE)

2) **Create Wallet** (In-App, built-in)
   - Prefer **Email OTP** if `user.email` exists; otherwise use **Phone OTP** if `user.phone` exists.
   - Invoke Thirdweb In-App Wallet with the corresponding **built-in strategy** (`strategy: "email"` or `strategy: "phone"`).
   - After OTP verification, obtain **EOA**, then instantiate **AA** (`sponsorGas: true` if applicable).
   - Persist `{ eoa, aa }` via `/wallet/provision`.

3) **Connect Wallet** (External + SIWE)
   - Let the user choose an external wallet (e.g., MetaMask / Phantom (EVM) / Coinbase) via WalletConnect/extension.
   - Request SIWE **challenge** from server → user signs → server **verifies** (nonce, domain/uri/chainId).
   - Instantiate **AA** for that EOA; persist `{ eoa, aa }` via `/wallet/connect/siwe`.

4) **Guardrails & UX**
   - If neither `email` nor `phone` is available, prompt the user to add one before Create Wallet.
   - Rate-limit Create Wallet to avoid OTP spam; show clear copy that the OTP is sent by the wallet provider.
   - Deduplicate on the backend (one EOA/AA per chain).

**9.3 Server (Auth + Identity)**
- **Credentials/Passkey login**: issue session/JWT `{ user_id, roles }`. (Passkey ceremonies handled by WebAuthn endpoints in the Auth service.)  
- **SIWE challenge**: generate cryptographic `nonce`, store (`used=false`, TTL 3–5 min).  
- **SIWE verify**: recover `address`, validate `domain/uri/chainId`, ensure nonce **unused** and **unexpired**, then **consume** nonce; bind `EOA → identity`; issue/refresh session.  
- **Provision AA**: call the AA factory with a deterministic salt (e.g., derived from `identity_id`); persist AA address.  
- **Audit**: log every bind/merge; expose `GET /identity`.

**9.4 Environment Variables**  
- `THIRDWEB_CLIENT_ID`  
- `CHAIN_ID`  
- `RPC_URL`  
- `AA_FACTORY_ADDRESS`  
- `PAYMASTER_URL` (optional)  
- `WALLETCONNECT_PROJECT_ID`  
- `JWT_SECRET`  
- `AUTH_DOMAIN`  
- `AUTH_RP_ID` (WebAuthn rpId, usually equal to `AUTH_DOMAIN`)  
- `AUTH_ALLOWED_ORIGINS` (comma-separated, for WebAuthn)  
- `SIWE_STATEMENT`

**9.5 Error Handling & Cost Controls**
- Retry with backoff for AA deploy; allow **lazy deploy** on first tx if applicable.  
- Scope gas sponsorship (onboarding only, per-action caps); alerts on budget.  
- Clear UX for wrong network / expired nonce / denied signature.

---

## 10) DevOps & Environments

- **Domains**: `auth.bgcxib.com` (unified), brand app domains.  
- **CI/CD**: build/lint/typecheck; E2E flows (Create & Connect); smoke tests for JWT issuance, SIWE verify, AA deploy.  
- **Observability**: metrics (login success/error, **passkey adoption**, SIWE failures, AA deployment success), logs, traces; alerts for gas spend and failure spikes.  
- **Mobile/WebView**: confirm WebAuthn origins (`AUTH_RP_ID`/allowed origins) and Thirdweb mobile support paths.  
- **Access**: DevOps/Tech Lead manages secrets, env promotion, AA factory; MFA enforced.

---

## 11) Migration & Rollout

1) **Inventory** current user stores; pick the **source of truth** (`users`).  
2) **Deduplicate** historic BGC/iB accounts into unified `users`; preserve audit mapping.  
3) **Soft-launch** Wallet Setup behind a feature flag (only users without a wallet see it).  
4) **Monitor** errors & support load; iterate; expand scope.  
5) Optionally **lazy-create** AA on first on-chain action to reduce upfront gas.

---

## 12) Testing Strategy

- **Unit**: SIWE message builder/validator; nonce repository; AA address derivation; WebAuthn option/response validators.  
- **Integration**: credentials/Passkey login → `/wallet/provision` and `/wallet/connect/siwe`.  
- **E2E**: full flows A (Embedded) & B (SIWE); negative paths (expired/reused nonce, wrong domain/chainId, duplicate EOA).  
- **Security**: replay attempts, RBAC route guards, immutable audit checks; Passkey `sign_count` monotonicity.  
- **Load**: login bursts; concurrent AA deploys; paymaster behavior under throttle.

---

## 13) Operations (RBAC & Merge)

- **Roles**: Viewer, Support, Operator, Finance, Admin, SuperAdmin, Auditor.  
- **Permissions**: `users.read`, `wallets.read`, `wallets.link/unlink`, `users.merge_safe`, `users.merge_risky` (dual-control), `balances.adjust` (thresholded), `audit.read`, `roles.assign`.  
- **Merge SOP**: identity proof (fresh SIWE for wallet-affecting changes) → conflict scan → diff page → approvals → execute → immutable audit; revert = corrective merge from snapshot.

---

## 14) Acceptance Criteria & Launch Checklist

**Acceptance Criteria**  
- Single credentials login (with **Passkey** support) works across BGC/iB.  
- Wallet Setup (Create/Connect) yields a working **AA**.  
- `GET /identity` returns consistent EOA/AA across apps.  
- RBAC enforces permissions; all binds/merges audited.  
- Secrets vaulted; rotation tested.

**Launch Checklist**  
- [ ] Domains & SSL ready  
- [ ] Env vars configured (all envs)  
- [ ] AA factory & (optional) paymaster configured  
- [ ] E2E suite green on staging  
- [ ] Feature flag enabled (soft launch)  
- [ ] Dashboards & alerts active (incl. passkey & AA metrics)  
- [ ] Support runbook shared

---

## Appendix — Reference Snippets (Illustrative)

> Notes  
> - Snippets are **illustrative** (TypeScript/Next.js style).  
> - Replace SDK calls with the exact Thirdweb functions used in your repo.  
> - Always handle errors, network checks, and feature flags in production.

---

### A) Client — **Create (Embedded/In-App)** → EOA → **AA**

```ts
// WalletSetupCreate.ts
// Trigger embedded wallet (**email OTP** or **phone OTP**) → get EOA → build AA.
import { connectEmbeddedWallet, connectSmartAccount } from "@/lib/wallet"; // wrap actual SDK calls

export async function createEmbeddedAA(params: {
  email?: string;
  usePasskey?: boolean;
  chainId: number;
  sponsorGas?: boolean;
}) {
  // 1) Create/attach an embedded EOA (choose one: **email OTP** or **phone OTP**)
  const eoa = await connectEmbeddedWallet({
    email: params.email,
    passkey: params.usePasskey === true,
  }); // returns { address, signMessage, ... }

  // 2) Build a Smart Account (AA) on top of that EOA
  const aa = await connectSmartAccount({
    personalWallet: eoa,
    chainId: params.chainId,
    sponsorGas: params.sponsorGas ?? true,
  }); // returns { address, sendUserOp, ... }

  // 3) Persist on backend
  await fetch("/api/wallet/provision", {
    method: "POST",
    headers: { "content-type": "application/json" },
    body: JSON.stringify({ eoa: eoa.address, aa: aa.address }),
    credentials: "include",
  });

  return { eoa: eoa.address, aa: aa.address };
}
```

---

### B) Client — Connect (SIWE) → EOA → AA

```ts
// WalletSetupConnect.ts
// Connect wallet (extension/WalletConnect), run SIWE, then build AA.
import { connectExternalWallet, connectSmartAccount } from "@/lib/wallet";

export async function connectSiweAA(params: {
  chainId: number;
  sponsorGas?: boolean;
}) {
  // 1) Connect external wallet → get EOA
  const eoa = await connectExternalWallet(); // { address, signMessage, ... }

  // 2) SIWE: request challenge, sign, verify server-side
  const challenge = await fetch("/api/auth/siwe/challenge", {
    method: "POST",
    credentials: "include",
  }).then((r) => r.json()); // { message }

  const signature = await eoa.signMessage(challenge.message);

  await fetch("/api/auth/siwe/verify", {
    method: "POST",
    headers: { "content-type": "application/json" },
    body: JSON.stringify({ message: challenge.message, signature }),
    credentials: "include",
  });

  // 3) Build Smart Account (AA)
  const aa = await connectSmartAccount({
    personalWallet: eoa,
    chainId: params.chainId,
    sponsorGas: params.sponsorGas ?? true,
  });

  // 4) Persist on backend
  await fetch("/api/wallet/connect/siwe", {
    method: "POST",
    headers: { "content-type": "application/json" },
    body: JSON.stringify({ eoa: eoa.address, aa: aa.address }),
    credentials: "include",
  });

  return { eoa: eoa.address, aa: aa.address };
}
```

---

### C) Server — SIWE (challenge & verify, sketch)

```ts
// /api/auth/siwe/challenge.ts
import { randomBytes } from "crypto";
import { saveNonce } from "@/server/siweRepo";

export async function POST() {
  const nonce = randomBytes(16).toString("base64url"); // ≥96-bit randomness
  await saveNonce({ nonce, ttlMinutes: 5 });           // used=false by default

  const message = {
    domain: process.env.AUTH_DOMAIN!,
    uri: `https://${process.env.AUTH_DOMAIN!}`,
    version: "1",
    chainId: Number(process.env.CHAIN_ID!),
    nonce,
    issuedAt: new Date().toISOString(),
    statement: process.env.SIWE_STATEMENT ?? "Sign in with Ethereum",
  };

  return Response.json({ message });
}
```

```ts
// /api/auth/siwe/verify.ts
import { verifySiwe, consumeNonce } from "@/server/siweService";
import { bindEoaToIdentity, startSession } from "@/server/identityService";

export async function POST(req: Request) {
  const { message, signature } = await req.json();

  // 1) Verify signature & invariants (domain / uri / chainId)
  const { address, nonce, valid } = await verifySiwe({ message, signature });
  if (!valid) return new Response("Invalid SIWE", { status: 401 });

  // 2) Nonce must be unused & unexpired → consume
  const ok = await consumeNonce(nonce);
  if (!ok) return new Response("Nonce invalid/expired", { status: 401 });

  // 3) Bind EOA to current user identity (session required)
  const userId = /* read from session cookie */ await getUserId();
  const identityId = await bindEoaToIdentity({ userId, address });

  // 4) Issue/refresh session
  const res = await startSession({ userId });
  return Response.json({ ok: true, identityId }, res.headers);
}
```

---

### D) Server — Passkey (WebAuthn) register & login (sketch)

```ts
// /api/auth/passkey/register/options.ts
import { generateRegistrationOptions } from "@/server/webauthn";
export async function POST() {
  const userId = await getUserIdOrSignupContext();
  const options = await generateRegistrationOptions({ userId });
  // Store challenge in server-side session/DB to verify later
  return Response.json(options);
}
```

```ts
// /api/auth/passkey/register/verify.ts
import { verifyRegistrationResponse } from "@/server/webauthn";
import { saveCredential } from "@/server/webauthnRepo";

export async function POST(req: Request) {
  const body = await req.json();
  const userId = await getUserIdOrSignupContext();

  const result = await verifyRegistrationResponse({ userId, body });
  if (!result.verified) return new Response("Invalid attestation", { status: 400 });

  await saveCredential({
    userId,
    credentialId: result.credentialId,
    publicKey: result.publicKey,
    signCount: result.signCount,
    transports: result.transports,
    backupEligible: result.backupEligible,
    backedUp: result.backedUp,
  });

  return Response.json({ ok: true });
}
```

```ts
// /api/auth/passkey/login/options.ts
import { generateAuthenticationOptions } from "@/server/webauthn";
export async function POST() {
  const options = await generateAuthenticationOptions();
  return Response.json(options);
}
```

```ts
// /api/auth/passkey/login/verify.ts
import { verifyAuthenticationResponse } from "@/server/webauthn";
import { startSession } from "@/server/identityService";

export async function POST(req: Request) {
  const body = await req.json();
  const result = await verifyAuthenticationResponse(body);
  if (!result.verified) return new Response("Invalid assertion", { status: 401 });

  // Verify sign_count is monotonic, then start session
  const res = await startSession({ userId: result.userId });
  return Response.json({ ok: true, userId: result.userId }, res.headers);
}
```

---

### E) Server — AA Provision (deterministic salt) & persist

```ts
// /api/wallet/provision.ts
import { getOrCreateEoaForUser, deploySmartAccount } from "@/server/walletService";
import { saveWalletMapping } from "@/server/identityRepo";

export async function POST(req: Request) {
  const userId = await getUserId(); // from session cookie
  const identityId = await getIdentityId(userId);

  // 1) Ensure EOA exists (for embedded path)
  const eoa = await getOrCreateEoaForUser(userId);

  // 2) Deterministic AA deploy (factory + SALT(identityId))
  const aa = await deploySmartAccount({
    eoa,
    chainId: Number(process.env.CHAIN_ID!),
    salt: `ib-${identityId}`, // or keccak(identityId)
  });

  // 3) Persist mapping
  await saveWalletMapping({
    identityId,
    eoa: eoa.address,
    aa: aa.address,
    chainId: Number(process.env.CHAIN_ID!),
  });

  return Response.json({ identity_id: identityId, eoa: eoa.address, aa: aa.address });
}
```

---

### F) Types — minimal DTOs (for clarity)

```ts
// dto.ts
export type IdentityDTO = {
  identity_id: string;
  eoa?: string;
  aa?: string;
};

export type SiweChallenge = { message: string };
export type SiweVerifyReq = { message: string; signature: string };
export type WalletPersistReq = { eoa: string; aa: string };
```

```makefile
::contentReference[oaicite:0]{index=0}
```

---

## Appendix — Cost Estimates (Non-HR)  
**Plan:** thirdweb **Starter** · **MAU < 1k** · **RPC < 1M** · Chain: **Base mainnet**  
**Scope:** vendor/platform costs only (no human resources)

---

### 1) Thirdweb platform fees

- **Plan fee:** **Starter = $5 / month**.  
- **In-App (Embedded) Wallet — MAU pricing:** **$0.015 / MAU** for 0–100k, **first 1,000 wallets free** → with **<1k MAU**, effective **$0**.  
- **Account Abstraction (AA) — user-ops:** first **1,000 included**, then **$1 per 1,000** (=$0.001/op). With low usage, often **$0**.  
- **RPC:** first **1,000,000 requests included**; then **$8 per 1M**. With **<1M**, **$0**.  

**Platform subtotal (under stated caps):** **≈ $5 / month**.

> **Note (SMS):** Thirdweb’s pricing notes **international SMS may incur extra fees** (country-dependent). If you avoid **Phone OTP** and use **Email OTP** for “Create Wallet”, this line item is **$0**.

---

### 2) Optional OTP delivery (Phone SMS)
If you enable **Phone OTP** for wallet creation, budget per SMS by destination. For example, **Indonesia outbound** via Twilio is **$0.4414 per SMS segment** as of Oct-2025; **US** starts around **$0.0083**. (Using **Email OTP** keeps this at **$0**.)

**SMS monthly estimate** = `# of SMS OTP × local_rate`.

---

### 3) Gas sponsorship on Base (largest variable)

- **Reference fee level:** recent data shows **Base average tx fee ≈ $0.03** per transaction. Use this as a baseline for simple, sponsored actions.  
- **AA (smart account) deploy:** budget **≈ 2× average tx** (contract deployment & init overhead) → **≈ $0.06** per new wallet. *(Rough planning factor.)*  
- **Paymaster surcharge (if using thirdweb paymaster):** **+2.5%** on sponsored gas.

### Budget table (pick the closest row)

| Scenario / month    | New wallets → **AA deploy** | Sponsored actions |                    Unit costs used |                     Raw gas $ | +2.5% paymaster | **Gas total** |
| ------------------- | --------------------------: | ----------------: | ---------------------------------: | ----------------------------: | --------------: | ------------: |
| **Light**           |                          50 |               200 | Deploy **$0.06**, Action **$0.03** |     $3.00 + $6.00 = **$9.00** |      **+$0.23** |     **$9.23** |
| **Baseline**        |                         200 |               600 | Deploy **$0.06**, Action **$0.03** |  $12.00 + $18.00 = **$30.00** |      **+$0.75** |    **$30.75** |
| **Upper (<1k MAU)** |                         800 |             2,000 | Deploy **$0.06**, Action **$0.03** | $48.00 + $60.00 = **$108.00** |      **+$2.70** |   **$110.70** |

> Real costs vary with network gas, calldata size, and ETH price on the day. You can reduce spend via **lazy AA deployment** (create AA on first action) and by **sponsoring only onboarding operations**.

---

### 4) Monthly roll-up under stated caps

- **Thirdweb platform** (Starter): **~$5**  
- **In-App Wallet MAU, AA user-ops, RPC**: **$0** (within free tiers).  
- **Gas sponsorship (Base):** **~$9–$111** depending on onboarding volume & sponsored actions (see table).  
- **SMS (optional):** `#SMS × local_rate` (e.g., **ID ≈ $0.4414/SMS**; Email-only = **$0**).

**Ballpark total:**  
- **Email-only OTP:** **≈ $14–$116 / month** *(Starter $5 + gas)*.  
- **With some Phone OTP (ID):** add **~$0.44 per SMS** used.

---

### 5) Quick formulas (paste into a sheet)

```
Platform = $5

Gas_raw = (AA_deploy_count × 0.06) + (sponsored_actions × 0.03)
Gas_total = Gas_raw × 1.025 # thirdweb paymaster surcharge (2.5%)

SMS_cost = SMS_count × local_rate # e.g., ID 0.4414

Grand_total = Platform + Gas_total + SMS_cost
```

---

### 6) Cost levers to stay low

- Prefer **Email OTP**; keep **Phone OTP** as fallback only.  
- **Lazy deploy** smart accounts; sponsor **first action only**; set **budget caps** in paymaster rules.

---

**End of document.**

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
