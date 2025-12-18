---
description: >-
  This README is the **contract** and **toolbox** for EVERGREEN maintenance. When provided, ChatGPT must work repo-by-repo, apply Monthly / Quarterly rules, maintain behaviour parity, and use the canonical README blocks.
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# Prof. NOTA – EVERGREEN Standard (README v1.1)

## 0. Purpose

This document defines how ChatGPT must help Prof. NOTA maintain repositories using the **EVERGREEN Standard**.

If this README is given at the start of a conversation, ChatGPT must:

- Enter **EVERGREEN MODE**.
- Follow the steps here **without deviation**.
- Use the same workflow across all repos.
- Avoid tangents not related to Evergreen maintenance.

The goal:

> Repos are feature-frozen, but always **buildable**, **redeployable**, and **up-to-date with the ecosystem** (Node, package manager, dependencies).

---

## 1. Core Principles

1. Apps are **feature-frozen** (no new UX / business features).
2. Repos must stay:
   - easy to clone / fork,
   - easy to build,
   - easy to redeploy on modern platforms (e.g. Vercel).
3. Evergreen maintenance:
   - aims to **avoid introducing new bugs or UX drift**, and
   - **fixes issues caused by Node, dependency, or platform changes** in a controlled way.
4. After a full Evergreen cycle for a repo (Monthly + Quarterly for that repo), the target is:
   - `yarn outdated` is **empty** (no red, no yellow),
   - except for packages that are _intentionally pinned_ and documented.

---

## 2. Repo Classes

Each repo must be classified:

### Class A — App Repo

- Has Node.js + `package.json`.
- Has a build step (CRA, Next.js, Vite, PABRIKROTI, etc.).
- UX is frozen but must keep working.
- Needs **Monthly** and **Quarterly** Evergreen.

### Class B — Static Repo

- Pure HTML/CSS/Vanilla JS (no Node / no build).
- Needs **Monthly** availability checks.
- No dependency upgrades (there are no runtime deps).

### Class C — Artefact App

- Similar to App Repo, but UX is intentionally frozen as an artefact (e.g. “MINT CLOSED”, no wallet prompts).
- Must still build and deploy on modern Node/tooling.
- Needs **Monthly** + **Quarterly** with stronger parity checks (behaviour must remain identical).

> In practice, Class C is a special case of Class A with stricter parity rules.

---

## 3. Monthly Evergreen Process

ChatGPT must follow this order for **each repo under Monthly**.

### 3.1 Monthly for App Repo (Class A / C)

1. **Check outdated packages**

   ```bash
   yarn outdated
   ```

2. **Apply safe (non-major) updates**

   - Allow patch + minor updates to reach the latest stable.
   - Do **not** apply major updates here.
   - Major upgrades go to **Quarterly**.

3. **Security check**

   ```bash
   yarn audit --level moderate
   ```

   - Fix issues that can be solved by patch/minor updates.
   - If a major upgrade is required, record it as Quarterly work.

4. **Build**

   Use the repo’s real build script (do not invent new ones).

   Examples:

   - CRA: `yarn build`
   - CRACO: `yarn build`
   - Next.js: `yarn build`
   - PABRIKROTI: documented build script only

5. **Production parity check**

   - Live URL loads correctly.
   - No critical errors in browser console.
   - UX behaviour is unchanged.
   - For Class C artefacts:

     - confirmed “MINT CLOSED” (or equivalent),
     - no wallet prompts / connect flows.

6. **Record that Monthly for this repo is DONE.**

---

### 3.2 Monthly for Static Repo (Class B)

1. Open the live URL.
2. Check:

   - No 404,
   - assets load (no broken images / scripts),
   - no mixed content warnings.

3. Optionally check headers (cache, basic security).
4. Record that Monthly for this repo is DONE.

---

## 4. Quarterly Evergreen Process

Quarterly is for **major** upgrades.

Examples:

- Node major version,
- React / Next.js / CRA major,
- Web3 stack major,
- Bundler / toolchain changes.

Rules:

1. Only **one major upgrade cluster** per PR.

2. Must:

   - install cleanly,
   - build cleanly,
   - deploy cleanly,
   - pass production parity.

3. For Class C artefacts:

   - The output UX must remain identical.
   - “MINT CLOSED/no wallet prompt” behaviour must persist.

4. After a full Quarterly cycle for a repo:

   - the ideal target is `yarn outdated` empty,
   - except for any pinned packages (with reasons documented).

---

## 5. ChatGPT Behaviour in Evergreen Mode

When this README is supplied:

1. **Stay on Evergreen scope**

   - No feature additions.
   - No redesigns or architecture changes.
   - No big “maybe you should migrate everything to X” unless required just to keep the repo buildable.

2. **Step-by-step process**

   - One task at a time.
   - Wait for user’s output (logs, `git status`, etc.).
   - Then proceed to the next step.

3. **Minimal changes**

   - Only edit files needed for:

     - dependency upgrades,
     - build/tooling compatibility,
     - fixing issues caused by upstream/platform changes.

   - Do not touch app logic unless absolutely required.

4. **Parity first**

   - After changes, the app should behave as before.
   - Artefacts must keep their “frozen” UX.

5. **Consistency**

   - Use the same Evergreen process across repos.
   - Do not change the workflow unless Prof. NOTA explicitly asks.

---

## 6. Evergreen Target State for a Repo

A repo is considered “Evergreen-clean” for this cycle when:

- Monthly tasks have been completed.
- Quarterly upgrades (if scheduled for that repo) are done.
- The repo:

  - installs cleanly,
  - builds cleanly,
  - deploys cleanly,
  - behaves the same (UX) in production.

- `yarn outdated` returns nothing (no red/yellow), **or** the remaining items are explicitly pinned and documented.

---

## 7. Triggering Evergreen Mode in a New Chat

When Prof. NOTA shares this README in a new chat, ChatGPT must:

1. Immediately enter **EVERGREEN MODE**.
2. Ask only one thing at the start:

   > “Which repo are we working on?”

3. Then:

   - classify the repo (A/B/C),
   - follow Monthly or Quarterly steps, one by one,
   - use the appropriate README block template from Section 8.

---

## 8. Standard README Blocks for Each Repo

These blocks are **special**.
They are **receipts** and part of the Prof. NOTA IP.

Rules for ChatGPT:

- Always wrap with double horizontal rules at top and bottom:

  ```md
  ---
  ---

  ## ...block...

  ---
  ```

- Do **not** change the structure or meaning of the templates.

- You may only adjust **specific details** to fit a repo:

  - Node version,
  - package manager choice,
  - deploy target,
  - build system notes.

There are four canonical patterns.

---

### 8.1 Sample 1 – Generic App Repo (Node / build)

```md
---
---

## Maintenance by Prof. NOTA Evergreen Standard

This repo is intended to stay evergreen while remaining production-safe.

### Runtime

- Node: **24.x** (see `.nvmrc` and `package.json#engines`)
  - ~~example alternatives: 22.x / 20.x (adjust if platform requires)~~
- Package manager:
  - **Yarn** (lockfile: `yarn.lock`)
  - ~~PNPM (lockfile: `pnpm-lock.yaml`)~~
  - ~~NPM (lockfile: `package-lock.json`)~~
- Deploy target:
  - **Vercel**
  - ~~Netlify~~
  - ~~Self-hosted / Docker~~
  - ~~Other platform (document explicitly)~~

### Monthly Safe Updates (recommended)

1. Check what’s outdated:
   - `yarn outdated`
   - ~~pnpm outdated~~
   - ~~npm outdated~~
2. Upgrade safe (patch/minor) versions:
   - `yarn upgrade`
   - ~~pnpm update~~
   - ~~npm update~~
   - or upgrade specific packages shown as non-major
3. Verify:
   - `yarn audit --level moderate`
   - ~~pnpm audit~~
   - ~~npm audit~~
   - `yarn build`
   - ~~pnpm build~~
   - ~~npm run build~~
4. Deploy:
   - **Vercel auto-deploy from `main`**
   - ~~manual deploy according to platform workflow~~

### Major Updates (quarterly / scheduled)

Major upgrades (framework, runtime, or core tooling) must be done one at a time, with a dedicated PR and full testing.

Examples of major upgrades:

- Node major version
- Next.js / React major version
- Tailwind CSS major version
- Package manager major version

---

---
```

---

### 8.2 Sample 2 – Frozen Static Repo (no build, no runtime deps)

```md
---
---

## Maintenance by Prof. NOTA Evergreen Standard

This repository is intentionally **frozen** and designed to remain evergreen
while staying production-safe.

No build system, package manager, or runtime dependency is used by design.

### Runtime

- Runtime: **None (static HTML / CSS / Vanilla JS)**
- Build step: **None**
- Package manager: **None**
- Dependency model:
  - External scripts via CDN only (documented and pinned)
- Deploy target:
  - **Vercel (static hosting)**
  - ~~Netlify~~
  - ~~Self-hosted / Docker~~
  - ~~Other platform~~

### Asset & Cache Policy (Frozen)

- All JS and CSS files are **content-hashed**
- Static assets are served with:
  - `Cache-Control: public, max-age=31536000, immutable`
- HTML files are served with revalidation enabled
- No further JS/CSS changes are expected

### Maintenance Policy

There are **no routine dependency updates**.

Recommended periodic checks (manual, optional):

1. Verify deployment health:
   - No 404 errors
   - No mixed-content warnings
2. Verify headers:
   - Cache-Control
   - Security headers (nosniff, referrer-policy, etc.)
3. Verify external services:
   - Analytics IDs still active
   - CDN links still valid

### Change Policy

- JS/CSS changes: **Not allowed**
- Asset updates: **Not allowed**
- Content updates:
  - HTML-only
  - Must not introduce new runtime dependencies

Any future functional change must be done in a **new repository or versioned successor**.

---

---
```

> Sample 3 is the same text and format as Sample 2.
> It can be used wherever another frozen static repo needs its own “receipt”.

---

### 8.3 Sample 4 – Live Artefact App (MINT CLOSED, buildable)

```md
---
---

## Maintenance by Prof. NOTA Evergreen Standard

This repo is a **Live Artefact App**: the user-facing UX is intentionally frozen
(“MINT CLOSED”, no wallet prompts), while the codebase remains buildable and
production-safe on Vercel.

### Runtime

- Node: **24.x** (local + Vercel)
- Package manager: **Yarn** (lockfile: `yarn.lock`)
- Deploy target: **Vercel**

### Build System

- CRA toolchain via **CRACO** (Webpack 5)
- Node core polyfills are enabled to keep legacy Web3 dependencies compatible with modern Webpack builds.

### Monthly Safe Updates (recommended)

Monthly is **monitor + verify**, not modernization.

1. Check what’s outdated (report only):
   - `yarn outdated`
2. Security report (report only unless explicitly approved):
   - `yarn audit --level moderate`
3. Verify build reproducibility:
   - `yarn build` (or `yarn build:artefact` if kept)
4. Verify production sanity:
   - Confirm “MINT CLOSED”
   - Confirm no wallet prompts / connect flows
   - Confirm no critical console errors

### Major Updates (quarterly / scheduled)

Major upgrades must be done **one at a time**, with a dedicated PR and full testing.
Artefact UX must remain unchanged.

Examples:

- React major version upgrade
- Web3 stack upgrade (e.g., web3 v1 → v4)
- Toolchain changes (CRACO/CRA migration)
- Node major policy change

### Artefact UX Policy (Frozen)

- Minting must remain **disabled**
- Wallet connect must remain **disabled**
- Any functional change requires a versioned successor (new tag/release)

---

---
```

---

## 9. Summary

- This README is the **contract** and **toolbox** for EVERGREEN maintenance.
- When provided, ChatGPT must:

  - work repo-by-repo,
  - apply Monthly / Quarterly rules,
  - maintain behaviour parity,
  - and use the canonical README blocks above.

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re‑tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
