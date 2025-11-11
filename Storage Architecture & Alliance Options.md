# EverMedia Vault Storage Architecture & Alliance Options

## 1. Overview
This document outlines the dual storage and participation models adopted by EverMedia Vault, enabling both automatic pinning (managed) and direct SP matching (customized).

## 2. Background
EverMedia Vault functions as an open data alliance that facilitates verifiable content storage on IPFS and Filecoin.  
To balance accessibility and flexibility for alliance members, two complementary mechanisms are introduced.

## 3. Storage Modes

### 3.1 Managed Pinning (托管撮合)
- **Description:** Members upload files via the Vault upload service, which automatically pins data to IPFS and creates verified Filecoin storage deals.
- **Use Cases:** Fast onboarding, small or medium contributors, media outlets.
- **Pros:**
  - Minimal setup required  
  - Immediate CID + DealID return  
  - Suitable for lightweight or public data  
- **Cons:**
  - No direct SP choice  
  - Standardized SLA and pricing  

### 3.2 Direct SP Matching (自选SP)
- **Description:** Members specify or apply for partnerships with verified Storage Providers. The Vault backend facilitates matching and contract signing.
- **Use Cases:** Institutional data contributors, DAO archives, partners requiring retrieval guarantees.
- **Pros:**
  - Full control over SP selection, region, SLA, and pricing  
  - Contract-based collaboration  
- **Cons:**
  - Requires more coordination and due diligence  

## 4. Comparative Summary

| Dimension | Managed Pinning | Direct SP Matching |
|------------|----------------|--------------------|
| Setup Time | Fast (minutes) | Moderate (days) |
| Flexibility | Low | High |
| Verification | Automatic (via pin API) | Manual + Contract |
| Cost Control | Fixed rate | Negotiable |
| Retrieval Guarantee | Basic | SLA-based |
| Suitable For | Media, individuals | Institutions, DAOs |

## 5. Integration Plan
Both modes share a unified front-end submission interface and output registry format.  
Each registry entry includes a `storage.mode` flag.

### Example
```json
"storage": {
  "mode": "direct",
  "dealId": "1234567",
  "provider": "f03385456",
  "verified": true,
  "region": "APAC",
  "references": [
    {"type":"sp_contract","cid":"bafycontract..."},
    {"type":"test_report","cid":"bafyreport..."}
  ]
}
```

## 6. Retrieval Mechanism and Applicability

### 6.1 What “Retrieval” Means
In the Filecoin ecosystem, **retrieval** refers to the process of fetching stored data back from a Storage Provider (SP) after it has been sealed and stored.  
Unlike IPFS, Filecoin separates **storage** (long-term archiving) from **retrieval** (downloading for reuse or verification).

### 6.2 Retrieval in Managed Pinning Mode
- When data is uploaded via pin services (e.g., Filecoin Cloud, web3.storage), it is stored in **cold storage**.  
- Retrieval speed is slow, and these services are optimized for **archival**, not real-time access.  
- This is acceptable for EverMedia Vault’s initial milestones, where only metadata and CID exposure are required.

**Conclusion:** Retrieval is *not required* for Managed Pinning mode in Milestone 1–2.

### 6.3 Retrieval in Direct SP Mode
- In Direct SP mode, partners may need faster or verifiable access to their stored content.  
- Retrieval becomes important when:
  - Data is used for validation or integrity testing.
  - DAO or enterprise contributors require proof-of-storage or regular access.
  - SPs provide SLA-based retrieval guarantees.
- Retrieval can be achieved through:
  1. **IPFS Gateway Retrieval:** via `https://ipfs.io/ipfs/<CID>` for light validation.  
  2. **Lotus/FOC Retrieval API:** for contract-based, monitored retrieval.  
  3. **PDP (Proof of Data Possession):** cryptographic verification that data remains intact on the SP.

**Conclusion:** Retrieval is *optional but recommended* for Direct SP mode starting from Milestone 3.

### 6.4 Governance Implications
- Managed Pinning: prioritizes ease of onboarding and open contribution.  
- Direct SP: adds verifiable guarantees, retrieval tests, and SLA transparency.  
- Both will be unified in reporting — retrieval data (if available) will appear as part of `storage.health` metrics.

Example:
```json
"health": {
  "last_check": "2025-11-11T03:00:00Z",
  "retrieval_ok": true,
  "p95_ms": 780,
  "availability_7d": 0.998
}
```

## 7. Adjustment on SP Engagement Plan
During Milestone 1, the EverMedia Vault team focused on validating the managed pinning mechanism and end-to-end data proof process.  
Based on the updated technical architecture, the Vault now integrates with Filecoin Pin Cloud for automated CID generation and verification.  
As a result, the direct SP engagement workflow (and corresponding contract template) has been postponed to later milestones, when the dual-track storage model (Managed Pinning + Direct SP Matching) becomes active.  

This adjustment ensures that the early-stage deliverables remain verifiable and open-sourced, while avoiding premature coordination with external Storage Providers before the technical pipeline is finalized.  

The SP contract module and matching mechanism will be included in **Milestone 2**, once the Vault frontend integrates user selection and SP registry capabilities.

## 8. Governance Implications
- The **Managed Pinning** mode lowers barriers for community participation, ensuring fast inclusion and visibility.  
- The **Direct SP** mode strengthens the alliance’s credibility through professionalized data management and transparent contracts.  
- Both models converge into a unified transparency layer through the Vault’s `registry.json` and monthly reporting system.

## 9. Future Outlook
In Milestone 2–3:
- Extend the Direct SP pathway into a semi-automated “deal proposal” interface.
- Introduce an SP reputation and performance dashboard.
- Support retrieval monitoring and SLA scoring.
- Implement opt-in pricing visibility and cost metrics.

---

**File Location Recommendation:**
```
/docs/
 ├── media-data-standard.md
 ├── evermedia-alliance.md
 └── storage-architecture-and-alliance-options.md
