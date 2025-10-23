---
description: >-
  We don't belong in your reality, your real life. In your reality, your real
  life, you can merely meet our avatars in any version. So, stay alert and
  beware of scams!
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# International Payments & Escrow — Web2 → Web3 Pragmatics

## -1) Pendahuluan

- Judul: **International Payments & Escrow — Web2 → Web3 Pragmatics**  
- Ruang-Waktu: **Universitas Kristen Petra** · **Kamis, 23 Okt 2025** · **10.30–13.00** · **AVT501**  
- Artefak: *Tanpa rekaman • Tanpa distribusi • ±90 mahasiswa*

<figure><img src="https://github.com/user-attachments/assets/37aff88e-09ff-4fb1-971f-fb6b21e18e6d" alt="Ilustrasi 1 oleh Prof. NOTA Inc. - International Payments dan Escrow"><figcaption><p>International Payments dan Escrow</p></figcaption></figure>

- Pendahuluan:  
  Di banyak proyek lintas negara, biaya dan waktu kirim dana kerap menjadi “bottleneck”. Blockchain—khususnya **stablecoin (mis. USDC)**—membuka opsi rails yang **lebih cepat, lebih transparan, dan dapat diprogram**. Sesi ini memetakan **opsi pembayaran internasional**, membedah **escrow tradisional vs smart-contract**, menyentuh **kepatuhan (KYC/AML & pajak)**, dan merancang **arsitektur minimal** dari **Web2 → Web3** agar audiens punya peta jalan yang **pragmatis, aman, dan bisa dieksekusi**.

> [!NOTE]
> 
> - Bagaimana mengirim uang lintas negara dengan murah & cepat?
> - Kapan escrow perlu jadi *kode* yang mengeksekusi aturan, bukan sekadar perjanjian?

---

## 0) Struktur Materi

<figure><img src="https://github.com/user-attachments/assets/2092ea40-018d-4012-943f-362a818d5410" alt="Ilustrasi 1 oleh Prof. NOTA Inc. - Struktur Materi"><figcaption><p>Struktur Materi</p></figcaption></figure>

1. **Peta Global Payment Rails:** bank/fintech vs **stablecoin** (USDC)
2. **Escrow:** tradisional vs **smart-contract** (milestone, release, dispute)
3. **Compliance & Record-Keeping:** KYC/AML, faktur, pajak dasar
4. **Arsitektur Praktis (Minimal):** Web2 app ↔ on/off-ramp ↔ wallet ↔ escrow ↔ records
5. **Mini-Demo Aman + Panduan Q&A**
6. **Next Steps / CTA:** Workshop 3 jam, Capstone Clinic, research/internship

- Speech:
  Hari ini kita fokus ke cara kirim-mengirim lintas negara lebih cepat, transparan, dan programmable. Kita bandingkan bank/fintech rails vs stablecoin rails, lalu kapan escrow dibutuhkan, sedikit compliance, dan arsitektur minimal supaya bisa langsung dipraktikkan.

---

## 1) Peta Global Payment Rails — Bank/Fintech vs Stablecoin

<figure><img src="https://github.com/user-attachments/assets/74094c31-6301-4a3b-ad5d-9463d4947d1c" alt="Ilustrasi 1 oleh Prof. NOTA Inc. - Peta Global Payment Rails — Bank/Fintech vs Stablecoin"><figcaption><p>Peta Global Payment Rails — Bank/Fintech vs Stablecoin</p></figcaption></figure>

- **Bank/Fintech Rails**
  * Kelebihan: infrastruktur mapan, reputasi kuat, dukungan regulasi lokal.
  * Kekurangan: **FX spread & biaya** lebih tinggi, **jam kantor**, potensi **chargebacks**.
  * Cocok untuk: transaksi institusi yang butuh *paper trail* konvensional & kepastian dari jaringan perbankan.

- **Stablecoin Rails (mis. USDC)**
  * Kelebihan: **settlement cepat**, biaya jaringan rendah, **programmable** (bisa diotomasi).
  * Kekurangan: perlu **on/off-ramp** patuh **KYC**; pengelolaan wallet & private key.
  * Cocok untuk: payout lintas negara, escrow terotomasi, eksperimen produk.

- **Hal Teknis yang Harus Diwaspadai**
  * Biaya total = biaya **network** + biaya **penyedia layanan** (on/off-ramp).
  * **Kinerja & latency** jaringan; pemilihan chain (fee, finality).
  * **Yurisdiksi & kebijakan kampus/perusahaan** terkait aset digital.

- Speech:
  Bank rails cocok saat butuh paper trail konvensional. Stablecoin cocok untuk kecepatan dan otomasi. Namun harus dihitung total biaya: bukan hanya gas, tapi juga on/off-ramp. Perhatikan juga finality—berapa cepat transaksi benar-benar dianggap selesai.
  
---

## 2) Escrow — Traditional vs Smart-Contract

<figure><img src="https://github.com/user-attachments/assets/23954453-5472-473d-baca-84de9850c0cd" alt="Ilustrasi 1 oleh Prof. NOTA Inc. - Escrow — Traditional vs Smart-Contract"><figcaption><p>Escrow — Traditional vs Smart-Contract</p></figcaption></figure>

- **Escrow Tradisional**
  * Pihak ketiga dipercaya menahan dana, melepas saat **syarat** dipenuhi.
  * Pro: familiar, sesuai kebiasaan legal; kontra: **biaya** & **waktu** proses.

- **Smart-Contract Escrow**
  * **Aturan → kode**: milestone, **time-lock**, kondisi rilis, **dispute path** ditulis sebagai *program*.
  * Pro: otomatis & transparan; kontra: butuh **audit/care** (bug/UX/kunci).
  * Gunakan smart-contract saat: alur **berulang**, jelas & bisa diprogram; perlu **otomasi** & **jejak transparan**.

- **Keputusan Praktis (Matrix Ringkas)**
  * **Sederhana & low risk?** Mulai tradisional.
  * **Berulang & *rules-based*?** Pertimbangkan smart-contract.
  * **Ada sengketa kompleks?** Siapkan **dispute path** hibrida (kode + arbitrase manusia).

- Speech:
  Escrow itu penjaga dana sementara. Kalau kebutuhannya sekali-pakai dan butuh negosiasi manusia, tradisional sering cukup. Kalau berulang dan syaratnya jelas, smart-contract memberi otomasi dan jejak transparan.

---

## 3) Compliance & Record-Keeping (Student/Startup)

<figure><img src="https://github.com/user-attachments/assets/0d20787e-d02e-40f7-8217-7ac8546cb263" alt="Ilustrasi 1 oleh Prof. NOTA Inc. - Compliance & Record-Keeping (Student/Startup)"><figcaption><p>Compliance & Record-Keeping (Student/Startup)</p></figcaption></figure>

* **KYC/AML** di on/off-ramp; **kenali batasan** akun & wilayah.
* **Dokumentasi**: invoice, tanda terima, *export* ledger → **akuntansi**.
* **Pajak dasar** lintas negara: catat nilai tukar & tanggal, hindari “*mixed wallets*” untuk proyek berbeda.
* **Privasi & minimasi data**: simpan yang perlu, hindari menyebar PII.

- Speech:
  Yang bikin tenang adalah catatan rapi. Simpan data minimal yang perlu. Pisahkan wallet per proyek agar audit mudah. Di on/off-ramp, KYC/AML itu wajib—ini relnya regulasi.

---

## 4) Arsitektur Praktis (Minimal)

<figure><img src="https://github.com/user-attachments/assets/f5fb8fff-9c4a-4857-a16a-4458b253c556" alt="Ilustrasi 1 oleh Prof. NOTA Inc. - Arsitektur Praktis (Minimal)"><figcaption><p>Arsitektur Praktis (Minimal)</p></figcaption></figure>

```

Web2 App / Admin
  - User auth, order info, invoices

Payments Layer
  - On/Off-ramp provider (KYC)
  - Stablecoin wallet (custodial / non-custodial)

Escrow Contract
  - Milestones, release logic, dispute path, time-locks

Records
  - Ledger, invoices, export to accounting
```

> [!NOTE]
> 
> **Catatan desain**
> * **Custodial vs non-custodial**: pertimbangkan UX & kepatuhan.
> * **Segregasi dana/proyek**: kurangi risiko pencampuran.
> * **Observability**: log transaksi, biaya, & waktu tempuh; siapkan laporan periodik.

- Speech:
  Ini peta minimal. Aplikasi Web2 mengelola user & order. Payments layer menghubungkan fiat-kripto melalui on/off-ramp dan wallet. Kalau perlu, escrow contract mengatur aturan rilis. Semua transaksi akhirnya masuk ke Records untuk akuntansi.

---

## 5) Aktivitas Bersama (Role-Play) + Q&A Terstruktur

<figure><img src="https://github.com/user-attachments/assets/392b6e96-3895-4967-8c39-693b909a4aef" alt="Ilustrasi 1 oleh Prof. NOTA Inc. - Aktivitas Bersama (Role-Play) + Q&A Terstruktur"><figcaption><p>Aktivitas Bersama (Role-Play) + Q&A Terstruktur</p></figcaption></figure>

> [!TIP]
> 
> **Catatan:**
> - Detail instruksi untuk masing-masing role-play berada pada dokumen terpisah, [International Payments & Escrow Role-Play](../../../archived-oioi/2025/10/international-payments-escrow-roleplay.md)
> - Bagian ini hanya menyiapkan kerangka, tujuan, dan batasan diskusi agar selaras dengan **Output Materi**.

- **Susunan singkat & tujuan**
  * **Role-Play 1 — International Transfers (tanpa escrow)**
    - Fokus: membandingkan **bank/fintech rails (privat)** vs **blockchain/stablecoin rails (publik)** dari sisi **latensi, transparansi, langkah proses, dan biaya**.
  * **Role-Play 2 — Escrow untuk transaksi/jual-beli**
    - Fokus: kapan perlu **escrow**, perbedaan **trusted intermediary** vs **rules-as-code**, konsep **kondisi rilis** dan **jalur sengketa** (tanpa implementasi teknis).

- **Alokasi waktu saran**:
  * RP1 **20–25’** 
  * RP2 **20–25’** 
  * Debrief+Q&A **10–15’**

- **Guardrails umum**:
  * tanpa rekaman; 
  * tidak ada kunci/PII; 
  * tidak ada transaksi live; 
  * contoh biaya/fee bersifat ilustratif; 
  * patuh kebijakan kampus.

- **Ekspektasi keluaran segmen ini**
  * Peserta bisa menjelaskan trade-off **privat vs publik** (siapa tahu apa), **latensi**, dan **biaya/overhead** pada jalur transfer lintas negara.
  * Peserta memahami **kapan escrow diperlukan**, apa itu **kondisi rilis** dan **dispute path** tingkat konsep, serta kapan memilih **tradisional** vs **smart-contract**.
  * Hasil ini menguatkan **Output Materi** (bagian 7) tentang pemilihan rails, pemahaman escrow, dan sketsa arsitektur minimal.

- **Q&A terstruktur (dibatasi per role-play)**
  * **Setelah RP1 (Transfer):**
    - Ruang tanya: perbandingan langkah/hop, sumber biaya (implisit vs terbuka), finality/konfirmasi, peran on/off-ramp & KYC dasar.
    - Di luar ruang tanya: spekulasi harga koin, rekomendasi investasi, detail teknis chain tertentu yang tidak relevan dengan tujuan belajar.
  * **Setelah RP2 (Escrow):**
    - Ruang tanya: kriteria butuh escrow, contoh kondisi rilis/milestone, peran manusia dalam sengketa, risiko UX & operasional.
    - Di luar ruang tanya: kode/audit smart-contract, konsultasi legal khusus, implementasi produk riil di luar konteks kelas.
  * **Penutup Q&A:** rekap poin pembelajaran → arahkan ke **Next Steps/CTA** (workshop 3 jam, capstone clinic, research/internship) dan form minat.

- Speech:
  * Kalau kalian mau lanjutan praktik, sampaikan ke panitia/dosen—kita bisa jadwalkan Workshop 3 jam atau Capstone Clinic. Yang minat riset, sebutkan ke saya setelah sesi.
  * Pertanyaan diarahkan ke teknis-pragmatis sesuai tujuan belajar. Untuk pendalaman, kita siapkan workshop dan clinic. Silakan sampaikan minat ke panitia setelah sesi.

---

## 6) Next Steps (Untuk Mahasiswa & Kampus)

<figure><img src="https://github.com/user-attachments/assets/32302916-20c8-482e-b7f4-ce1e8d8434b1" alt="Ilustrasi 1 oleh Prof. NOTA Inc. - Next Steps (Untuk Mahasiswa & Kampus)"><figcaption><p>Next Steps (Untuk Mahasiswa & Kampus)</p></figcaption></figure>

* **Workshop 3 jam (diskon kampus)** — latihan **alur pembayaran global + escrow (USDC)** dari nol → siap produksi sederhana.
* **Capstone Clinic (6 tim, 2×60’)**
* **Research internship (selektif)** — rails & escrow.

<img width="1536" height="1024" alt="qr-code-1" src="https://github.com/user-attachments/assets/6aedfbd1-5f2e-4500-95b0-f5f2441ebb07" />

> [!NOTE]
> 
> **What to do:**  
> silahkan scan **QR Code** (link ke formulir pendaftaran minat); **khusus mahasiswa** tersedia (kuota terbatas, 30 hari).

---

## 7) Output Materi (Ujian Peserta)

<figure><img src="https://github.com/user-attachments/assets/cc9945f6-8b1e-4579-a919-d55a6dbc6ced" alt="Ilustrasi 1 oleh Prof. NOTA Inc. - Output Materi (Ujian Peserta)"><figcaption><p>Output Materi (Ujian Peserta)</p></figcaption></figure>

* Peserta mampu menyebutkan **opsi rails** beserta implikasi biaya/waktu.
* Peserta memahami **escrow tradisional vs smart-contract** dan kapan memilihnya.
* Peserta tahu **kebutuhan compliance** minimal dan pola dokumentasi.
* Peserta dapat membuat **sketsa arsitektur minimal** Web2 → Web3.
* Peserta tahu **langkah lanjut** (workshop/klinik/internship) dan kanal informasi.

> [!NOTE]
> 
> **What to do:**  
> silahkan scan **QR Code** (link ke soal uji coba); jawab dan selesaikan semampunya saja.

---

## 8) Lampiran: Handout Singkat (Ringkasan)

<figure><img src="https://github.com/user-attachments/assets/5da6cff5-efd2-4252-8de6-a48b998fe8eb" alt="Ilustrasi 1 oleh Prof. NOTA Inc. - Lampiran: Handout Singkat (Ringkasan)"><figcaption><p>Lampiran: Handout Singkat (Ringkasan)</p></figcaption></figure>

* **What You’ll Learn**: peta opsi pembayaran, escrow, compliance, arsitektur minimal, next steps.  
* **Quick Comparison**: Bank/Fintech (mapan/overhead) vs Stablecoin (cepat/programmable).  
* **Pragmatic Escrow**: pilih tradisional untuk sederhana; pilih smart-contract untuk otomatisasi & milestone.  
* **Next Steps**: Workshop 3 jam · Capstone Clinic · Research internship.  
* **Kontak**: Prof. NOTA — (isi handle/WA/Email)

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
