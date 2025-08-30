
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
