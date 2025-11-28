SYSTEM_ARCHITECTURE.md

# System Architecture (Public Overview)
*Eedulogy Infrastructure — Zero-Knowledge Edition*

This document describes the architecture of the Eedulogy System without
exposing any private data. It outlines the layers, flows, and safety boundaries
that enable an evolving, self-organizing knowledge graph.

---

## 1. High-Level Diagram

┌──────────────────────────┐
│  BlackBox (Private Core) │
│  - raw data              │
│  - sessions              │
│  - logs                  │
│  - encrypted snapshots   │
└───────────────┬──────────┘
│
▼
Local Tools & Engines
┌──────────────────────────┐
│  Kiro Orchestrator       │
│  Weave Engine            │
│  Web3 Engine             │
│  Density Analyzer        │
└───────────────┬──────────┘
│
▼
┌──────────────────────────┐
│   Obsidian Vault (Private) │
│   - domain notes          │
│   - world model           │
│   - schema files          │
└───────────────┬──────────┘
│
▼
┌──────────────────────────┐
│      Snapshots (Encrypted)│
│      - tar → age/gpg      │
│      - IPFS CID           │
└───────────────┬──────────┘
│
▼
┌──────────────────────────┐
│     GitHub (Public)      │
│  - code                   │
│  - docs                   │
│  - snapshot references    │
│  - public metrics         │
└──────────────────────────┘

---

## 2. Components

### **1. BlackBox (Private Device Layer)**
A 1TB external encrypted data store containing:
- Raw recordings
- Logs
- Sessions
- Semantic indexes
- Local backups
- Encrypted IPFS-ready snapshots

Acts as the **hardware-level memory**.

### **2. Obsidian Vault (Private Knowledge Layer)**
- Structured notes
- World model
- Research domains
- Integration schemas
- Temporal → Permanent conversions

Acts as the **cognitive layer**.

### **3. Engines (Computation Layer)**
- `weave` → strengthens graph structure
- `web3_engine` → domain-specific integration
- `density` → entropy & link analysis
- `kiro` → orchestrates workflows and pipelines

Acts as the **thinking module**.

### **4. Snapshot Pipeline (Encrypted)**
- Packages vault + metadata
- Encrypts using `age` or GPG
- Adds to IPFS
- Emits CID → GitHub

Acts as the **serialization module**.

### **5. GitHub (Public Interface Layer)**
- Public code
- Architecture diagrams
- Zero-knowledge documents
- Encrypted snapshot references

Acts as the **public-facing nerve ending**.

---

## 3. Data Flow Summary

### Private → Public Boundary (The Firewall)
Only **encrypted** or **derived** data crosses the boundary.

Raw → Processed → Structured → Encrypted → Published

### Example Flow:
1. Eetu works in Obsidian  
2. weave/kiro update local topology  
3. Snapshot pipeline extracts & encrypts  
4. IPFS stores ciphertext  
5. GitHub stores CID and documentation  

---

## 4. Security Invariants

Regardless of evolution:

- **No raw data leaves BlackBox or Obsidian.**
- **Snapshots are encrypted before publication.**
- **Public repos contain structure, not content.**
- **Engines operate locally and never transmit data.**
- **Only zero-knowledge artifacts become public.**

These invariants ensure safety, privacy, and integrity.

---

## 5. Roadmap (Public Summary)

- v1.1: Introduce encrypted snapshots
- v1.2: Add architecture diagrams
- v1.3: Public SDK for weave/kiro pipelines
- v1.4: Add differential privacy to derived metrics
- v2.0: Full open-source version of the Eedulogy framework

---

*This document describes the public-facing architecture and intentionally omits private operational details.*
