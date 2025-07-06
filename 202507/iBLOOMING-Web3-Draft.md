# iBLOOMING x Prof. NOTA — Web3 Integration Draft

## 🧩 Overview

This document outlines two foundational elements for the iBLOOMING Web3 transition:
1. **Unified Web3 Login System** using ThirdWeb SDK
2. **Alpha Coin** as a loyalty-driven simulation token

These systems are designed for internal testing and user behavior analysis, paving the way toward a public token launch with real economic and governance utility.

---

## 1. Web3 Login System (Unified Wallet Identity)

### 🎯 Objective

To integrate a seamless Web3 login system across all iBLOOMING applications, enabling each user to:
- Automatically generate and own an in-app wallet
- Use a consistent **smart account wallet** across platforms (web/mobile)
- Benefit from on-chain features without crypto knowledge

---

### 🔧 Technical Components

| Component             | Technology                         | Description |
|-----------------------|-------------------------------------|-------------|
| In-App Wallet         | ThirdWeb Embedded/Smart Wallet SDK | Automatically created upon login |
| Smart Account Wallet  | ThirdWeb Smart Wallet SDK          | Contract-based wallet (ERC-4337) |
| Login Bridge          | Middleware (e.g., Node.js/Next.js) | Connects Web2 auth with wallet creation |
| Session Sync          | JWT / App Metadata                 | Keeps session identity synced |
| Wallet Registry       | Database or Smart Contract         | Maps user ID to wallet address |

---

### 🔄 Login Flow

```plaintext
[1] User logs in via existing iBLOOMING account (email/password)
     ↓
[2] System checks if user has wallet (in-app + smart account)
     ↓
    [Yes] → Load wallet address → Sync with session
    [No] → Auto-create wallet → Save wallet info → Proceed with login
     ↓
[3] When user logs into another app (e.g., mobile), system recognizes same user → assigns same wallet
```

---

### ✅ Key Principles

- **Single Wallet Identity** across all platforms
- **Zero Friction Onboarding** — wallets are created behind the scenes
- **Modular** — applicable to any iBLOOMING app without refactoring frontend logic
- **Private** — wallet data is stored securely and linked to internal user ID

---

## 2. Alpha Coin — Loyalty Simulation & Distribution Logic

### 🎯 Purpose

To simulate token-based rewards, saving patterns, and spending behaviors within a controlled loyalty program — before launching a public crypto token.

---

### 🏷 Temporary Name: `ALPHA COIN`

---

### ⚙️ Token Attributes

| Attribute       | Value |
|----------------|-------|
| Token Type      | ERC-20 (non-tradable at first) |
| Initial Use     | Loyalty + engagement reward |
| Tradability     | Disabled during simulation phase |
| Transferability | Disabled (mint + burn only) |
| Smart Wallet    | Required for claiming & holding |

---

### 📊 Proposed Distribution Logic

| User Action                                                  | Reward (Alpha Coins) |
|--------------------------------------------------------------|-----------------------|
| Finish 1 educational video                                   | 5 AC                  |
| Purchase single video (pay-per-view)                         | 10 AC                 |
| Subscribe to a creator’s channel (monthly)                   | 25 AC                 |
| Login daily for 7 days straight                              | 20 AC                 |
| Complete AI profiling (PROFILE.IBLOOMING.AI)                 | 50 AC                 |
| Refer new user who studies for 3+ days                       | 75 AC                 |

---

### 💰 Saving vs Spending Simulation

| User Type         | Save Ratio | Spend Ratio | Behavior Notes |
|-------------------|------------|-------------|----------------|
| Regular Learner   | 20%        | 80%         | Uses coins to unlock more content |
| Active Affiliate  | 40%        | 60%         | Uses coins for team reward bonuses |
| Content Creator   | 60%        | 40%         | Saves for governance/reinvestment |

These simulations should be tracked via internal dashboard or analytics module.

---

### 🪜 Coin Rollout Phases

| Phase | Description |
|-------|-------------|
| Phase 1: Alpha Coin (Internal Only) | Closed-loop simulation inside iBLOOMING apps |
| Phase 2: Feedback & Data Analysis   | Evaluate distribution ratio, saving vs. spending behavior |
| Phase 3: iBLOOMING COIN (Public)    | Tradable token, usable in partner apps, supports governance |

---

## 🌱 Vision Alignment

This system supports iBLOOMING’s transition into a **Web3-native learning ecosystem** with:
- Trustless user incentives
- Distributed economic models
- Governance-by-participation
- Seamless onboarding for non-crypto users

Prof. NOTA’s role is to lead, simulate, and refine both the architecture and token logic before scale-up.

---