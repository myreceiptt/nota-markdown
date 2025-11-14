---
description: >-
  Bagaimana BGC × iBLOOMING memirror alur nilai ke Base blockchain dengan EventHub (append-only, bukti ter-hash) dan menata hak/loyalti dengan ALPHA (non-transferable, via AlphaController).
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# iBLOOMING × BGC — Whitepaper

_Integrasi Loyalti, Nilai, dan Transparansi On-Chain_

---

{% hint style="success" %}

- title: Whitepaper v1 • 1-Pager Eksekutif  
- version: v1.0.0-draft  
- date: 2025-10-28  
- language: ID  

{% endhint %}

---

## Dampak pada 5 Sasaran Strategis ([LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100#pdf-page-ijQlNvGkp9UTE2LR2Tjm-strategic-objectives-reaffirmed))
- **Revenue ↑**: utilitas di dalam platform mendorong GMV & ARPU.
- **Cost ↓**: otomasi event ledger & pembatasan laju (*rate limit*) menekan biaya operasional/transaksi.
- **Tax burden ↓**: settlement internal yang compliant menurunkan kejadian pajak.
- **Affiliate ↑**: insentif & utility yang jelas meningkatkan aktivasi/retensi.
- **Active users ↑**: utilitas terpadu + Web3 Login mempermudah adopsi.

## Tokenomics (sekilas)
- **Prinsip**: berbasis perilaku (hasil simulasi **ALPHA**), bukan spekulasi.
- **Utilitas & Serapan Nilai (Sinks)**: belanja produk/kelas/fitur, akses premium, staking untuk peningkatan (boost); serapan nilai melalui biaya pemakaian & burn berbasis peristiwa.
- **Kebijakan Konversi**: PC/SP → **hak ALPHA** (default: belanja/akses/stake); **cash-out windows** terjadwal, berkuota, anti-penyalahgunaan.
- **Governance & Compliance**: tata kelola bertahap; catatan kepatuhan per yurisdiksi (memo terpisah).

## Roadmap Ringkas
- 1a) Simulasi ALPHA → 2a) **Whitepaper v1** → 3a) **Tokenflow Map v1** → 4) Single Founder Sign-Off (incl. Legal Gate) → 5) Pilot utility iBC/iBTC → 6) Perluasan lintas aplikasi.
- 1b) **Web3 Login** Plan → 2b) Implementasi **Web3 Login** → 3b) Launch **Web3 Login** → 4) Single Founder Sign-Off (incl. Legal Gate) → 5) Pilot utility iBC/iBTC → 6) Perluasan lintas aplikasi.

## Keputusan yang Diminta (Founder)
**Menyetujui Whitepaper v1** dengan 3 parameter terbuka untuk ditetapkan pada **Single Founder Sign-Off (incl. Legal Gate)**: rasio konversi awal PC/SP→ALPHA, kebijakan **cash-out windows**, dan prioritas **sinks Q1**.

---

{% hint style="success" %}

- title: WHITEPAPER v1 (Outline)  
- version: v1.0.0-draft  
- date: 2025-10-28  
- language: ID  
- single_language_rule: true  
- sources_of_truth:  
  - [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100) (model bisnis/marketing)  
  - [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100#pdf-page-ijQlNvGkp9UTE2LR2Tjm-strategic-objectives-reaffirmed) (Strategic Objectives & guardrails)  

{% endhint %}

## 1. Ringkasan Eksekutif

BGC × iBLOOMING memirror alur nilai yang telah berjalan sejak 2023 ke Base melalui **EventHub** (append-only) yang menyimpan peristiwa kunci beserta **hash** bukti off-chain. Hak/loyalti ditata dengan **ALPHA**—berantarmuka ERC-20 yang **non-transferable**; **mint/burn** hanya melalui **AlphaController**—sehingga nilai **default** diputar di dalam ekosistem (belanja/akses/stake). **Payout USD** untuk komponen BGC tertentu **tetap AS-IS** sesuai [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100), sedangkan **cash-out windows** mengatur penyaluran keluar secara terjadwal dan terkendali. Arsitektur **Web3 Login + Wallet Registry → Smart Account (AA)** menjaga UX rendah friksi dan auditabilitas tinggi. Setelah **validasi data 24 bulan** dan **legal sign-off (hard gate)**, fase publik **iBC/iBTC** diluncurkan untuk memperluas utilitas lintas aplikasi. Strategi tiga babak ini menargetkan **5 Sasaran Strategis** (Revenue↑, Cost↓, Tax↓, Affiliate↑, Active Users↑) dengan KPI terukur, termasuk **Koefisien Gini Reward** untuk fairness distribusi. Peluncuran diikat oleh **Single Founder Sign-Off (incl. Legal Gate)** sebelum deployment.

- Masalah inti (6 gap alur nilai) → Solusi (ALPHA → iBC/iBTC) yang langsung memetakan ke **5 Sasaran Strategis**.

## 2. Pernyataan Masalah (Singkat)
- Gap-1: Jembatan konversi PC/SP → hasil terbatas.
- Gap-2: Interoperabilitas & kebocoran nilai (keluar ekosistem).
- Gap-3: Ketergantungan admin (operasional manual).
- Gap-4: Transparansi waktu nyata rendah (jejak audit kurang).
- Gap-5: Beban pajak tinggi akibat proses fiat-first.
- Gap-6: Pertumbuhan BGC > iBLOOMING (ketimpangan).

Catatan: daftar gap mengacu pada [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100) + [LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100#pdf-page-ijQlNvGkp9UTE2LR2Tjm-strategic-objectives-reaffirmed); rinciannya dipadatkan di [TOKENFLOW Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100).

## 3. Ikhtisar Solusi (C → A → B)
### 3.1 Konsep
- Membingkai ulang PC/SP sebagai **hak ter-tokenisasi** melalui lapisan penyelesaian **ALPHA**.
- Target: utility default di dalam ekosistem; cash-out jadi jalur sekunder & terkendali.

### 3.2 Analogi
- “Jembatan konversi” internal: PC/SP → **hak ALPHA** → belanja/akses/stake lintas aplikasi.
- Nilai berputar lebih lama di dalam; kebocoran ke luar menurun.

### 3.3 Rancangan (Implementasi Tingkat Tinggi)
- Settlement Layer (ALPHA): aturan konversi, model peristiwa, pembatasan laju (*rate limit*), dan jejak audit.
  * **ALPHA** berantarmuka ERC-20, **non-transferable**, **mint/burn hanya via AlphaController**; transfer bebas dinonaktifkan (kecuali *system-governed flows* — alur yang diatur sistem).
  * **EventHub** sebagai *append-only ledger* dengan **hashed proofs** ke dokumen off-chain.
- Peta utilitas: belanja (produk/layanan), akses (fitur/kelas), stake (komitmen).
- Dasbor transparan (*append-only ledger*) untuk klaim/hak (entitlement).
- Sponsor gas (aktif – Pilot v1): onboarding, convert_to_alpha, spend/access; batas per akun per hari ≈ $0,10; batas global per hari ≈ $20; throttle/pause aktif.

## 4. Tokenomics (Kerangka)
### 4.1 Tujuan ↔ KPI
- Revenue↑ → KPI: ARPU/GMV di dalam platform.
- Cost↓ → KPI: biaya operasional per 1.000 transaksi.
- Tax burden↓ → KPI: penurunan kejadian pajak melalui internal settlement (taat aturan).
- Affiliate↑ → KPI: jumlah afiliasi aktif; retensi 30/90 hari.
- Active users↑ → KPI: MAU/WAU lintas aplikasi.
- Fairness → KPI: Koefisien Gini Reward (ketimpangan distribusi).

*Catatan: baseline & target diisi setelah sesi data 24 bulan.*

### 4.2 Supply & Emission
- Prinsip: berbasis perilaku (hasil simulasi ALPHA), bukan spekulasi.
- Parameter: [PLACEHOLDER angka awal + metode penyesuaian berkala].

### 4.3 Distribusi
- Pool utilitas (spend/access/stake), insentif afiliasi, cadangan ekosistem.

### 4.4 Utilitas & Serapan Nilai (Sinks)
- Utilitas: belanja produk, akses fitur/kelas, staking untuk peningkatan (boost).
- Serapan nilai (sinks): biaya pemakaian, burn berbasis peristiwa, biaya premium.

### 4.5 Conversion Policy (PC/SP → ALPHA → iBC/iBTC)
- PC → ALPHA: 100 PC (= $1) → 1 ALPHA; fee 0 bps; cooldown 0 hari.
- SP → ALPHA: $1 SP → 1 ALPHA; fee 0 bps; cooldown 0 hari.
- Default pemanfaatan ALPHA: belanja / akses / stake di dalam ekosistem.
- Payout USD pada komponen BGC tertentu tetap AS-IS (lihat UNDERSTANDING Doc).

#### 4.5.1 Cash-Out Windows (Pilot v1)
- Frekuensi: 4× per tahun (triwulanan).
- Durasi jendela: 7 hari per jendela.
- Minimum payout: $50.
- Biaya payout: 100 bps (1%).
- KYC: wajib untuk setiap payout.
- Catatan: cash-out window adalah jalur sekunder & terjadwal untuk penyaluran nilai ke luar ekosistem.

### 4.6 Tata Kelola & Risiko
- Tata kelola bertahap; rate-limit; orkestrasi kebijakan.
- Peta risiko; operasional; pasar; kepatuhan; reputasi.
- Anti-Penyalahgunaan & Sybil (Pilot v1): referral cooldown 1 hari; maksimum 10 pendaftaran Tier-1 per aktor per hari; require_unique_device = true; duplicate_device_limit = 2; audit sampling 5%; penalti: wash_trade_zeroing = true, cooling_off = 7 hari.

### 4.7 Catatan Kepatuhan
* **PC** adalah bukti transaksi produk fisik (MLM legal requirement).
* **Keanggotaan afiliasi hanya bisa dibeli dengan fiat** (tidak dengan PC maupun token).
* **Legal sign-off** diperlukan sebelum peluncuran publik iBC/iBTC.
- KYC diberlakukan untuk pelaksanaan payout melalui cash-out windows (Pilot v1).
## 5. Roadmap (Tingkat Tinggi)
- Simulasi ALPHA → Whitepaper v1 → Tokenflow Map v1 → **Single Founder Sign-Off (incl. Legal Gate)** → Pilot utilitas iBC/iBTC → Perluasan lintas aplikasi.
- Web3 Login Plan → Web3 Login Implementation → Launch Web3 Login → **Single Founder Sign-Off (incl. Legal Gate)** → Pilot utilitas iBC/iBTC → Perluasan lintas aplikasi.

## 6. Data & Metodologi
- Sumber data 24 bulan; definisi metrik; aturan cleaning; reprodusibilitas.
- Standar privasi: anonimisasi PII dan *manifest* dataset untuk reprodusibilitas.

## 7. Pertanyaan Terbuka
- Ambang cash-out, rasio konversi awal, prioritas sinks Q1, daftar use case prioritas.

## Lampiran
- Tabel istilah; tabel event; diagram arsitektur ringkas.

### Daftar Parameter Awal (v1 Pilot)
**Konversi ke ALPHA (v1)**
- pc_to_alpha.ratio = 100 PC : 1 ALPHA; fee = 0 bps; cooldown = 0 hari.
- sp_to_alpha.ratio = $1 : 1 ALPHA; fee = 0 bps; cooldown = 0 hari.

**Cash-Out Windows (v1)**
- windows_per_year = 4; window_length_days = 7; min_payout_usd = 50; payout_fee_bps = 100; kyc_required = true.

**Sponsor Gas & Batas (v1)**
- sponsor_gas.enabled = true; actions_covered = [onboarding, convert_to_alpha, spend/access];
- daily_cap_per_user ≈ $0.10; global_daily_budget ≈ $20; throttle_global = true; pausable = true.

**Anti-Penyalahgunaan & Sybil (v1)**
- referral_cooldown_days = 1; max_tier1_joins_per_actor_per_day = 10;
- require_unique_device = true; duplicate_device_limit = 2;
- audit_sample_rate_pct = 5; wash_trade_zeroing = true; penalty_cooling_off_days = 7.

**Siklus Penyelesaian (v1)**
- accrual_frequency = harian; points_settlement_frequency = mingguan;
- pool_distribution: GPS = semesteran; WEC = triwulanan; MC = bulanan; GMP = bulanan; GEC = bulanan.

### Model Peristiwa (Minimal Final)

**Daftar event (audit trail):**
`JoinAffiliate`, `MintPC`, `SpendPC`, `EarnSP`/`AccrueLTS`, `CPContribution`, `PoolAccrual` (GPS/GMP/WEC/MC/GEC), `ConvertToALPHA`, `SpendAccess` / `Stake` / `Vote`, `CashoutWindowOpened`, `CashoutWindowClosed`, `PayoutUSD`.

**Kolom minimal per peristiwa:**
`actor`, `what`, `amount`, `unit`, `timestamp`, `refId`, `dataHash` (jangkar ke bukti off-chain).

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
