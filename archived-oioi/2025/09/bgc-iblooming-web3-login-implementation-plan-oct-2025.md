---
description: >-
  We don't belong in your reality, your real life. In your reality, your real
  life, you can merely meet our avatars in any version. So, stay alert and
  beware of scams!
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# Web3 Login Identity Bridge — Implementation Plan (Oct 2025)

**Authors:** Prof. NOTA (proposal), Yuku (technical owner), BGC & iBLOOMING engineering/DevOps  
**Audience:** BGC & iBLOOMING founders, engineers, QA, DevOps, PMs  
**Status:** Draft for implementation sign‑off  
**Last updated:** 2025‑09‑29 (Asia/Jakarta)

---

## 1) Executive Summary
We propose to **ship Web3 Login first** (October) while the team finalizes the Whitepaper & Tokenomics. This delivers a visible, low‑risk foundation for the ecosystem:

- **Unified identity** across BGC Web, iBLOOMING Web, and iBLOOMING Mobile via **one EOA** (Externally Owned Account) and **one Smart Account** (Account Abstraction/AA) per user per chain.  
- **Bridges Web2 ↔ Web3**: users can start with email/phone/passkey or existing BGC/iB credentials and seamlessly obtain a self‑custodial wallet; Web3‑native users can connect existing wallets.  
- **Faster analytics**: reliable, on‑chain‑addressed telemetry for behavior simulations (Alpha Coin → later iBC/iBTC).  
- **Partner signal**: live working login across apps shows momentum while tokenomics is being finalized.

### Why ship this first?
1) **Quick win** with high user impact.  
2) **Necessary base layer** for identity‑keyed rewards & future settlements.  
3) **Decoupled scope** (can be executed by a small pod; minimal cross‑team contention).

### Non‑goals (October)
- Launch of production token contracts, DEX/CEX listings, or final economic parameters.  
- Complex KYC/AML flows (beyond optional email/phone verification).  
- Multi‑chain rollout (focus on a single chain first; propose **Base** testnet → mainnet).

---

## 2) Architecture Principles
- **Single EOA per user (master identity).**  
- **One Smart Account (AA)** per user per chain, **deterministic** (CREATE2) from the EOA + salt so the **AA address stays the same** across BGC & iBLOOMING.  
- **Identity Bridge Service** maps: `identity_id ⇄ EOA ⇄ AA ⇄ bgc_user_id ⇄ ib_user_id`.  
- **Standards‑first:** SIWE (EIP‑4361) for wallet authentication; ERC‑4337 for account abstraction.  
- **Security by design:** no plaintext private keys; passkeys/OTP; audit trails for link/merge.

---

## 3) Scope (October)
**In‑scope**
- A single **Login** entry with six options:  
  **(1)** Login with BGC  
  **(2)** Login with iBLOOMING  
  **(3)** Login with Email (OTP)  
  **(4)** Login with Phone (OTP)  
  **(5)** Login with Passkey (biometric)  
  **(6)** Login with Web3 Wallet (Connect Wallet)
- Automatic wallet provisioning & upgrade:  
  - Options **1‑5** → create **EOA (In‑App/Embedded Wallet)** if missing → **auto‑enable Smart Account** (AA).  
  - Option **6** → use user’s existing **EOA** → **auto‑enable Smart Account** (AA).  
- Identity linking page: allow users to **link/merge** BGC and iB accounts to the same identity.
- Environments: **Staging** on Base testnet; **Production** on Base mainnet (toggle via config).

**Out‑of‑scope** (defer to later sprints)
- Gas sponsorship in production (can pilot on staging).  
- OAuth socials (Google/Apple/etc.) unless trivial to include.  
- Mobile deep‑linking polish (basic flows supported; advanced UX later).

---

## 4) System Overview
```
[ User ]
   │
   ├─ Web2 Login (BGC/iB) ──────► [ Identity Bridge API ] ◄───── Web3 Login (Email/Phone/Passkey/Connect)
   │                                      │
   │                                      ├─ map identity_id ⇄ (EOA, AA)
   │                                      └─ link bgc_user_id / ib_user_id
   │
   ├─ BGC Web App ──────── calls getIdentity() ────────► returns { identity_id, EOA, AA, bgc_user_id, ib_user_id }
   └─ iB Web/Mobile ───── calls getIdentity() ────────► returns { …same… }

On‑chain:
[ EOA ] ─(owner/admin)─► [ Smart Account (ERC‑4337, deterministic) ] ──(optional)─► Paymaster (gasless)
```

---

## 5) User Login Flows (Six Options)

### A) Login with BGC (legacy account)
1. Redirect to BGC auth (new tab or modal).  
2. BGC returns JWT → Identity Bridge **provisions In‑App EOA** if missing; **enables AA**.  
3. Identity Bridge **binds** `bgc_user_id` to `identity_id` and wallet(s).  
4. If user also has iB account, offer **Link Account**.

### B) Login with iBLOOMING (legacy account)
Same as A but with iB auth and `ib_user_id` binding.

### C) Login with Email (OTP)
1. Send OTP → verify.  
2. Create/restore **In‑App Wallet EOA** → **enable AA**.  
3. Offer to **create** or **link** BGC/iB accounts.

### D) Login with Phone (OTP)
Same as C but using phone number.

### E) Login with Passkey (biometric)
1. Passkey/WebAuthn ceremony → **In‑App Wallet EOA** → **enable AA**.  
2. Offer to create/link BGC/iB accounts.

### F) Login with Web3 Wallet (Connect Wallet)
1. User connects MetaMask/OKX/Phantom‑EVM/Rainbow/etc.  
2. **SIWE** challenge → verify.  
3. **Enable AA** with connected wallet as admin.  
4. Offer to create/link BGC/iB accounts.

**Zero‑Redundancy Policy:**
- If a login flow reveals an EOA already mapped to another identity, we **reuse** the existing `identity_id` (no duplicates).  
- Link/merge requires **dual proof** (OTP+SIWE) and writes an **audit log**.

---

## 6) Components
- **Connect UI** (Web): prebuilt modal shows Email/Phone/Passkey + 3rd‑party wallets. Two custom CTAs for “Login with BGC/iB”.  
- **In‑App Wallet (Embedded/MPC)**: creates EOAs for Email/Phone/Passkey; passkey‑first UX where available.  
- **Account Abstraction (Smart Wallet)**: auto “upgrade” any connected EOA to an AA account; optional gas sponsorship via Paymaster.  
- **Identity Bridge Service**: minimal microservice for mapping & merge operations.  
- **Admin Console**: search `identity_id`, view bindings, approve merges.

---

## 7) Data Model (minimal viable)
**identities**  
- `identity_id` (UUID, PK), `created_at`

**wallets**  
- `wallet_id` (PK), `identity_id` (FK), `type` (`EOA` | `AA`), `address`, `chain_id`, `salt`, `created_at`  
- Constraints: UNIQUE(`address`,`chain_id`)

**accounts**  
- `account_id` (PK), `identity_id` (FK), `app` (`BGC` | `IB`), `app_user_id`, `created_at`  
- Constraints: UNIQUE(`app`,`app_user_id`)

**auth_providers**  
- `provider_id` (PK), `identity_id` (FK), `provider_type` (`email` | `phone` | `passkey` | `siwe` | `bgc` | `ib`), `provider_ref` (email/phone hash or wallet addr), `created_at`

**audit_logs**  
- `log_id` (PK), `identity_id`, `action` (`bind` | `merge` | `unlink`), `actor`, `metadata`, `created_at`

---

## 8) Identity Bridge — API Contracts (HTTP/JSON)
- `POST /auth/web2/bgc/start` → redirect URL  
- `GET  /auth/web2/bgc/callback?code=…` → returns session JWT  
- `POST /wallet/provision` → body: `{ session_jwt }` → creates EOA if missing; prepares AA  
- `POST /wallet/connect/siwe` → body: `{ address, signature, nonce }` → returns `{ identity_id }`  
- `POST /account/link` → body: `{ identity_id, app, app_user_id }` (requires OTP or SIWE per policy)  
- `GET  /identity` → returns `{ identity_id, eoa, aa, bgc_user_id?, ib_user_id? }`  
- `POST /identity/merge` (admin) → body: `{ from_identity_id, to_identity_id, reason }`

---

## 9) Security & Privacy
- **No plaintext private keys** stored server‑side; In‑App Wallet uses secure enclaves/MPC and user factors (email/phone/passkey).  
- **SIWE** + **per‑login nonce** to prevent replay.  
- **Rate limiting** for OTP and link/merge endpoints.  
- **PII minimization**: store hashed emails/phones where feasible.  
- **Secrets** in vault; rotate regularly.  
- **RBAC** for Admin Console and merge operations.  
- **Logs** include who/when/how for every bind/merge.

---

## 10) Environments & DevOps
- **Chains**: Staging → Base testnet; Production → Base mainnet.  
- **Third‑party infra**: Bundler/Paymaster (staging only at first).  
- **Config** (12‑factor): `THIRDWEB_CLIENT_ID`, `WC_PROJECT_ID`, `CHAIN_ID`, `AA_FACTORY_ADDR`, `JWT_SECRET`, `BGC_AUTH_URL`, `IB_AUTH_URL`.  
- **CI/CD**: build, lint, type‑check, smoke test **/login → /identity** happy paths; e2e on staging before production promote.  
- **Monitoring**:  
  - Auth success/error rate per provider.  
  - Duplicate identity attempts.  
  - AA deployment rate & failures.  
  - OTP latency, SIWE errors.

---

## 11) Implementation Plan — October 2025 (target)
**Week 1 (Oct 1–7)**  
- Kickoff & sign‑off scope; create repos and envs.  
- Web apps: add unified **Login** button + Connect UI (Email/Phone/Passkey/Wallet).  
- Identity Bridge skeleton (DB schemas; `/identity` read‑only).

**Week 2 (Oct 8–14)**  
- Web2 logins: BGC/iB redirects & callbacks; session JWT.  
- Wallet provisioning for Web2 flows (EOA) + enable AA on staging chain.  
- SIWE flow for external wallets.  
- Basic Admin Console (read‑only).

**Week 3 (Oct 15–21)**  
- **Link/merge** flows (dual proof policy, audit logs).  
- Mobile (iB): implement ConnectButton RN or HTTP API (Email/Phone/Passkey + WalletConnect).  
- QA: unit + e2e (happy paths + failure cases).

**Week 4 (Oct 22–31)**  
- Staging bake‑off (gasless trial via Paymaster).  
- Hardening: rate limiting, retries, telemetry dashboards.  
- Production launch window with feature flags; rollback plan.

**Deliverables**  
- Web: unified Login + AA.  
- Mobile: at least Email/Phone/WalletConnect + AA.  
- Identity Bridge: mapping APIs + Admin Console.  
- Runbooks: oncall, incident, rollback, key/secrets management.

**Acceptance Criteria**  
- A user can log in via any of the six options and end with **one identity** having **one EOA** and **one AA** on the target chain.  
- The same identity is recognized across BGC and iB apps.  
- Admins can safely link/merge with full auditability.

---

## 12) Testing Plan
- **Unit**: OTP, SIWE nonce, DB constraints (unique address per chain).  
- **Integration**: `/wallet/provision`, `/account/link`, `/identity`.  
- **E2E**: six login paths (new user, existing Web2, existing Web3), identity reuse, link both accounts, forced collision & merge.  
- **Security**: replay protection, authZ on admin routes, rate limits, secret scanning.  
- **Load**: peak login bursts; OTP provider throttling behavior.

---

## 13) Migration & Rollout
1) **Soft launch** on staging; internal dogfooding across both apps.  
2) Email/WA campaign: “Bind your wallet” (3 clicks).  
3) Progressive feature flag: new signups auto‑provision wallets; after ≥95% existing users are bound, auto‑create BGC+iB accounts for new identities.  
4) Post‑launch monitoring; incident playbook; weekly audit of merges.

---

## 14) Risks & Mitigations
- **Duplicate identities** due to race conditions → enforce DB uniqueness + retry/merge workflow.  
- **OTP deliverability** → fallback channel (email↔SMS), resend with backoff.  
- **Mobile deep‑link quirks** → use universal links + WalletConnect v2; provide QR fallback.  
- **Gas spikes on mainnet** → keep Paymaster off in prod initially; batch AA deployments; pre‑fund only when needed.  
- **User confusion** → clear copy in UI: “You will get a self‑custodial wallet; keep access factors safe.”

---

## 15) Minimal Code Samples

### 15.1 Next.js (Web)
```tsx
// components/UnifiedLogin.tsx
"use client";
import { ConnectButton } from "thirdweb/react";
import { createThirdwebClient, defineChain } from "thirdweb";
import { inAppWallet, walletConnect, metamaskWallet } from "thirdweb/wallets";

const client = createThirdwebClient({ clientId: process.env.NEXT_PUBLIC_THIRDWEB_CLIENT_ID! });
const base = defineChain(8453); // Base mainnet; use 84532 for Base Sepolia

export default function UnifiedLogin() {
  return (
    <div className="flex flex-col gap-3 items-center">
      {/* Legacy Web2 CTAs */}
      <div className="flex gap-2">
        <a className="btn" href="/api/auth/bgc/start">Login with BGC</a>
        <a className="btn" href="/api/auth/ib/start">Login with iBLOOMING</a>
      </div>

      {/* Connect UI: Email / Phone / Passkey / External Wallets */}
      <ConnectButton
        client={client}
        wallets={[
          inAppWallet({ auth: { options: ["email", "phone", "passkey"] } }),
          metamaskWallet(),
          walletConnect({ projectId: process.env.NEXT_PUBLIC_WC_PROJECT_ID! }),
        ]}
        accountAbstraction={{ chain: base, sponsorGas: false }}
      />
    </div>
  );
}
```

### 15.2 Identity Bridge (pseudo‑routes)
```http
POST /auth/web2/bgc/start           -> 302 redirect
GET  /auth/web2/bgc/callback        -> returns session JWT
POST /wallet/provision              -> ensures EOA; prepares AA; returns { identity_id, eoa, aa }
POST /wallet/connect/siwe           -> verifies SIWE; returns { identity_id }
POST /account/link                  -> links bgc_user_id/ib_user_id; audit log
GET  /identity                      -> returns identity mapping
POST /identity/merge (admin only)   -> merges two identities
```

### 15.3 React Native (Mobile iB)
- Use the **ConnectButton (React Native)** or the **HTTP API** to support Email/Phone/Passkey + WalletConnect.  
- Keep the same `accountAbstraction` settings; reuse Identity Bridge endpoints.

---

## 16) Glossary

> A founder‑friendly glossary of terms and acronyms used in this plan. Short, plain‑English definitions come first; technical notes follow in parentheses when helpful.

### Core Identity & Wallets
- **EOA (Externally Owned Account):** A standard crypto wallet controlled by a private key (e.g., MetaMask address). (EVM concept.)
- **Smart Account / Smart Wallet:** A programmable wallet implemented as a smart contract. In our plan it’s created from the user’s EOA and follows **ERC‑4337** rules.
- **Account Abstraction (AA):** A model (EIP‑4337) that makes smart accounts act like normal wallets but with extra powers (gas sponsorship, batching, policies).
- **EntryPoint:** The on‑chain contract used by ERC‑4337 to validate and execute UserOperations (the “router” for smart account actions).
- **Bundler:** A service that collects UserOperations from many users and submits them to the EntryPoint in one transaction.
- **Paymaster:** A component that sponsors transaction gas on behalf of users (enables “gasless” UX) with rules/limits.
- **Deterministic Deployment / CREATE2:** A method to pre‑compute a smart contract address before it is deployed (address determined by salt + bytecode + deployer). Used so a user’s smart account address stays consistent across apps.
- **Counterfactual Address:** A contract address computed before deployment (via CREATE2); it becomes real when deployed.
- **Chain / Chain ID:** A specific blockchain network (e.g., Base mainnet has a numeric chain ID). Apps must explicitly select the chain.

### Authentication & Linking
- **Web2 Login:** Traditional login via existing BGC/iB accounts, email+OTP, phone+OTP, or passkey.
- **Web3 Login:** Authentication using a crypto wallet (EOA) and **SIWE**.
- **SIWE (Sign‑In With Ethereum / EIP‑4361):** A standard where users sign a human‑readable message with their wallet to prove control of an address (no transaction required).
- **Passkey (WebAuthn):** Passwordless sign‑in using device biometrics/secure hardware (Face/Touch ID). In our setup, passkeys can secure an **In‑App Wallet**.
- **OTP (One‑Time Password):** A one‑time code sent by email/SMS for verifying ownership of a channel during login or linking.
- **In‑App (Embedded) Wallet:** A non‑custodial wallet generated and secured via SDK (e.g., with passkey/OTP). Users don’t paste private keys; recovery relies on chosen factors (e.g., passkey, email).
- **WalletConnect / EIP‑6963:** Protocols enabling dApp ↔ wallet connections across browsers/devices; EIP‑6963 improves wallet discovery in browsers.
- **Link (Account Linking):** Attaching an app account (BGC/iB) to a single on‑chain identity (EOA/Smart Account). Requires proofs (OTP/SIWE).
- **Merge (Identity Merge):** Combining two identities into one (e.g., when duplicate records exist). Requires stronger proofs and admin approval.

### Security & Compliance
- **No Plaintext Private Keys:** Private keys are never stored or transmitted as raw text. In‑App wallets use secure enclaves/MPC/OS keystores.
- **MFA (Multi‑Factor Authentication):** Requiring >1 proof (e.g., passkey + OTP) for sensitive operations.
- **Nonce:** A unique value used once to prevent replay (exists in SIWE and in on‑chain transactions; context differs).
- **Replay Attack:** An attacker reuses a previously valid message; prevented by unique nonces and expiration windows.
- **PII (Personally Identifiable Information):** Data that can identify a person (email, phone, etc.). We minimize and protect it.
- **RBAC (Role‑Based Access Control):** Access permissions based on user roles (e.g., Admin, SecurityOps).
- **KYC/AML:** Know‑Your‑Customer / Anti‑Money‑Laundering checks. Out‑of‑scope for October beyond basic OTP verification.
- **Phishing:** Trick users to reveal secrets; we never ask users to paste private keys in app UIs.
- **Audit Trail:** An immutable record of critical actions (link/merge), including who/what/when/how, for forensics and accountability.
- **WORM Storage:** Write‑Once‑Read‑Many log storage to ensure logs cannot be tampered with post‑write.

### Tokens & Economics (context only)
- **Tokenomics:** The economic design of a token (supply, emissions, rewards). Final parameters are out‑of‑scope for October.
- **DEX/CEX:** Decentralized/Centralized Exchanges where tokens can be traded. Listings are out‑of‑scope for October.
- **Airdrop / Faucet:** Token distribution mechanisms; faucets usually provide small testnet funds for testing.
- **Settlement:** Converting points/rights into transferable value (often requires final token design; not in October scope).

### Blockchain & EVM Basics
- **EVM (Ethereum Virtual Machine):** The execution environment for smart contracts used by Ethereum and many L2s (including Base).
- **Base:** An Ethereum Layer‑2 (OP Stack) we target for staging (testnet) and production (mainnet).
- **Gas / Gas Price / Gwei:** Computational fee paid to execute transactions. Gas sponsorship = someone else pays.
- **Address / Checksum Address:** Public identifier of a wallet/contract; checksum casing helps detect typos.
- **ABI (Application Binary Interface):** The interface (function/event signatures) used to call smart contracts.
- **Event Logs:** On‑chain records emitted by contracts (used for indexing and analytics).
- **Hash:** A fixed‑length fingerprint of data (used for integrity, signatures, addresses, logs).

### App & Service Architecture
- **Identity Bridge Service:** A small service (our component) that maps `identity_id ⇄ EOA ⇄ AA ⇄ bgc_user_id ⇄ ib_user_id`, exposes `/identity`, `/account/link`, `/identity/merge`, etc.
- **JWT (JSON Web Token):** A signed token for session/auth between services (header.payload.signature).
- **OAuth 2.0 / OIDC:** Web auth standards used by many platforms; optional for later social logins (Google/Apple).
- **Twelve‑Factor Config:** A practice of storing configuration in environment variables (not in code), enabling portable deployments.
- **Feature Flags:** Switches to enable/disable features at runtime without redeploying; used for safe launches and rollbacks.
- **Rollback Plan:** A predefined, step‑by‑step procedure to revert a release safely.
- **Idempotency:** Designing APIs so repeating the same request doesn’t produce duplicate effects (important for wallet provisioning/linking).
- **Rate Limiting / 429:** Limits requests per time window to protect from abuse; HTTP 429 is “Too Many Requests.”
- **Observability:** The trio of **metrics, logs, traces** used to monitor health and diagnose issues.
- **CI/CD:** Continuous Integration/Continuous Delivery pipelines for automated build/test/deploy.
- **E2E Tests:** End‑to‑end tests simulating real user flows across systems (e.g., six login paths → EOA → AA → link accounts).

### Mobile & Deep Linking
- **Deep Link / Universal Link (iOS) / App Link (Android):** Mechanisms to open an app to a specific screen from a URL.
- **Wallet Deep Linking:** Opening a wallet app from a dApp and returning the user after approval.
- **QR Fallback:** Displaying a QR code users can scan with their wallet if deep linking fails.

### Data & Analytics (light)
- **Telemetry:** Operational data (success/error rates, latency) used for monitoring.
- **Behavior Analytics:** Measuring user actions tied to on‑chain identity (for simulations like Alpha Coin → later iBC/iBTC).
- **Anomaly Detection:** Automated alerts for suspicious patterns (e.g., unusual merges or link spikes).

### Governance & Process
- **Sign‑off:** Formal approval gate before production release (scope, security, QA, monitoring, rollback ready).
- **Runbook / Playbook:** Step‑by‑step guides for operations (incident response, rollback, key rotation).
- **Change Log:** Human‑readable list of changes per release for transparency.
## 17) References & Further Reading
- thirdweb React SDK v5 — Connect UI & components: https://portal.thirdweb.com/react/v5  
- ConnectButton docs (supports email/phone/passkey & external wallets): https://portal.thirdweb.com/react/v5/components/ConnectButton  
- In‑App Wallets (Email/Phone/Passkey, socials, custom auth): https://portal.thirdweb.com/react/v5/in-app-wallet/get-started  
- Passkey sign‑in changelog: https://portal.thirdweb.com/changelog/passkey-sign-in-for-in-app-wallets  
- Account Abstraction — Get started (auto‑smart‑account via Connect): https://portal.thirdweb.com/react/v5/account-abstraction/get-started  
- Smart Wallet (TypeScript API): https://portal.thirdweb.com/references/typescript/v5/smartWallet  
- Wallets overview + HTTP/TypeScript/React/RN: https://portal.thirdweb.com/wallets  
- Connect UI overview: https://portal.thirdweb.com/react/v5/connecting-wallets/ui-components  
- Linking multiple identities to one wallet: https://portal.thirdweb.com/wallets/link-profiles  
- SIWE (EIP‑4361) spec: https://eips.ethereum.org/EIPS/eip-4361  
- Account Abstraction (EIP‑4337) spec: https://eips.ethereum.org/EIPS/eip-4337  
- Ethereum.org — Account Abstraction explainer: https://ethereum.org/roadmap/account-abstraction/

---

## 18) Sign‑off Checklist

This section is the **final quality gate** before enabling production features. All items must be checked to proceed.

1) **Scope & timeline approved (Founders, PM)**  
   - **Acceptance:** October scope is frozen (six login options, EOA→AA, Identity Bridge basics) with a clear calendar and signed‑off responsibilities.  
   - **Artifacts:** finalized scope doc, sprint plan, locked epics/tickets.

2) **Security review (keys, OTP, SIWE nonces, rate limiting)**  
   - **Acceptance:** secrets management validated; OTP anti‑abuse configured; SIWE uses per‑login nonce + expiry; rate‑limits in place; admin routes protected with RBAC.  
   - **Artifacts:** lightweight threat model, security checklist, findings & fixes, signed review note.

3) **Staging sign‑off (QA, DevOps)**  
   - **Acceptance:** all six login paths pass on **staging/testnet**; **EOA→AA** works; **link/merge** flows pass; audit logs recorded; E2E suite green; basic load test acceptable.  
   - **Artifacts:** QA report (pass rates), evidence of AA on testnet, load test summary.

4) **Production feature flags & rollback plan**  
   - **Acceptance:** feature flags exist per capability (Connect UI, provisioning, link/merge); defaults documented; rollback playbook verified in rehearsal; backups/restores tested.  
   - **Artifacts:** flag registry & defaults, rollback playbook, post‑rollback checklist.

5) **Post‑launch monitoring dashboards**  
   - **Acceptance:** dashboards & alerts live for: login success/error, AA provisioning latency/failure, OTP delivery, SIWE errors, duplicate‑identity attempts; on‑call rota confirmed.  
   - **Artifacts:** links to Grafana/ELK dashboards, alert thresholds, escalation policy.

**Green‑light rule:** proceed to production only when **all five** items are checked ✅.  
**Owner mapping:** (1) Founders/PM, (2) Security/Eng, (3) QA/DevOps, (4) DevOps/Eng Mgmt, (5) SRE/DevOps.

---

**End of document.**
