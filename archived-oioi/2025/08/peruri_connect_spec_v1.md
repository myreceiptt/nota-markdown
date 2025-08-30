---
description: >-
  We don't belong in your reality, your real life. In your reality, your real
  life, you can merely meet our avatars in any version. So, stay alert and
  beware of scams!
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# Spec Eksekusi v1 — Peruri Connect × Blockchain

## 1. Topologi Infrastruktur
- **Blockchain**: Hyperledger Besu, konsensus IBFT2, 3 validator (Peruri, PDS, Voyage/Prof. NOTA).  
- **Tx Node**: 2 node.  
- **Mirror Worker + BAS**: service Node.js/TS.  
- **Monitoring**: Prometheus + Grafana.  

### VM Sizing (2000 user)
- Validator: 4 vCPU, 8 GB RAM, 200 GB SSD.  
- Tx Node: 4 vCPU, 8 GB RAM, 200 GB SSD.  
- BAS + Mirror: 4 vCPU, 8 GB RAM.  

---

## 2. Endpoint CI3 / Flutter
- `GET /wallet/status` → `{ walletAddress, type, ready }`  
- `POST /activity/track` → `{ type, payload }`  
- `GET /activity/:id` → status + txHash  

---

## 3. ABI & Policy Rules
- **PeruriToken.sol (ERC20)**: mint/burn by BAS.  
- **PeruriBadge.sol (ERC1155)**: SBT‑like, non‑transferable.  
- **PeruriLog.sol**: simpan merkleroot batch log.  

Policy:
- Attendance → PTKN + monthly badge.  
- Training completion → badge + PTKN bonus.  
- Milestone → badge + log.  

---

## 4. SOP Keamanan
- Kunci privat di KMS/HSM, tidak pernah plaintext.  
- Role‑based access; semua call via mTLS.  
- PII tetap off‑chain; on‑chain hanya hash.  
- Audit log untuk semua call ke BAS.  

---

## 5. Runbook Pilot (2000 User)
1. Deploy 3 validator + 2 tx node.  
2. Setup BAS + Mirror Worker.  
3. Tambah endpoint CI3.  
4. Deploy kontrak PTKN, PBADGE, PLOG.  
5. Enroll user_id → wallet mapping.  
6. Jalankan pilot attendance → token issuance.  
7. Monitoring metrik:  
   - TX success rate > 99%  
   - Latency < 5s  
   - Token issuance sesuai policy  
8. Report hasil + iterasi ke Fase 2.  

---

## 6: Tim & SDM

| **Role**                    | **Tim**                | **Tugas Utama** |
|------------------------------|------------------------|-----------------|
| Flutter Developer            | Peruri Connect         | Integrasi UI/UX untuk wallet, token, badge di mobile app |
| Backend CI3 Developer        | Peruri Connect         | Tambah endpoint (wallet status, activity track), update API & auth |
| QA/Tester (Mobile)           | Peruri Connect         | Uji integrasi end-to-end di aplikasi Flutter |
| UI/UX Designer               | Peruri Connect         | Desain tampilan wallet, token, badge sesuai identitas Peruri |
| DevOps/Infra Support         | Peruri Connect         | CI/CD mobile app & API deployment |
|------------------------------|------------------------|-----------------|
| Blockchain Protocol Engineer | PDS + Voyage           | Setup & maintain Hyperledger Besu + IBFT2, validator/tx node |
| Smart Contract Developer     | PDS + Voyage           | Buat & audit kontrak PTKN (ERC20), PBADGE (ERC1155), PLOG |
| Integration Engineer (BAS)   | PDS + Voyage           | Bangun Blockchain Adapter Service & Mirror Worker, integrasi CI3 |
| Security/Infra Engineer      | PDS + Voyage           | Setup HSM/KMS, mTLS, audit log, backup & observability |
| QA/Tester (Blockchain)       | PDS + Voyage           | Uji policy issuance (attendance→token, training→badge), simulasi failover |
|------------------------------|------------------------|-----------------|
| Solution Architect (Hybrid)  | Joint                  | Pastikan blueprint App ↔ CI3 ↔ BAS ↔ Chain berjalan |
| Product/Project Manager      | Joint                  | Jaga timeline, komunikasi lintas tim, milestone deliverables |
| Compliance & Legal Specialist| Joint                  | Review token usage & regulasi, dokumentasi untuk otoritas/BUMN |
| Training & Adoption Specialist| Joint                 | Sosialisasi ke karyawan pilot, buat panduan penggunaan wallet/badge |
|------------------------------|------------------------|-----------------|
| Data Analyst (On/Off-chain)  | Opsional (lanjut)      | Analisis pola aktivitas → insight loyalty & performance |
| 4337/AA Engineer             | Opsional (lanjut)      | Implementasi smart account, paymaster, gasless UX |
| Public Chain Integration Eng.| Opsional (lanjut)      | Anchor hash ke Base/OP/Ethereum untuk notarization publik |

Uraian peran, fungsi, dan scope kerja setiap SDM yang dibutuhkan dalam implementasi **Peruri Connect × Blockchain (Hybrid, Tokenized, Interop)**: [Uraian SDM — Peruri Connect × Blockchain](peruri_connect_sdm.md)

---

# Closing Note

## Peruri Connect × Blockchain

Di bawah cahaya semesta 0101,  
kita menulis ulang relasi antara manusia, sistem, dan jejaknya.

Peruri Connect bukan sekadar aplikasi,  
melainkan pintu menuju jaringan kepercayaan baru.  
Setiap aktivitas — hadir, belajar, bekerja —  
akan terpantul di rantai waktu,  
menjadi token, menjadi catatan,  
menjadi bukti yang tak bisa disangkal.

Kita tidak mengganti dunia lama,  
hanya menambahkan cermin kedua:  
yang tak bisa retak,  
yang tak bisa dilupakan.

Dari Flutter dan CI3,  
hingga Besu dan IBFT2,  
alur ini adalah doa digital,  
supaya langkah kecil 2000 karyawan pertama  
menjadi gema besar di ekosistem Peruri,  
dan mungkin kelak, di luar Peruri.

0101 bukan sekadar angka,  
ia semesta yang menyimpan segala doa yang berbentuk kode.  
Dan hari ini, kita telah menambah satu doa lagi.  

#OiOi #ProfNOTA #0101Universe

---
