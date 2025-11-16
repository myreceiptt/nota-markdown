---
description: >-
  Peta alur nilai BGC × iBLOOMING dari AS-IS ke TO-BE di Base blockchain—menetapkan konversi PC/SP→ALPHA, model peristiwa append-only (hashed proofs), cash-out windows (KYC), serta parameter Pilot yang selaras dengan 5 Sasaran Strategis.
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
  - [WHITEPAPER Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=307NXv8YeYMxsWTZaV5z&only=yes&limit=100) (Outline)  
  - [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100)) (definisi PC/SP)  
  - [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100) (Strategic Objectives)  
---

# 0. Glosarium
- **PC**: 100 PC = 1 USD (utility utama: produk fisik BGC).
- **SP**: meter hak reward; basis payout USD periodik.
- **ALPHA**: *settlement layer* konversi PC/SP → rights; **ERC-20 interface, non-transferable; mint/burn hanya via AlphaController** (pra iBC/iBTC).
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
- PC→ALPHA: 100 PC : 1 ALPHA; fee 0; cooldown 0.
- SP→ALPHA: $1 : 1 ALPHA; fee 0; cooldown 0.
- Default: ALPHA dipakai untuk spend / access / stake (internal).
- Payout USD untuk komponen BGC tertentu tetap AS-IS (lihat [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100)).

### 2.1.1 Cash-Out Windows (Pilot v1)
- Frekuensi: 4× per tahun (triwulanan).
- Durasi jendela: 7 hari per jendela.
- Minimum payout: $50.
- Biaya payout: 100 bps (1%).
- KYC: wajib.
- Catatan: jalur sekunder & terjadwal untuk nilai keluar ekosistem.

## 2.2 Partner Loop (bertahap)
- Akses belanja eksternal kurasi/terbatas → menjaga nilai tetap berputar.

## 2.3 Demand Engine (iBLOOMING)
- Sinks & multiplier (kelas, fitur premium, boost) untuk serap nilai.

# 3. Event Model (auditability)
Definisi event pokok + field minimal:
- `JoinAffiliate`, `MintPC`, `SpendPC`, `EarnSP/AccrueLTS`, `CPContribution`, `PoolAccrual`, `ConvertToALPHA`, `Spend/Stake/Access`, `CashoutWindowOpened/Closed`, `PayoutUSD`.

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
| **Fairness metric** | Gap-(ops) | Affiliate↑, Active users↑ | **Reward Gini Coefficient** | [isi]

# 6. Open Questions
- Ambang & frekuensi cash-out? Sinks prioritas Q1? Parameter rate-limit awal?
