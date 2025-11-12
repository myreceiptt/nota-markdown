---
description: >-
  We don't belong in your reality, your real life. In your reality, your real
  life, you can merely meet our avatars in any version. So, stay alert and
  beware of scams!
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# iBLOOMING x BGC - WHITEPAPER

---

{% hint style="success" %}

- title: Whitepaper v1 • 1-Pager Eksekutif  
- version: v1.0.0-draft  
- date: 2025-10-28  
- language: ID  

{% endhint %}

---

## Ringkasan
Ekosistem iBLOOMING × BGC sudah berjalan, namun terdapat 6 gap alur nilai: (1) jembatan konversi PC/SP terbatas, (2) value leakage ke luar ekosistem, (3) admin-dependency tinggi, (4) transparansi real-time rendah, (5) fiat-first tax drag, (6) pertumbuhan BGC > iBLOOMING (imbalance).
**Solusi:** lapisan settlement **ALPHA** yang mengonversi PC/SP menjadi hak ter-tokenisasi (spend/access/stake) → transisi terukur ke **iBC/iBTC**. Nilai berputar di dalam ekosistem, cash-out menjadi jalur sekunder dan terkendali.

## Dampak pada Strategic Objectives ([LIVING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100#pdf-page-ijQlNvGkp9UTE2LR2Tjm-strategic-objectives-reaffirmed))
- **Revenue ↑**: utility on-platform mendorong GMV & ARPU.
- **Cost ↓**: otomasi event ledger & rate-limit menekan biaya ops/tx.
- **Tax burden ↓**: settlement internal yang compliant menurunkan kejadian pajak.
- **Affiliate ↑**: insentif & utility yang jelas meningkatkan aktivasi/retensi.
- **Active users ↑**: unified utility + WEB3LOGIN mempermudah adopsi.

## Tokenomics (sekilas)
- **Prinsip**: berbasis perilaku (hasil simulasi **ALPHA**), bukan spekulasi.
- **Utility & Sinks**: belanja produk/kelas/fitur, akses premium, staking/boost; sink lewat biaya pemakaian & event-based burn.
- **Conversion Policy**: PC/SP → **ALPHA rights** (default: spend/access/stake); **cash-out windows** terjadwal, berkuota, anti-abuse.
- **Governance & Compliance**: tata kelola bertahap; catatan kepatuhan per yurisdiksi (memo terpisah).

## Roadmap Ringkas
- 1a) Simulasi ALPHA → 2a) **Whitepaper v1** → 3a) **Tokenflow Map v1** → 4) Sign-off Founder → 5) Pilot utility iBC/iBTC → 6) Perluasan lintas-app.
- 1b) **Web3 Login** Plan → 2b) Implementasi **Web3 Login** → 3b) Launch **Web3 Login** → 4) Sign-off Founder → 5) Pilot utility iBC/iBTC → 6) Perluasan lintas-app.

## Keputusan yang Diminta (Founder)
**Menyetujui Whitepaper v1** dengan 3 parameter terbuka untuk ditetapkan saat rapat: rasio konversi awal PC/SP→ALPHA, kebijakan **cash-out windows**, dan prioritas **sinks Q1**.

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
[PLACEHOLDER — 150 kata]
- Masalah inti (6 gap alur nilai) → Solusi (ALPHA → iBC/iBTC) yang langsung memetakan ke 5 Strategic Objectives.

## 2. Problem Statement (singkat)
- Gap-1: Conversion bridge PC/SP → outcomes terbatas.
- Gap-2: Interoperability & value leakage (nilai keluar ekosistem).
- Gap-3: Admin-dependency (operational manual).
- Gap-4: Transparansi real-time rendah (auditability).
- Gap-5: Fiat-first tax drag.
- Gap-6: Pertumbuhan BGC > iBLOOMING (imbalance).

Catatan: daftar gap mengacu pada [UNDERSTANDING Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=4Eh8GomcmSGx85uX6sBg&only=yes&limit=100) + [LIVING Doc ](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=ijQlNvGkp9UTE2LR2Tjm&only=yes&limit=100#pdf-page-ijQlNvGkp9UTE2LR2Tjm-strategic-objectives-reaffirmed); rinciannya dipadatkan di [TOKENFLOW Doc](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=USH0cBRq7yGXLwTmmFDJ&only=yes&limit=100).

## 3. Solution Overview (C → A → B)
### 3.1 Concept
- Reframe PC/SP sebagai **hak ter-tokenisasi** via lapisan settlement **ALPHA**.
- Target: utility default di dalam ekosistem; cash-out jadi jalur sekunder & terkendali.

### 3.2 Analogy
- “Jembatan konversi” internal: PC/SP → ALPHA rights → spend / access / stake lintas-aplikasi.
- Nilai berputar: lebih sedikit bocor ke luar.

### 3.3 Build (Implementasi Tingkat Tinggi)
- Settlement Layer (ALPHA): aturan konversi, event model, rate-limit, audit trail.
  * **ALPHA** berantarmuka ERC-20, **non-transferable**, **mint/burn hanya via AlphaController**; transfer bebas dinonaktifkan (kecuali *system-governed flows*).
  * **EventHub** sebagai *append-only ledger* dengan **hashed proofs** ke dokumen off-chain.
- Utility Map: spend (produk/layanan), access (fitur/kelas), stake (komitmen).
- Dashboard transparan (append-only ledger) untuk klaim/entitlement.

## 4. Tokenomics (kerangka)
### 4.1 Objectives ↔ KPI
- Revenue↑ → KPI: ARPU/GMV on-platform.
- Cost↓ → KPI: biaya operasional/tx per 1.000 tx.
- Tax burden↓ → KPI: penurunan kejadian pajak melalui internal settlement (taat aturan).
- Affiliate↑ → KPI: #affiliate aktif, retention 30/90D.
- Active users↑ → KPI: MAU/WAU lintas-app.
[Isi baseline & target setelah sesi data.]

### 4.2 Supply & Emission
- Prinsip: berbasis perilaku (hasil simulasi ALPHA), bukan spekulasi.
- Parameter: [PLACEHOLDER angka awal + metode penyesuaian berkala]

### 4.3 Distribution
- Pool utilitas (spend/access/stake), insentif afiliasi, cadangan ekosistem.

### 4.4 Utilities & Sinks
- Utilities: belanja produk, akses fitur/kelas, staking untuk boost.
- Sinks: biaya pemakaian, burn event-based, biaya premium.

### 4.5 Conversion Policy (PC/SP → ALPHA → iBC/iBTC)
- Jalur default: internal utility. **Payout USD** pada komponen BGC yang telah ada **tetap berjalan sesuai UNDERSTANDING Doc.**; **cash-out windows** mengatur *externalization* nilai secara terjadwal & terkendali.
- Cash-out windows: terjadwal, berkuota, anti-abuse, cooling-off.

### 4.6 Governance & Risk
- Tata kelola bertahap; rate-limit; orkestrasi kebijakan.
- Peta risiko: operasional, pasar, kepatuhan, reputasi.

### 4.7 Compliance Note
* **PC** adalah bukti transaksi produk fisik (MLM legal requirement).
* **Affiliate membership hanya bisa dibeli dengan fiat** (tidak dengan PC maupun token).
* **Legal sign-off** diperlukan sebelum peluncuran publik iBC/iBTC.

## 5. Roadmap (tingkat tinggi)
- Simulasi ALPHA → Whitepaper v1 → Tokenflow Map v1 → **Single Founder Sign-Off (incl. Legal Gate)** → Pilot utility iBC/iBTC → Perluasan lintas-app.
- Web3 Login Plan → Web3 Login Implementation → Launch Web3 Login → **Single Founder Sign-Off (incl. Legal Gate)** → Pilot utility iBC/iBTC → Perluasan lintas-app.

## 6. Data & Metodologi
- Sumber data 24 bulan; definisi metrik; aturan cleaning; reproducibility.

## 7. Open Questions
- Ambang cash-out, rasio konversi awal, prioritas sinks Q1, daftar use case prioritas.

## Lampiran
- Tabel istilah; tabel event; diagram arsitektur ringkas.

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---

