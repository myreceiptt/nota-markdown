# 🎲 NOTA BOARD GAME: Perjalanan Digital Menuju Kesadaran

> *“Ini bukan soal menang. Ini soal mengenali siapa kamu saat semua sistem tidak lagi menyembunyikanmu.”*  
> — Prof. NOTA

---

## ✨ Cerita & Filosofi

**NOTA BOARD GAME** adalah board game edukatif-satiris yang membawa para pemain dalam perjalanan sosial digital — dari kebingungan menjadi kesadaran. Setiap pemain mewakili peran dalam ekosistem digital global dan harus menghadapi kondisi, membuat pilihan, dan memengaruhi pemain lain melalui jalur menuju **Puncak Kesadaran**.

Permainan ini bukan hanya alat permainan. Ia adalah kritik, simulasi, sekaligus cermin sosial bagi siapa pun yang pernah scroll, klik, atau menyembunyikan sesuatu dari internet.

---

## 📘 Game Design Document (GDD)

### 🎭 Karakter & Peran Pemain

| Peran             | Deskripsi |
|------------------|-----------|
| The Scroller     | Konsumen pasif, doyan konten |
| The Clicker      | Impulsif, klik dulu pikir belakangan |
| The Shadow       | Anonim, mencari arah |
| The Burner       | Identitas palsu, oportunis |
| The Sovereign    | Sadar kendali data dan privasi |
| The Cipher       | Penjaga akses, simbol enkripsi |
| The Catalyst     | Pemantik ide dan perubahan |
| The Forker       | Pembuat alternatif sistem |

> 🎯 Setiap peran mulai dari titik awal yang berbeda, tapi semua menuju titik akhir: **PUNCAK KESADARAN**

---

### 🎲 Komponen Permainan

- 1 Papan permainan modular
- 1 Dadu
- 8 Token karakter
- 6 Jenis kartu:
  - 📍 KONDISI
  - ⚡ AKSI
  - 🎭 KEJUTAN
  - 🛑 RINTANGAN
  - ⭐ LEVEL UP
  - 🔒 Kartu SPESIAL *(VPN, Jalan Tikus, BackDoor, dll)*
- Token skor:
  - Biru = Kesadaran
  - Kuning = Kemandirian
  - Merah = Partisipasi
- Lembar skor pemain (semi-terbuka)

---

### 🗺️ Desain Papan Permainan

![nota-board-game](https://github.com/user-attachments/assets/336a9344-6443-45d1-b2f7-27c90041eb5e)

#### 📌 Peta papan memiliki:

- 8 titik START (satu per peran)
- Jalur bercabang dengan titik KONDISI, AKSI, KEJUTAN, RINTANGAN
- Titik SPESIAL (🔒) dan titik LEVEL UP (⭐)
- Semua jalur akhirnya bertemu di 🏁 PUNCAK KESADARAN

---

### 🔄 Aturan Dasar

1. Pemain pilih peran dan token, lalu mulai dari titik sesuai.
2. Giliran pemain:
   - Lempar dadu → pindah langkah
   - Ambil kartu sesuai titik (📍⚡🎭🛑⭐🔒)
   - Baca narasi kartu → pilih jawaban → efek skor diberlakukan
3. Skor dibagi 3: **Kesadaran**, **Kemandirian**, **Partisipasi**
4. Pemain lain bisa terkena imbas skor berdasarkan perannya.
5. Kartu SPESIAL diperoleh dari titik 🔒 atau hasil tindakan berani.

---

## 🃏 Contoh Kartu Permainan

### 📍 Kartu KONDISI #1

**Judul:** Akunmu dibekukan tanpa alasan  
**Narasi:** Semua akses hilang. Tidak ada notifikasi. Keluargamu bertanya-tanya.

**Pilihan 1:**  
_Buat akun baru dan lanjutkan hidupmu._  
- The Scroller: +1 Partisipasi  
- The Shadow: +1 Kemandirian  
- The Catalyst: -2 Kesadaran

**Pilihan 2:**  
_Tulis utas kritik dan banding._  
- The Forker: +2 Kesadaran  
- The Sovereign: +1 Kemandirian  
- The Clicker: -1 Partisipasi

---

### 📍 Kartu KONDISI #2

**Judul:** Hoax menyebar di grup keluarga  
**Narasi:** Kamu tahu itu salah, tapi tidak semua siap mendengar kebenaran.

**Pilihan 1:**  
_Berikan tautan resmi, lalu diam._  
- The Cipher: +1 Kemandirian  
- The Clicker: -1 Kesadaran  
- The Shadow: +1 Partisipasi

**Pilihan 2:**  
_Biarkan saja. Damai itu indah._  
- The Scroller: +2 Kemandirian  
- The Catalyst: -1 Partisipasi  
- The Sovereign: -1 Kesadaran

---

### ⚡ Kartu AKSI #1

**Judul:** Jadi admin grup diskusi kebijakan  
**Pilihan 1:**  
_Terima tantangan. Buat aturan._  
- The Sovereign: +2 Kemandirian  
- The Catalyst: +1 Partisipasi  
- The Forker: -1 Kesadaran

**Pilihan 2:**  
_Tolak. Tidak ingin ribet._  
- The Scroller: +1 Kemandirian  
- The Clicker: +1 Partisipasi  
- The Cipher: -1 Kesadaran

---

### 🎭 Kartu KEJUTAN #1

**Judul:** Google Drive Down selama 48 Jam  
**Efek Langsung:**  
- The Scroller: -1 Kemandirian  
- The Cipher: +2 Kesadaran  
- The Sovereign: +1 Partisipasi

---

### 🔒 Kartu SPESIAL #1 — Kartu VPN

**Narasi:** Kamu sembunyi lewat jaringan alternatif.  
**Efek:** Tukar posisi dengan pemain lain. Tambah +1 Kemandirian untuk The Cipher & The Sovereign.

---

### 🔒 Kartu SPESIAL #2 — Kartu Jalan Tikus

**Narasi:** Kamu gunakan celah birokrasi untuk lolos dari sensor.  
**Efek:** Hindari 1 efek negatif, atau lewati 1 titik RINTANGAN.

---

### 🔒 Kartu SPESIAL #3 — Kartu BackDoor

**Narasi:** Kamu menemukan pintu tersembunyi dalam sistem yang bisa kamu akses.  
**Efek:** Lempar ulang dadu. Alihkan 1 efek negatif ke peran lain.

---

## 🏁 Akhir Permainan

- Saat 1 pemain mencapai **Level 5**, semua pemain menyelesaikan giliran terakhir.
- Nilai akhir = total 3 skor + refleksi akhir
- Akhiri permainan dengan **tukar kesadaran antar pemain**, bukan sekadar menentukan pemenang

---

## 🧠 Akhir Kata dari Prof. NOTA

> *Permainan ini adalah sarana belajar, alat pengganggu sistem, dan pengingat bahwa yang tampak “biasa saja” bisa menyimpan ironi besar.*

---

