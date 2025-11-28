---
description: >-
  If this kind of QA is useful, we’d be very happy to keep testing multi-identity / multi-brand scenarios and even contribute to docs or pre-release testing going forward.
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# ENS & Base Name profile resolution is inconsistent (secondary names not detected, some URLs return 404)

> Hey Talent Protocol team! 👋   
> 
> We are a Talent Plus user, and we are running into some confusing behavior around how ENS and Basenames are detected and resolved into profiles on talentprotocol.com / talent.app.
> 
> We’ve been digging deep into how ENS and Basenames behave across talentprotocol.com / talent.app and we ran into some inconsistencies between what’s detected in my account and what actually resolves as public profile URLs (especially around secondary names like skateshop.eth / skateshop.base.eth, and a regression where myreceipt.eth links that worked yesterday now return 404).
> 
> From reading your docs on Users, Accounts, Profiles, and Data Points (especially Primary ENS Domain and Basename under Base data points), it’s clear that ENS/Basenames are part of the identity model and can be queried via the API. What’s not totally clear is which of those identities are meant to be stable URL aliases (e.g., /name, /name.eth, /name.base.eth) and which ones are intentionally unsupported — and that’s exactly what our issue tries to map out with concrete examples.
> 
> Here’s a detailed write-up with all the addresses, URLs, and references to your docs:  
> ➡️ [link to full issue](#id-1.-context)
> 
> If this kind of QA is useful, we’d be very happy to keep testing multi-identity / multi-brand scenarios and even contribute to docs or pre-release testing going forward.

---

## 1. Context

- Account: [Prof. NOTA / endhonesa (Talent Plus)](https://talent.app/endhonesa)
- Location: Jakarta, Indonesia
- Observed: 27–28 November 2025
- Platform: Desktop, macOS 10.15.7, Chrome 142 (tested both logged-in and logged-out)
- Naming setup:
  - We use multiple ENS names and Basenames that all point to a set of verified wallet addresses.
  - Some of these names are primary; others are secondary aliases that still resolve to the same address onchain.

From your public docs, our understanding of the canonical model is:

- **User** – an individual who signs up on talentprotocol.com and aggregates multiple accounts into a single Builder Score and a single canonical profile URL, e.g. `talentprotocol.com/UUID`.  
  (Docs: [User](https://docs.talentprotocol.com/docs/protocol-concepts/user))

- **Account** – a connection to an external data source (wallet, GitHub, Farcaster, etc.) that initially has its own account-specific URL like  
  `talentprotocol.com/address/0xbd…` or `talentprotocol.com/github/filmacedo`, which later redirects to the user’s profile if linked.  
  (Docs: [Account](https://docs.talentprotocol.com/docs/protocol-concepts/account))

- **Profile** – the entity that represents a builder’s digital identity and reputation. Profiles can be:
  - User Profiles (for verified users) or
  - Account Profiles (for unclaimed accounts),  
  and can be searched via identity info (names, ENS, usernames), accounts, and Builder Score.  
  (Docs: [Profile](https://docs.talentprotocol.com/docs/protocol-concepts/profile))

- **Data Points & Identity** – ENS and Basenames are treated as identity-related data:
  - ENS: *Primary ENS Domain* and *ENS Account Age* data points.  
    (Docs: [ENS Data Points](https://docs.talentprotocol.com/docs/data-points/ens))
  - Basenames: *Basename* data point under the Base category, verifying ownership of a Basename.  
    (Docs: [Base Data Points](https://docs.talentprotocol.com/docs/data-points/base))
  - All of this fits into the general Data Points catalog.  
    (Docs: [Data Points](https://docs.talentprotocol.com/docs/data-points))

- **Talent API & Profile Search** – the API exposes advanced search over:
  - Identity information (names, ENS domains, usernames),
  - Connected accounts (wallets, GitHub, etc.),
  - Human verification / Builder Score, etc.  
  (Docs: [Talent API](https://docs.talentprotocol.com/docs/developers/talent-api),  
  [Profile Search](https://docs.talentprotocol.com/docs/protocol-concepts/profile#profile-search),  
  [Profiles Default Search Fields](https://docs.talentprotocol.com/docs/developers/talent-api/api-reference/profiles-default-search-fields))

What we are reporting below is specifically about how these identities behave in the *public-facing URLs* of talentprotocol.com and talent.app.

---

## 2. What we are seeing

### 2.1. ENS & Basenames detection in the app

Under our account, in the Social Accounts / Wallet Addresses area, not all ENS/Basenames that resolve to our verified addresses appear to be detected equally:

1. `myreceipt.eth`  
   → `0x29bf68e3969e0b6686ea55b7c48241ba3f6b9ba0` (our primary verified address)  
   **Status:** detected ✅

2. `endhonesa.eth`  
   → `0x35b68340c61f26147b7b22f5ab931892bd9358b3` (Base account)  
   **Status:** detected ✅

3. `skateshop.eth`  
   → `0x35b68340c61f26147b7b22f5ab931892bd9358b3` (same Base account as above, but *not* the primary name)  
   **Status:** *not detected* ❌

4. `myreceipt.base.eth`  
   → `0x29bf68e3969e0b6686ea55b7c48241ba3f6b9ba0` (primary verified address)  
   **Status:** detected ✅

5. `endhonesa.base.eth`  
   → `0x35b68340c61f26147b7b22f5ab931892bd9358b3` (Base account)  
   **Status:** detected ✅

6. `skateshop.base.eth`  
   → `0x35b68340c61f26147b7b22f5ab931892bd9358b3` (same Base account, non-primary name)  
   **Status:** *not detected* ❌

7. `myreceiptt.base.eth`  
   → `0x70caa9feefc36e1422ecc055ac1f0de48cb320d7` (smart account for our secondary Zora account)  
   **Status:** detected ✅

From a user’s perspective, it’s surprising that:

- `endhonesa.eth` / `endhonesa.base.eth` and `myreceipt.*` are detected,
- but `skateshop.eth` and `skateshop.base.eth` (which resolve onchain to the same verified addresses) are not, even though ownership should be equally verifiable via the respective ENS / Basename data points.

---

## 3. Profile URLs via address vs ENS/Basenames

### 3.1. Address-based URLs (working as expected)

For our verified addresses, the address-based profile URLs work consistently:

Examples (all returning 200 OK):

- `https://talentprotocol.com/0x29bf68e3969e0b6686ea55b7c48241ba3f6b9ba0`  
  `https://talent.app/0x29bf68e3969e0b6686ea55b7c48241ba3f6b9ba0`

- `https://talentprotocol.com/0x35b68340c61f26147b7b22f5ab931892bd9358b3`  
  `https://talent.app/0x35b68340c61f26147b7b22f5ab931892bd9358b3`

… and similarly for:

`0xff809a9b2085a7247edd03e03ed71df905c2af32`  
`0x8c62c144278152187ac3101e99cc5fc39a3d4a9e`  
`0x4e106aa5353517e42cbba4c91442fcb687feaf99`  
`0x7e9d35b9db5dea61f85f4f14f4c972b77d75a674`  
`0x70caa9feefc36e1422ecc055ac1f0de48cb320d7`  
`0xeafb7ffef83ea0a1ae82366f13dcc32d9377818c`  
`0x649c96d36f55c3f55962a080b638e8a6680475a9`  
`0x0ba3623d2ea6bb1c39f5a95607ff11505ddc9a2d`  
`0x30f217404a91e8c82d126a82a197637bb951a166`  
`0x2efd6cfc8ec8c7c0e69a358c85b3a121e0e8c2fd`  
`0xa580287b4e3d5d1c07392b8b805a8470dabdf9dc`  
`0x2eade7ea53ca2ca6477c0ba5526393eaeeef1784`  
`0xd186573cb7fdb21af5bbc6fad9d02b19e7dd1951`  
`0x2218599ab3ed37effbe514f1c0b1001b4833eec3`  
`0x9e26b98d4fadf70d0c0e57c609347358934a934c`

This is perfectly aligned with the **Account** model and account-specific URLs described in your docs.

---

### 3.2. ENS & Basename URLs (inconsistent behavior)

When we try to access our profiles via ENS/Basenames instead of raw addresses, we see mixed results:

#### A. `myreceipt`

- `https://talentprotocol.com/myreceipt.base.eth` → 404 Not Found  
- `https://talentprotocol.com/myreceipt.eth` → 404 Not Found **(this worked yesterday)**    
- `https://talentprotocol.com/myreceipt` → 404 Not Found **(this worked yesterday)**   

- `https://talent.app/myreceipt.base.eth` → 404 Not Found  
- `https://talent.app/myreceipt.eth` → 404 Not Found **(this worked yesterday)**  
- `https://talent.app/myreceipt` → 404 Not Found **(this also worked yesterday)**  

This feels like a regression, because at least some of these URLs used to resolve to our profile.

#### B. `endhonesa`

- `https://talentprotocol.com/endhonesa.base.eth` → 404 Not Found  
- `https://talentprotocol.com/endhonesa.eth` → 200 OK  
- `https://talentprotocol.com/endhonesa` → 200 OK  

- `https://talent.app/endhonesa.base.eth` → 404 Not Found  
- `https://talent.app/endhonesa.eth` → 200 OK  
- `https://talent.app/endhonesa` → 200 OK  

So for `endhonesa`, the “short” forms (`/endhonesa` and `/endhonesa.eth`) work as aliases, but the Basename form (`/endhonesa.base.eth`) does not.

#### C. `skateshop`

- `https://talentprotocol.com/skateshop.base.eth` → 404 Not Found  
- `https://talentprotocol.com/skateshop.eth` → 404 Not Found  
- `https://talentprotocol.com/skateshop` → 404 Not Found  

- `https://talent.app/skateshop.base.eth` → 404 Not Found  
- `https://talent.app/skateshop.eth` → 404 Not Found  
- `https://talent.app/skateshop` → 404 Not Found  

In this case, none of the variants resolve, even though:

- `skateshop.eth` and `skateshop.base.eth` correctly resolve onchain to a verified address, and  
- that underlying address already has a working address-based profile URL.

---

## 4. Expected vs Actual

We couldn’t find an explicit spec in the docs that says:

> “Every ENS or Basename that resolves to a verified address will always be available as `/name`, `/name.eth` or `/name.base.eth`.”

So this issue is more about **consistency and clarity** than about contradicting a written spec.

**Based on the current behavior and docs, our expectations are:**

- Since Talent Protocol already:
  - tracks a **Primary ENS Domain** and ENS/Basename identity data points, and  
  - supports searching profiles by ENS / Basename via the API,

  it would be natural if any *supported* ENS or Basename that resolves to a verified address could be used as a stable profile URL alias as well — or, if that’s intentionally not the case, that the intended behavior is clearly documented.

- At minimum, we’d expect:
  - Behavior to be consistent across `talentprotocol.com` and `talent.app`, and  
  - URLs that used to work (like `myreceipt.eth` on talent.app) should not silently regress to 404 unless there is a deliberate breaking change and some guidance on the new pattern.

**Actual behavior:**

- Some ENS/Basename URLs resolve correctly (e.g. `/endhonesa`, `/endhonesa.eth`).  
- Some ENS/Basename URLs that used to resolve (`/myreceipt`, `/myreceipt.eth` on talent.app) now return 404.  
- Some ENS/Basenames for the same underlying address (`skateshop.eth`, `skateshop.base.eth`) don’t resolve at all, despite the underlying address having a working address-based profile URL.  
- In the app UI, primary names are surfaced as expected, but secondary ENS/Basenames pointing to the same verified addresses are not consistently surfaced.

---

## 5. Impact

From a user perspective:

- It’s hard to know which identity strings are “safe” to share as public profile links (ENS vs Basename vs short handle).  
- Links using ENS/Basename that previously worked (like `myreceipt.eth`) can become 404s, which isn’t ideal for long-term reputation and identity.  
- For multi-brand setups (e.g. `myreceipt`, `endhonesa`, `skateshop` all pointing to the same or related wallets), the mental model:
  > “Any verified ENS or Basename for my wallets is a valid profile URL alias”
  currently doesn’t hold, even though it feels aligned with the Data Points and identity model.

---

## 6. Suggestions

If it fits your roadmap, it might help to:

1. **Document URL alias rules**  
   - Clearly state which naming schemes (ENS, Basename, others) are supported as profile URL aliases.  
   - Clarify which patterns are expected to work (e.g. `/name`, `/name.eth`, `/name.base.eth`) and how they map to Users / Accounts / Profiles.

2. **Clarify primary vs secondary names**  
   - If only primary ENS/Basenames are meant to behave as URL aliases, stating that explicitly in the docs (and maybe in the app UI) would already reduce confusion.  
   - If multiple aliases per wallet are intended, then `skateshop.eth` and `skateshop.base.eth` feel like good test cases to surface.

3. **Guard against regressions**  
   - If some ENS-based URLs are officially supported, it would be great to avoid regressions like the `myreceipt.eth` URLs that worked yesterday and are now 404, or at least to signal that behavior is experimental/subject to change.

---

## 7. Happy to help more

We are very happy to keep reporting issues like this as a heavy user of Talent, especially around multi-identity setups (multiple ENS/Basenames and wallets mapped to one person/organization).

If you find this kind of detailed QA useful, we’d love to contribute more formally as well:

- Testing new identity/profile features before launch.  
- Opening detailed issues or even documentation PRs in your public repositories.  
- Providing structured feedback on edge cases (multi-brand, multiple smart accounts, Base builder rewards participants, etc.).

Please let us know:

- If there’s a preferred place to report issues like this (GitHub repo, specific Discord channel, or an issue form).  
- And if there are contribution paths (open issues, QA tasks, docs) where something like us could be listed as a contributor.

Thanks a lot for building Talent Protocol & Talent App — and for taking the time to look into this.

Reported by,  
**Prof. NOTA** (on [Farcaster](https://farcaster.xyz/myreceipt) / [X](https://x.com/MyReceiptTT))

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---

