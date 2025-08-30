---
description: >-
  We don't belong in your reality, your real life. In your reality, your real
  life, you can merely meet our avatars in any version. So, stay alert and
  beware of scams!
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# Uraian SDM — Peruri Connect × Blockchain

Dokumen ini menguraikan peran, fungsi, dan scope kerja setiap SDM yang dibutuhkan dalam implementasi **Peruri Connect × Blockchain (Hybrid, Tokenized, Interop)**.  
Setiap role diplotkan dengan bagian relevan di dokumen:  
- 📄 [**peruri_connect_plan.md**](../../../archived-oioi/2025/08/peruri_connect_plan.md) (Rencana Teknis, 2000 user)  
- 📄 [**peruri_connect_spec_v1.md**](../../../archived-oioi/2025/08/peruri_connect_spec_v1.md) (Spec Eksekusi v1).  

---

## 1. Peruri Connect Team (Mobile App)

### a. Flutter Developer  
- **Fungsi:** Menjaga dan mengembangkan aplikasi mobile Peruri Connect (Flutter).  
- **Scope Kerja:**  
  - Implementasi UI/UX untuk tab **Wallet**, **Tokens**, **Badges**.  
  - Integrasi endpoint baru (`/wallet/status`, `/activity/track`, `/activity/:id`).  
  - Sinkronisasi status activity → token/badge dari backend CI3.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Integrasi Flutter**.  
  - *Spec*: Bagian **Endpoint CI3 / Flutter**.

### b. Backend CI3 Developer  
- **Fungsi:** Mengembangkan API pada CodeIgniter 3.  
- **Scope Kerja:**  
  - Membuat endpoint wallet status, activity track, activity status.  
  - Integrasi ke **Blockchain Adapter Service (BAS)**.  
  - Middleware untuk autentikasi (JWT, mTLS).  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Integrasi CI3 (auth middleware, BAS, Mirror Worker)**.  
  - *Spec*: Bagian **Endpoint CI3 / Flutter**, **SOP Keamanan**.

### c. QA/Tester (Mobile)  
- **Fungsi:** Menjamin kualitas integrasi blockchain di aplikasi Flutter.  
- **Scope Kerja:**  
  - Uji end-to-end flow: user activity → reward token/badge.  
  - Uji error handling (gagal tx, status pending).  
  - Regression test setelah update app.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Alur Data**.  
  - *Spec*: Bagian **Runbook Pilot**.

### d. UI/UX Designer  
- **Fungsi:** Mendesain pengalaman pengguna untuk fitur blockchain di app.  
- **Scope Kerja:**  
  - Desain visual tab Wallet/Token/Badge.  
  - Pastikan branding Peruri konsisten.  
  - Membuat flow sederhana agar user tidak bingung dengan konsep “wallet”.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Integrasi Flutter (UI/UX minimal)**.  
  - *Spec*: Bagian **Endpoint CI3/Flutter**.

### e. DevOps/Infra Support (Mobile)  
- **Fungsi:** Menjaga alur CI/CD untuk app + API.  
- **Scope Kerja:**  
  - Release management Flutter app.  
  - Deploy CI3 API dengan endpoint baru.  
  - Monitoring availability backend CI3.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Arsitektur Tingkat Tinggi (Flutter + CI3)**.  
  - *Spec*: Bagian **Runbook Pilot**.

---

## 2. PDS + Voyage Team (Blockchain & Protocol)

### a. Blockchain Protocol Engineer  
- **Fungsi:** Men-setup dan mengelola private blockchain (Besu + IBFT2).  
- **Scope Kerja:**  
  - Deploy validator & tx nodes sesuai VM sizing.  
  - Konfigurasi konsensus IBFT2 (3–5 validator).  
  - Monitoring jaringan blockchain.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Private Chain — Rekomendasi & Sizing Pilot (2000 user)**.  
  - *Spec*: Bagian **Topologi Infrastruktur**, **VM Sizing**.

### b. Smart Contract Developer  
- **Fungsi:** Membuat & audit kontrak token dan badge.  
- **Scope Kerja:**  
  - Buat kontrak: PTKN (ERC20), PBADGE (ERC1155 non-transferable), PLOG (merkleroot log).  
  - Unit testing & audit kontrak.  
  - Dokumentasi ABI untuk integrasi BAS.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Tokenisasi Aktivitas (PTKN, PBADGE, PLOG)**.  
  - *Spec*: Bagian **ABI & Policy Rules**.

### c. Integration Engineer (BAS)  
- **Fungsi:** Bangun service integrasi CI3 ↔ Blockchain.  
- **Scope Kerja:**  
  - Implementasi **Blockchain Adapter Service (BAS)**.  
  - Implementasi Mirror Worker (consume activity stream).  
  - Mapping identity (user_id → wallet).  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Integrasi CI3 (BAS + Mirror Worker)**.  
  - *Spec*: Bagian **Endpoint CI3 / Flutter**, **Runbook Pilot**.

### d. Security/Infra Engineer  
- **Fungsi:** Menjaga keamanan wallet & jaringan blockchain.  
- **Scope Kerja:**  
  - Setup HSM/KMS untuk kunci privat.  
  - Implementasi mTLS antar service, audit log, RBAC.  
  - Backup & recovery node blockchain.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Keamanan & Kepatuhan**.  
  - *Spec*: Bagian **SOP Keamanan**.

### e. QA/Tester (Blockchain)  
- **Fungsi:** Menjamin integrasi kontrak & policy berjalan sesuai.  
- **Scope Kerja:**  
  - Uji minting PTKN/PBADGE sesuai rules (attendance, training).  
  - Simulasi failover validator.  
  - Monitoring latency & tx success rate.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Alur Data**, **Roadmap Pilot**.  
  - *Spec*: Bagian **Runbook Pilot**.

### f. DevOps/Cloud Infra  
- **Fungsi:** Menyediakan dan menjaga infrastruktur blockchain.  
- **Scope Kerja:**  
  - Provisioning VM (validator, tx node, BAS).  
  - Setup monitoring (Prometheus, Grafana).  
  - Incident handling & scaling infra.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **VM sizing**.  
  - *Spec*: Bagian **Topologi Infrastruktur**, **Monitoring**.

---

## 3. Tim Lintas (Joint)

### a. Solution Architect (Hybrid)  
- **Fungsi:** Menjembatani desain App ↔ CI3 ↔ BAS ↔ Chain.  
- **Scope Kerja:**  
  - Validasi blueprint teknis.  
  - Pastikan alur data dan endpoint sesuai kebutuhan.  
  - Menjadi referensi lintas tim.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Arsitektur Tingkat Tinggi + Alur Data**.  
  - *Spec*: Semua bagian, sebagai penghubung.

### b. Product/Project Manager  
- **Fungsi:** Menjaga timeline, milestone, komunikasi antar tim.  
- **Scope Kerja:**  
  - Breakdown deliverables dari roadmap (F0–F4).  
  - Mengatur sprint meeting antar tim.  
  - Laporkan progress ke stakeholder Peruri.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Roadmap**.  
  - *Spec*: Bagian **Runbook Pilot**.

### c. Compliance & Legal Specialist  
- **Fungsi:** Menjamin regulasi tokenisasi sesuai aturan.  
- **Scope Kerja:**  
  - Review token PTKN sebagai loyalty/internal token (non-speculative).  
  - Dokumentasi internal untuk Peruri & otoritas.  
  - Proyeksi keperluan regulasi bila anchor ke public chain.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Keamanan & Kepatuhan**.  
  - *Spec*: Bagian **SOP Keamanan + Policy Rules**.

### d. Training & Adoption Specialist  
- **Fungsi:** Sosialisasi dan adopsi internal karyawan.  
- **Scope Kerja:**  
  - Menyiapkan panduan penggunaan wallet di app.  
  - Pelatihan untuk 2000 user pilot.  
  - Feedback loop untuk iterasi fitur.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Integrasi Flutter (UI/UX minimal)**.  
  - *Spec*: Bagian **Runbook Pilot (step 6–8)**.

---

## 4. Opsional (Fase Lanjut)

### a. Data Analyst (On/Off-chain)  
- **Fungsi:** Analisis data aktivitas user.  
- **Scope Kerja:**  
  - Sinkronisasi off-chain DB dengan on-chain log.  
  - Visualisasi loyalty/performance metrics.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Tokenisasi Aktivitas + Roadmap F3/F4**.  

### b. 4337/AA Engineer  
- **Fungsi:** Implementasi smart account & gasless UX.  
- **Scope Kerja:**  
  - Paymaster setup untuk biaya gas nol.  
  - Session keys & policy-based spending.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Fase 4 (4337 & Gasless)**.  

### c. Public Chain Integration Engineer  
- **Fungsi:** Menghubungkan private chain ke Base/OP/Ethereum.  
- **Scope Kerja:**  
  - Implementasi anchoring hash batch.  
  - Membuat proof public untuk notarization.  
- **Plot Dokumen:**  
  - *Plan*: Bagian **Fase 3 (Interop & Anchoring)**.  

---

## ✅ Kesimpulan
Komposisi SDM yang dirinci di atas **langsung diturunkan dari dokumen plan dan spec**.  
Dengan ini, setiap role jelas posisinya, scope kerja, dan keterhubungan dengan milestone implementasi Peruri Connect × Blockchain.

---
