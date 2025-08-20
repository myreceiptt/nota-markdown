---
description: >-
  We don't belong in your reality, your real life. In your reality, your real
  life, you can merely meet our avatars in any version. So, stay alert and
  beware of scams!
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# 📋 TASK CARD TEKNIS — NFT Claim Prof. NOTA Inc. Skateboards

## 🧱 1. FRONTEND – HALAMAN FORM RETUR
**Task ID**: FE-RETUR-01  
**Judul**: Buat halaman `/retur` untuk form pengembalian skateboard  
**Deskripsi**:
- Form input: Nama, Email, Wallet Address, Foto Skateboard Rusak, Dropdown Desain, Checkbox Komitmen Kirim
- Tambahkan integrasi ThirdWeb Connect untuk wallet
- Responsive dan minimalis (tailwind-ready)

**Dikerjakan oleh**: Frontend Developer  
**Dependency**: Desain UI (jika disediakan), komponen `ReturForm.tsx`

---

## 🧩 2. FRONTEND – STATUS SUBMISSION & FEEDBACK
**Task ID**: FE-RETUR-02  
**Judul**: Tambahkan komponen feedback status  
**Deskripsi**:
- Setelah form dikirim, tampilkan status: `Pending Review`, `Approved`, atau `Rejected`
- Berikan estimasi waktu respon dan link tracking (jika ada)

**Dikerjakan oleh**: Frontend Developer  
**Dependency**: Backend endpoint `/api/retur`

---

## 🔧 3. BACKEND – FORM HANDLER API
**Task ID**: BE-RETUR-01  
**Judul**: Buat API handler untuk menyimpan submission form  
**Deskripsi**:
- Endpoint: `POST /api/retur`
- Simpan data ke MongoDB: nama, email, wallet, design, foto URL, status
- Validasi minimal: email + foto wajib

**Dikerjakan oleh**: Backend Developer  
**Dependency**: DB setup + image hosting (Cloudinary/IPFS/etc)

---

## 🔐 4. BACKEND – DASHBOARD VERIFIKASI
**Task ID**: BE-ADMIN-01  
**Judul**: Dashboard internal admin untuk approval  
**Deskripsi**:
- Menampilkan list pengajuan dengan filter status
- Tombol: Approve, Reject
- Form untuk masukkan nomor resi, catatan, dsb

**Dikerjakan oleh**: Fullstack Developer  
**Dependency**: Login/role management (optional)

---

## ✍️ 5. BACKEND – MINT NFT VIA THIRDWEB SDK
**Task ID**: BE-NFT-01  
**Judul**: Implementasi fungsi mint NFT ke wallet pengguna  
**Deskripsi**:
- Gunakan `mintTo` atau `claimWithSignature` dari ThirdWeb SDK v5
- NFT metadata: nama desain, foto deck, waktu retur
- Image dapat diambil dari yang diupload user

**Dikerjakan oleh**: Web3 Developer  
**Dependency**: Smart contract ERC-1155 sudah dideploy

---

## 🔗 6. SMART CONTRACT – DEPLOY ERC-1155 UNTUK SETIAP DESAIN
**Task ID**: SC-DEPLOY-01  
**Judul**: Deploy smart contract NFT ERC-1155  
**Deskripsi**:
- 1 token ID per desain (misalnya: Phoenix Flame = tokenId `0`)
- Gunakan ThirdWeb dashboard untuk deploy dan setup
- Pastikan metadata standar IPFS-ready

**Dikerjakan oleh**: Smart Contract Engineer / Web3 Dev  
**Dependency**: Daftar desain yang tersedia

---

## 📁 7. NFT METADATA – TEMPLATE & UPLOAD IPFS
**Task ID**: META-IPFS-01  
**Judul**: Siapkan metadata NFT tiap desain  
**Deskripsi**:
- Buat template `.json` metadata
- Upload ke IPFS via ThirdWeb Storage atau Pinata
- Simpan link metadata per desain/token ID

**Dikerjakan oleh**: Web3 Support / Admin Teknis  
**Dependency**: Asset gambar dan nama desain

---

## 📨 8. NOTIFIKASI – EMAIL / WHATSAPP FOLLOW-UP
**Task ID**: OPS-NOTIF-01  
**Judul**: Kirim notifikasi setelah verifikasi diterima  
**Deskripsi**:
- Email atau WhatsApp berisi instruksi pengiriman fisik
- Tambahkan nomor referensi dan estimasi NFT dikirim

**Dikerjakan oleh**: Ops/Support Team  
**Dependency**: Admin approval + kontak user valid

---

## 🧪 9. TESTING – PILOT RETURN 10 DECK PERTAMA
**Task ID**: TEST-PILOT-01  
**Judul**: Uji coba pengembalian 10 deck dari komunitas  
**Deskripsi**:
- Rekrut 10 pengguna pertama
- Simulasikan seluruh alur dari form → kirim deck → mint NFT
- Catat feedback dan perbaikan UX

**Dikerjakan oleh**: Tim QA / Ops  
**Dependency**: Semua task sebelumnya selesai

---

## 📢 10. PUBLIKASI – COPYWRITING & LANDING PAGE
**Task ID**: PUB-CLAIM-01  
**Judul**: Buat copywriting dan halaman informasi untuk user umum  
**Deskripsi**:
- Narasi: “Kirim kembali, bukan buang.”
- Deskripsi langkah-langkah + FAQ
- Sertakan CTA ke form `/retur`

**Dikerjakan oleh**: Content Writer + Frontend  
**Dependency**: Final sistem siap digunakan

---

## ✅ LABEL & PRIORITAS

| Label   | Keterangan                  |
|---------|-----------------------------|
| FE      | Frontend                    |
| BE      | Backend                     |
| SC      | Smart Contract              |
| META    | Metadata NFT                |
| OPS     | Operasional & Support       |
| TEST    | Testing dan QA              |
| PUB     | Publikasi & Edukasi         |
