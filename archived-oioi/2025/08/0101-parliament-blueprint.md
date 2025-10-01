---
description: >-
  We don't belong in your reality, your real life. In your reality, your real
  life, you can merely meet our avatars in any version. So, stay alert and
  beware of scams!
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# 0101 Parliament — Perwakilan yang Dapat Difork (Blueprint Prof. NOTA)

> **Tujuan (singkat)**  
> Ini adalah **karya civic-tech + budaya** di **Semesta 0101** (ruang digital). Dokumen ini **bukan** klaim untuk membubarkan DPR RI secara hukum.  
> Ia mendemonstrasikan—secara terbuka, damai, dan terukur—bagaimana **“kedaulatan rakyat”** dapat dipraktikkan dengan **mem-fork** sebuah **kembar-digital perwakilan** ketika legitimasi jatuh di bawah metrik yang disepakati.  
> **Kekerasan ditinggalkan. Transparansi diwajibkan.**

---

## A) Realitas Hukum Indonesia (singkat, sebagai pagar batas)

- Dalam kerangka hukum Indonesia, **tidak ada “tombol” konstitusional untuk membubarkan DPR**.  
  **UUD 1945 Pasal 7C** tegas menyatakan **Presiden tidak dapat membekukan atau membubarkan DPR**.  
  Rujukan: [UUD 1945 (MK RI) – Pasal 7C, PDF](https://mkri.id/public/content/profil/kedudukan/UUD_1945_Perubahan%204.pdf),  
  [UUD 1945 (Kominfo) – Pasal 7C, PDF](https://ppidkemkominfo.files.wordpress.com/2017/09/uud-1945-satunaskah.pdf).

- **PAW/recall anggota** diatur undang-undang (mis. **UU No. 17 Tahun 2014 – MD3**) dan bersifat **melalui partai politik**, bukan “langsung oleh rakyat.”  
  Rujukan: [Analisis recall, Pasal 239(2) UU 17/2014, PDF](https://ejournal.up45.ac.id/index.php/JHCJ/article/download/2192/1299/8097),  
  [Sistem PAW & praktik, PDF](https://jurnal.usahid.ac.id/hukum/article/download/1998/880/5332),  
  [Landasan PAW & Pasal 22B UUD 1945, PDF](https://journal.unigha.ac.id/index.php/JSH/article/download/231/279).

- **Amandemen konstitusi (Pasal 37 UUD 1945)** adalah rute formal untuk mengubah kerangka, namun politisnya berat: pengajuan oleh ≥ **1/3 MPR** dan ambang persetujuan tertentu.  
  Rujukan: [Hukumonline – Prosedur perubahan UUD 1945](https://www.hukumonline.com/klinik/a/prosedur-perubahan-uud-1945-dan-dasar-hukumnya-lt618a54773ee93/),  
  [Detik – Mekanisme & tata cara amandemen](https://news.detik.com/berita/d-5737492/ini-mekanisme-dan-tata-cara-amandemen-uud-nri-1945).

> **Kesimpulan dunia nyata**: Tidak ada jalur instan untuk “membubarkan DPR”. Yang tersedia: pemilu, PAW/recall via partai, dan amandemen UUD.  
> **Karena itu, blueprint ini adalah cermin digital yang damai**—sebuah perwakilan yang **dapat difork** untuk **mendidik, mengukur legitimasi, dan mendokumentasikan kehendak warga** tanpa klaim kekuatan hukum.

---

## B) Pendekatan Semesta 0101 — “Kembar-Digital Perwakilan”

- **Kita tidak membakar institusi; kita mengarsipkan dan mem-fork.**  
- Bangun **perwakilan publik yang dapat difork dan diaudit**, di mana “dissolve” berarti **mengarsipkan instansi berjalan** dan **memunculkan instansi baru** saat legitimasi gagal.  
- Ini adalah **seni + rekayasa + pedagogi**. Menunjukkan metodenya; tidak menghasut kekerasan atau tindakan melawan hukum.

### Prinsip Inti
1. **Tanpa kekerasan & sesuai hukum** (budaya/civic-tech/edukasi).  
2. **Aturan & data terbuka** (charter, event, dan kode transparan).  
3. **Fork-by-design** (jika legitimasi gagal, lahir instansi baru; sejarah tetap).  
4. **Anti vendor lock-in** (modular, multi-chain, mudah pindah).  
5. **Aksesibel** (pemungutan suara gasless via Account Abstraction + paymaster).

### Stack Minimum (selaras dengan proyek Prof. NOTA)
- **Frontend**: Next.js + TypeScript + Tailwind.  
- **Wallet/AA**: Thirdweb SDK v5 (embedded wallet + smart account).  
- **Rantai**: Base (L2, biaya rendah) untuk aksi publik; opsional **EVM privat (Besu/IBFT)** untuk draf deliberasi sensitif.  
- **Governance**:  
  - Voting **off-chain** terlebih dahulu (gaya Snapshot; tanda tangan EIP-712).  
  - **Adapter/registry on-chain** untuk mendaftarkan hasil final dan mengelola **status** (Active/Archived).  
- **Penyimpanan**: IPFS/Arweave + enkripsi opsional.  
- **Observabilitas**: dashboard berisi Indeks Legitimasi, tren kuorum, keunikan partisipan, dan silsilah versi.

---

## C) Mekanika “Dissolve” (di 0101)

1) **Seats-as-Tokens (SBT/ERC-1155, opsional)**  
   - “Kursi”/“Badge Pemilih” yang **non-transferable** untuk pendekatan *one person, one vote* (bisa diupgrade).

2) **Indeks Legitimasi (IL)** — skor 0–1 (atau 0–10000 bps) dari metrik publik, misal:  
   - **QuorumRate** = votes / quorumTarget  
   - **UniqueParticipantsRate** = uniqueVoters / eligibleSet (atau heuristik)  
   - **Convergence** = kestabilan proporsi “ya” (mis. lintas jendela waktu)  
   - **Continuity** = kesinambungan partisipasi antar-epoch  
   Contoh formula: `IL = 0.35*QuorumRate + 0.35*UniqueParticipantsRate + 0.2*Convergence + 0.1*Continuity`

3) **Pemicu Pembubaran (DT)** — dua jalur:  
   - **DT-A (Indeks)**: `IL < ambang` secara **kontinu** selama `coolingPeriod` → arsip.  
   - **DT-B (Votum)**: proposal **#DISSOLVE** lulus kuorum & mayoritas → arsip.

4) **Efek “Dissolve”**  
   - Set `status = ARCHIVED`; tidak menerima proposal baru; riwayat tetap dapat dibaca.  
   - Emit event `Dissolved(version, reason)`.  
   - Bot off-chain atau factory **memunculkan** `PeopleParliament_v{n+1}` dengan parameter yang diperbarui.

> **Bahasa publik**: *“Saat perwakilan digital gagal, publik **fork**—tanpa gas air mata; hanya metrik transparan dan sejarah yang diarsip.”*

---

## D) Rencana Eksekusi (ramah solo)

### Fase 0 — Bootstrap 3 hari
- Monorepo `0101-parliament`.  
- Halaman publik: `/debates`, `/vote/[proposalId]`, `/dashboard`, `/charter`.  
- **Kontrak v0** untuk status + event dissolve; voting off-chain dulu.

### Fase 1 — MVP 2 minggu
- Implement **orakel IL** (sederhana, alamat updater).  
- Terapkan **DT-A** (indeks) + **DT-B** (votum) → `status=ARCHIVED` + event.  
- Bangun **Dashboard** (grafik IL, tren kuorum, pemilih, lineage).  
- Tambah **circuit breaker** (multisig guardian dengan tanggal kedaluwarsa).

### Fase 2 — Penguatan
- **AA + Paymaster** (gasless).  
- **SBT/POAP** (heuristik anti-Sybil).  
- **Deliberasi terenkripsi** untuk draf sensitif; terbitkan ringkasan.  
- **Adapter** untuk memetakan isu dunia nyata tanpa klaim legal.

---

## E) Piagam Terbuka (1 halaman, publik)
- **Apa ini**: kembar-digital perwakilan yang **dapat difork**.  
- **Apa bukan**: bukan lembaga negara; bukan nasihat hukum; bukan ajakan tindakan melawan hukum.  
- **Aturan**: target kuorum, formula & ambang IL, kondisi DT, kebijakan fork.  
- **Etika & Lisensi**: kode terbuka, anti-ujaran kebencian, anti-kekerasan, hormati privasi.  
- **Audit Publik**: changelog, catatan pendanaan, konflik kepentingan.  
- **Semboyan**: **“Dissolve adalah fitur, bukan ancaman.”**

---

## F) Naskah Komunikasi (aman & singkat)

**ID (pendek)**  
> Kami tak mencari tank. Kami mencari **fungsi**.  
> Ketika wakil digital gagal, kami **fork**—tanpa gas air mata.  
> Kedaulatan: **fitur**, bukan slogan. #OiOi #0101

**EN (pendek)**  
> We don’t burn institutions; we **archive** and **fork**.  
> Legitimacy is open-source. Violence is deprecated. #OiOi #0101

---

## G) Risiko & Rambu
- Bukan nasihat hukum; *edukasi & budaya*.  
- Tidak mengajak tindakan kekerasan atau melawan hukum.  
- Moderasi anti-hoaks & anti-ujaran kebencian.  
- Publikasi yang menghormati privasi (agregat atau dianonimkan).

---

## H) Kerangka Solidity — `Parliament.sol` (≈120 LOC)

> Catatan: **Minimal dan edukatif**. Menggunakan pendekatan 1 alamat = 1 suara (sementara; dapat ditingkatkan ke SBT/POAP).  
> Memiliki dua jalur dissolve: **berbasis indeks** (orakel memperbarui IL) dan **berbasis votum** (#DISSOLVE lulus).

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

/// @title Parliament (Semesta 0101) - perwakilan minimal yang dapat difork
/// @notice Kontrak civic-tech edukatif. Bukan organ negara, bukan nasihat hukum.
contract Parliament {
    enum Status { Active, Archived }

    struct Proposal {
        string title;
        string uri;        // tautan ke detail/charter di IPFS/HTTP
        uint256 yes;
        uint256 no;
        uint256 deadline;  // unix time
        bool executed;
        mapping(address => bool) voted;
    }

    address public owner;
    address public oracle;          // pengubah Indeks Legitimasi (IL)
    Status public status;
    uint256 public version;
    uint256 public quorum;          // minimum total suara yang disyaratkan
    uint16  public liBps;           // 0..10000 (basis points) representasi IL
    uint16  public liThresholdBps;  // ambang IL untuk auto-dissolve
    uint256 public liLastUpdated;
    uint256 public liCoolingPeriod; // detik
    uint256 public proposalCount;

    mapping(uint256 => Proposal) private _proposals;

    event Proposed(uint256 indexed id, string title, string uri, uint256 deadline);
    event Voted(uint256 indexed id, address indexed voter, bool support, uint256 weight);
    event Finalized(uint256 indexed id, bool passed);
    event LegitimacyUpdated(uint16 liBps);
    event Dissolved(uint256 indexed version, string reason);

    modifier onlyOwner() { require(msg.sender == owner, "bukan pemilik"); _; }
    modifier onlyOracle() { require(msg.sender == oracle, "bukan orakel"); _; }
    modifier active() { require(status == Status.Active, "sudah diarsip"); _; }

    constructor(
        uint256 _version,
        uint256 _quorum,
        address _oracle,
        uint16  _liThresholdBps,
        uint256 _liCoolingPeriod
    ) {
        owner = msg.sender;
        version = _version;
        quorum = _quorum;
        oracle = _oracle;
        status = Status.Active;
        liThresholdBps = _liThresholdBps;
        liCoolingPeriod = _liCoolingPeriod;
        liLastUpdated = block.timestamp;
    }

    function propose(
        string memory title,
        string memory uri,
        uint256 lifetime
    ) external active returns (uint256 id) {
        require(lifetime >= 1 hours && lifetime <= 30 days, "durasi salah");
        id = ++proposalCount;
        Proposal storage p = _proposals[id];
        p.title = title;
        p.uri = uri;
        p.deadline = block.timestamp + lifetime;
        emit Proposed(id, title, uri, p.deadline);
    }

    function vote(uint256 id, bool support) external active {
        Proposal storage p = _proposals[id];
        require(block.timestamp < p.deadline, "berakhir");
        require(!p.voted[msg.sender], "sudah memilih");
        p.voted[msg.sender] = true;
        uint256 weight = 1; // placeholder: 1 alamat = 1 suara (tingkatkan dengan SBT/POAP nanti)
        if (support) p.yes += weight;
        else p.no += weight;
        emit Voted(id, msg.sender, support, weight);
    }

    function finalize(uint256 id) external active returns (bool passed) {
        Proposal storage p = _proposals[id];
        require(block.timestamp >= p.deadline, "belum berakhir");
        require(!p.executed, "sudah dieksekusi");
        require(p.yes + p.no >= quorum, "tidak kuorum");
        p.executed = true;
        passed = p.yes > p.no;
        emit Finalized(id, passed);
    }

    /// @notice Orakel mengirim IL terbaru (0..10000 bps)
    function updateLegitimacy(uint16 _liBps) external onlyOracle active {
        require(_liBps <= 10000, "bps");
        liBps = _liBps;
        liLastUpdated = block.timestamp;
        emit LegitimacyUpdated(_liBps);
    }

    /// @notice Dissolve karena IL di bawah ambang melewati cooling period
    function dissolveByIndex() public active {
        require(liBps > 0 && liBps < liThresholdBps, "IL masih aman");
        require(block.timestamp >= liLastUpdated + liCoolingPeriod, "masih cooling");
        _archive("otomatis: IL di bawah ambang");
    }

    /// @notice Dissolve lewat proposal (mis. #DISSOLVE) yang lulus setelah finalize()
    function dissolveByVote(uint256 id) public active {
        Proposal storage p = _proposals[id];
        require(p.executed, "belum dieksekusi");
        require(p.yes > p.no, "tidak lulus");
        _archive("votum: proposal disetujui");
    }

    function _archive(string memory reason) internal {
        status = Status.Archived;
        emit Dissolved(version, reason);
    }

    // --- pengaturan admin (dengan transparansi off-chain) ---
    function setOracle(address _oracle) external onlyOwner { oracle = _oracle; }
    function setQuorum(uint256 q) external onlyOwner { quorum = q; }
    function setLiThreshold(uint16 bps) external onlyOwner { require(bps <= 10000, "bps"); liThresholdBps = bps; }
    function setLiCoolingPeriod(uint256 s) external onlyOwner { liCoolingPeriod = s; }

    // --- tampilan (view) ---
    function getProposal(uint256 id)
        external view
        returns (string memory title, string memory uri, uint256 yes, uint256 no, uint256 deadline, bool executed)
    {
        Proposal storage p = _proposals[id];
        return (p.title, p.uri, p.yes, p.no, p.deadline, p.executed);
    }
}
```

---

## I) Pseudocode IL/DT (referensi)

```txt
# Metrik berjendela (epoch = 7 hari)

Untuk setiap epoch t:
  quorumRate_t   = min(1.0, votes_t / quorumTarget)
  uniqueRate_t   = min(1.0, uniqueVoters_t / eligibleHeuristic_t)
  converge_t     = 1 - |0.5 - yesShare_t| * 2      # dekat ke 0.5 atau 1.0 (pilih kebijakan)
  continuity_t   = min(1.0, participants_t_minus_1 ∩ participants_t / participants_t)

IL_t = 0.35*quorumRate_t + 0.35*uniqueRate_t + 0.20*converge_t + 0.10*continuity_t
IL_bps_t = floor(IL_t * 10000)

# Pemicu Dissolve A (berbasis indeks)
if IL_bps_t < threshold_bps untuk durasi kontinu >= cooling_period:
    contract.updateLegitimacy(IL_bps_t)
    contract.dissolveByIndex()

# Pemicu Dissolve B (berbasis votum)
if proposal.type == DISSOLVE dan finalize(proposal) == lulus:
    contract.dissolveByVote(proposal.id)
```

> Implementasi perhitungan IL dilakukan **off-chain** dengan kode sumber terbuka; publikasikan input, output, dan tanda tangan dari alamat `oracle` ke publik.

---

## J) Struktur Next.js (MVP)

```txt
0101-parliament/
├─ app/
│  ├─ page.tsx
│  ├─ charter/page.tsx
│  ├─ dashboard/page.tsx
│  ├─ debates/page.tsx
│  └─ vote/[id]/page.tsx
├─ components/
│  ├─ ParliamentCard.tsx
│  ├─ ProposalForm.tsx
│  ├─ VoteButton.tsx
│  └─ LIWidget.tsx
├─ lib/
│  ├─ web3.ts            # thirdweb client, chains
│  ├─ parliament.ts      # helper baca/tulis (getProposal, propose, vote, dissolve)
│  ├─ legitimacy.ts      # fetcher IL/verifikator tanda tangan
│  └─ snapshot.ts        # integrasi voting off-chain (opsional)
├─ contracts/
│  ├─ Parliament.sol
│  └─ addresses.ts       # alamat deployment / versi
├─ public/
│  └─ charter.md
├─ README.md
└─ LICENSE
```

Contoh tipe helper TypeScript untuk `lib/parliament.ts`:

```ts
export type ProposalView = {
  id: number;
  title: string;
  uri: string;
  yes: bigint;
  no: bigint;
  deadline: number;
  executed: boolean;
};

export async function getProposal(id: number): Promise<ProposalView> { /* ... */ }
export async function propose(title: string, uri: string, ttlHours: number): Promise<number> { /* ... */ }
export async function vote(id: number, support: boolean): Promise<void> { /* ... */ }
export async function dissolveByIndex(): Promise<void> { /* ... */ }
export async function dissolveByVote(id: number): Promise<void> { /* ... */ }
```

---

## K) Referensi (dipilih)

- **UUD 1945 – Pasal 7C (Presiden tidak dapat membubarkan DPR)**:  
  MK RI (PDF): https://mkri.id/public/content/profil/kedudukan/UUD_1945_Perubahan%204.pdf  
  Kominfo (PDF): https://ppidkemkominfo.files.wordpress.com/2017/09/uud-1945-satunaskah.pdf

- **PAW / Recall oleh partai (UU 17/2014 MD3)**:  
  Analisis hak recall (Pasal 239(2)) – UP45 (PDF): https://ejournal.up45.ac.id/index.php/JHCJ/article/download/2192/1299/8097  
  Sistem PAW & praktik – USAHID (PDF): https://jurnal.usahid.ac.id/hukum/article/download/1998/880/5332  
  Landasan PAW (Pasal 22B UUD) – UNIGHA (PDF): https://journal.unigha.ac.id/index.php/JSH/article/download/231/279

- **Amandemen Konstitusi (Pasal 37 UUD 1945)**:  
  Hukumonline: https://www.hukumonline.com/klinik/a/prosedur-perubahan-uud-1945-dan-dasar-hukumnya-lt618a54773ee93/  
  Detik: https://news.detik.com/berita/d-5737492/ini-mekanisme-dan-tata-cara-amandemen-uud-nri-1945

---

### Pengingat Akhir
Blueprint ini **damai**, **edukatif**, dan **sumber-terbuka**. Ia menghormati hukum Indonesia, sekaligus memberi warga cermin digital yang **dapat difork** untuk mempraktikkan akuntabilitas dan pengambilan keputusan kolektif.

> **Semboyan**: *“Dissolve adalah fitur, bukan ancaman.”* — **Prof. NOTA**

---
---

# 0101 Parliament — Forkable Representation (Prof. NOTA Blueprint)

> **Purpose (tl;dr)**  
> This is a **civic-tech + cultural work** in the **0101 Universe** (digital space). It does **not** claim to dissolve Indonesia’s DPR in real life.  
> Instead, it demonstrates—openly, peacefully, and measurably—how **“sovereignty of the people”** can be exercised by **forking** a **digital twin of representation** when legitimacy falls below agreed metrics.  
> **Violence is deprecated. Transparency is mandatory.**

---

## A) Legal Reality (brief, to set the boundary)

- In Indonesia’s real legal framework, **there is no constitutional “button” to dissolve DPR**.  
  The **1945 Constitution, Article 7C** explicitly states the **President cannot freeze or dissolve DPR**.  
  See: [UUD 1945 (MK RI) – Pasal 7C, PDF](https://mkri.id/public/content/profil/kedudukan/UUD_1945_Perubahan%204.pdf),  
  [UUD 1945 (Kominfo) – Pasal 7C, PDF](https://ppidkemkominfo.files.wordpress.com/2017/09/uud-1945-satunaskah.pdf).

- **Member replacement/recall (PAW)** is regulated by statute (e.g., **UU No. 17 Tahun 2014 – MD3**); recall is **party-driven**, not “direct by the people.”  
  See: [Analisis Recall, Pasal 239(2) UU 17/2014, PDF](https://ejournal.up45.ac.id/index.php/JHCJ/article/download/2192/1299/8097),  
  [Sistem PAW & praktiknya, PDF](https://jurnal.usahid.ac.id/hukum/article/download/1998/880/5332),  
  [Landasan PAW & Pasal 22B UUD 1945, PDF](https://journal.unigha.ac.id/index.php/JSH/article/download/231/279).

- **Constitutional amendment (Pasal 37 UUD 1945)** is the formal route to change the framework and is politically arduous: requires proposal by ≥ **1/3 MPR** and approval thresholds.  
  See: [Hukumonline – Prosedur perubahan UUD 1945](https://www.hukumonline.com/klinik/a/prosedur-perubahan-uud-1945-dan-dasar-hukumnya-lt618a54773ee93/),  
  [Detik – Mekanisme & tata cara amandemen](https://news.detik.com/berita/d-5737492/ini-mekanisme-dan-tata-cara-amandemen-uud-nri-1945).

> **Conclusion for IRL**: There is **no immediate legal path** to “dissolve DPR”. What exists: elections, party-driven recall/PAW, and constitutional amendment.  
> **Therefore this blueprint is a digital, peaceful mirror**—a *forkable* representation to **educate, measure legitimacy, and document civic will** without claiming legal force.

---

## B) The 0101 Universe Approach — “Digital Twin of Representation”

- **We don’t burn institutions; we archive and fork.**  
- Build a **public, forkable, audit-able** representation where “dissolve” means **archive current instance** and **spawn a new one** when legitimacy fails.  
- This is **art + engineering + pedagogy**. It shows the method; it does not incite violence or illegal acts.

### Core Principles
1. **Non-violence & legality** (cultural/civic-tech/education).  
2. **Open rules & open data** (transparent charter, events, and code).  
3. **Fork-by-design** (if legitimacy falls, a new instance is born; history remains).  
4. **Anti vendor lock-in** (modular, multi-chain-capable).  
5. **Accessible UX** (gasless voting via AA + paymaster, light clients).

### Minimum Stack (aligned with Prof. NOTA projects)
- **Frontend**: Next.js + TypeScript + Tailwind.  
- **Wallet/AA**: Thirdweb SDK v5 (embedded wallet + smart account).  
- **Chain**: Base (L2, low fees) for public actions; optionally **private EVM (Besu/IBFT)** for sensitive deliberation logs.  
- **Governance**:  
  - Off-chain voting first (Snapshot-like; EIP-712 signatures).  
  - On-chain **adapter/registry** to register finalized results and manage **status** (Active/Archived).  
- **Storage**: IPFS/Arweave + optional encryption for sensitive drafts.  
- **Observability**: dashboard with legitimacy index, quorum trend, voter uniqueness, and version lineage.

---

## C) Mechanics of “Dissolve” (in 0101)

1) **Seats-as-Tokens (optional SBT/ERC-1155)**  
   - Non-transferable “Seats” or “Voting Badges” to enforce one-person-one-vote heuristics (upgradeable later).

2) **Legitimacy Index (LI)** — a 0–1 score (or 0–10000 bps) computed from public metrics, e.g.:  
   - **QuorumRate** = votes / quorumTarget  
   - **UniqueParticipantsRate** = uniqueVoters / eligibleSet (or heuristics)  
   - **Convergence** = yes/(yes+no) stability across time windows  
   - **Continuity** = participation in consecutive epochs  
   Example: `LI = 0.35*QuorumRate + 0.35*UniqueParticipantsRate + 0.2*Convergence + 0.1*Continuity`

3) **Dissolve Triggers (DT)** — two pathways:  
   - **DT-A (Index)**: `LI < threshold` continuously for `coolingPeriod` → archive.  
   - **DT-B (Vote)**: a special **#DISSOLVE** proposal passes quorum & majority → archive.

4) **Effect of Dissolve**  
   - Set `status = ARCHIVED`; prevent new proposals; keep read-only history.  
   - Emit `Dissolved(version, reason)` event.  
   - Off-chain bot or factory **spawns** `PeopleParliament_v{n+1}` with updated parameters.

> **Public phrasing**: *“When digital representation fails, the public **forks**—no tear gas, no violence; only transparent metrics and archived history.”*

---

## D) Solo-Friendly Execution Plan

### Phase 0 — 3 days bootstrap
- Monorepo `0101-parliament`.  
- Public pages: `/debates`, `/vote/[proposalId]`, `/dashboard`, `/charter`.  
- **Contract v0** for status + dissolve events; off-chain voting first.

### Phase 1 — 2 weeks MVP
- Implement **LI oracle** (simple, address-based updater).  
- Enforce **DT-A** (index) + **DT-B** (vote) → `status=ARCHIVED` and event emission.  
- Build **Dashboard** (LI chart, quorum trend, voters, lineage).  
- Add **circuit breaker** (guardian multisig with sunset date).

### Phase 2 — Hardening
- **AA + Paymaster** for gasless.  
- **SBT/POAP** gate (anti-Sybil heuristic).  
- **Encrypted deliberation** for sensitive drafts; publish summaries.  
- **Adapters** to map real-world issues without legal claims.

---

## E) Open Charter (1-page, public)
- **What this is**: a digital twin (forkable) of representation.  
- **What this is not**: not a state organ; not legal advice; not a call for unlawful action.  
- **Rules**: quorum target, LI formula & threshold, DT conditions, fork policy.  
- **Ethics & License**: open code, no hate speech, anti-violence, privacy-respect.  
- **Public Audit**: changelog, funding notes, conflicts of interest.  
- **Motto**: **“Dissolve is a feature, not a threat.”**

---

## F) Communication Scripts (safe, concise)

**ID (short)**  
> Kami tak mencari tank. Kami mencari **fungsi**.  
> Ketika wakil digital gagal, kami **fork**—tanpa gas air mata.  
> Kedaulatan: **fitur**, bukan slogan. #OiOi #0101

**EN (short)**  
> We don’t burn institutions; we **archive** and **fork**.  
> Legitimacy is open-source. Violence is deprecated. #OiOi #0101

---

## G) Risks & Guardrails
- Not legal advice; *education & culture only*.  
- No calls for violence or unlawful behavior.  
- Anti-hoax & anti-hate moderation.  
- Privacy-respecting publication (aggregate or anonymized metrics).

---

## H) Solidity Skeleton — `Parliament.sol` (≈120 LOC)

> Notes: **Minimal, educational**. Uses a simple address-based, 1 person = 1 vote placeholder (upgrade with SBT/POAP later).  
> Has two dissolve paths: **index-based** (oracle updates LI) and **vote-based** (#DISSOLVE proposal).

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

/// @title Parliament (0101 Universe) - minimal forkable representation
/// @notice Educational civic-tech contract. Not a state organ, not legal advice.
contract Parliament {
    enum Status { Active, Archived }

    struct Proposal {
        string title;
        string uri;        // link to details/charter on IPFS/HTTP
        uint256 yes;
        uint256 no;
        uint256 deadline;  // unix time
        bool executed;
        mapping(address => bool) voted;
    }

    address public owner;
    address public oracle;          // updater for legitimacy index (LI)
    Status public status;
    uint256 public version;
    uint256 public quorum;          // minimum total votes required
    uint16  public liBps;           // 0..10000 (basis points)
    uint16  public liThresholdBps;  // LI threshold for auto-dissolve
    uint256 public liLastUpdated;
    uint256 public liCoolingPeriod; // seconds
    uint256 public proposalCount;

    mapping(uint256 => Proposal) private _proposals;

    event Proposed(uint256 indexed id, string title, string uri, uint256 deadline);
    event Voted(uint256 indexed id, address indexed voter, bool support, uint256 weight);
    event Finalized(uint256 indexed id, bool passed);
    event LegitimacyUpdated(uint16 liBps);
    event Dissolved(uint256 indexed version, string reason);

    modifier onlyOwner() { require(msg.sender == owner, "not owner"); _; }
    modifier onlyOracle() { require(msg.sender == oracle, "not oracle"); _; }
    modifier active() { require(status == Status.Active, "archived"); _; }

    constructor(
        uint256 _version,
        uint256 _quorum,
        address _oracle,
        uint16  _liThresholdBps,
        uint256 _liCoolingPeriod
    ) {
        owner = msg.sender;
        version = _version;
        quorum = _quorum;
        oracle = _oracle;
        status = Status.Active;
        liThresholdBps = _liThresholdBps;
        liCoolingPeriod = _liCoolingPeriod;
        liLastUpdated = block.timestamp;
    }

    function propose(
        string memory title,
        string memory uri,
        uint256 lifetime
    ) external active returns (uint256 id) {
        require(lifetime >= 1 hours && lifetime <= 30 days, "lifetime out of range");
        id = ++proposalCount;
        Proposal storage p = _proposals[id];
        p.title = title;
        p.uri = uri;
        p.deadline = block.timestamp + lifetime;
        emit Proposed(id, title, uri, p.deadline);
    }

    function vote(uint256 id, bool support) external active {
        Proposal storage p = _proposals[id];
        require(block.timestamp < p.deadline, "ended");
        require(!p.voted[msg.sender], "voted");
        p.voted[msg.sender] = true;
        uint256 weight = 1; // placeholder: 1 person, 1 vote
        if (support) p.yes += weight;
        else p.no += weight;
        emit Voted(id, msg.sender, support, weight);
    }

    function finalize(uint256 id) external active returns (bool passed) {
        Proposal storage p = _proposals[id];
        require(block.timestamp >= p.deadline, "not ended");
        require(!p.executed, "executed");
        require(p.yes + p.no >= quorum, "no quorum");
        p.executed = true;
        passed = p.yes > p.no;
        emit Finalized(id, passed);
    }

    /// @notice Oracle pushes updated legitimacy index (0..10000 bps)
    function updateLegitimacy(uint16 _liBps) external onlyOracle active {
        require(_liBps <= 10000, "bps");
        liBps = _liBps;
        liLastUpdated = block.timestamp;
        emit LegitimacyUpdated(_liBps);
    }

    /// @notice Dissolve due to index falling below threshold for the cooling period
    function dissolveByIndex() public active {
        require(liBps > 0 && liBps < liThresholdBps, "LI ok");
        require(block.timestamp >= liLastUpdated + liCoolingPeriod, "cooling");
        _archive("auto: LI below threshold");
    }

    /// @notice Dissolve via a proposal (e.g., #DISSOLVE) that passed after finalize()
    function dissolveByVote(uint256 id) public active {
        Proposal storage p = _proposals[id];
        require(p.executed, "not executed");
        require(p.yes > p.no, "not passed");
        _archive("vote: proposal passed");
    }

    function _archive(string memory reason) internal {
        status = Status.Archived;
        emit Dissolved(version, reason);
    }

    // --- admin setters (with off-chain transparency) ---
    function setOracle(address _oracle) external onlyOwner { oracle = _oracle; }
    function setQuorum(uint256 q) external onlyOwner { quorum = q; }
    function setLiThreshold(uint16 bps) external onlyOwner { require(bps <= 10000, "bps"); liThresholdBps = bps; }
    function setLiCoolingPeriod(uint256 s) external onlyOwner { liCoolingPeriod = s; }

    // --- views ---
    function getProposal(uint256 id)
        external view
        returns (string memory title, string memory uri, uint256 yes, uint256 no, uint256 deadline, bool executed)
    {
        Proposal storage p = _proposals[id];
        return (p.title, p.uri, p.yes, p.no, p.deadline, p.executed);
    }
}
```

---

## I) LI/DT Pseudocode (reference)

```txt
# Windowed metrics (epoch = 7 days)

For each epoch t:
  quorumRate_t   = min(1.0, votes_t / quorumTarget)
  uniqueRate_t   = min(1.0, uniqueVoters_t / eligibleHeuristic_t)
  converge_t     = 1 - |0.5 - yesShare_t| * 2         # closer to 0.5 or 1.0 (choose policy)
  continuity_t   = min(1.0, participants_t_minus_1 ∩ participants_t / participants_t)

LI_t = 0.35*quorumRate_t + 0.35*uniqueRate_t + 0.20*converge_t + 0.10*continuity_t
LI_bps_t = floor(LI_t * 10000)

# Dissolve Trigger A (Index-based)
if LI_bps_t < threshold_bps for continuous duration >= cooling_period:
    contract.updateLegitimacy(LI_bps_t)
    contract.dissolveByIndex()

# Dissolve Trigger B (Vote-based)
if proposal.type == DISSOLVE and finalize(proposal) == passed:
    contract.dissolveByVote(proposal.id)
```

> Implement the LI computation off-chain with open-source code and publish: inputs, outputs, and signatures from the `oracle` address.

---

## J) Next.js Structure (MVP)

```txt
0101-parliament/
├─ app/
│  ├─ page.tsx
│  ├─ charter/page.tsx
│  ├─ dashboard/page.tsx
│  ├─ debates/page.tsx
│  └─ vote/[id]/page.tsx
├─ components/
│  ├─ ParliamentCard.tsx
│  ├─ ProposalForm.tsx
│  ├─ VoteButton.tsx
│  └─ LIWidget.tsx
├─ lib/
│  ├─ web3.ts            # thirdweb client, chains
│  ├─ parliament.ts      # read/write helpers (getProposal, propose, vote, dissolve)
│  ├─ legitimacy.ts      # LI fetcher/signature verifier
│  └─ snapshot.ts        # off-chain voting integration (optional)
├─ contracts/
│  ├─ Parliament.sol
│  └─ addresses.ts       # deployed addresses / versions
├─ public/
│  └─ charter.md
├─ README.md
└─ LICENSE
```

Optional TypeScript helper signature for `lib/parliament.ts`:

```ts
export type ProposalView = {
  id: number;
  title: string;
  uri: string;
  yes: bigint;
  no: bigint;
  deadline: number;
  executed: boolean;
};

export async function getProposal(id: number): Promise<ProposalView> { /* ... */ }
export async function propose(title: string, uri: string, ttlHours: number): Promise<number> { /* ... */ }
export async function vote(id: number, support: boolean): Promise<void> { /* ... */ }
export async function dissolveByIndex(): Promise<void> { /* ... */ }
export async function dissolveByVote(id: number): Promise<void> { /* ... */ }
```

---

## K) References (selected)

- **UUD 1945 – Pasal 7C (President cannot dissolve DPR)**:  
  MK RI (PDF): https://mkri.id/public/content/profil/kedudukan/UUD_1945_Perubahan%204.pdf  
  Kominfo (PDF): https://ppidkemkominfo.files.wordpress.com/2017/09/uud-1945-satunaskah.pdf

- **PAW / Recall by political parties (UU 17/2014 MD3)**:  
  Analisis hak recall (Pasal 239(2)) – UP45 (PDF): https://ejournal.up45.ac.id/index.php/JHCJ/article/download/2192/1299/8097  
  Sistem PAW & praktiknya – USAHID (PDF): https://jurnal.usahid.ac.id/hukum/article/download/1998/880/5332  
  Landasan PAW (Pasal 22B UUD) – UNIGHA (PDF): https://journal.unigha.ac.id/index.php/JSH/article/download/231/279

- **Constitutional Amendment (Pasal 37 UUD 1945)**:  
  Hukumonline: https://www.hukumonline.com/klinik/a/prosedur-perubahan-uud-1945-dan-dasar-hukumnya-lt618a54773ee93/  
  Detik: https://news.detik.com/berita/d-5737492/ini-mekanisme-dan-tata-cara-amandemen-uud-nri-1945

---

### Final Reminder
This blueprint is **peaceful**, **educational**, and **open-source**. It respects Indonesian law while giving citizens a transparent, forkable **digital mirror** to practice accountability and collective decision-making.

> **Motto**: *“Dissolve is a feature, not a threat.”* — **Prof. NOTA**

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
