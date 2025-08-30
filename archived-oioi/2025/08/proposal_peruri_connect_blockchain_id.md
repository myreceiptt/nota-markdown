---
description: >-
  We don't belong in your reality, your real life. In your reality, your real
  life, you can merely meet our avatars in any version. So, stay alert and
  beware of scams!
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# PERURI CONNECT × BLOCKCHAIN — Template Proposal (Versi Bahasa Indonesia, Ramah Non‑Teknis)

> Tanggal draf: {{TANGGAL}}  
> Disiapkan untuk: **PERURI — Departemen TI/HR**  
> Disiapkan oleh: **Peruri Digital Security × Voyage**  
> Versi: {{VERSI}}

---

## 0) Ringkasan Eksekutif
**Tujuan.** Membangun sistem **Reward** karyawan yang **tercatat, bisa diverifikasi, dan aman** di atas **Blockchain** privat (permissioned). Sistem ini menyatu dengan **Peruri Connect** (login/SSO) dan aplikasi mobile yang sudah ada.  
**Manfaat utama.**
- Semua penerbitan Reward, transfer antar rekan (peer‑to‑peer), dan **redeem** (voucher/merch/fasilitas internal) **tercatat otomatis** dan **bisa diaudit**.
- **Aturan & kuota** dapat dikontrol (siapa boleh memberi, berapa banyak per hari/minggu/bulan).  
- **Dashboard** untuk HR/Manajemen: laporan, grafik, dan ekspor CSV untuk audit.  
**Target go‑live.** {{TANGGAL_GO_LIVE}} dengan pilot {{JUMLAH_PENGGUNA_PILOT}} pengguna.

> Catatan: Di dokumen ini, istilah yang umum dan teknis seperti **Reward**, **Blockchain**, **API**, **Dashboard**, **Token**, **Node** tetap menggunakan Bahasa Inggris agar konsisten dan mudah dikenali.

---

## 1) Sasaran & Indikator Keberhasilan
- **S1 — Verifiable Rewards.** Semua fungsi (issue/transfer/redeem) terekam di ledger dan mudah dilacak.  
- **S2 — P2P Recognition.** Karyawan dapat memberi Reward ke rekan kerja sesuai **kebijakan & kuota**.  
- **S3 — Integrasi Mulus.** Login pakai **Peruri Connect**; UI/UX konsisten di mobile app.  
- **S4 — Kontrol & Tata Kelola.** Role & approval flow yang jelas; bisa **pause/resume** saat darurat.  
- **S5 — Audit & Laporan.** Dashboard real‑time, ekspor data, dan jejak audit per transaksi.  

**KPI contoh (bisa disesuaikan):**
- SLA layanan ≥ **99,5%**; p95 waktu respons API < **2 detik**.  
- Finality transaksi < **5 detik** di jaringan privat.  
- UAT pass rate ≥ **95%**; kepuasan pengguna (CSAT) ≥ **80%**.

---

## 2) Ruang Lingkup Pekerjaan (Scope of Work)

### 2.1 Analisis & Desain
- Memetakan alur Reward saat ini (aktor, peran, kuota, pengecualian).  
- Mendesain **model token Reward** (mint dari Treasury → user, P2P dengan batasan).  
- Menentukan mekanisme **redeem** (katalog, settlement, refund, anti‑fraud).

### 2.2 Blockchain Core & Smart Contracts
- **Jaringan:** **Hyperledger Besu** (Blockchain privat/permissioned) + konsensus **IBFT 2.0** (finality cepat).  
- **Kontrak inti:** `RewardToken.sol` (token), `Treasury.sol` (kas), `Redemption.sol` (penukaran), `PolicyRegistry.sol` (kebijakan).  
- **Fitur kunci:** mint/burn; transfer P2P dengan kuota & cooldown; **pause/resume**; **role‑based access**; event untuk audit/log.

### 2.3 Integration Layer (Services/API)
- Backend **Node.js + TypeScript** (REST/GraphQL) sebagai gerbang ke Blockchain.  
- **Auth** via **Peruri Connect** (OAuth 2.0 + JWT).  
- **OpenAPI** (spesifikasi) + contoh request/response, serta **webhook** untuk mitra redeem.

### 2.4 Treasury & Admin Tools
- Dashboard admin (atur penerbit, kuota, kebijakan, katalog redeem, laporan).  
- Rekonsiliasi on‑chain/off‑chain & alert bila ada anomali.

### 2.5 Keamanan & Audit
- Review kode & **audit kontrak**; **penetration test** untuk API.  
- **Monitoring** (Prometheus) & **visualisasi** (Grafana); log terpusat.  
- Backup & Disaster Recovery (RPO/RTO disepakati).

### 2.6 Enablement
- Pelatihan untuk admin/ops/dev; runbook; handover; sesi **knowledge transfer**.

### 2.7 Support & Maintenance
- **Hypercare** pasca rilis; patch minor & perbaikan sesuai SLA.

---

## 3) Arsitektur Teknis — Penjelasan Gamblang

### 3.1 Kenapa **Hyperledger Besu** + **IBFT 2.0**?
- **Besu** adalah **Ethereum client** open‑source untuk **public** maupun **private/permissioned** network. Di mode privat, kita bisa membatasi **validator** (hanya node yang disetujui).  
- **IBFT 2.0 (Proof‑of‑Authority)** memberi **finality cepat** (blok yang disetujui tidak fork), cocok untuk transaksi internal perusahaan.  

> Referensi resmi:  
> • **Hyperledger Besu (docs)**: https://besu.hyperledger.org/  
> • **Besu — Private (Permissioned) Networks**: https://besu.hyperledger.org/private-networks  
> • **Tutorial — Create an IBFT 2.0 network**: https://besu.hyperledger.org/private-networks/tutorials/privacy

### 3.2 Topologi Dasar
- **Validator Nodes:** {{N_VALIDATORS}} (contoh 2–4; bisa ditempatkan di TI PERURI & PDS).  
- **Transaction Nodes (API‑facing):** {{N_TX_NODES}} untuk melayani aplikasi.  
- **BAS/Indexer (opsional):** untuk analitik dan pencarian cepat.  
- **Monitoring:** **Prometheus** (kumpulkan metrik) + **Grafana** (grafik/dashboards).  
- **Spesifikasi VM awal (per node):** 4 vCPU, 8 GB RAM, 200 GB SSD (disesuaikan hasil uji beban).

> Referensi resmi:  
> • **Start Besu / System Requirements**: https://besu.hyperledger.org/private-networks/get-started/start-node  
> • **Prometheus (official)**: https://prometheus.io/  
> • **Grafana (official)**: https://grafana.com/

### 3.3 Identitas & Akses
- User masuk lewat **Peruri Connect**; sistem memetakan role HR/Manajemen/Admin ke **role on‑chain** (mis. Minter, Policy Admin).  
- Aksi kritikal (ubah kebijakan, mint besar) dapat diproteksi **multisig** atau approval berjenjang.

### 3.4 Data & Privasi
- **On‑chain** hanya menyimpan data minimal (saldo token, event transaksi).  
- **PII** tetap di database **Peruri Connect** (off‑chain). Untuk audit, bisa simpan **hash/pointer** di on‑chain.

### 3.5 Kontrak API (Sketsa Awam)
- `POST /rewards/issue` — HR/Admin menerbitkan Reward ke karyawan.  
- `POST /rewards/transfer` — karyawan A memberi Reward ke karyawan B (sesuai kuota).  
- `POST /rewards/redeem` — menukar Reward ke item katalog (voucher/merch/benefit).  
- `GET /ledger/tx/:id` — cek detail transaksi.  
- `GET /reports/summary` — ringkasan agregat (periode, unit kerja, dsb.).

**Teknologi pendukung API:**  
- **Node.js** (runtime JavaScript untuk server) + **TypeScript** (pengetikan statis agar kode lebih aman/terbaca).  
- **OpenAPI** (standar deskripsi API) untuk dokumentasi otomatis.  
- **OAuth 2.0** (protokol otorisasi) + **JWT** (format token) untuk akses aman.

> Referensi resmi:  
> • Node.js: https://nodejs.org/  
> • TypeScript: https://www.typescriptlang.org/  
> • OpenAPI Initiative: https://www.openapis.org/  
> • OAuth 2.0: https://oauth.net/2/  
> • JWT (RFC 7519): https://datatracker.ietf.org/doc/html/rfc7519

---

## 4) Kebutuhan Fungsional (Functional Requirements)

### 4.1 Issue (Penerbitan)
- **Siapa** yang boleh menerbitkan (role Issuer/HR/Admin).  
- **Kuota** per periode (bulanan/kuartal), dan **batas per orang**.  
- **Aturan pembatalan** (burn/revoke) bila ada kesalahan input.

### 4.2 P2P Recognition (Transfer)
- **Batas harian/mingguan** dan **cooldown** per pengguna.  
- **Filter penerima** (mis. unit kerja/kontrak aktif).  
- **Pencegahan penyalahgunaan** (mis. anti “saling kirim” berulang).

### 4.3 Redeem
- **Katalog** item (voucher, merchandise, fasilitas internal).  
- **Proses settlement** (siapa yang memotong stok, siapa yang mengganti biaya).  
- **Anti‑fraud** (cek duplikasi/timing). **Refund** bila gagal.

### 4.4 Admin & Reporting
- **Role matrix**, approval flow, ekspor CSV, dan **audit trail**.  
- **Anomaly detection** (mis. lonjakan transfer di jam tidak lazim).

### 4.5 Integrasi Mobile
- Komponen UI sederhana: daftar Reward, form transfer, katalog redeem, riwayat transaksi.  
- **Error state** yang jelas (kuota habis, jaringan offline, dsb.).  
- **Offline handling** (antrian, retry).

---

## 5) Non‑Functional Requirements (NFR) — Bahasa Sederhana
- **Security:** Standar praktik aman aplikasi web (contoh panduan OWASP ASVS), manajemen kunci, rotasi rahasia.  
- **Performance:** Target respons cepat (p95 < 2 detik), dan proses transaksi selesai < 5 detik.  
- **Availability:** Target ketersediaan ≥ 99,5%; jika ada gangguan, layanan **degrade gracefully**.  
- **Compliance/Audit:** Logging, retensi data, jejak perubahan terkelola.  
- **Observability:** Metrik + log + alert yang ditindaklanjuti tim on‑call.

---

## 6) Deliverables (Apa yang PERURI terima)
1) **Blockchain core & Smart Contracts** (source code, test, skrip deploy).  
2) **API service** (containerized) + **OpenAPI docs**.  
3) **Admin dashboards** (issuer/treasury/reports).  
4) **Dokumentasi lengkap:** BRD, FSD, Arsitektur, Runbook, UAT, User/Admin Manual.  
5) **Pelatihan & KT** (bahan + rekaman bila diizinkan).  
6) **Laporan bulanan**, **Final report**, **Masa garansi & support** sesuai SLA.

---

## 7) Organisasi Proyek & Peran
- **Project Manager** — timeline, risiko, koordinasi stakeholder.  
- **Blockchain Architect** — desain jaringan, keamanan, tata kelola.  
- **Smart Contract Developer** — pengembangan Solidity + review/audit.  
- **Backend/API Developer** — service, integrasi, monitoring.  
- **QA (Fungsional)** — rencana uji, otomasi, UAT.  
- **QA/Security** — pen‑test, SAST/DAST, hardening.  
- **DevOps** — CI/CD, IaC, environment.  
- **UI/UX** — desain dashboard & alur mobile.

> Lengkapi dengan nama personil, ringkas CV, dan alokasi FTE per fase.

---

## 8) Timeline (Contoh)
- **Phase 0 — Discovery (2–3 minggu):** BRD/FSD, persetujuan desain.  
- **Phase 1 — Build (6–8 minggu):** chain + contracts + API + dashboards.  
- **Phase 2 — UAT (2 minggu):** skenario uji, perbaikan, persetujuan.  
- **Phase 3 — Launch (1 minggu):** produksi + **Hypercare** (4 minggu).

> Gunakan tanggal absolut agar sinkron dengan **change window** TI PERURI.

---

## 9) Budget (BOQ Skeleton)

### A. Implementation (Man‑Months)
| Role | Qty | Durasi | Rate | Subtotal |
|---|---:|---:|---:|---:|
| Project Manager | {{Q_PM}} | {{D_PM}} | {{R_PM}} | {{S_PM}} |
| Blockchain Architect | {{Q_ARCH}} | {{D_ARCH}} | {{R_ARCH}} | {{S_ARCH}} |
| Smart Contract Dev | {{Q_SC}} | {{D_SC}} | {{R_SC}} | {{S_SC}} |
| Backend/API Dev | {{Q_BE}} | {{D_BE}} | {{R_BE}} | {{S_BE}} |
| QA (Func) | {{Q_QA}} | {{D_QA}} | {{R_QA}} | {{S_QA}} |
| QA (Sec) | {{Q_SEC}} | {{D_SEC}} | {{R_SEC}} | {{S_SEC}} |
| DevOps | {{Q_DEVOPS}} | {{D_DEVOPS}} | {{R_DEVOPS}} | {{S_DEVOPS}} |

### B. Validator/Node (Tahunan/Periode Proyek)
| Item | Spec | Qty | Term | Rate | Subtotal |
|---|---|---:|---:|---:|---:|
| Validator Node VM | 4 vCPU / 8GB / 200GB SSD | {{Q_VAL}} | {{TERM}} | {{RATE_VAL}} | {{SUB_VAL}} |
| Tx Node VM | 4 vCPU / 8GB / 200GB SSD | {{Q_TX}} | {{TERM}} | {{RATE_TX}} | {{SUB_TX}} |
| BAS/Indexer | 4 vCPU / 8GB / 200GB SSD | {{Q_BAS}} | {{TERM}} | {{RATE_BAS}} | {{SUB_BAS}} |

### C. Dokumentasi & Pelatihan
| Item | Qty | Subtotal |
|---|---:|---:|
| BRD, FSD, Dev Plan | 1 | {{SUB_DOC}} |
| Source + Config Packages | 1 | {{SUB_SRC}} |
| UAT Docs & Sessions | 1 | {{SUB_UAT}} |
| User/Admin Manuals | 1 | {{SUB_MAN}} |
| Monthly & Final Report | 1 | {{SUB_REP}} |

---

## 10) Acceptance & Handover
- **Kriteria UAT** disepakati HR + TI; hasilnya ditandatangani.  
- **Serah terima operasional**: node, keys, runbook, dashboard monitoring.  
- **Garansi**: {{MASA_GARANSI}} dengan SLA/respon time terdefinisi.

---

## 11) Risiko & Mitigasi (Contoh)
- **Penyalahgunaan kuota** → batas harian/mingguan + alert anomali + audit rutin.  
- **Kompromi kunci** → kebijakan HSM/penyimpanan aman, rotasi, multisig, prinsip least‑privilege.  
- **Drift integrasi** → contract test, API versioning, staging yang disiplin.  
- **Vendor lock‑in** → standar terbuka, serah‑terima source, **knowledge transfer**.

---

## 12) Glosarium (Untuk Pembaca Non‑Teknis)
- **Blockchain:** Buku besar digital (ledger) yang mencatat transaksi secara berurutan dan sulit diubah.  
- **Permissioned Network:** Jaringan privat; hanya pihak yang diizinkan yang dapat menjadi **validator**.  
- **Validator:** Server yang memvalidasi dan menyetujui blok transaksi.  
- **IBFT 2.0:** Mekanisme kesepakatan (consensus) berbasis otoritas; blok yang disetujui bersifat final (tidak fork).  
- **Reward Token:** Satuan poin digital untuk sistem penghargaan (bukan koin untuk trading).  
- **API:** Antarmuka untuk aplikasi saling berkomunikasi (mis. mobile app ↔ backend ↔ blockchain).  
- **OAuth 2.0 / JWT:** Mekanisme otorisasi & format token akses untuk memastikan hanya pengguna yang berhak yang bisa memakai API.  
- **OpenAPI:** Cara standar menulis dokumentasi API yang bisa dibaca manusia & mesin.  
- **Prometheus/Grafana:** Alat untuk mengumpulkan metrik dan menampilkan dashboard monitoring.

---

## 13) Referensi Resmi (Official Links)
- **Hyperledger Besu (Docs/Official):** https://besu.hyperledger.org/  
  - Private/Permissioned Networks: https://besu.hyperledger.org/private-networks  
  - Start node & system requirements: https://besu.hyperledger.org/private-networks/get-started/start-node
- **OpenAPI Initiative:** https://www.openapis.org/  
- **OAuth 2.0 (official community site):** https://oauth.net/2/  
- **JWT — RFC 7519 (IETF):** https://datatracker.ietf.org/doc/html/rfc7519  
- **Node.js:** https://nodejs.org/  
- **TypeScript:** https://www.typescriptlang.org/  
- **Prometheus:** https://prometheus.io/  
- **Grafana:** https://grafana.com/

---

### Lampiran A — Skema Kontrak (Garis Besar, Bahasa Umum)
- **RewardToken.sol**  
  - Menyimpan saldo Reward per karyawan.  
  - Event: `Issued`, `Transferred`, `Redeemed`, `Burned`.
- **Treasury.sol**  
  - Tempat mint/burn resmi; kontrol oleh Admin/Issuer sesuai kuota.  
- **Redemption.sol**  
  - Menyimpan katalog dan memotong saldo saat redeem; event `RedeemRequested`, `RedeemSettled`/`Refunded`.
- **PolicyRegistry.sol**  
  - Menyimpan aturan kuota/cooldown/role; bisa diperbarui lewat approval.

> Catatan: Implementasi teknis (Solidity, test, gas policy) akan dilampirkan di repositori teknis saat Development Phase.

---

### Lampiran B — Contoh Alur 1 Menit
1. **Login** ke mobile app via **Peruri Connect**.  
2. Buka **Transfer Reward**, pilih rekan kerja, masukkan jumlah (mis. 5 poin).  
3. Sistem cek **kuota** & **cooldown** → jika OK, transaksi dibuat.  
4. Backend mengirim transaksi ke **Blockchain (Besu)** → **finality** < 5 detik.  
5. Penerima melihat saldo bertambah; event muncul di **Riwayat** & **Dashboard**.

