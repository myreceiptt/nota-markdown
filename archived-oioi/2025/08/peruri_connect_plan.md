# Rencana Teknis — Peruri Connect × Blockchain (Hybrid, Tokenized, Interop)

## 0) Target & Prinsip
- **Setiap account = 1 wallet on‑chain** (di-generate/ditautkan otomatis).
- **Activity → ditokenisasi/mirrored** ke on‑chain (event, poin, badge, verifiable log).
- **Integrasi lintas app**: standar identitas & token seragam untuk Peruri ecosystem.
- **Non‑disruptive**: tetap Flutter + CI3; tambah service _adapter_ & _mirror_ tanpa bongkar core.

---

## 1) Arsitektur Tingkat Tinggi

**Flutter App (Peruri Connect)**
- Tetap call **CI3 API**.
- Tambahan: 2–3 endpoint baru (wallet status, signable payload, activity track).

**CI3 Backend (API)**
- Tambah **Blockchain Adapter Service** (BAS) sebagai microservice terpisah (Go/Node/TS).
- Event bus (Kafka/RabbitMQ) untuk **Activity Stream** → diambil oleh **Mirror Worker**.

**Blockchain Layer (Permissioned EVM)**
- **Private chain** (saran: Hyperledger Besu, konsensus IBFT2).  
  Validator: **Peruri**, **PDS**, (**Voyage/Prof. NOTA** opsional).
- **Bridging opsi** (nanti): _anchor_ hash ke public chain (Base/OP) utk notarization.

**Key/Wallet Layer**
- **Embedded/in‑app wallet** default (custodial‑enterprise; HSM/KMS).  
- Opsi _upgrade_ ke **smart account (ERC‑4337)** + **gas sponsor (paymaster)**.

---

## 2) Skema Identitas & Wallet
- `user_id (Peruri Connect)` ⇄ `did:peruri:<…>` ⇄ `wallet_address`
- **Custodial enterprise** → KMS/HSM untuk kunci privat.
- **Hybrid**: mulai custodial → _opt‑out_ non‑custodial.
- **4337 Smart Account** (opsional Fase 2).

---

## 3) Tokenisasi Aktivitas
- **PTKN** (Peruri Token; fungible).  
- **PBADGE** (Non‑fungible badge/kredensial).  
- **PLOG** (Event log/merkleroot batch).

---

## 4) Alur Data
1. Activity di App → Flutter → CI3 `/activity/track`  
2. CI3 → Activity Stream → Mirror Worker  
3. Mirror Worker → BAS → submit ke blockchain  
4. BAS → txHash → CI3 update → Flutter tampilkan status  

---

## 5) Integrasi Flutter
- Endpoint: `/wallet/status`, `/activity/track`, `/activity/:id`  
- UI minimal: Wallet aktif, Tab Token/Badge, Activity History  

---

## 6) Integrasi CI3
- Tambah auth middleware, BAS service, Mirror Worker  
- Tabel inti: `identity_map`, `activity_queue`, `token_balance_cache`, `badge_index`  

---

## 7) Private Chain — Rekomendasi & Sizing Pilot (±2000 user)
- **Besu IBFT2**, block time 2s, gasPrice ~0  
- Validator: 3 (Peruri, PDS, Voyage/Prof. NOTA)  
- **VM Sizing**:  
  - Validator: 4 vCPU, 8 GB RAM, 200 GB SSD  
  - Tx node: 4 vCPU, 8 GB RAM, 200 GB SSD  
  - BAS+Mirror: 4 vCPU, 8 GB RAM  
- Throughput kebutuhan < 10 TPS (2000 user daily)  

---

## 8) Keamanan
- HSM/KMS, JWT + mTLS, audit trail  
- PII tetap off‑chain, hash/ID terproteksi on‑chain  
- Backup & DR: snapshot genesis & key  

---

## 9) Roadmap
- **F0**: Blueprint 1–2 minggu  
- **F1**: Pilot Chain + Service 2–4 minggu  
- **F2**: Flutter + Use Case v1 2–4 minggu  
- **F3**: Interop & Anchoring (opsional)  
- **F4**: 4337 & Gasless (opsional)  

---

## 10) Contoh Kontrak & API
```solidity
function mintBadge(address to, uint256 id, uint256 amount, bytes memory data) external onlyMinter {
    _mint(to, id, amount, data);
}
function safeTransferFrom(address, address, uint256, uint256, bytes calldata) public pure override {
    revert("Non-transferable");
}
```
```json
POST /mintToken
{ "userId": "u123", "amount": "100", "reason": "attendance:2025-08-25" }
→ { "txHash": "0xabc..." }
```

---

## 11) Nilai untuk Peruri
- Minim friksi: Flutter + CI3 tetap
- Kontrol privat: private chain, validator terbatas
- Trust: immutable log, interoperable ecosystem
