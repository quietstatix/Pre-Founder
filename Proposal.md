# Project Proposal
## Anonymous Hardware-Bound Onboarding Protocol
Author: quietstatix  
License: AGPLv3  
Contact: quietstatix@proton.me  
GitHub: https://github.com/quietstatix  

---

# 1. Summary

This project develops a new cryptographic onboarding primitive designed for decentralized systems: anonymous, hardware-bound role activation supported by a local-only behavioral consistency check (“IRWIN Candidate Mode / 3+1”) and multi-sig approval.

Current decentralized communities—including open-source governance groups, privacy-focused collectives, activists, journalists, and federated platform operators—lack a safe, identity-free method to elevate trusted participants. Existing approaches depend on reputation, centralized identity systems, or in-person key-signing ceremonies, all of which weaken anonymity, accessibility, and resilience to infiltration.

The proposed protocol (“Pre-Founder Channel”) introduces:

- anonymous, device-bound attestation  
- a Secure Package that only unlocks on the original hardware  
- a minimal local-only behavioral baseline (“3+1”)  
- a multi-sig activation process to distribute trust  
- zero-retention data handling  
- safe failure behavior (WARN → SAFE ABORT)  
- a bootstrap → stable governance transition  

The implementation will be open-source (AGPLv3), privacy-first, reproducible, and testable across x86 and ARM devices.

---

# 2. Motivation & Impact

Decentralized ecosystems lack a safe, identityless trust-onboarding mechanism. This protocol provides a foundational security building block for communities that require anonymity, resilience, and decentralized authority.

## 2.1 Open-Source Governance (Debian, Tor, QubesOS)
- anonymous trust elevation  
- hardware-bound activation  
- multi-sig approval to prevent rogue elevation  
- resistance to infiltration  

## 2.2 Journalists, Whistleblowers, and Human Rights Workers
- identity-less membership  
- hardware-anchored trust  
- local-only behavioral vetting  
- strict privacy guarantees  

## 2.3 Federated Platforms (Mastodon, Matrix)
- secure administrator onboarding  
- decentralized moderator approval  
- capture-resistant role assignment  

## 2.4 Activist & Community Organizing
- anonymous verification  
- decentralized role assignment  
- infiltration and capture resistance  

## 2.5 Distributed Developer Teams
- elevation of trusted contributors without corporate identity or reputation systems.

---

# 3. Technical Approach & Architecture

## 3.1 Pre-Founder Channel  
Anonymous, hardware-attested onboarding pipeline.

## 3.2 Hardware Fingerprint Bundle (HFB)  
Generated locally; combines CPU/SoC entropy, TPM/secure element if present, and randomized challenge-response. No raw hardware identifiers leave the device.

## 3.3 Secure Package (v1 → v3)  
Encrypted, hardware-bound role package that unlocks only when:

1. HFB matches  
2. Local behavioral baseline passes  
3. Multi-sig approval threshold is satisfied  

## 3.4 Multi-Sig Founder Activation  
Uses M-of-N approval to distribute trust and resist governance capture.

## 3.5 IRWIN Candidate Mode / 3+1 Behavioral Model

### Components:
1. **Timing Rhythm** (ephemeral pacing)  
2. **Pattern Stability** (hashed sequences only)  
3. **Local Entropy Interaction** (challenge/response)  
4. **“+1” Hardware-Verified Action** (TPM/CPU entropy match)

### Privacy:
- fully local  
- no logs  
- no storage  
- only pass/fail score  

### Security Purpose:
Prevents cloned hardware, VM impersonation, or unauthorized unlock attempts.

---

# 3.8 Operational Security Properties

## Memory Purge  
Sensitive materials zeroized immediately after use.

## Revocation  
Device-bound roles revocable via multi-sig. No identity required.

## Expiration & Renewal  
Prevents indefinite trusted status; renewal requires full checks.

## Zero-Retention Guarantee  
No identifiers, logs, or behavioral artifacts persist.

## Local Integrity Guard (WARN → SAFE ABORT)  
Detects tampering (screen capture, parallel access, exfil patterns).  
Actions:
- Local warning  
- Secure purge  
- Clean abort  
No logs or metadata written.

## Minimal Trusted Computing Base (TCB)  
Single small auditable library + CLI.

## Reproducible Builds  
Independent rebuilds ensure supply-chain integrity.

## Configuration Simplicity  
Only quorum and expiry user-configurable.

## Attempt Rate Limiting  
Prevents brute-force or panic-driven retries.

## Role Separation  
User vs founder operations isolated.

## Simulation Mode  
Allows safe testing with dummy data.

## Logging Philosophy  
Minimal, local-only, non-forensic.

---

# 4. Deliverables

## Phase 1 (Months 0–2)
- Spec v0.5  
- Threat model v1  
- CLI scaffold  
- TCB plan  
- Reproducible build framework  

## Phase 2 (Months 3–4)
- HFB v1  
- Secure Package v1  
- 3+1 v1  
- Zero-retention logic  
- Integrity Guard v1  
- Multi-sig simulator v1  

## Phase 3 (Months 5–7)
- IRWIN Candidate Mode v1  
- VM detection + anti-spoofing  
- Multi-device tests  
- Secure Package v2  
- Documentation v1  

## Phase 4 (Months 8–10)
- Specification v1.0  
- Multi-sig toolkit v1  
- Behavior v2  
- Public sandbox  
- Documentation v2  

## Phase 5 (Months 11–14)
- Secure Package v3  
- Cluster simulator  
- Threat model v2  

## Phase 6 (Months 15–18)
- Whitepaper  
- Implementation v1.0  
- Multi-node public testbed  
- Documentation v3  

---

# 5. Roadmap (0–18 Months)

## Phase 1 — Months 0–2  
Specification v0.2-0.5, threat model, architecture flow, CLI scaffold, TCB, reproducibility plan.

## Phase 2 — Months 3–4  
HFB v1, Secure Package v1, 3+1 baseline, zero-retention, Integrity Guard v1, multi-sig simulator.

## Phase 3 — Months 5–7  
Candidate Mode v1, anti-spoofing, multi-device tests, Secure Package v2, documentation v1.

## Phase 4 — Months 8–10  
Spec v1.0, multi-sig toolkit, behavior v2, sandbox, documentation v2.

## Phase 5 — Months 11–14  
Secure Package v3, cluster simulation, hardening, threat model v2.

## Phase 6 — Months 15–18  
Whitepaper, implementation v1.0, reproducible build validation, public testbed, documentation v3.

---

# 6. Funding Scenarios

## Tier A — €5,000  
Minimal viable prototype.

## Tier B — €10,000–€15,000  
Complete prototype with multi-device testing.

## Tier C — €20,000  
Full implementation and public testing environment.

## Tier D — €30,000–€50,000  
Extended simulation, hardening, reproducible builds, partial audit.

---

# 7. Budget Breakdown

| Item | Tier A (€5k) | Tier B (€10–15k) | Tier C (€20k) | Tier D (€30–50k) | Justification |
|------|--------------|------------------|----------------|-------------------|----------------|
| Primary Workstation | €800 | €1,200 | €1,500 | €1,500 | Development + simulation |
| ARM SBCs | €150 | €450 | €600 | €1,000 | Multi-platform testing |
| Mini-PC Nodes | – | €300 | €600 | €1,200 | Multi-sig simulation |
| Networking Gear | €100 | €250 | €400 | €800 | VLAN isolation |
| SSD / Backup | €150 | €300 | €500 | €1,500 | Encrypted storage |
| UPS | €80 | €150 | €200 | €400 | Prevent corruption |
| Partial Audit | – | – | – | €5,000–10,000 | Security review |

---

# 8. Risks & Mitigation

- **Hardware spoofing** → mitigated by multi-entropy HFB  
- **VM impersonation** → mitigated by 3+1 and IRWIN Candidate Mode  
- **Rogue founder** → multi-sig activation  
- **Governance capture** → quorum thresholds  
- **Misconfiguration** → minimal configuration surface  
- **Supply chain attack** → reproducible builds  
- **Panic-driven user mistakes** → WARN → SAFE ABORT  

---

# 9. Why the Developer Can Execute This

The developer has practical experience in high-pressure, prototype-driven work, managing complex timelines, and building systems where clear reasoning, safety, and reliability are essential.

This project benefits from a construction-style mindset: iterative building, immediate testing, threat awareness, and real-world problem-solving. Combined with IRWIN-assisted local development and long-hour capability, the project is feasible at the proposed scale.

The Quietstatix identity exists solely for this work, with public repositories, timestamped drafts, and transparent intentions. Development will be open, reproducible, and documented throughout.

---

# 10. Licensing & Open-Source Model

AGPLv3 (strong copyleft).  
Fully open-source.  
Free for individuals, nonprofits, and FOSS contributors.  
Corporate use governed by AGPL compliance.

---

# 11. Additional Information

GitHub: https://github.com/quietstatix/  
Specification drafts forthcoming.  
Testbed and reproducible build infrastructure included in later phases.
