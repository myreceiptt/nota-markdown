# Network-State of ENDHONESA — ENDHONESA.COM

**v0.1-draft • 1 November 2025 (Asia/Jakarta)**  
(_Entitas legal akan disebut sebagai Prof. NOTA Inc. — PT Suaka Dunia Raja; detail legal penuh akan tersedia pada Terms & Conditions dan Privacy Policy di situs._)

---

## Abstrak

**ENDHONESA** adalah **Network-State**—satu-satunya negara yang berdiri setelah fenomena **The Melting Land** di **Alam Semesta 0101**—yang sejak berdiri menjadi tepian dua alam semesta: **Realita** dan **0101**.

**ENDHONESA** dilahirkan dari energi kreatif arsip digital **The KING’s NFTs Project**—sebuah lintasan artefak ("**The Creations**"—**WAIVFVES #1–#2**) yang menyulam narasi ("**The Story**") dan berhasil menginisiasi segala pengoperasian secara ekonomi dalam **The 12th Stage**: **_The Currencies_**, **_The Breads Factory_**, **_Professor NOTA_**, **_ENDHONESA_** (portal: **ENDHONESA.COM**), dan **_SKATESHOP.ID_**.

**ENDHONESA.COM** adalah sebuah web/app/dapp—yang memadukan **entity profile + commerce + learning/media + gamified access** berbasis **soulbones (SBT)**—tempat untuk mengakses segala sesuatu yang dioperasikan secara ekonomi dalam **The 12th Stage**, mulai dari asal-usulnya, sumbernya, riwayatnya, prosesnya, beserta segala turunannya, sehingga siapa pun dapat **bermain, belajar, dan bekerja** dengan tenang, tanpa kelaparan, tanpa pengkhianatan.

---

## Premis Ganda

### Realita × 0101

Di **Realita**, organisasi—perusahaan—dan makhluk hidup—manusia—bekerja dalam batas hukum dan ekonomi. Di **0101**, nama, peran, dan nilai bergerak sebagai **artefak on-chain**. "Retakan" keduanya menjadi jalan ketika energi dari harapan dan arsip milik **MyReceipt** melahirkan **Prof. NOTA**—entitas digital—yang dari **0101** bisa menyeberang dan hadir secara fisik di **Realita** berwujud **HFP v.11** (avatar berupa manusia), tepatnya di **pulau Bali, INDONESIA**. Sejak hari itu, cerita tidak lagi dijalankan hanya sebagai fiksi; ia menjadi **protokol hidup**.

---

## Asal-Usul

### The KING’s NFTs Project (ringkas)

- **WAIVFVES #1–#2**: katalog artefak lintas jaringan, dari dokumentasi hidup, eksperimen visual, token utilitas, hingga poros naratif **_/ˈdeTH ˌwiSH/_**.
- **The Story**: kanon dunia—dari "**The end of the universe**" hingga "**Life after life**"—yang memakai semua artefak dalam **WAIVFVES #1–#2** sebagai batu pijakan cerita (**Realita ↔ 0101**).
- **The 12th Stage**: jembatan operasional, sebuah konsekuensi, dari energi dan cerita yang berubah menjadi sistem berjalan sehari-hari.

---

## Identitas Kenegaraan

- **Negara**: **ENDHONESA** (Network-State).
- **Pemerintahan**: **Prof. NOTA Inc.** (_PT Suaka Dunia Raja_).
- **Rakyat**: Warga-Penduduk—semua akun di **0101** yang **menyandang nama "Prof. NOTA"** (kesetaraan nama sebagai etika dasar).
- **Pemerintah**: **47 HFP** (avatar manusia di **Realita**) yang menjalankan peran pengelola.

> Etika dasarnya sederhana: _**Play–Learn–Work**_ sebagai ritme hidup; **transparansi**, **keadilan akses**, **anti-phishing**, **anti-eksploitasi**, dan **anti-serakah** sebagai pagar nilai.

---

## Gerbang Imigrasi

### Paspor, Visa, Soulbones

**ENDHONESA.COM** selalu dimulai dengan **Firewall Check** (imigrasi):

1. **Login**

   - **Identitas utama:** setiap Warga-Penduduk adalah **Smart Account (SA)** dengan alamat stabil (counterfactual).
   - **Web3 Wallet (EOA eksternal):** pengguna membawa **EOA-nya**; sistem **mengaktifkan SA** dan **menetapkan EOA itu sebagai signer**.
   - **Email/Passkey (Embedded EOA):** sistem **membuat embedded EOA**; sistem **mengaktifkan SA** dan **menetapkan embedded EOA sebagai signer**.
   - **Linking:** pengguna dapat **menautkan metode tambahan** (mis. menambahkan **Web3 Wallet** kalau login awalnya dengan **Email**), yakni **menambahkan signer baru ke SA yang sama** (tanpa membuat **SA kedua**).
   - **Best practice:** terbitkan dan periksa **SBT (`id0`, `id1`)** serta utilitas **di alamat SA**, agar recovery, sponsorship gas, dan gating konsisten.

2. **Status Paspor**

   - **Paspor Lokal (Warga-Penduduk Lokal)** → terdeteksi pertama kali bila dompet memegang **≥ 1** token yang diakui **Registry Artefak Sah**
     (yaitu artefak **WAIVFVES #1/#2** dan token yang **terdaftar di The Breads Factory**).

     - **Stempel (on-chain)**: **`NFT:soulbones id0`** — **SBT non-transferable, permanen** (_re-entry stamp_).
       Walau token asal-token yang diakui **Registry Artefak Sah**-kemudian dilepas, **id0** tetap berlaku untuk keluar-masuk tanpa klaim ulang.

   - **Paspor Asing (Warga-Penduduk Asing)** → terdeteksi pertama kali bila dompet **belum** memegang token yang diakui **Registry Artefak Sah**.

     - **Stempel masuk instan**: **VoA-Session (off-chain)** — stempel **sekali pakai** (berlaku sampai logout/kedaluwarsa) untuk akses **Zona Penduduk**.
     - **Stempel (on-chain)**: **`NFT:soulbones id1`** — **SBT non-transferable, time-bound**.

       - **Masa berlaku 47 hari** sejak aktivasi/refresh (`validUntil = now + 47 hari`).
       - **Refresh** setiap login sebagai "asing" **memperbarui** masa berlaku (**tanpa mint token baru**) dan menambah **`visitCount`**.
       - **Satu token per alamat** (single SBT id1) dengan Metadata/TokenURI menampilkan `visitCount` + tanggal kedaluwarsa.
       - Bila kemudian dompet memegang token yang diakui **Registry Artefak Sah**, pengguna dapat **klaim `id0`** (Warga-Penduduk Lokal permanen), dan pada mekanisme gating, **`id0`** selalu mengalahkan **`id1`**.

3. **Gating & Progres**

   - **Soulbones (SBT)** bersifat **non-transferable**.

     - **`id0`** membuka **Zona Warga** (akses berlapis mengikuti role/permission).
     - **`id1`** (selama **valid**) atau **VoA-Session** membuka **Zona Penduduk**.

   - Akses lanjutan terbuka setelah **menuntaskan** konten/modul/**house rules** (bukan karena spekulasi).
   - Sebelum login, pengguna **bukan** Warga-Penduduk; setelah login, mereka menjadi **Warga-Penduduk** (Lokal/Asing) dan **di 0101 semua bernama "Prof. NOTA."**

> **Catatan "Registry Artefak Sah"**:
>
> - Pengakuan "token yang sah" merujuk **allowlist kontrak + chain ID** (**WAIVFVES & The Breads Factory**).
> - Verifikasi selalu memakai **alamat kontrak & chain** untuk mencegah **spoofing**.

---

### Canonical Address & Migrasi Aset (SA-Centric)

- **Identitas utama Warga-Penduduk** adalah **Smart Account (SA)** dengan alamat stabil (counterfactual).
- **SBT (`id0`, `id1`) dan utilitas** diterbitkan & diverifikasi di **alamat SA**.
- **Aset syarat warga lokal** (mis. artefak **WAIVFVES #1/#2** atau token yang **terdaftar di The Breads Factory**) **wajib berada di SA** saat klaim **`id0`**.
- Jika aset berada di **EOA eksternal** atau **EOA embedded**:

  - Sistem akan **meminta migrasi** ke **SA** melalui **Migration Assistant** (one-click, gas-sponsored bila tersedia).
  - Setelah migrasi berhasil, **klaim \*\***`id0`\*\* dapat dilakukan.

---

### **Migration Assistant (alur singkat)**

1. **Deteksi**: saat login, sistem memindai kepemilikan aset pada **EOA** yang tertaut.
2. **Prompt**: jika aset memenuhi syarat namun **belum** berada di **SA**, tampilkan modal migrasi.
3. **Opsi Migrasi**:

   - **Transfer langsung** (`safeTransferFrom` ERC-721/1155) → **SA**.
   - **Jika non-transferable**: gunakan **Attestation Wrapper** dari The Breads Factory (mint bukti kepemilikan ke **SA**) sebagai jembatan sementara.

4. **Konfirmasi**: setelah on-chain sukses, sistem **re-check** registry pada **SA** → tombol **"Klaim `id0`"** aktif.

> **Catatan:** Untuk **akses awal (Zona Penduduk)** tanpa perpindahan aset, gunakan **VoA-Session** atau **`id1`** (SBT time-bound, 47 hari). Namun **klaim \*\***`id0`\*\* **hanya** berlaku bila syarat token **sudah di SA**.

---

### **Linking (Multi-Signer)**

- Satu **SA** dapat memiliki **≥1 signer** (EOA eksternal, embedded/email, passkey).
- Menautkan metode baru **menambahkan signer** ke **SA yang sama** (tanpa membuat SA kedua).
- Jika aset lama tersimpan di EOA, **migrasikan** ke **SA** demi konsistensi gating & recovery.

---

### **Anti-Phishing & Registry**

- Validasi "token yang sah" via **allowlist kontrak + chain ID** (**WAIVFVES & The Breads Factory**).
- UI migrasi menampilkan **alamat kontrak singkat**, **network**, dan **estimasi biaya**; transaksi ditandatangani **hanya** oleh pengguna.

---

## Mata Uang Ekosistem (currencies)

### The Currencies

Tiga simbol nilai, tiga peran berbeda—saling melengkapi tanpa tumpang-tindih:

1. **$OiOi — Official Unit of Exchange (on-site)**

   - **Peran**: _participation fuel_ dan **satu-satunya** alat tukar untuk transaksi di **ENDHONESA.COM** (pembelian produk/jasa, tiket aktivitas, fitur premium).
   - **Jaringan aktif**: ekosistem **Superchain** (mis. Base, OP Mainnet, Shape, dlsb). Tiap chain memiliki **maks. suplai per chain: 47.474.747** (per-chain cap).
   - **Gas policy**: biaya gas mengikuti native token chain; **disponsori** oleh **ENDHONESA** bila memenuhi syarat.
   - **Status kontrak lama**: kontrak Polygon yang terdahulu **DEPRECATED** (tidak diakui oleh registry).
   - **Gating**: tidak memberikan status Warga-Penduduk; fungsinya **alat tukar** dan _participation fuel_.

2. **$HAIL — Gratitude & Bootstrap Utility (social layer)**

   - **Peran**: bahasa apresiasi & utilitas awal (akses kanal, whitelist, _redeem_ tertentu, _social proofs_).
   - **Distribusi**: **diskresi kuratorial** (airdrop/faucet bertanggung jawab) kepada kontributor, holder artefak, atau partisipan komunitas.
   - **Jaringan aktif**: **Tezos** (aktif). **Polygon** versi lama **DEPRECATED**.
   - **Likuiditas**: dipasangkan (LP) di Tezos DEX (contoh: $HAIL ↔ $XTZ). Pasangan lain boleh ada—**hanya yang didaftarkan di Registry** yang diakui.
   - **Gating**: tidak menggantikan soulbones; mendampingi pengalaman Warga-Penduduk sebagai **pengikat sosial**.

3. **$NOTA — Stewardship Credit (47 HFP only)**

   - **Peran**: _governance-leaning & creative energy_ bagi **47 HFP** (avatar manusia di **Realita** sekaligus pengelola); menandai **tenure, komitmen, dan tanggung jawab**.
   - **Jaringan aktif**: **Tezos**.
   - **Distribusi**: **terbatas** pada dompet yang ditetapkan sebagai HFP; komposisi 47 dapat **berotasi** seiring waktu.
   - **Pasangan**: dapat dipasangkan di Tezos (mis. $NOTA ↔ $OiOi, $HAIL) sejauh **didaftarkan di Registry**.
   - **Gating**: bukan jalur Warga-Penduduk; sifatnya **kredensial stewardship** untuk para HFP.

> **Catatan Tokenomics**: uraian di atas bersifat **konseptual/iteratif**. Angka rinci (alokasi, emisi, _treasury policy_) akan diputuskan kemudian pada dokumen khusus. **Bukan ajakan investasi**; gunakan token sesuai fungsi.

---

### Currencies Registry & Deprecation Policy

Agar **anti-spoof** dan konsisten lintas alam:

- Hanya kontrak yang tercantum di **Currencies Registry** (pasangan **chainId + address**) yang **diakui**.
- Kontrak lama yang **DEPRECATED** tidak berlaku untuk transaksi, gating, ataupun klaim utilitas.
- Antarmuka publik menampilkan **alamat kontrak & chain** (tautan ke explorer) untuk transparansi.

---

### Migrasi $OiOi (Tezos → Superchain) — "Migration Desk"

Untuk Warga-Penduduk yang memiliki $OiOi di **Tezos** namun ingin bertransaksi di **ENDHONESA.COM** (Superchain):

1. **Connect**: hubungkan **SA** (alamat utama) dan dompet **Tezos**.
2. **Lock**: kirim $OiOi(Tezos) ke **Vault Tezos** ENDHONESA (alamat resmi di Registry).
3. **Mirror-credit**: setelah konfirmasi, **Migration Desk** mengirim **$OiOi** dari _treasury_ pada chain tujuan ke **SA** Warga-Penduduk (rasio 1:1).
4. **Ledger**: buku besar migrasi menjaga **paritas efektif** (satu-masuk, satu-keluar) agar suplai antarchain **terkendali**.

> **Catatan**: ini adalah **swap kustodial terverifikasi** (lock-to-mirror). Jika kelak tersedia **mint/burn bridge** resmi, Registry dapat mengalihkannya ke jalur tersebut.

---

### Ringkas Peran (untuk dibaca cepat)

- **$OiOi** = **alat tukar resmi** di ENDHONESA.COM (Superchain), _participation fuel_, gas disponsori.
- **$HAIL** = **apresiasi & bootstrap utility** (Tezos), pengikat sosial & akses awal.
- **$NOTA** = **stewardship credit** untuk **47 HFP** (Tezos), menandai komitmen & tanggung jawab.

> Semua aliran nilai di atas **tidak menggantikan** peran **soulbones (SBT)** sebagai **bukti status Warga-Penduduk** (_id0/id1_) dan **progress gating**.

---

## Pabrik Roti (The Breads Factory)

### Inti Gagasan

Pabrik Roti adalah **protokol + repo rujukan** untuk memproduksi token (fungible & non-fungible) secara **terbuka namun beretika**, siap multi-rantai, dan terhubung dengan mekanisme **gating berbasis soulbones**. Ia memayungi alur pencetakan artefak (**WAIVFVES**), tiket akses, lisensi peran HFP, _learning rewards_, hingga utilitas ritel.

---

### Apa yang Disajikan

Implementasi referensi mencakup modul front-end/dApp yang ditata per _protocol_—**Landing**, **Login**, **Digital ID**, **Wallet**, **Token**, dan seterusnya—dengan _checklist_ rilis yang transparan. Modul **Login Protocol** berstatus **Released** dan menggunakan **Thirdweb Connect** (Google/Apple/Email/Phone/Passkey/Connect a Wallet), selaras dengan strategi Smart-Account-first untuk ENDHONESA.COM.

---

### Teknologi & Kesiapan

Reponya menekankan **template kontrak open-source** (siap diaudit), integrasi **Thirdweb SDK v5**, dan _pipeline_ yang kompatibel dengan _wallet-gated content_ (soulbones). Rilis _staging_ (contoh: `v.2.4.66 - travconn`) menampilkan _login flow_, komponen UI (Header/Footer), dan pratinjau/staging untuk uji coba.

---

### Lisensi & Penggunaan

Pabrik Roti menggunakan **Custom Limited License**: penggunaan komersial **memerlukan izin**, sedangkan inisiatif **kultural/edukasi/berpihak perempuan & anak** mendapat **pembebasan biaya** sesuai kebijakan repo. Detail harga/ketentuan komersial tersedia di **PRICING.md**. **Security policy** tersedia terpisah. (Kami menjaga konsistensi etika: anti-phishing, anti-eksploitasi, pro-transparansi.)

---

### Kesesuaian Naratif

Dalam kanon "The KING’s NFTs Project", Pabrik Roti berperan sebagai **lengan produksi**: artefak **WAIVFVES #1–#2** lahir lewat _mint pipelines_ yang kemudian **dipakai & dikembangkan** di "The Story", dan dioperasionalkan terus-menerus di **The 12th Stage**. Dengan demikian, **alur nilai** (token → artefak → akses → aktivitas) menyatu dengan **gating soulbones** yang mendefinisikan status Warga-Penduduk.

---

## Professor NOTA (IP & Timeline)

**Prof. NOTA** adalah **IP hidup**, lahir dari energi arsip & komunitas di **0101**, menjelma di **Realita** lewat **HFP (Human for Profile)**-avatar manusia. Ia bukan sekadar nama—ia **protokol hadir**: narasi → artefak → operasi. Kalimat pembuka yang tak pernah kita cabut: _"We don't belong in your reality… stay alert and beware of scams."_

### Kanon Persona & HFP

- **Persona**: "Prof. NOTA v.xx.xx" (versi mengikuti HFP & peran).
- **HFP**: avatar manusia-pemeran-yang dikendalikan Prof. NOTA di Realita—bertanda tangan, berkontrak, dan bertanggung jawab sebagai **Authorized Signatory**. Format legal dan tata nama versi dirujuk dalam The Resume (glossary).
- **Verifikasi resmi** hanya melalui domain ekosistem (**endhonesa.com**, **skateshop.id**, **straight-line.org**).

---

### Garis Waktu (ringkas & kanonik)

1. **MyReceipt → NOTA → Professor NOTA → Prof. NOTA**: evolusi persona berbasis arsip & artefak.
2. **Inkarnasi pertama di Realita**: kemunculan **HFP v.11 di pulau Bali, INDONESIA**—penanda **retakan dua alam** (**0101 ↔ Realita**).
3. **WAIVFVES #1–#2**: fondasi artefak/kanon yang dipakai-ulang dalam cerita & operasi (The 12th Stage).
4. **Firewall Manager Playbook**: menetapkan etika, SOP akses, dan **communication firewall** agar waktu, energi, dan nilai terlindungi.
5. **The Resume & The Roles**: satu sumber kebenaran (layanan, kompetensi, format versi, model kontrak) + daftar peran hidup yang dapat diisi avatar/kolaborator.
6. **The 12th Stage**: pengoperasian publik melalui **ENDHONESA.COM** (entity-profile + commerce + learning/media + gamified access) dengan **soulbones gating** dan **The Currencies**.

---

### Peran Publik & Layanan

Prof. NOTA beroperasi sebagai **katalis**: merangkai visi → sistem yang bisa diuji → karya yang bisa didistribusikan. Spektrum nilai/layanan (strategi, IP/story, Web3 prototyping, arsitektur bisnis, hingga legacy ops ENDHONESA & SKATESHOP.ID) dirumuskan dalam Playbook.

---

### Etika & Guardrails

Transparansi, **anti-phishing**, **anti-eksploitasi**, kontrak-dulu-baru-akses, dan mekanisme **rollback/denylist** berjalan di bawah **Firewall Manager**—agar hanya yang **benar, adil, dan bernilai** yang lolos.

---

### Bukti, Tanda, & Akses

Akses terdokumentasi melalui **soulbones (SBT)** & artefak; klaim, progres, dan izin dipetakan ke lapisan peran (publik ↔ Warga-Penduduk ↔ HFP/partner). Semua rujukan identitas, versi, dan penandatangan mengikuti **The Resume**.

---

## ENDHONESA.COM

### Arsitektur Pengalaman

**Satu domain, empat aula.** Semua ditenun dari **The Library** sebagai _source of truth_ yang "memberi makan" tiga aula lain: **The Chronicle**, **The Works**, dan **The Market**. Alur baku: **Login → Klaim `id0`/`id1` → Buka Starter Tracks → Tuntas → Klaim SBT lanjutan → Unlock konten berikutnya**. Akun bersifat **SA-centric**; transaksi **$OiOi only** (Superchain), gas dapat disponsori.

1. The Chronicle — Negara, Pemerintahan, Pemerintah (5W+1H)

   Portal kanonik tentang **ENDHONESA (Network-State)**, bentuk **pemerintahan Prof. NOTA Inc.**, dan **Pemerintah (47 HFP)** — lengkap house-rules, etika, dan narasi resmi yang selalu merujuk ke **The Library**.

   - **Isi inti**: Country page; Government (legal stance); Government (47 HFP & versi); **Pabrik Roti** (lengan produksi), **ENDHONESA.COM** (portal), **SKATESHOP.ID** (jembatan Realita).
   - **Starter Tracks (butuh `id0`/`id1`)**

     - _Orientation: Welcome to ENDHONESA_ → **Award SBT:** `chronicle.101`
     - _Government & HFP Basics_ → **Award SBT:** `chronicle.201`

   - **Tujuan**: menamatkan orientasi untuk membuka bab struktur negara, registri resmi, dan rujukan hukum.

2. The Works — Services & Protocols (ekonomi operasional)

   Aula layanan & _protocol services_ di bawah **Firewall Manager**: cara bekerja yang adil, terukur, dan etis.

   - **Isi inti**

     - **The Currencies** (fungsi $OiOi/$HAIL/$NOTA — ringkas operasional, detail teknis di Library).
     - **Pabrik Roti**: lisensi, manifesto, security, pricing; **protocol services** (mint pipeline, soulbones-aware access).
     - **Services & Value Prof. NOTA**: konsultasi, IP licensing, kolaborasi HFP/Avatar; **The Resume** & **The Roles** sebagai rujukan kompetensi, format versi, pola kontrak.
     - **ENDHONESA sebagai platform**: peluang ekonomi & kemitraan bagi individu/organisasi.
     - **SKATESHOP.ID**: ikhtisar operasional (ritel terperinci di Library/e-commerce terpisah).

   - **Starter Tracks (butuh `id0`/`id1`)**

     - _Firewall Manager Orientation_ → **Award SBT:** `works.fw.101`
     - _Using Pabrik Roti Protocols (Overview)_ → **Award SBT:** `works.pr.101`

   - **Hasil**: membuka dokumen kontrak, lisensi standar, dan daftar layanan ber-role.

3. The Market — Goods (fisik & digital) + Fixed Services

   Toko terkurasi untuk **produk fisik/digital** (brand Prof. NOTA, sub-brand, mitra) dan **fixed services** (mis. jaket anti AI, topi pikiran, kaos penggoda, konsultasi 1 jam, lisensi IP standar, paket Pabrik Roti).

   - **Pembayaran**: **$OiOi only** (Superchain). Jika membawa $OiOi di Tezos, tersedia **Migration Desk** (lock→mirror) dari Library/Works.
   - **Gating harga & akses**: **Role Switcher + SBT** menentukan visibilitas, harga dinamis, atau diskon partisipasi.
   - **Onboarding SKUs (butuh `id0`/`id1`)**: _Trial Pass_, _Starter Artifact_, atau _Voucher $OiOi_ → **Award SBT:** `market.101`
   - **Artefak**: item digital dapat menjadi **artefak** yang memicu jalur belajar/cerita berikutnya (dengan Award SBT spesifik).

4. The Library — Arsip & Sumber (GitHub/GitBook-sync)

   Gudang **Markdown**: **The KING’s NFTs Project**, SOP, draft, materi kuliah, riset, rilis Pabrik Roti, _working docs_ mitra, dan lain-lain. Inilah pusat rujukan; tiga aula lain selalu menaut kembali ke sini.

   - **Starter Tracks (butuh `id0`/`id1`)**

     - _Reading Pack: KING’s NFTs — Primer_ → **Award SBT:** `library.king.101`

   - **Course-like**: tuntas bab → klaim SBT → membuka bab lanjutan di aula lain.

---

### Pola Navigasi & Progres

- **Komponen UI**: Role Switcher · SBT Badge · Prereq/Award chips · Progress Meter · Claim Modal · Unlock Banner · Buy with $OiOi.
- **State machine**: _Locked_ (butuh `id0`/`id1`) → _Readable_ → _Completed_ (verifikasi tuntas) → _Claim SBT_ (on-chain ke SA).
- **Transparansi**: setiap halaman menampilkan **Prereq SBT**, **Award SBT**, serta **chainId+address** untuk token terkait (tautan explorer/registry).

---

### Kebijakan Transaksi & Akun

- **SA-centric**: EOA dapat ditautkan; aset syarat Warga-Penduduk sebaiknya dipindahkan ke SA.
- **Checkout**: **$OiOi only**; gas dapat disponsori jika syarat terpenuhi.
- **Migration Desk**: membantu perpindahan likuiditas $OiOi (Tezos → Superchain) bila diperlukan.

---

### Prinsip Pengalaman

- **Narrative-first**: setiap aula membalut materi sebagai pengalaman "masuk negara".
- **Measurable learning**: SBT = "sertifikat hidup" yang membuka jalur ekonomi/kolaborasi.
- **Ethical ops**: kontrak-dulu-baru-akses; anti-phishing/eksploitasi; rollback/denylist jika perlu.

---

## SKATESHOP.ID

### Kendaraan di The Melting Land

Di "The Story", **skateboard** adalah kendaraan terbaik menembus The Melting Land (0101). Di Realita, ia menjelma sebagai **SKATESHOP.ID**: rantai **produksi–distribusi–ritel** yang menjaga jembatan _karya ↔ tubuh_ dan _cerita ↔ jalanan_. Setiap item ritel dapat memuat **artefak/utility** yang dikenali oleh ENDHONESA (klaim SBT, akses konten, atau jalur cerita).

---

### Peran & Akses

- **SSO/SA-centric**: login SKATESHOP.ID memakai akun yang sama dengan **ENDHONESA.COM** (Smart Account; EOA/Email dapat ditaut).
- **Pembeli (customer)**: **tanpa syarat SBT** untuk menjelajah & bertransaksi.
- **Tenant (merchant)**: butuh **SBT lisensi tenant** (didapat via produk lisensi di **The Market** di ENDHONESA.COM) untuk menyiapkan toko.

---

### Main Site & Subdomain

- **Main site**: `https://skateshop.id` menjelaskan apa & bagaimana SKATESHOP.ID, plus **Directory** tenant.
- **Tenant sites**: `https://{tenant}.skateshop.id` — setiap tenant punya katalog, cart, checkout, dan dashboard sendiri.

---

### Multi-Tenant E-Commerce (Fiat-first)

- **Katalog → Cart → Checkout** standar.
- **Pengiriman**: ongkir dihitung dari alamat gudang/gerai **per-tenant** ke alamat pembeli.
- **Pembayaran**: **payment gateway fiat** (kartu/VA/QR).
- **SBT untuk pembeli**: setelah pembayaran **berhasil**, pembeli dapat **klaim SBT** (mis. `skateshop.customer.101`) ke **SA** mereka—berfungsi membuka diskon/akses di ENDHONESA.COM atau jalur "artefak aware".

---

### POS Mode (In-store = Online)

SKATESHOP.ID juga berfungsi sebagai **Point of Sale** untuk transaksi **offline** di lokasi tenant:

- Staff cukup **membuat order di web yang sama** (tenant site).
- Metode pembayaran dapat **tunai/QR/card** via gateway; pengiriman dapat **Pick-up/Carry-out** atau **Ship later**.
- Tidak ada perbedaan data antara online vs offline—semua **satu sistem**, memudahkan stok, pelaporan, dan SBT award.

---

### Onboarding Tenant (Lisensi lewat ENDHONESA.COM)

1. Calon tenant login di **SKATESHOP.ID** → diarahkan memperoleh **SBT lisensi tenant** melalui **produk lisensi** di **The Market** (ENDHONESA.COM).
2. Setelah produk tuntas & **SBT lisensi tenant** diklaim, merchant kembali ke SKATESHOP.ID untuk **menyelesaikan setup** (nama tenant, subdomain, gudang/gerai, kurir/ongkir, payment gateway, kebijakan retur).
3. Tenant aktif → dapat **dashboard**: produk, stok, order, pelanggan, laporan, pengiriman, dan pengaturan POS.

---

### Artefak-Aware Retail

- Produk dapat memuat **kode/claim link** yang memicu **klaim SBT/artefak** di ENDHONESA.COM (contoh: edisi deck tertentu membuka akses cerita atau diskon event).
- Semua klaim diarahkan ke **SA**, sehingga progres user **terukur** lintas aula.

---

### Konsistensi dengan ENDHONESA

- **Tidak ada syarat SBT untuk membeli** di SKATESHOP.ID (ritel Realita, fiat-first).
- **Ada syarat SBT untuk membuka toko (tenant)**—lisensi dibeli di **The Market** (pembayaran $OiOi), dan menghasilkan **SBT lisensi tenant** untuk setup di SKATESHOP.ID.
- SBT hasil belanja di SKATESHOP.ID dapat dipakai **mengakses/meningkatkan** jalur di ENDHONESA.COM (belajar, layanan, diskon peran).

> **Catatan implementasi singkat (non-teknis):**
>
> - SSO dengan **ENDHONESA Identity (SA-centric)**.
> - **Webhooks** dari payment gateway → "Order Paid" → **Issue SBT claim** ke SA pembeli.
> - **Rate plans** tenant & ketentuan lisensi mengikuti kebijakan di **The Market** (ENDHONESA.COM), dengan halaman rujukan lengkap di **The Library**.

---
