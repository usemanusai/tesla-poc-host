# Project Hydra: Tesla Fleet API Security Research (PoC)

## ⚠️ Security Research Notice
This repository is part of an authorized security assessment within the **Tesla Bug Bounty Program**. It is maintained exclusively for Proof of Concept (PoC) purposes to demonstrate a "Trust Decoupling" vulnerability in the Tesla Fleet Telemetry and Command Signing infrastructure.

**ID:** `TSLA-SEC-AUDIT-2026-001`  
**Status:** Under Triage (Bugcrowd)  
**Security Level:** Restricted / Educational

---

## 🔍 Vulnerability Overview: "Trust Decoupling"
The central hypothesis of this research is that the Tesla backend architecture derives identity trust from non-cryptographic string matching and OID (Object Identifier) presence rather than strict cryptographic path validation to a hardware-tethered Root CA.

### Technical Vector
This repository hosts a forged Virtual Key artifact at a standard `.well-known` path. This setup demonstrates how an unauthorized party can stage a "Identity Masquerade" by:
1. Generating a spoofed Root CA chain mimicking Tesla's internal naming conventions.
2. Injecting proprietary OIDs (e.g., `1.3.6.1.4.1.49279.2.5.1`) into leaf certificates.
3. Using the Fleet API's domain-validation logic to whitelist a forged credential.

---

## 📂 Repository Structure (PoC Artifacts)

| Path | Purpose |
| :--- | :--- |
| `/.well-known/appspecific/` | Hosts the Virtual Key for Fleet API registration. |
| `com.tesla.3p.public-key.pem` | The generated public key used in the Trust Decoupling handshake. |
| `.nojekyll` | Configuration file to ensure GitHub Pages serves dot-folders. |
| `index.html` | Status page confirming host activity. |

---

## 🛡️ Safe Harbor & Compliance
This research adheres to the **Tesla Vulnerability Disclosure Policy (VDP)** and Bugcrowd's Standard Terms:
* **No Impact:** No live vehicles or physical hardware were impacted during this research.
* **No Data Access:** No personal or owner data was accessed or compromised.
* **Responsible Disclosure:** All findings have been reported directly to Tesla via the official Bugcrowd portal.

## 🛑 Notice to Third Parties
This repository is **NOT** for public use. Attempts to utilize these artifacts for unauthorized purposes are strictly prohibited and outside the scope of this research. This repository will be decommissioned immediately upon the conclusion of the triage and payout process.

---
*Authorized Security Researcher: @usemanusai*
