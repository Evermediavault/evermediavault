# EverMedia Vault — Media & Web3 Data Standard Specification
**Version:** v1.0  
**Date:** Sep 30, 2025  
**Author:** EverMedia Vault Core Team 

---

## 1. Purpose

EverMedia Vault aims to establish an open and trusted Web3 content alliance by bringing diverse media and community data on-chain through IPFS/Filecoin.  
This document defines the unified data structure, metadata schema, and cleaning rules for all contributors of the EverMedia Vault ecosystem.

---

## 2. Scope

This standard applies to all data uploaded and stored within the EverMedia Vault platform, including but not limited to:  
- Media content (articles, images, videos)  
- DAO proposals or records  
- Community events and workshops  
- NFT metadata and related documentation  
- Other Web3-related datasets

---

## 3. Data Categories

| Category | Description | Examples |
|-----------|-------------|-----------|
| **media** | Articles, interviews, videos, and images from media outlets | reports, interviews, event photos |
| **dao** | DAO governance materials or proposals | Snapshot proposals, DAO reports |
| **event** | Records from community events, meetups, or conferences | Filecoin Builder Day, Orbit Meetup |
| **nft** | NFT project metadata, art descriptions, or smart contract data | NFT whitepaper, artwork JSON metadata |
| **other** | Any other Web3-related content | Tutorials, research datasets, documentation |

---

## 4. Data Schema

### Minimal JSON Schema
```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "EverMedia Vault Data Schema",
  "type": "object",
  "properties": {
    "title": {"type": "string"},
    "creator": {"type": "string"},
    "timestamp": {"type": "string", "format": "date-time"},
    "content_hash": {"type": "string"},
    "category": {
      "type": "string",
      "enum": ["media", "dao", "event", "nft", "other"]
    },
    "metadata": {
      "type": "object",
      "additionalProperties": true
    }
  },
  "required": ["title", "creator", "timestamp", "content_hash", "category"]
}
```

### Example Record
```json
{
  "title": "Filecoin Builder Day Hong Kong 2025 Recap",
  "creator": "Media platrom",
  "timestamp": "2025-08-18T12:00:00Z",
  "content_hash": "bafybeigdyrgh5w3qzvlbn5r6k7y6…",
  "category": "event",
  "metadata": {
    "language": "EN",
    "file_format": "PDF",
    "link": "https://ipfs.io/ipfs/bafybeigdyrgh5w3qzvlbn5r6k7y6…",
    "description": "Summary report of the Filecoin Builder Day Hong Kong 2025"
  }
}
```

---

## 5. Data Cleaning & Validation Rules

| Item | Rule |
|------|------|
| **File Naming** | Use the format `[Category]_[Title]_[Date]` (e.g., `media_FilecoinDigest_2025-08.pdf`) |
| **File Formats** | Acceptable: PDF, JPG, PNG, MP4, ZIP, JSON |
| **Metadata Fields** | Must include timestamp and creator name |
| **Duplicate Detection** | Files with identical title + creator + hash are considered duplicates |
| **Sensitive Data** | No private, confidential, or copyrighted materials |
| **Language** | English or bilingual (EN/中文), UTF-8 encoding |
| **Minimum Size** | > 1KB to avoid empty or invalid files |

---

## 6. IPFS Upload & Verification Process

### Recommended Tools
- [web3.storage](https://web3.storage)  
- [Lighthouse.storage](https://lighthouse.storage)  
- [Estuary.tech](https://estuary.tech)  
- Filecoin Onchain Cloud (FOC) Storage MCP API  

### Steps
1. Upload file using IPFS CLI or one of the listed storage APIs.  
2. Retrieve and verify the CID for accessibility.  
3. (Optional) Export CAR file and push to Storage Provider (SP) for on-chain sealing.  
4. Record CID and metadata in the `registry.json` ledger or Notion database.  

### Verification
- Check gateway access: `https://ipfs.io/ipfs/<CID>`  
- Record `CID → File Mapping` in Vault registry  
- Maintain proof of storage in deal receipts

---

## 7. Example Dataset Record Table

| Title | Creator | CID | Category | Timestamp | Size | Verified | Description |
|--------|----------|------|-----------|------------|------------|-------------|--------------|
| Filecoin Ecosystem Digest | A | bafybeig… | media | 2025-08-15 | 4.2MB | ✅ | Monthly summary |
| Orbit Builder Day Recap | B | bafybeih… | event | 2025-08-18 | 12MB | ✅ | Event recap |
| DAO Proposal #23 | C | bafybei… | dao | 2025-08-12 | 1.8MB | ❌ | Pending verification |

---

## 8. Version Control & Change Log

| Version | Date | Changes | Reviewed By |
|----------|------|----------|--------------|
| v1.0 | 2025-08-30 | Initial draft | Reviewer1 |
| v1.1 | TBD | Add new category definition | — |


---

## 9. License
All content and metadata under EverMedia Vault are shared under the **MIT License** and follow the open data principles of the Filecoin/IPFS ecosystem.

---

