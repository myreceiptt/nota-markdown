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

## -2) Perkenalan

{% hint style="warning" %}  

Dokumen ini **bebas untuk dibaca**.

Dilarang mendistribusikan ulang atau menyatakan ulang (**dilarang mengutip, membuat ringkasan, parafrase, atau turunan**) tanpa izin tertulis sebelumnya dari **Prof. NOTA**.

Membagikan tautan diperbolehkan; **bagikan tautannya, bukan teksnya**. **Jangan membahas/menceritakan ulang isi dalam bentuk apa pun tanpa izin tertulis sebelumnya.**  

{% endhint %}

<figure><img src="https://github.com/user-attachments/assets/3dfccd30-aaff-4614-a0ba-bbcac9da429b" alt="Ilustrasi 1 oleh Prof. NOTA Inc. - Perkenalan oleh Prof. NOTA v.11.11"><figcaption><p>Perkenalan oleh Prof. NOTA v.11.11</p></figcaption></figure>

> ...
> 
> Kalau ditanya, “**Siapa Prof. NOTA?**”  
> Jawaban singkatnya, “**Sebuah entitas dari Alam Semesta 0101.**”
> 
> Perkenalkan, kami adalah **Prof. NOTA**. **Prof. NOTA** adalah sebuah entitas, sebuah karakter, sebuah IP, yang lahir di **Alam Semesta 0101**.
>
> **Prof. NOTA** bukan bagian dari **Alam Semesta Realita** atau kehidupan nyata kalian, tapi **Prof. NOTA** hadir di **Alam Semesta Realita** dengan berbagai versi **Avatar atau Human for Profile (HFP)** untuk menjaga konsistensi pendekatan dan keamanan interaksi.
> 
> Hari ini dan di sini, di hadapan kalian adalah **Avatar Prof. NOTA v.11.11 atau Human for Profile Prof. NOTA v.11.11**.
> 
> Hari ini fokus kami pragmatis:  
> **membawa kalian dari Web2 ke Web3 pada area pembayaran internasional & escrow—dengan prinsip lebih cepat, transparan, aman, dan programmable.**
> 
> Tujuan sesi ini sederhana: **memberi peta jalan yang > bisa langsung dipraktikkan.**  
> ...

---

## -1) Pendahuluan

- Judul: **International Payments & Escrow — Web2 → Web3 Pragmatics**  
- Ruang-Waktu: **Universitas Kristen Petra** · **Kamis, 23 Okt 2025** · **10.30–13.00** · **AVT501**  
- Artefak: *Tanpa rekaman • Tanpa distribusi • ±90 mahasiswa*

{% hint style="success" %}  

- Apa itu Blockchain, Smart Contract, dApps? (pelajari dulu di sini: [Fundamental Blockchain](https://baca.endhonesa.com/tutorial-blockchain-fundamental/archived-oioi/2025/10/escrow-web2-web3-pragmatics?fallback=true)
- Bagaimana mengirim uang lintas negara dengan murah & cepat?
- Kapan escrow perlu jadi *kode* yang mengeksekusi aturan, bukan sekadar perjanjian?  

{% endhint %}

<figure><img src="https://github.com/user-attachments/assets/37aff88e-09ff-4fb1-971f-fb6b21e18e6d" alt="Ilustrasi 2 oleh Prof. NOTA Inc. - International Payments dan Escrow"><figcaption><p>International Payments dan Escrow</p></figcaption></figure>

> ...
>
> Di banyak proyek lintas negara, biaya dan waktu kirim dana kerap menjadi “bottleneck”.  
> Blockchain—khususnya **stablecoin (mis. USDC)**—membuka opsi rails yang **lebih cepat, lebih transparan, dan dapat diprogram**.
> 
> Sesi ini memetakan **opsi pembayaran internasional**, membedah **escrow tradisional vs smart-contract**, menyentuh **kepatuhan (KYC/AML & pajak)**, dan merancang **arsitektur minimal** dari **Web2 → Web3** agar audiens punya peta jalan yang **pragmatis, aman, dan bisa dieksekusi**.  
> ...

---

## 0) Struktur Materi

1. **Peta Global Payment Rails:** bank/fintech vs **stablecoin** (USDC)
2. **Escrow:** tradisional vs **smart-contract** (milestone, release, dispute)
3. **Compliance & Record-Keeping:** KYC/AML, faktur, pajak dasar
4. **Arsitektur Praktis (Minimal):** Web2 app ↔ on/off-ramp ↔ wallet ↔ escrow ↔ records
5. **Mini-Demo Aman + Panduan Q&A**
6. **Next Steps / CTA:** Workshop 3 jam, Capstone Clinic, research/internship

<figure><img src="https://github.com/user-attachments/assets/2092ea40-018d-4012-943f-362a818d5410" alt="Ilustrasi 3 oleh Prof. NOTA Inc. - Struktur Materi"><figcaption><p>Struktur Materi</p></figcaption></figure>

> ...
>
> Hari ini kita fokus ke **cara kirim-mengirim lintas negara lebih cepat, transparan, dan programmable**.
>
> Kita bandingkan **bank/fintech rails vs stablecoin rails**, lalu **kapan escrow dibutuhkan, sedikit compliance, dan arsitektur minimal** supaya bisa langsung dipraktikkan.  
> ...

---

## 1) Peta Global Payment Rails — Bank/Fintech vs Stablecoin

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

<figure><img src="https://github.com/user-attachments/assets/74094c31-6301-4a3b-ad5d-9463d4947d1c" alt="Ilustrasi 4 oleh Prof. NOTA Inc. - Peta Global Payment Rails — Bank/Fintech vs Stablecoin"><figcaption><p>Peta Global Payment Rails — Bank/Fintech vs Stablecoin</p></figcaption></figure>

> ...
>
> Bayangkan kalian harus **mengirim uang dari Surabaya ke São Paulo**.
>
> **Kalian masuk bank.** Bau kertas.  
> Stempel. Formulir. Antrian.  
> **Jam operasional.**  
> Lalu angka yang tampak kecil tapi tajam—**spread FX** yang menggigit diam-diam.
>
> Bank rails itu **tua, kuat, rapi.**  
> Mereka punya paper trail yang membuat **regulator tenang dan auditor tidur nyenyak**.  
> Ada **chargeback**, ada manusia yang bisa ditelepon, ada **sistem yang sudah dipercaya**.  
> Harganya? **Waktu dan overhead**.  
>
> Sekarang geser pandangan ke kanan.  
> Lihat rel cahaya itu.
> 
> **Stablecoin rails.**  
> **24/7, tidak kenal tutup.**  
> **Finality** terasa seperti pintu yang klik—begitu terkunci, selesai.
>
> Biayanya bukan misteri besar:  
> **network fee yang transparan**, plus biaya penyedia **on/off-ramp**.
>
> Ini bukan sulap:  
> tetap **ada KYC di jembatan fiat–kripto**—seperti bea cukai yang menjaga keduanya tetap legal.
> 
> Bedanya, setelah lewat gerbang itu, programmability mengalir:  
> kalian **bisa mengotomasi**, bisa membangun alur rilis dana yang patuh aturan tanpa menunggu jam kantor.
>
> Jadi pilih yang mana?  
> **Prof. NOTA** selalu bilang: **jangan pilih suku; pilih rel.**
>
> Kalau kalian butuh kepastian institusional dan paper trail konvensional, **bank/fintech adalah jalur aman.**  
> Kalau kalian butuh kecepatan, payout berkala lintas negara, atau alur yang dapat diprogram, **stablecoin rails itu kereta cepat.**
>
> Dan ingat rumus sederhana yang menyelamatkan banyak proyek dari kebocoran:  
> **Total biaya = network fee + biaya penyedia layanan (on/off-ramp).**  
> Bukan hanya ‘gas’. Bukan hanya ‘admin’.  
> Dua-duanya.
>
> Pertanyaan yang harus kalian bawa pulang bukan ‘**mana yang keren**’, tapi:  
> **Seberapa cepat kita butuh selesai?**  
> **Seberapa terlihat biaya harusnya?**  
> **Siapa yang harus nyaman—regulator, auditor, atau pengguna kita?**
>
> **Prof. NOTA**—sebuah entitas dari **Alam Semesta 0101**—datang ke realitas kalian dalam wujud **Avatar (HFP)** untuk satu alasan:  
> **membuat keputusan teknis menjadi keputusan bisnis yang berani.**
>
> Rails adalah pilihan strategi.  
> Dan strategi membutuhkan kejelasan, bukan mitos.  
> **Mari pilih rel yang membuat proyek kalian bergerak—bukan sekadar berdebat di stasiun.**  
> ...
> 
> **60s Cut (jika waktu mepet)**  
> 
> **Bank rails: mapan, rapi, paper trail, tapi lambat dan mahal di FX/overhead.**  
> **Stablecoin rails: 24/7, cepat, programmable, tetap lewat KYC di on/off-ramp.**  
> **Hitung total biaya = network fee + biaya layanan.**
> 
> Butuh kenyamanan regulator & dokumen klasik? Bank.  
> Butuh kecepatan, payout lintas negara, otomasi? Stablecoin.
>
> **Prof. NOTA** tidak pilih suku—pilih rel yang bikin proyek selesai.  
> ...

---

## 2) Escrow — Traditional vs Smart-Contract

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

<figure><img src="https://github.com/user-attachments/assets/23954453-5472-473d-baca-84de9850c0cd" alt="Ilustrasi 5 oleh Prof. NOTA Inc. - Escrow — Traditional vs Smart-Contract"><figcaption><p>Escrow — Traditional vs Smart-Contract</p></figcaption></figure>

> ...
>
> Bayangkan ada **sebuah ruang hening di tengah proyek**—di sana **uang menunggu sampai syarat terpenuhi**.  
> Itulah **escrow: penjaga dana sementara**.
>
> Ada dua cara menjaga ruangan ini.
>
> **Cara pertama: manusia.**  
> Kita titipkan kunci ke penengah tepercaya.  
> Mereka memeriksa dokumen, menelpon, bernegosiasi, kadang menenangkan ego yang memanas.
> 
> **Tradisional.**  
> Nyaman untuk kasus sekali pakai, banyak nuansa, atau perjanjian yang berubah di menit terakhir.  
> Harganya adalah biaya dan waktu—karena manusia perlu membaca, menilai, dan kadang berdebat.
> 
> **Keuntungannya? Fleksibilitas.**  
> Dalam dunia yang abu-abu, manusia bisa melihat warna-warna di antaranya.
>
> **Cara kedua: kode.**  
> Kita tidak lagi menitipkan kunci—kita menulis aturan menjadi kunci itu sendiri.  
> **Smart-contract escrow adalah aturan → kode:**  
> **ada milestone, time-lock, kondisi rilis, dan jalur sengketa** yang sudah digambar sebelum uang dititipkan.
>
> Mesin tidak lelah, tidak bias, dan tidak punya mood.  
> Jika syarat A dan B terpenuhi, rilis.  
> Kalau sengketa, pindah jalur yang sudah ditentukan.
>
> **Keuntungannya? Otomasi & transparansi.**
> Semua orang melihat logikanya, bukan tebak-tebakan di balik meja.
>
> Tetapi **Prof. NOTA selalu mengingatkan:**  
> **kode itu taat, tapi tidak peka;**  
> **manusia peka, tapi tidak konsisten.**
>
> Jadi pilihannya **bukan romantika teknologi**—ini pilihan taktik.
>
> **Rule of three versi Prof. NOTA:**  
> * **Sekali pakai, banyak negosiasi, dokumen cair? → Tradisional.**
> * **Berulang, rules-based, syarat jelas & terukur? → Smart-contract.**
> * **Sengketa berpotensi kompleks? → Hibrida: logika dasar di kontrak, dispute path ke arbiter manusia dengan bukti on-chain/off-chain.**
>
> Ingat juga **tiga risiko klasik di sisi kode**:
> - **Bug/logic gap** (audit itu investasi, bukan dekorasi),
> - **UX & key management** (fitur paling sulit adalah “tidak salah klik”),
> - **Governance** (siapa yang boleh upgrade kontrak, kapan, dan dengan syarat apa).
>
> Sementara **di sisi tradisional**:
> - **Biaya & latensi** meningkat sesuai keruwetan kasus,
> - **Opasitas** (sulit dilihat dari luar mengapa keputusan A bukan B),
> - **Single point of trust** (kalau penjaga lelah, sistem ikut lelah).
>
> Kesimpulannya sederhana:
> - **Kalau kalian butuh keadilan yang lentur, ambil manusia.**
> - **Kalau kalian butuh kepastian yang dapat diprogram, ambil kode.**
>
> **Prof. NOTA** tidak memuja salah satunya—kita **memadukan keduanya supaya dana aman, proses jelas, dan proyek maju.**  
> ...
> 
> **60s Cut (jika waktu mepet)**  
> 
> **Escrow adalah ruang tunggu dana.**  
> **Tradisional** cocok untuk kasus sekali pakai yang **banyak negosiasi—fleksibel** tapi lambat dan berbiaya.  
> **Smart-contract** cocok untuk alur berulang, **rules-based—otomatis dan transparan**, tapi perlu audit, UX, dan tata kelola.  
> Pakai **hibrida saat sengketa** bisa kompleks: **aturan di kode, banding ke manusia**.
>
> Ingat: **kode taat tapi tak peka; manusia peka tapi tak konsisten**—pilih kombinasi yang membuat proyek kalian selesai.   
> ...

---

## 3) Compliance & Record-Keeping (Student/Startup)

* **KYC/AML** di on/off-ramp; **kenali batasan** akun & wilayah.
* **Dokumentasi**: invoice, tanda terima, *export* ledger → **akuntansi**.
* **Pajak dasar** lintas negara: catat nilai tukar & tanggal, hindari “*mixed wallets*” untuk proyek berbeda.
* **Privasi & minimasi data**: simpan yang perlu, hindari menyebar PII.

<figure><img src="https://github.com/user-attachments/assets/0d20787e-d02e-40f7-8217-7ac8546cb263" alt="Ilustrasi 6 oleh Prof. NOTA Inc. - Compliance & Record-Keeping (Student/Startup)"><figcaption><p>Compliance & Record-Keeping (Student/Startup)</p></figcaption></figure>

> ...
>
> Bayangkan kalian **lewat imigrasi bandara**.  
> Ada dua hal yang membuat petugas mengangguk: **identitas yang jelas dan jejak perjalanan yang rapi**.
>
> Di pembayaran lintas negara, **on/off-ramp adalah imigrasi itu**.  
> Ia bertanya hal yang sama: **siapa kamu, dari mana uangmu, ke mana ia pergi**.  
> Nama formalnya **KYC/AML**—bukan hiasan, tetapi gerbang.
>
> Sekarang bayangkan kalian sudah lolos imigrasi dan masuk kota.  
> Di sini yang bekerja adalah catatan.  
> **Tanpa catatan, kota itu gelap**.  
> _**If it isn’t recorded, it didn’t happen.**_
>
> **Prof. NOTA suka menyederhanakan ke empat lapisan:**
> * **Identitas & Akses** – siapa yang boleh apa.  
>   Akun on/off-ramp pakai nama legal yang benar, role-based access, dan audit trail login.  
> * **Money Trail** – uangnya lewat mana.  
>   Pisahkan wallet per proyek.  
>   Campur-campur itu seperti memasukkan resi lima toko ke satu kantong tanpa label—auditnya pecah kepala.  
> * **Tax Snapshot** – foto transaksi yang bisa dipahami akuntan manusia.  
>   Simpan tanggal/timestamp (zona waktu), nominal & mata uang, nilai tukar saat kejadian, fee, tx hash, alamat asal/tujuan, dan ID invoice/kontrak.  
> * **Privacy by Design** – kita hemat data pribadi.  
>   Simpan yang perlu;  
>   jangan taruh PII (Personally Identifiable Information / Informasi Identifikasi Pribadi) di channel publik;  
>   pakai folder izin granular; enkripsi bila sensitif.
>
> Bagaimana **cara menjaga empat lapisan** ini supaya ringkas tapi kuat?  
> **Ritual kecil, dampak besar:**
> - **Satu wallet = satu proyek**. (Dan satu treasury tim punya prosedur sendiri.)
> - **Jadwal export**: mingguan ke akuntansi (CSV/ledger), bulanan rekonsiliasi.
> - **Nama file konsisten**: YYYY-MM-DD_invoiceID_proyek.csv.
> - **Checklist ramp sebelum payout**: nama legal cocok → sumber dana jelas → pajak/retensi tercatat.
> - **Red flags yang langsung kita tahan**:  
>   nama penerima ≠ nama di on/off-ramp, FX rate tidak tercatat, wallet proyek dipakai untuk proyek lain, tak ada invoice padanannya.
>
> Ingat, tujuan **compliance bukan membuat hidup lambat**—tujuannya **membuat keputusan cepat tanpa rasa takut**.  
> Saat auditor bertanya, kalian tidak panik; kalian klik folder, keluarkan bukti, dan lanjut bangun produk.
>
> **Prof. NOTA** datang dalam wujud **Avatar (HFP)** untuk satu hal:  
> membuat rel yang cepat tetap sah, dan rel yang sah tetap cepat.
> 
> Compliance yang benar itu seperti sabuk pengaman—kalian melaju, tapi tetap selamat sampai tujuan.  
> ...
> 
> **60s Cut (jika waktu mepet)**
> 
> **On/off-ramp = imigrasi**.  
> **KYC/AML** itu gerbang.
> 
> Sesudahnya, yang menyelamatkan kalian adalah **catatan**:  
> Simpan **timestamp, nominal, FX rate, fee, tx hash, alamat asal/tujuan, ID invoice**.
>
> Pisahkan **wallet per proyek**—jangan campur.  
> Export ke akuntansi tiap minggu, rekon tiap bulan.
>
> **Minimasi PII** & pakai izin folder yang ketat.
> **Compliance** bukan rem; ia **sabuk pengaman** agar proyek melaju cepat & sah.  
> ...

---

## 4) Arsitektur Praktis (Minimal)

{% hint style="success" %}

**Catatan desain**
* **Custodial vs non-custodial**: pertimbangkan UX & kepatuhan.
* **Segregasi dana/proyek**: kurangi risiko pencampuran.
* **Observability**: log transaksi, biaya, & waktu tempuh; siapkan laporan periodik.  

{% endhint %}

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

<figure><img src="https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=m7BRN9YDV8pnvI2I5ZsI&only=yes&limit=100" alt="Ilustrasi 7 oleh Prof. NOTA Inc. - Arsitektur Praktis (Minimal)"><figcaption><p>Arsitektur Praktis (Minimal)</p></figcaption></figure>

> ...
>
> Bayangkan sistem kalian seperti **sebuah kota kecil**.  
> **Tidak megah, tapi teratur.**  
> Ada empat distrik yang saling **terhubung**, masing-masing dengan **tugas jelas**.
>
> Distrik 1 — **Web2 App/Admin (Balai Kota)**.  
> Di sinilah identitas, order, dan invoice lahir.  
> Balai kota tidak memindahkan uang; ia **mencatat niat: siapa membayar apa, untuk apa**.  
> Kuncinya: satu order_id yang akan menempel sampai akhir hidup transaksi.
>
> Distrik 2 — **Payments Layer (Jembatan)**.  
> Dari balai kota, kalian menyeberangi jembatan: **on/off-ramp (KYC) dan wallet**.  
> Di sinilah uang berpindah: **fiat ↔ stablecoin**.  
> Jembatan yang baik itu sempit—hanya fungsi pemindahan, tanpa logika bisnis.
>
> Tombol-tombol **pilihan Prof. NOTA**:  
> - **Custodial** (UX lebih lembut, delegasi kunci) vs **non-custodial** (kedaulatan, tapi perlu merawat kunci).  
> - **Chain & biaya**: pilih **finality dan fee** yang sesuai profil transaksi, bukan sekadar populer.  
>
> Distrik 3 — **Escrow Contract (Gerbang Penjaga)**.  
> Ini gerbang otomatis.  
> Kalau proyek butuh, **aturan → kode**: **milestone, time-lock, release logic, plus jalur sengketa**.  
> Jika syarat A & B terpenuhi, gerbang terbuka; kalau ada konflik, alur berbelok ke arbiter manusia.  
> Ingat: **kode itu patuh, manusia itu peka**—kadang kalian butuh hibrida.
>
> Distrik 4 — **Records (Perpustakaan Kota)**.  
> Setiap gerakan di jembatan atau gerbang meninggalkan cap di perpustakaan: ledger, invoice, export ke akuntansi.  
> Formatnya membosankan—dan itu bagus.  
> _**If it isn’t recorded, it didn’t happen.**_
>
> **Tiga Hukum Prof. NOTA** untuk arsitektur minimal:
> * **Satu sumber kebenaran (order_id) mengalir dari App → Payments → Escrow → Records.**
> * **Pisahkan peran: App mencatat niat, Payments memindah dana, Escrow menegakkan aturan, Records membuktikan.**
> * **Rekonsiliasi terjadwal: webhook in → ledger out; mingguan ke akuntansi, bulanan tutup buku.**
>
> Anti-pola yang mahal:
> * **Campur wallet antar proyek**
>   - **Apa itu:** 1 wallet dipakai untuk **banyak proyek/produk/klien** sekaligus.
>   - **Gejala:** sulit melacak saldo & transaksi per proyek; laporan labur; rekonsiliasi lama.
>   - **Risiko:** audit & pajak **kabur**, salah hitung margin, potensi temuan kepatuhan.
>   - **Yang benar:**
>     - **1 proyek = 1 wallet (atau 1 sub-treasury)**.
>     - Tag transaksi pakai `project_id` dan simpan mapping **on-chain addr ↔ project**.
>     - Tutup periode per proyek (rekon mingguan/bulanan).
>   - **Tes 5 detik:** Bisa nggak export **semua transaksi proyek X** dalam 1 klik? Kalau tidak, wallet-nya bercampur.
> * **Logika bisnis di payments layer**
>   - **Apa itu:** aturan produk (harga/discount/refund policy/milestone) ditaruh di **gateway/on-ramp/wallet service** alih-alih di **App/Service**.
>   - **Gejala:** pindah vendor/chain = migrasi berat; perubahan kecil butuh ticket ke provider.
>   - **Risiko:** **vendor lock-in**, duplikasi aturan, sulit diuji (unit test), **change-blast** besar.
>   - **Yang benar:**
>     - **App/Admin** pegang **aturan bisnis** (harga, diskon, policy, milestone).
>     - **Payments layer** cuma **adapter** yang **memindahkan dana** & mengirim event (webhook).
>     - Escrow logic di **smart-contract** (kalau dipakai), tapi **orchestration/approval** tetap di App.
>   - **Tes 5 detik:** Kalau ganti on/off-ramp, apakah logika harga/milestone aman? Kalau tidak, logika kebablasan ada di payments.
> * **Tidak ada idempotensi**
>   - **Apa itu:** operasi pembayaran (capture/release/refund) bisa **tereksekusi ganda** saat network retry/webhook duplikat.
>   - **Gejala:** webhook dobel → saldo ganda/dua kali rilis dana.
>   - **Risiko:** **over-payment**, refund manual, tutup buku kacau.
>   - **Yang benar:**
>     - Setiap operasi punya **`idempotency_key`** unik (mis. `order_id` + langkah).
>     - Di DB, **upsert** berdasarkan `idempotency_key` + **unique constraint**.
>     - Abaikan event duplikat; log sebagai “already processed”.
      - **Contoh cepat (pseudo):**
>       ```
>       -- unique index on idempotency_key
>       INSERT INTO payments (idempotency_key, order_id, amount, status)
>       VALUES (:key, :order, :amt, 'captured')
>       ON CONFLICT (idempotency_key) DO NOTHING;
>       ```
>   - **Tes 5 detik:** matikan internet saat klik "Bayar", nyalakan lagi → **harus** jadi **1 transaksi** saja.
> * **PII nyasar ke tempat publik**
>   - **Apa itu:** data pribadi (KTP/paspor, nomor HP, email, alamat, selfie KYC) ikut nongol di **log publik, ticket, dashboard, Git, Notion, atau on-chain**.
>   - **Gejala:** screenshot/chat yang berisi PII tersebar; field PII "kebawa" ke analitik.
>   - **Risiko:** **pelanggaran privasi/kepatuhan**, reputasi rusak, remediasi mahal.
>   - **Yang benar:**
>     - **Minimisasi**: simpan yang perlu saja, **jangan** bawa PII ke pipeline analitik umum.
>     - **RBAC** ketat, enkripsi di rest/transit untuk PII; **jangan pernah** taruh PII **on-chain**.
>     - Masking di log: `+62xxxx…`, `email: a***@domain`.
>     - Pisahkan storage PII dari transaksi; referensikan via **token/ID** saja.
>   - **Tes 5 detik:** cari nama/telepon di log/dashboard publik—kalau ketemu, kebocoran sudah terjadi.
>
> **Minimal bukan berarti miskin, minimal berarti berani bilang "cukup":**  
> **cukup fitur untuk bergerak cepat, cukup catatan untuk tidur tenang, cukup batas untuk selamat.**
>
> **Prof. NOTA menyukai kota kecil yang disiplin**—karena kota kecil yang rapi lebih mudah dibesarkan daripada metropolis yang kacau.  
> ...
>
> **60s Cut (jika waktu mepet)**
> 
> Empat blok:  
> **App (order/invoice) → Payments (on/off-ramp + wallet) → Escrow (aturan → kode, opsional) → Records (ledger → akuntansi)**.
> 
> Pegang **satu order_id dari awal sampai akhir**, **pisahkan peran**, dan **rekonsiliasi terjadwal**.  
> Hindari campur **wallet**, jangan masukkan **logika bisnis** ke **payments layer**, dan **jaga PII**.  
> Minimal = **cepat, sah, dan siap tumbuh**.  
> ...

---

## 5) Aktivitas Bersama (Role-Play) + Q&A Terstruktur

{% hint style="success" %}

**Catatan:**
- Detail instruksi untuk masing-masing role-play berada pada dokumen terpisah, [International Payments & Escrow Role-Play](../../../archived-oioi/2025/10/international-payments-escrow-roleplay.md)
- Bagian ini hanya menyiapkan kerangka, tujuan, dan batasan diskusi agar selaras dengan **Output Materi**.

{% endhint %}

- **Susunan singkat & tujuan**
  * **Role-Play 1 — International Transfers (tanpa escrow)**
    - Fokus: membandingkan **bank/fintech rails (privat)** vs **blockchain/stablecoin rails (publik)** dari sisi **latensi, transparansi, langkah proses, dan biaya**.
  * **Role-Play 2 — Escrow untuk transaksi/jual-beli**
    - Fokus: kapan perlu **escrow**, perbedaan **trusted intermediary** vs **rules-as-code**, konsep **kondisi rilis** dan **jalur sengketa** (tanpa implementasi teknis).

- **Alokasi waktu saran**: RP1 **20–25’**, RP2 **20–25’**, dan Debrief + Q&A **10–15’**

- **Guardrails umum**: tanpa rekaman, tidak ada kunci/PII, tidak ada transaksi live, contoh biaya/fee bersifat ilustratif, dan patuh kebijakan kampus.

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
  * **Penutup Q&A:** rekap poin pembelajaran → lanjutkan ke **Next Steps** (workshop 3 jam, capstone clinic, research/internship) dan form minat.

<figure><img src="https://github.com/user-attachments/assets/392b6e96-3895-4967-8c39-693b909a4aef" alt="Ilustrasi 8 oleh Prof. NOTA Inc. - Aktivitas Bersama (Role-Play) + Q&A Terstruktur"><figcaption><p>Aktivitas Bersama (Role-Play) + Q&A Terstruktur</p></figcaption></figure>

> ...
>
> Sekarang giliran kalian.
> 
> Biasanya pertanyaan datang dalam tiga rasa: **taktis hari ini, sistemik bulan ini, dan filosofis sepanjang tahun**.  
> Di sesi ini, kita **fokus ke taktis–pragmatis**—yang bisa kalian bawa pulang dan dipakai minggu ini.
>
> Rel Q&A-nya sederhana:  
> **On-track: memilih rails (bank/fintech vs stablecoin), membaca biaya/latency, kapan escrow dipakai, dokumen minimal yang harus disimpan, dan sketsa arsitektur paling ramping.**  
> **Off-track dulu: tebak-tebakan harga koin, trading signals, audit kode tingkat kedalaman, atau konsultasi legal spesifik kasus.**  
> Yang ini kita parkir ke workshop atau clinic supaya dapat ruang yang tepat.
>
> Cara bertanya: **angkat tangan, sebut konteks dalam tujuh kata, lalu pertanyaannya.**  
> Contoh: ‘freelance lintas negara—payout mingguan—wallet apa?’
>
> Semakin tajam konteks, semakin tajam jawaban.  
> Kalau pertanyaan kalian butuh pembahasan panjang, jangan khawatir—itu pertanyaan yang bagus.
>
> Sekarang, mari kita gunakan sisa waktu dengan pertanyaan yang membuat proyek kalian bergerak.  
> Bukan pertanyaan paling pintar—pertanyaan yang paling membantu kalian ship.  
> ...
>
> **60s Cut (jika waktu mepet)**
>
> **Q&A kita taktis–pragmatis**: pilih rails, baca biaya/latency, kapan escrow, dokumen minimal, dan sketsa arsitektur.  
> Off-track (harga koin, trading, audit mendalam, legal spesifik) kita parkir ke: Workshop 3 jam, Capstone Clinic, atau Research/Internship.  
> Silakan **angkat tangan, sebut konteks singkat, lalu pertanyaannya**. Kita cari jawaban yang membuat proyek kalian jalan.  
> ...

---

## 6) Next Steps (Untuk Mahasiswa & Kampus)

{% hint style="success" %}

**What to do:**  
silahkan scan **QR Code** (link ke formulir pendaftaran minat); **khusus mahasiswa** tersedia (kuota terbatas, 30 hari).

{% endhint %}

* **Workshop 3 jam (via kampus)** — latihan **alur pembayaran global + escrow (USDC)** dari nol → siap produksi sederhana.
* **Capstone Clinic (6 tim, 2×60’)**
* **Research internship (selektif)** — rails & escrow.

<figure><img src="https://github.com/user-attachments/assets/32302916-20c8-482e-b7f4-ce1e8d8434b1" alt="Ilustrasi 9 oleh Prof. NOTA Inc. - Next Steps (Untuk Mahasiswa & Kampus)"><figcaption><p>Next Steps (Untuk Mahasiswa & Kampus)</p></figcaption></figure>

<figure><img src="https://github.com/user-attachments/assets/6aedfbd1-5f2e-4500-95b0-f5f2441ebb07" alt="Ilustrasi 10 oleh Prof. NOTA Inc. - QR Code Interest Form"><figcaption><p>QR Code Interest Form</p></figcaption></figure>

> ...
> 
> Kita tidak memaksa jawaban cepat untuk masalah lambat; kita pindahkan ke **wadah yang benar**:  
> **Workshop 3 jam** — latihan hands-on: dari on/off-ramp sampai rekonsiliasi.  
> **Capstone Clinic** — 6 tim, case-by-case: rancang arsitektur minimal yang bisa kalian ship.  
> **Research/Internship** (terseleksi) — jalur eksplorasi untuk yang ingin mendalami rails & escrow.
>
> Sekarang silahkan di-**scan QR code** formulir ketertarikan di depan kalian.  
> Jika berkenan, silahkan **tuliskan tanggapan, komentar, kritik dan saran terkait Prof. NOTA** di formulir tersebut.  
> ...

---

## 7) Output Materi (Ujian Peserta)

{% hint style="success" %}
 
**What to do:**  
silahkan scan **QR Code** (link ke soal uji coba); jawab dan selesaikan semampunya saja.

{% endhint %}

* Peserta mampu menyebutkan **opsi rails** beserta implikasi biaya/waktu.
* Peserta memahami **escrow tradisional vs smart-contract** dan kapan memilihnya.
* Peserta tahu **kebutuhan compliance** minimal dan pola dokumentasi.
* Peserta dapat membuat **sketsa arsitektur minimal** Web2 → Web3.
* Peserta tahu **langkah lanjut** (workshop/klinik/internship) dan kanal informasi.

<figure><img src="https://github.com/user-attachments/assets/cc9945f6-8b1e-4579-a919-d55a6dbc6ced" alt="Ilustrasi 11 oleh Prof. NOTA Inc. - Output Materi (Ujian Peserta)"><figcaption><p>Output Materi (Ujian Peserta)</p></figcaption></figure>

<figure><img src="https://github.com/user-attachments/assets/628bc041-1b8e-43b3-867f-a76d77118008" alt="Ilustrasi 12 oleh Prof. NOTA Inc. - QR Code Post-Session Quiz"><figcaption><p>QR Code Post-Session Quiz</p></figcaption></figure>

---

## 8) Lampiran: Handout Singkat (Ringkasan)

{% hint style="success" %}
 
**What to do:**  
silahkan di-**[Export as PDF](https://baca.endhonesa.com/all-notas-markdowns/~gitbook/pdf?page=0ilGqwmB5DvZmEv8miBS&only=yes&limit=100)**; gunakan, dan jangan disebarkan tanpa ijin.

{% endhint %}

* **What You’ll Learn**: peta opsi pembayaran, escrow, compliance, arsitektur minimal, next steps.  
* **Quick Comparison**: Bank/Fintech (mapan/overhead) vs Stablecoin (cepat/programmable).  
* **Pragmatic Escrow**: pilih tradisional untuk sederhana; pilih smart-contract untuk otomatisasi & milestone.  
* **Next Steps**: Workshop 3 jam · Capstone Clinic · Research internship.  
* **Kontak**: **[Prof. NOTA](https://baca.endhonesa.com/all-notas-markdowns/contact)**

<figure><img src="https://github.com/user-attachments/assets/5da6cff5-efd2-4252-8de6-a48b998fe8eb" alt="Ilustrasi 13 oleh Prof. NOTA Inc. - Lampiran: Handout Singkat (Ringkasan)"><figcaption><p>Lampiran: Handout Singkat (Ringkasan)</p></figcaption></figure>

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
