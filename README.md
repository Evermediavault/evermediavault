# 🌐 EverMedia Vault
**An Open Web3 Data Alliance built on Filecoin & IPFS**  

EverMedia Vault (also referred to as *EverVault*) is an open collaboration initiative that brings verified Web3 media, community, and project data on-chain.  
It provides a transparent registry of content stored on IPFS/Filecoin and showcases alliance members who contribute data to the ecosystem.

---

## 🧭 Overview

| Item | Description |
|------|--------------|
| **Goal** | Build a decentralized, verifiable data alliance bridging web3 projects content into Filecoin/IPFS. |
| **Started** | Sep 2025 |
| **X** |https://x.com/EverMediaVault |
| **Website(demo)** |http://8.130.142.163:81/|
| **Maintained by** | EverMedia Vault Core Team  |
| **Status** | Phase 1 — Initialization & Testing |
| **License** | MIT |

---

## 🏗️ Architecture Overview
```
┌──────────────────────┐
│  Contributor Data    │
│ (Media, DAO, Event)  │
└──────────┬───────────┘
           │ JSON Schema / Metadata
┌──────────▼───────────┐
│  EverMedia Vault     │
│  Registry (GitHub)   │
│  + RSS Feed Builder  │
└──────────┬───────────┘
           │
   IPFS/Filecoin Storage Deals
           │
┌──────────▼───────────┐
│ Storage Providers    │
│ (SP, FOC, etc.)      │
└──────────────────────┘
```

---

## 📁 Repository Structure
```
/docs/                      → Technical and governance documents
/docs/media-data-standard.md → Data format & schema specification
/registry.json              → Public ledger of uploaded content
/scripts/                   → Automation and RSS feed generation scripts
/public/                    → Feed, assets, and media resources
```

---

## 🧩 Data Standard
All uploads follow a unified JSON schema to ensure data consistency and traceability.  
👉 [View the Media & Web3 Data Standard Specification](./docs/media-data-standard.md)

### Minimal Example
```json
{
  "title": "Filecoin Builder Day 2025 Recap",
  "creator": "A",
  "timestamp": "2025-08-18T12:00:00Z",
  "content_hash": "bafybeigdyr...",
  "category": "event",
  "metadata": {
    "language": "EN",
    "format": "PDF"
  }
}
```

---

## 🔄 Automation & Feed System (TBD)
- Each new contribution added to `registry.json` automatically triggers:  
  - RSS feed rebuild (`/public/feed.xml`)  
  - Social post (via Zapier / IFTTT integration)  

- Feed URL:  
  ```
  https://evermedia.xyz/feed.xml
  ```
---

## 💾 Storage & Verification Partners

EverMedia Vault integrates with multiple Filecoin storage layers:

| Service | Role |
|----------|------|
| **Filecoin Onchain Cloud (FOC)** | On-chain cloud service for data persistence and compute APIs |
| **Storage Providers (SPs)** | Provide verified and long-term storage deals |
| **Lighthouse / Estuary / web3.storage** | IPFS gateway and on-ramp APIs for uploads |

Each dataset includes a verifiable record (DealID, PieceCID, Provider ID, Timestamp).

---

## 🧱 Project Phases

| Phase | Timeline | Key Deliverables | Status |
|-------|-----------|------------------|--------|
| **Phase 1** | Jun–Sep 2025 | Define data standards, select SPs, initial upload testing | 🟢 Active |
| **Phase 2** | Sep–Oct 2025 | Launch frontend, registry site, and feed system | ⏳ Upcoming |
| **Phase 3** | Oct–Dec 2025 | Expand alliance partners, optimize UX and community dashboard | 🔜 Planned |
| **Phase 4** | Dec 2025 | Publish final report and future roadmap | 🔜 Planned |

---

## 🤝 How to Contribute

1. **Fork this repository**  
2. **Add a new entry** in `registry.json` following the [data standard](./docs/media-data-standard.md)  
3. **Submit a Pull Request**  
4. The core team will verify and merge your contribution  

Early contributors will receive:
- 🎖️ *Vault Contributor* SBT badge  
- 🌍 Exposure on the [Alliance Page](https://evermedia.xyz)  
- 💬 Mention in monthly ecosystem updates  

---

## 🧾 Example Registry Entry
```json
{
  "title": "Filecoin Ecosystem Digest – August 2025",
  "creator": "A",
  "timestamp": "2025-08-20T08:00:00Z",
  "content_hash": "bafybeigdyr...",
  "category": "media",
  "metadata": {
    "language": "EN",
    "format": "PDF",
    "dealId": "1234567",
    "provider": "f03151456",
    "verified": true
  }
}
```

---

## 📊 Verification Workflow

1. Upload file to IPFS or on-ramp API  
2. Record generated CID  
3. Send CID for Filecoin deal (manual or automated via FOC/Lighthouse)  
4. Add record with DealID and SP info to `registry.json`  
5. Automation script regenerates RSS + social feed  

---
 

## 🗓️ Roadmap Highlights

- ✅ M1 — Data standard finalized  
- ✅ M2 — SP partnership & initial storage test  
- ⏳ M3 — Public registry & automation launch  
- 🔜 M4 — Alliance expansion and final reporting  

---

## 🧠 Why EverMedia Vault?

- Demonstrates **Filecoin’s usability** through real, verifiable content storage.  
- Promotes **data integrity and transparency** across Web3 media and community ecosystems.  
- Provides a **low-barrier entry** for contributors to store and showcase verified data.  
- Serves as a **hub for decentralized collaboration** — media, projects, DAOs, and researchers.  

---

## 📜 License
This project and all metadata standards are released under the [MIT License](./LICENSE).  
All contributions must comply with Filecoin’s open data principles.

