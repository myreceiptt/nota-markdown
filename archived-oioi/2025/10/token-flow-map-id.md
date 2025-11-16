---
description: >-
  Peta alur nilai BGC × iBLOOMING dari AS-IS ke TO-BE di Base—menetapkan konversi PC/SP→ALPHA, model peristiwa append-only (bukti ter-hash), cash-out windows (KYC), serta parameter Pilot v1 yang selaras dengan 5 Sasaran Strategis.
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
  - [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100) (definisi PC/SP)
  - [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100) (Sasaran Strategis)
---

# 0. Glosarium (sinkron UNDERSTANDING)
- **PC** — 100 PC = 1 USD (utilitas utama: produk fisik BGC).
- **SP** — meter/hak reward; basis payout USD periodik.
- **ALPHA** — *settlement layer* konversi PC/SP → hak (rights); **antarmuka ERC-20, non-transferable; mint/burn hanya via AlphaController** (pra iBC/iBTC).
- **iBC / iBTC** — token on-chain yang diaktifkan pasca simulasi/validasi & legal sign-off.
- **AA (Smart Account / Account Abstraction)** — dompet berbasis kontrak yang dipetakan via Wallet Registry (setelah Web3 Login).
- **EventHub** — pencatat peristiwa *append-only* dengan **bukti ter-hash** ke dokumen/bukti off-chain.

# 1. AS-IS (ringkas)
## 1.1 BGC On-Ramp & PC
- Fiat masuk → PC naik → belanja produk fisik → PC turun.  
  *Pain:* PC menganggur; utilitas terbatas.

## 1.2 BGC SP & Payout
- SP terbentuk dari aktivitas (LTS/RR/GR/…) → payout USD periodik.  
  *Pain:* nilai keluar ekosistem; ketergantungan admin.

## 1.3 iBLOOMING Revenue & Rewards
- Penerimaan & distribusi fiat periodik; transparansi real-time terbatas.

# 2. TO-BE (konversi via ALPHA)
## 2.1 Konversi Terpadu (v1 Pilot)
- **PC→ALPHA:** 100 PC : 1 ALPHA; biaya **0**; cooldown **0**.  
- **SP→ALPHA:** $1 : 1 ALPHA; biaya **0**; cooldown **0**.  
- **Default:** ALPHA dipakai untuk **belanja / akses / stake** (internal).  
- **Payout USD** pada komponen BGC tertentu tetap **AS-IS** (rujuk UNDERSTANDING Doc).

### 2.1.1 Cash-Out Windows (v1 Pilot)
- **Frekuensi:** 4× per tahun (triwulanan).  
- **Durasi jendela:** 7 hari per jendela.  
- **Minimum payout:** $50.  
- **Biaya payout:** 100 bps (1%).  
- **KYC wajib.**  
- **Catatan:** jalur sekunder & terjadwal untuk nilai yang keluar ekosistem.

## 2.2 Partner Loop (bertahap)
Akses belanja eksternal yang terkurasi/terbatas → menjaga nilai tetap berputar di jaringan.

## 2.3 Demand Engine (iBLOOMING)
*Sinks* & pengali (kelas, fitur premium, *boost*) untuk menyerap nilai di dalam platform.

# 3. Model Peristiwa (auditabilitas)
**Daftar event (minimal final):**  
`JoinAffiliate`, `MintPC`, `SpendPC`, `EarnSP/AccrueLTS`, `CPContribution`, `PoolAccrual`, `ConvertToALPHA`, `Spend/Stake/Access`, `CashoutWindowOpened/Closed`, `PayoutUSD`.

**Kolom minimal per event (skema):**
- `actor_id` (string) — id internal pengguna/entitas  
- `what` (enum) — tipe event (sesuai daftar di atas)  
- `amount` (decimal) — nilai numerik event  
- `unit` (string) — PC | SP | ALPHA | USD | count  
- `timestamp` (iso8601) — waktu event (UTC)  
- `ref_id` (string) — id rujukan (nota/invoice/dokumen)  
- `channel` (string) — web/app/partner (opsional)  
- `data_hash` (hex) — hash jangkar ke bukti off-chain (berkas/url)

> *Append-only:* catatan tidak diubah/dihapus; koreksi dibuat sebagai event baru dengan keterkaitan `ref_id`.

# 4. Kebijakan & Parameter
**Prinsip:** berbasis perilaku (*behavior-based*), non-spekulatif; perubahan kebijakan diberi versi.

## 4.1 Nilai Pilot v1 (selaras WHITEPAPER)
**Sponsor Gas & Batasan (v1)**
- `sponsor_gas.enabled = true`  
- `actions_covered = [onboarding, convert_to_alpha, spend/access]`  
- `daily_cap_per_user ≈ $0.10`  
- `global_daily_budget ≈ $20`  
- `throttle_global = true` ; `pausable = true`

**Anti-Penyalahgunaan & Sybil (v1)**
- `referral_cooldown_days = 1` ; `max_tier1_joins_per_actor_per_day = 10`  
- `require_unique_device = true` ; `duplicate_device_limit = 2`  
- `audit_sample_rate_pct = 5`  
- `wash_trade_zeroing = true` ; `penalty_cooling_off_days = 7`

**Ritme Penyelesaian (v1)**
- `accrual_frequency = harian` ; `points_settlement_frequency = mingguan`  
- `pool_distribution = { GPS: semesteran, WEC: triwulanan, MC: bulanan, GMP: bulanan, GEC: bulanan }`

## 4.2 Placeholder yang diisi oleh Tokenomics
- Aturan penyesuaian PC/SP→ALPHA pasca pilot; kuota mingguan; cooldown lanjutan.  
- Penyempurnaan anti-wash/self-dealing; kebijakan *dispute* & *rollback* terbatas.

# 5. Catatan Kepatuhan & Komunikasi
- **ALPHA = loyalty/rights**, **non-transferable**; transfer bebas dinonaktifkan (hanya alur yang dikendalikan Controller).  
- **USD payout (AS-IS)** untuk komponen BGC tertentu tetap berjalan tanpa perubahan.  
- **Cash-out windows = jalur sekunder & terjadwal; KYC wajib.**  
- **Legal sign-off adalah gerbang keras** sebelum fase publik **iBC/iBTC**.  
- Komunikasi publik menghindari bahasa investasi; cantumkan risiko & batas penggunaan.

# 6. Tabel Penyelarasan (Solusi ↔ GAP ↔ Sasaran ↔ KPI)
| Solusi/Kebijakan               | GAP yang Ditutup | Sasaran                      | KPI Utama                    | Catatan             |
|---|---|---|---|---|
| Jembatan PC/SP→ALPHA          | Gap-1            | Revenue↑, Active users↑      | ARPU, MAU/WAU               | (untuk simulasi)    |
| Cash-out window terjadwal     | Gap-2            | Cost↓, Tax↓                  | Biaya/tx, Insiden pajak     | (untuk simulasi)    |
| Ledger append-only (events)   | Gap-4            | Cost↓                        | MTTR ops, Error rate        | (untuk simulasi)    |
| Rate-limit + anti-abuse       | Gap-3            | Cost↓, Affiliate↑            | Biaya ops, Retensi          | (untuk simulasi)    |
| Sinks (kelas/fitur/boost)     | Gap-6            | Revenue↑                     | GMV on-platform             | (untuk simulasi)    |
| **Metrik fairness**           | Gap-ops          | Affiliate↑, Active users↑    | **Koefisien Gini Reward**   | (untuk simulasi)    |

# 7. Catatan Keputusan — v1 (Pilot)
- **Konversi:** `100 PC → 1 ALPHA` ; `$1 SP → 1 ALPHA` ; biaya `0` ; cooldown `0`.  
- **Cash-Out Windows:** `4×/tahun` ; `7 hari` ; `min $50` ; `biaya 1%` ; `KYC = true`.  
- **Sponsor Gas Caps:** `≈$0.10 / pengguna / hari` ; `≈$20 / global / hari` ; throttle/pause aktif.  
- **Anti-Abuse:** referral cooldown `1 hari` ; `10` pendaftaran Tier-1/aktor/hari ; aturan perangkat ; sampling `5%` ; `zeroing + cooling_off 7 hari`.  
- **Ritme Penyelesaian:** akrual `harian` ; rekap poin `mingguan` ; distribusi pool sesuai §4.1.

# 8. Pertanyaan Terbuka
- Ambang & frekuensi cash-out pasca pilot; prioritas sink Q1/Q2; parameter rate-limit awal/penyesuaian; *gates* ekspansi partner loop.

