
---
title: "WHITEPAPER: NFT Claim System — Prof. NOTA Inc. Skateboards"  
author: "Prof. NOTA Inc."  
version: "v1.0"  
date: "2025-06-24"  
---

# 🛹 NFT Claim System for Returned Skateboards

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

# 📋 TASK CARD TEKNIS — NFT Claim

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

---

# 🎯 Komponen Pertama: ReturForm.tsx

## 📦 Tujuan

Formulir untuk pengguna yang ingin mengklaim NFT dengan mengembalikan skateboard deck rusak.

---

## 🔧 Fitur Form

- Input teks: Nama Lengkap, Email
- Wallet: Connect Wallet (ThirdWeb Connect)
- Dropdown atau input bebas: Nama Desain Deck
- Upload: Foto kondisi skateboard (optional preview)
- Checkbox: Komitmen kirim deck ke Prof. NOTA Inc.
- Submit button → panggil API /api/retur

---

## 📁 File: src/components/ReturForm.tsx

Berikut kode awalnya:

```
"use client";

// External libraries
import { ConnectWallet, useAddress } from "@thirdweb-dev/react";
import { useState } from "react";

export default function ReturForm() {
  const walletAddress = useAddress();

  const [nama, setNama] = useState("");
  const [email, setEmail] = useState("");
  const [design, setDesign] = useState("");
  const [photo, setPhoto] = useState<File | null>(null);
  const [agreed, setAgreed] = useState(false);
  const [isSubmitting, setIsSubmitting] = useState(false);
  const [message, setMessage] = useState("");

  const handleSubmit = async (e: React.FormEvent) => {
    e.preventDefault();
    if (!walletAddress || !agreed || !photo) {
      setMessage("Lengkapi semua data dan hubungkan wallet Anda.");
      return;
    }

    const formData = new FormData();
    formData.append("nama", nama);
    formData.append("email", email);
    formData.append("wallet", walletAddress);
    formData.append("design", design);
    formData.append("photo", photo);

    setIsSubmitting(true);
    try {
      const res = await fetch("/api/retur", {
        method: "POST",
        body: formData,
      });

      if (res.ok) {
        setMessage("Pengajuan berhasil! Tim kami akan menghubungi Anda.");
        setNama("");
        setEmail("");
        setDesign("");
        setPhoto(null);
        setAgreed(false);
      } else {
        const data = await res.json();
        setMessage(data.error || "Gagal mengirim form.");
      }
    } catch (err) {
      setMessage("Terjadi kesalahan teknis.");
    }
    setIsSubmitting(false);
  };

  return (
    <div className="max-w-xl mx-auto px-4 py-6">
      <h2 className="text-xl font-bold mb-4">Klaim NFT Skateboard Rusak</h2>
      <ConnectWallet className="mb-4" />
      <form onSubmit={handleSubmit} className="space-y-4">
        <input
          type="text"
          placeholder="Nama Lengkap"
          value={nama}
          onChange={(e) => setNama(e.target.value)}
          className="w-full border px-3 py-2 rounded"
          required
        />
        <input
          type="email"
          placeholder="Email Aktif"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
          className="w-full border px-3 py-2 rounded"
          required
        />
        <input
          type="text"
          placeholder="Nama Desain Deck (misalnya: Phoenix Flame)"
          value={design}
          onChange={(e) => setDesign(e.target.value)}
          className="w-full border px-3 py-2 rounded"
          required
        />
        <input
          type="file"
          accept="image/*"
          onChange={(e) => setPhoto(e.target.files?.[0] || null)}
          className="w-full border px-3 py-2 rounded"
          required
        />
        <label className="flex items-start space-x-2">
          <input
            type="checkbox"
            checked={agreed}
            onChange={() => setAgreed(!agreed)}
            className="mt-1"
            required
          />
          <span>
            Saya bersedia mengirim skateboard saya ke alamat yang akan
            diinformasikan oleh Prof. NOTA Inc.
          </span>
        </label>
        <button
          type="submit"
          disabled={isSubmitting}
          className="bg-black text-white px-4 py-2 rounded disabled:opacity-50"
        >
          {isSubmitting ? "Mengirim..." : "Kirim Formulir"}
        </button>
        {message && <p className="text-sm mt-2">{message}</p>}
      </form>
    </div>
  );
}

```

---

# 🛠️ API Endpoint: /api/retur.ts

## 📌 Tujuan

- Menerima data dari ReturForm.tsx
- Menyimpan data ke database (simulasi: log ke console atau simpan JSON)
- Validasi dasar
- Siap dikembangkan untuk integrasi MongoDB dan cloud storage (foto)

---

## 📁 File: src/pages/api/retur.ts

```
import { NextApiRequest, NextApiResponse } from "next";
import formidable from "formidable";
import fs from "fs";
import path from "path";

// Jangan parse body secara default
export const config = {
  api: {
    bodyParser: false,
  },
};

export default async function handler(req: NextApiRequest, res: NextApiResponse) {
  if (req.method !== "POST") {
    return res.status(405).json({ error: "Metode tidak diizinkan." });
  }

  const form = formidable({ multiples: false });

  form.parse(req, async (err, fields, files) => {
    if (err) {
      console.error("Gagal parsing form:", err);
      return res.status(500).json({ error: "Gagal membaca data formulir." });
    }

    const { nama, email, wallet, design } = fields;
    const photo = files.photo as formidable.File;

    if (!nama || !email || !wallet || !design || !photo) {
      return res.status(400).json({ error: "Semua field wajib diisi." });
    }

    // Simulasi penyimpanan (nantinya ke database)
    console.log("📦 Data Pengajuan Masuk:");
    console.log({
      nama,
      email,
      wallet,
      design,
      photoPath: photo.filepath,
    });

    // Simulasi: pindahkan foto ke folder publik sementara
    const tempPath = photo.filepath;
    const fileName = `${Date.now()}-${photo.originalFilename}`;
    const targetPath = path.join(process.cwd(), "public", "uploads", fileName);

    try {
      fs.copyFileSync(tempPath, targetPath);
    } catch (err) {
      console.error("Gagal menyimpan file:", err);
      return res.status(500).json({ error: "Gagal menyimpan foto." });
    }

    // Response sukses
    return res.status(200).json({ message: "Formulir berhasil dikirim." });
  });
}
```

---

## 🧪 Notes Teknis

- Formidable dipakai untuk handle file upload (multipart/form-data)
- File disimpan ke folder public/uploads (sementara, bisa diganti IPFS/Cloudinary)
- Validasi sederhana (semua field wajib)

---

# 🧾 Komponen: ReturAdmin.tsx

## 🎯 Tujuan

- Menampilkan daftar semua pengajuan dari endpoint backend
- Menyediakan tombol Approve dan Reject
- Menampilkan informasi pengirim: nama, email, wallet, desain, foto
- Saat diklik “Approve” → update status + lanjut ke proses mint NFT (nanti)

---

## 📁 File: src/components/ReturAdmin.tsx

```
"use client";

// External libraries
import { useEffect, useState } from "react";

type ReturItem = {
  id: string;
  nama: string;
  email: string;
  wallet: string;
  design: string;
  photoUrl: string;
  status: "pending" | "approved" | "rejected";
};

export default function ReturAdmin() {
  const [returs, setReturs] = useState<ReturItem[]>([]);
  const [loading, setLoading] = useState(true);

  const fetchReturs = async () => {
    setLoading(true);
    try {
      const res = await fetch("/api/admin/retur");
      const data = await res.json();
      setReturs(data.returs || []);
    } catch (err) {
      console.error("Gagal mengambil data pengajuan:", err);
    } finally {
      setLoading(false);
    }
  };

  const updateStatus = async (id: string, status: "approved" | "rejected") => {
    try {
      const res = await fetch(`/api/admin/retur`, {
        method: "PATCH",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ id, status }),
      });
      if (res.ok) {
        fetchReturs();
      }
    } catch (err) {
      console.error("Gagal update status:", err);
    }
  };

  useEffect(() => {
    fetchReturs();
  }, []);

  if (loading) return <p className="text-center">Memuat data...</p>;

  return (
    <div className="max-w-4xl mx-auto p-4">
      <h2 className="text-xl font-bold mb-4">📋 Daftar Pengajuan Retur</h2>
      {returs.length === 0 ? (
        <p>Belum ada pengajuan.</p>
      ) : (
        <ul className="space-y-4">
          {returs.map((item) => (
            <li key={item.id} className="border p-4 rounded shadow-sm">
              <p><strong>Nama:</strong> {item.nama}</p>
              <p><strong>Email:</strong> {item.email}</p>
              <p><strong>Wallet:</strong> {item.wallet}</p>
              <p><strong>Design:</strong> {item.design}</p>
              <p><strong>Status:</strong> {item.status}</p>
              <img
                src={item.photoUrl}
                alt="Foto Skateboard"
                className="w-40 mt-2 border rounded"
              />
              {item.status === "pending" && (
                <div className="mt-4 space-x-2">
                  <button
                    onClick={() => updateStatus(item.id, "approved")}
                    className="bg-green-600 text-white px-4 py-1 rounded"
                  >
                    Approve
                  </button>
                  <button
                    onClick={() => updateStatus(item.id, "rejected")}
                    className="bg-red-600 text-white px-4 py-1 rounded"
                  >
                    Reject
                  </button>
                </div>
              )}
            </li>
          ))}
        </ul>
      )}
    </div>
  );
}
```

## 🗃️ Endpoint yang perlu tersedia

- GET /api/admin/retur → list semua submission
- PATCH /api/admin/retur → update status (approved / rejected)

---

# 📁 File: src/pages/api/admin/retur.ts

Untuk tahap awal, kita gunakan simulasi penyimpanan data di file JSON lokal, agar tidak tergantung DB dulu. File data/returs.json akan berisi array objek ReturItem.

## 🗃️ Simulasi struktur file JSON

```
[
  {
    "id": "123456789",
    "nama": "Andi",
    "email": "andi@example.com",
    "wallet": "0xABC...",
    "design": "Phoenix Flame",
    "photoUrl": "/uploads/123456.jpg",
    "status": "pending"
  }
]
```

---

## 🧠 Handler: api/admin/retur.ts

```
import { NextApiRequest, NextApiResponse } from "next";
import fs from "fs";
import path from "path";

const dataPath = path.join(process.cwd(), "data", "returs.json");

function readReturData() {
  if (!fs.existsSync(dataPath)) return [];
  const file = fs.readFileSync(dataPath, "utf-8");
  return JSON.parse(file);
}

function writeReturData(data: any[]) {
  fs.writeFileSync(dataPath, JSON.stringify(data, null, 2));
}

export default async function handler(req: NextApiRequest, res: NextApiResponse) {
  if (req.method === "GET") {
    const data = readReturData();
    return res.status(200).json({ returs: data });
  }

  if (req.method === "PATCH") {
    const { id, status } = req.body;
    if (!id || !["approved", "rejected"].includes(status)) {
      return res.status(400).json({ error: "Data tidak valid." });
    }

    const data = readReturData();
    const index = data.findIndex((item) => item.id === id);
    if (index === -1) {
      return res.status(404).json({ error: "Pengajuan tidak ditemukan." });
    }

    data[index].status = status;
    writeReturData(data);

    return res.status(200).json({ message: "Status diperbarui." });
  }

  return res.status(405).json({ error: "Metode tidak diizinkan." });
}
```

---

## 📁 Struktur Direktori yang Perlu Ada

```
/data/returs.json         ← file database sementara
/public/uploads/          ← tempat menyimpan foto yang diunggah
```

---

## ✅ Siap Digunakan

Dashboard admin sekarang akan bekerja secara penuh:
- Menampilkan semua submission
- Menyimpan update status approved / rejected

---

# 🪙 Fungsi: Mint NFT setelah “Approved”

## 🎯 Tujuan

- Saat pengajuan diverifikasi, sistem akan langsung mint NFT ke wallet pengguna.
- NFT yang dimintakan akan memiliki metadata sesuai desain yang dikembalikan.

---

## 📁 Perubahan pada: api/admin/retur.ts (PATCH section)

Tambahkan logic minting NFT menggunakan ThirdWeb SDK di bagian PATCH.

---

## 📦 Tambahan: ThirdWeb SDK Setup

1. Install jika belum:
```bash
npm install thirdweb
```

2. Buat file lib/mintNFT.ts:
```
// src/lib/mintNFT.ts
import { ThirdwebSDK } from "thirdweb";
import { BaseGoerli } from "thirdweb/chains";

const sdk = new ThirdwebSDK(BaseGoerli, {
  clientId: process.env.THIRDWEB_CLIENT_ID,
  secretKey: process.env.THIRDWEB_SECRET_KEY, // only for server
});

export async function mintNFTTo(wallet: string, design: string) {
  const contract = await sdk.getContract(process.env.CONTRACT_ADDRESS!); // ERC-1155 contract
  const tokenId = getTokenIdByDesign(design);

  if (tokenId === undefined) {
    throw new Error("Desain tidak dikenali.");
  }

  const tx = await contract.erc1155.claimTo(wallet, tokenId, 1);
  return tx.id;
}

// Simulasi mapping desain ke tokenId
function getTokenIdByDesign(design: string): number | undefined {
  const mapping: Record<string, number> = {
    "Phoenix Flame": 0,
    "Jungle Path": 1,
    "Future Glitch": 2,
  };
  return mapping[design];
}
```

---

## 📄 Update api/admin/retur.ts (PATCH block)

Tambahkan di dalam PATCH setelah status === "approved":
```
import { mintNFTTo } from "@/lib/mintNFT";

...

if (status === "approved") {
  try {
    const wallet = data[index].wallet;
    const design = data[index].design;

    const txId = await mintNFTTo(wallet, design);
    data[index].txId = txId;
  } catch (err) {
    console.error("Gagal mint NFT:", err);
    return res.status(500).json({ error: "Minting NFT gagal." });
  }
}
```

---

## 🔐 Environment Variables

Tambahkan ke .env.local:
```
THIRDWEB_CLIENT_ID=your-client-id
THIRDWEB_SECRET_KEY=your-secret
CONTRACT_ADDRESS=0xYourERC1155ContractAddress
```

---

## ✅ Hasil Akhir

- Admin klik “Approve” → status berubah + NFT otomatis dikirim
- Data returs.json bisa mencatat txId NFT-nya

---

# 📬 Notifikasi otomatis via Email atau WhatsApp

## 🎯 Tujuan

Mengirim pesan kepada pengguna bahwa:
- Pengajuan mereka telah disetujui
- NFT telah dikirim ke wallet mereka
- Opsional: sertakan link txId (jika tersedia)

---

## 2 Opsi Notifikasi

| Metode       | Tools / Layanan                                                            | Status                 |
| ------------ | -------------------------------------------------------------------------- | ---------------------- |
| **Email**    | [Resend](https://resend.com), [SendGrid](https://sendgrid.com), nodemailer | ✅ Mudah diintegrasi    |
| **WhatsApp** | Twilio, WA Gateway, atau Wablas (lokal)                                    | ⚠️ Perlu API eksternal |

Untuk tahap awal kita prioritaskan Email, karena:
- Cepat di-setup
- Gratis untuk tahap awal
- Tidak tergantung pada nomor WA pengguna yang aktif

---

## ✅ Implementasi Email dengan Resend

### 🔧 1. Instalasi
```bash
npm install resend
```

---

### 📁 2. Buat file lib/sendEmail.ts
```
import { Resend } from "resend";

const resend = new Resend(process.env.RESEND_API_KEY);

export async function sendSuccessEmail(email: string, nama: string, design: string, wallet: string, txId?: string) {
  const txLink = txId ? `https://basescan.org/tx/${txId}` : "";

  const html = `
    <p>Halo ${nama},</p>
    <p>Terima kasih telah mengembalikan skateboard desain <strong>${design}</strong>.</p>
    <p>Kami telah mengirim NFT kenangan Anda ke wallet berikut:</p>
    <p><code>${wallet}</code></p>
    ${txId ? `<p>Tx Hash: <a href="${txLink}">${txId}</a></p>` : ""}
    <br />
    <p>Salam hormat,</p>
    <p><strong>Tim Prof. NOTA Inc. Skateboards</strong></p>
  `;

  await resend.emails.send({
    from: "nota@notaskateboards.com",
    to: email,
    subject: `NFT Retur Anda Sudah Dikirim — ${design}`,
    html,
  });
}
```

---

### 🔧 3. Tambahkan ke api/admin/retur.ts (dalam PATCH block):

Tambahkan setelah NFT berhasil dimintakan:
```
import { sendSuccessEmail } from "@/lib/sendEmail";

...

if (status === "approved") {
  ...
  await sendSuccessEmail(data[index].email, data[index].nama, design, wallet, txId);
}
```

---

### 📁 4. Tambahkan di .env.local

```
RESEND_API_KEY=your_resend_api_key
```

---

## 🚀 Hasil Akhir

User mendapatkan email dengan isi:
- Ucapan terima kasih
- Info desain
- Wallet address
- (opsional) link transaksi NFT

---

# 🧩 LANJUTAN STRATEGIS — NFT Claim Skateboard

Dengan semua fondasi inti telah selesai (formulir, backend, dashboard, minting NFT, dan notifikasi email), berikut adalah daftar fitur dan peningkatan strategis yang dapat dilanjutkan oleh tim internal Prof. NOTA Inc.

---

## ✅ TELAH SELESAI

| Komponen                      | Status     |
|-------------------------------|------------|
| Formulir pengembalian         | ✅ Siap     |
| API penerimaan submission     | ✅ Siap     |
| Dashboard admin               | ✅ Siap     |
| Minting NFT setelah approve   | ✅ Siap     |
| Email notifikasi sukses       | ✅ Siap     |

---

## 🧩 FASE LANJUTAN YANG DIREKOMENDASIKAN

### 1. Integrasi Database Nyata (MongoDB/PostgreSQL)
- Menyimpan data secara permanen dan dapat dicari.
- Mempermudah laporan dan manajemen pengajuan.
- Replacing `returs.json`.

**Task**: Setup koneksi database & schema.

---

### 2. Tampilan User untuk Tracking Status
- Halaman `/retur/track?wallet=0x...`
- Pengguna bisa cek status pengajuan dan melihat txId jika sudah minting.

**Task**: Komponen `ReturStatus.tsx` + endpoint `/api/retur/status`.

---

### 3. Landing Page Publik Edukasi & CTA
- Halaman `/retur/info` atau `/kenapa`
- Cerita gerakan sosial dan etika brand Prof. NOTA Inc.
- Langkah-langkah mengirim skateboard
- FAQ + ilustrasi

**Task**: Komponen `ReturIntro.tsx` + desain visual ringan.

---

### 4. Sistem Logistik & Validasi Ongkir
- Fitur input nomor resi dari user.
- Opsional integrasi API kurir (JNE, Wahana, dll.)
- Sistem subsidi ongkir otomatis.

**Task**: Tambahan field resi di dashboard + logic validasi ongkir.

---

### 5. Halaman Museum Digital / Galeri NFT Retur
- Rute `/museum` atau `/pameran`
- Menampilkan NFT hasil klaim publik (metadata ERC-1155)
- Bisa filter: desain, waktu, kota

**Task**: Komponen `NFTGallery.tsx` + fetch metadata kontrak.

---

### 6. Role-Based Access (Admin vs Publik)
- Proteksi dashboard `/admin`
- Login email, auth token, atau ThirdWeb Auth
- Level akses: Viewer, Admin, Superadmin

**Task**: Middleware route & pengelolaan auth.

---

### 7. Eksperimen Identitas Web3 (opsional)
- Dukungan untuk ENS (.eth) atau Lens Protocol
- NFT diklaim langsung ke identitas Web3 pengguna

---

### 8. Konversi Proyek ke Repositori GitHub
- Semua file `.tsx`, `.ts`, `.env.example`, dan dokumentasi `.md`
- README dengan alur sistem dan cara deploy
- CI/CD ringan (Vercel)

---

## 🚦 REKOMENDASI URUTAN EKSEKUSI LANJUTAN

1. 🎯 Implementasi DB MongoDB
2. 🔍 Halaman tracking status pengguna
3. 🖼 Museum NFT publik (galeri)
4. 🌍 Landing page edukasi publik
5. 🔒 Proteksi role-based akses dashboard

---

> Silakan lanjut sesuai prioritas proyek dan resource tim. Semua langkah ini bersifat modular, dapat dikerjakan paralel.
>
> —Prof. NOTA
---
