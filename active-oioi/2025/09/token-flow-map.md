---
description: >-
  We don't belong in your reality, your real life. In your reality, your real
  life, you can merely meet our avatars in any version. So, stay alert and
  beware of scams!
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

---
title: "iBLOOMING × BGC — TOKENFLOW v1 (AS-IS → TO-BE)"  
version: "v1.0.0-draft"  
date: "2025-10-28"  
language: "ID"  
ties_to:  
  - WHITEPAPER v1 (Outline)  
  - UNDERSTANDING Doc (definisi PC/SP)  
  - LIVING Doc (Strategic Objectives)  
---

# 0. Glossary (sinkron UNDERSTANDING)
- **PC**: 100 PC = 1 USD (utility utama: produk fisik BGC).
- **SP**: meter hak reward; basis payout USD periodik.
- **ALPHA**: settlement layer konversi PC/SP → rights (pra iBC/iBTC).
- **iBC/iBTC**: token on-chain pasca simulasi/validasi.

# 1. AS-IS (ringkas)
## 1.1 BGC On-Ramp & PC
- Fiat in → PC naik → belanja produk fisik → PC turun.
- Pain: PC idle; utility terbatas.

## 1.2 BGC SP & Payout
- SP terbentuk dari aktivitas (LTS/RR/GR/...) → payout USD.
- Pain: value keluar ekosistem; admin-dependency.

## 1.3 iBLOOMING Revenue & Rewards
- Penerimaan & distribusi fiat periodik; transparansi real-time terbatas.

# 2. TO-BE (konversi via ALPHA)
## 2.1 Unified Conversion
- PC/SP → **ALPHA rights** → default: spend / access / stake (internal).
- Cash-out jadi opsi sekunder (window terjadwal, limit, anti-abuse).

## 2.2 Partner Loop (bertahap)
- Akses belanja eksternal kurasi/terbatas → menjaga nilai tetap berputar.

## 2.3 Demand Engine (iBLOOMING)
- Sinks & multiplier (kelas, fitur premium, boost) untuk serap nilai.

# 3. Event Model (auditability)
Definisi event pokok + field minimal:
- `JoinAffiliate`, `MintPC`, `SpendPC`, `EarnSP(LTS/RR/GR/...)`,
  `PayoutUSD`, `ConvertToALPHA`, `MintRights`, `Spend/Stake/Access`,
  `CashoutWindowOpened/Closed`.
Field: `actor`, `timestamp`, `delta`, `new_state`, `proofs|refs`.

# 4. Policy Placeholders (diisi Tokenomics)
- Rasio PC/SP → ALPHA, fee konversi, kuota mingguan, cooling-off.
- Anti-wash & anti-self-dealing rules; dispute & rollback policy terbatas.

# 5. Alignment Table (Solusi ↔ GAP ↔ Objective ↔ KPI)
| Solusi/Aturan | GAP yang Ditutup | Objective | KPI Utama | Catatan |
|---|---|---|---|---|
| Jembatan PC/SP→ALPHA | Gap-1 | Revenue↑, Active users↑ | ARPU, MAU/WAU | [isi] |
| Cash-out window terjadwal | Gap-2 | Cost↓, Tax↓ | Biaya/tx, Tax incidents | [isi] |
| Append-only ledger (events) | Gap-4 | Cost↓ | MTTR ops, error rate | [isi] |
| Rate-limit + anti-abuse | Gap-3 | Cost↓, Affiliate↑ | Ops cost, Retention | [isi] |
| Sinks (kelas/fitur/boost) | Gap-6 | Revenue↑ | GMV on-platform | [isi] |

# 6. Open Questions
- Ambang & frekuensi cash-out? Sinks prioritas Q1? Parameter rate-limit awal?
