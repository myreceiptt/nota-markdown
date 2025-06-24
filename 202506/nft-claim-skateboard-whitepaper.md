
---
title: "WHITEPAPER: NFT Claim System — Prof. NOTA Inc. Skateboards"  
author: "Prof. NOTA Inc."  
version: "v1.0"  
date: "2025-06-24"  
---

# 🛹 Prof. NOTA Inc. — NFT Claim System for Returned Skateboards

## 🎯 TUJUAN UTAMA

Menghadirkan sistem NFT berbasis Web3 yang **menghargai pengguna** skateboard Prof. NOTA Inc. yang telah **mengembalikan produk rusak atau tidak terpakai**. NFT tidak diberikan saat pembelian, melainkan saat pengguna **mengembalikan** skateboard bekas kepada Prof. NOTA Inc., sebagai bentuk:

- Kepedulian lingkungan
- Pelestarian sejarah pemakaian
- Kontribusi komunitas

---

## 🧠 KONSEP DASAR

- NFT **bukan** bukti pembelian, tetapi **bukti pengembalian sadar**.
- Setiap **design skateboard** memiliki satu token ID NFT.
- NFT diberikan setelah **deck fisik diterima** oleh Prof. NOTA Inc.
- Deck yang dikembalikan akan didokumentasikan, dipamerkan, atau digunakan kembali untuk proyek keberlanjutan.

---

## 💡 SKENARIO SINGKAT

1. Siapapun boleh membeli skateboard deck Prof. NOTA Inc. dari manapun.
2. Jika deck rusak/tidak terpakai → jangan dibuang.
3. Pemilik mengakses situs: `https://notaskateboards.com/retur`
4. Isi form dan upload foto → sistem verifikasi manual
5. Jika valid → pemilik mengirimkan deck ke alamat yang ditentukan
6. Setelah diterima → NFT dikirim ke wallet pemilik

---

## 📦 ARSITEKTUR SISTEM

### 1. Frontend: Web Form Pengguna
- **URL**: `/retur`
- Dibangun dengan: `Next.js 15` + `Tailwind CSS`
- Form input:
  - Nama lengkap
  - Email
  - Alamat Wallet (atau tombol Connect Wallet)
  - Upload foto skateboard rusak
  - Pilih desain (dropdown / upload bukti pembelian opsional)
  - Checklist: “Saya akan mengirim skateboard ini ke alamat Prof. NOTA Inc.”

### 2. Backend: Sistem Verifikasi & Minting NFT
- Dibangun dengan: `Node.js / Express`
- Database: `MongoDB`
- Fitur utama:
  - Verifikasi manual submission (dashboard internal)
  - Tandai status (valid / ditolak / pending)
  - Endpoint minting NFT dengan ThirdWeb SDK `claimWithSignature` atau `mintTo`

### 3. Smart Contract NFT
- Standar: **ERC-1155** (tiap desain = token ID)
- Diterapkan dengan ThirdWeb Signature Drop
- Metadata NFT:
  ```json
  {
    "name": "Returned Deck — Phoenix Flame",
    "description": "You've sent back a used Prof. NOTA Inc. skateboard. This NFT is proof of your journey.",
    "image": "ipfs://...",
    "attributes": [
      { "trait_type": "Design", "value": "Phoenix Flame" },
      { "trait_type": "Claim Date", "value": "2025-06-24" },
      { "trait_type": "Condition", "value": "Used" },
      { "trait_type": "Return Verified", "value": true }
    ]
  }
  ```

---

## 🔐 STRATEGI ANTI-PENYALAHGUNAAN

| Risiko                                      | Solusi Teknis dan Operasional                                      |
|--------------------------------------------|---------------------------------------------------------------------|
| Klaim palsu (tidak benar-benar punya deck) | Upload foto, verifikasi manual oleh tim Prof. NOTA                 |
| Orang minta NFT tanpa mengirim fisik       | NFT hanya dikirim setelah barang diterima dan diperiksa            |
| Spam submission                            | Rate limiting, CAPTCHA, validasi email                             |
| Klaim ganda                                | Batasi satu NFT per wallet per design / serial / bukti unik        |
| Deck tiruan                                | Validasi visual, optional QR/sticker atau nomor produksi internal  |

---

## 🛠️ FILE STRUKTUR PROYEK

```plaintext
src/
├── app/
│   └── retur/
│       └── page.tsx               # Halaman form pengguna
├── components/
│   ├── ReturForm.tsx              # Komponen form utama
│   └── ReturStatus.tsx            # Status tracking
├── lib/
│   └── mintNFT.ts                 # Logika backend mint NFT
├── pages/api/
│   └── retur.ts                   # Handler API form submission
│   └── verify.ts                  # Endpoint admin approval
```

---

## 💌 ALUR LOGISTIK DAN OPERASIONAL

1. Pengguna isi form dan upload foto deck rusak.
2. Sistem mencatat submission dan status = “pending”.
3. Tim Prof. NOTA melakukan verifikasi manual.
4. Jika valid:
   - Email/WhatsApp instruksi pengiriman fisik.
   - Setelah deck diterima → status updated → NFT dikirim.
5. Jika tidak valid → user diberi alasan penolakan.

---

## 🔧 STACK TEKNOLOGI YANG DIGUNAKAN

| Komponen             | Teknologi                        |
|----------------------|----------------------------------|
| Frontend             | Next.js 15 + Tailwind CSS        |
| Wallet Integration   | ThirdWeb Connect (email opsional)|
| Backend              | Node.js + MongoDB                |
| NFT Contract         | ERC-1155 via ThirdWeb SDK v5     |
| Hosting              | Vercel                           |
| API Gateway (opsional)| Express / Next.js API route     |

---

## 🎁 UTILITY DAN VISI NFT

NFT yang didapat oleh pengirim deck bekas **bukan hanya simbol**, tapi juga bisa memiliki utility tambahan:

- Akses diskon pembelian deck generasi berikutnya
- Undangan pameran atau event komunitas
- Koleksi unik yang akan dimuseumkan secara digital
- Voting desain edisi terbatas
- NFT sebagai akses token untuk fitur eksklusif (Discord / event)

---

## 📣 PESAN KEPADA PENGGUNA

> “Jangan dibuang. Kirimkan saja kembali.  
> Kami akan abadikan jejakmu di blockchain.”  
>
> – Prof. NOTA Inc. Skateboards, 2025

---

## ✅ TAHAP IMPLEMENTASI

Checklist pengerjaan tahap awal:

- [ ] Bangun halaman form `/retur`
- [ ] Siapkan backend API form submission
- [ ] Buat dashboard admin untuk approval
- [ ] Siapkan smart contract ERC-1155 untuk tiap desain
- [ ] Uji coba pengembalian 10 deck pertama (pilot)
- [ ] Integrasi minting NFT saat pengembalian diverifikasi

---

## 📬 KONTAK DAN TANGGUNG JAWAB

- **Inisiator**: Prof. NOTA (v11)
- **Operasional Teknis**: Tim Web3 Prof. NOTA Inc.
- **Kontak**: [nota@endhonesa.com](mailto:nota@endhonesa.com)
- **Versi Dokumen**: `v1.0`
- **Tanggal Rilis**: `2025-06-24`

---
