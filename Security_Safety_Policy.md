SECURITY_SAFETY_POLICY

# Security & Safety Policy  
*Zero-Knowledge Architecture — Public Documentation Layer*

This document describes how data flows through the Eedulogy System without
revealing any private content. The purpose is to show the security model,
boundaries, and operational guarantees of the system.

---

## 1. Core Principles

1. **Zero-Knowledge Exposure**  
   Public repositories must never contain identifiable, raw, or personal data.
   Only structures, schemas, and encrypted artifacts may be published.

2. **Separation of Layers**  
   - **Private Layer:** raw data, personal archives, logs, journals  
   - **Derived Layer:** anonymized aggregates, schemas, metrics  
   - **Public Layer:** code, documentation, encrypted snapshots (CID only)

3. **Minimal Attack Surface**  
   - No API keys in the repo  
   - No absolute paths to private locations  
   - No plaintext Obsidian notes or BlackBox content  

4. **Immutability & Transparency**  
   All public changes are versioned, traceable, and auditable.

---

## 2. Data Classification

### 🔒 **Private Data (Never Public)**
- Raw notes (Obsidian Vault)
- Personal recordings, audio, video
- BlackBox `/raw`, `/sessions`, `/logs` contents
- Machine-state logs
- Local metrics before aggregation
- Tokens, keys, SSH identities

### 🟡 **Derived / Semi-Public Data**
- Aggregated metrics (counts, categories, trends)
- Cryptographic hashes
- Encrypted snapshot tarballs (age/gpg)
- System-level architecture & philosophy

### 🟢 **Public Data**
- Code (Python/CLI/Web3/Weave Engine)
- Documentation (system design, schemas)
- Encrypted snapshot CIDs
- Non-sensitive metadata

---

## 3. Snapshot Safety Model

Snapshots follow a strict rule:

### **Rule: Raw snapshots must be encrypted before any CID is published.**

Pipeline:
tar → encrypt (age) → encrypted.tar → ipfs add → CID → GitHub
Guarantees:
- CID exposes **only ciphertext**, not content
- Anyone can fetch the blob, but only the private key can decrypt it
- The structure of your system is public, but the data remains private

---

## 4. GitHub Safety Requirements

### Allowed
- High-level system documentation  
- Scripts (no embedded secrets)  
- Kiro / Weave / Web3 Engines  
- Encrypted snapshot CIDs  
- Architecture diagrams  
- Public roadmap  

### Forbidden
- `.tar.gz` snapshots (unencrypted)  
- Any data from `/Volumes/BlackBox/blackbox/raw`  
- Any personal notes or journals  
- Obsidian vault content  
- SSH keys / tokens / `.env` files  
- Local machine paths that could leak information  

---

## 5. Risk Model

### Threat Vectors Considered:
- Repository scraping / automated harvesting
- Indexation of CIDs from public repos
- Exposure through misconfigured snapshot scripts
- Accidental pushes of data folders
- Time-correlated metadata reconstruction

### Mitigation:
- `.gitignore` controlled boundaries
- Encrypted snapshots only
- Hard boundary: Only derived information enters public space
- No temporal or geolocation-sensitive data published

---

## 6. Future Hardening

- Local hardware key integration (YubiKey)
- IPFS private network mode for private snapshots
- Differential privacy for analytical aggregates
- Automated scanning for sensitive patterns before commits

---

## 7. Summary

This project aims to share methodology, architecture, and tools —  
**not personal data**.

The separation between *private content* and *public structure*  
is the foundation of the system’s zero-knowledge design.

```md
*This policy evolves as the system grows. Version: 1.0 (Public Layer)*
