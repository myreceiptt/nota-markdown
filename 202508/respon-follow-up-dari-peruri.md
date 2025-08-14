# Tanggapan & Jawaban Pertanyaan Follow-Up dari Peruri

## 1. Konsensus Blockchain idealnya pakai apa?
**Pertanyaan:**  
Konsensus blockchain idealnya pakai apa? Tadi sudah dijelaskan bisa pakai Base, tapi Peruri ingin setup Private Chain.

**Jawaban:**  
Kita akan menggunakan **Fully Private Blockchain** yang di-deploy **on-premises** di lingkungan Peruri.  
- Keunggulan:
  - Kontrol penuh terhadap data & infrastruktur.
  - Validator terbatas sehingga keamanan dan governance lebih mudah diatur.
  - Gas fee dapat diminimalisir hingga 0.
- Kekurangan dibanding public chain:
  - Interoperabilitas eksternal lebih terbatas (namun ini tidak menjadi masalah untuk use case internal).
  - Skalabilitas jaringan bergantung pada sumber daya internal.

---

## 2. Plus minus private chain vs public chain
**Pertanyaan:**  
Apa plus minusnya private chain dan public chain?

**Jawaban:**
- **Private Chain**:
  - **Plus:** Akses terbatas, kontrol penuh, gas fee minim/nol, data tetap dalam lingkup organisasi.
  - **Minus:** Tidak terbuka untuk ekosistem global, integrasi eksternal memerlukan gateway khusus.
- **Public Chain**:
  - **Plus:** Validator dari ekosistem global, interoperabilitas tinggi, transparansi penuh.
  - **Minus:** Gas fee bergantung kondisi jaringan, data publik, kontrol validator lebih longgar.

---

## 3. Spek server untuk transaksi piloting 500 karyawan
**Pertanyaan:**  
Spek server untuk transaksi piloting 500 karyawan — Peruri akan pakai VM sendiri, dan PDS akan menjadi 2nd validator.

**Jawaban:**  
**Minimal requirement per node validator:**
- CPU: 4 vCPU
- RAM: 8 GB
- Storage: 200 GB SSD
- Network: 1 Gbps

**Setup HA (High Availability):**
- Peruri: 1 VM utama (validator utama)
- PDS: 1 VM cadangan (validator sekunder)

---

## 4. Peruri Connect sudah ada database, arsitekturnya seperti apa?
**Pertanyaan:**  
Peruri Connect sudah ada database, arsitekturnya seperti apa?

**Jawaban:**  
Integrasi akan memanfaatkan **API** yang disediakan Peruri Connect (format mengikuti yang tersedia, baik REST maupun GraphQL).  
- Skema database dan API mengikuti desain Peruri Connect yang sudah ada.
- Blockchain akan menyesuaikan format data yang tersedia tanpa memaksa perubahan besar.
- Fokus awal: integrasi user profile, autentikasi, dan pencatatan transaksi reward.

---

## 5. Reporting kalau di blockchain seperti apa?
**Pertanyaan:**  
Jika sudah integrasi dengan blockchain, seperti apa reporting-nya?

**Jawaban:**  
- **Pendekatan:** Middleware analytics yang mengagregasi data dari blockchain ke dashboard internal Peruri.
- Alur:
  1. Event & log dari blockchain dibaca oleh middleware.
  2. Data dinormalisasi & disimpan di analytics store.
  3. Dashboard admin/super admin menampilkan laporan real-time dan historis.
- Keuntungan: fleksibel, dapat disesuaikan formatnya, kompatibel dengan role super admin yang sudah ada.

---

## 6. Daily Quest
**Pertanyaan:**  
Daily Quest dibuat seperti Garuda Miles/Kaskus (ada sistem “cendol”).

**Jawaban:**  
- Akan menggunakan **Hybrid Tokenized Points**:
  - Perhitungan & validasi di-offchain (untuk efisiensi & anti-abuse).
  - Pencatatan kepemilikan dan saldo poin di-onchain.
- Mekanisme: setiap quest yang valid akan menghasilkan poin, poin dapat ditukar dengan benefit tertentu.

---

## 7. My Event
**Pertanyaan:**  
Event ada yang private dan public.

**Jawaban:**  
- Event akan dicatat di blockchain (Event Registry smart contract) dengan metadata akses (private/public).
- Partisipasi peserta dicatat onchain untuk transparansi & integritas data.

---

## 8. My Contribution
**Pertanyaan:**  
Masih to be discussed karena ada kaitannya dengan tim SDM.

**Jawaban:**  
- Modul My Contribution akan mengakomodasi kontribusi formal dan informal karyawan.
- Skor dan poin awalnya dihitung offchain sesuai aturan SDM, lalu dicatat onchain untuk keperluan audit dan transparansi.

---

## 9. Peruri Connect basisnya API, consumed via Web dan Mobile
**Pertanyaan:**  
Jika basisnya API, seperti apa integrasi ke blockchain?

**Jawaban:**  
- Akan dibuat **API Gateway terpisah** untuk modul blockchain:
  - Menjembatani Web/Mobile ↔ Blockchain Node.
  - Mengisolasi beban & domain keamanan dari API utama Peruri Connect.
  - Memudahkan update modul blockchain tanpa mengganggu API inti.
