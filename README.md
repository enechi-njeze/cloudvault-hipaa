# cloudvault-hipaa

![HIPAA](https://img.shields.io/badge/Framework-HIPAA%2FHITECH-navy)
![PHI](https://img.shields.io/badge/Data-PHI%20HIGH-critical)
![FedRAMP High](https://img.shields.io/badge/FedRAMP-High-red)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)
![CHP](https://img.shields.io/badge/Cert-CHP-blue)

---

## HIPAA Compliance Program
### CloudVault Federal Health Exchange (FHX)

This repository documents the complete HIPAA/HITECH compliance program for the CloudVault Federal Health Exchange (FHX). CloudVault FHX processes Protected Health Information (PHI) for 890,000+ patients across 47 federal health agencies. HIPAA compliance is not optional for this system: it is a legal mandate under 45 CFR Parts 160 and 164, and every security control in the FedRAMP High baseline that touches PHI is shaped by HIPAA requirements.

This repository demonstrates the practitioner-level HIPAA competency required for senior GRC roles in federal health, healthcare IT, and any organization handling PHI. It reflects the knowledge embodied in the Certified HIPAA Professional (CHP) credential held by the author.

---

## System Reference Card

| Field | Detail |
|---|---|
| System Name | CloudVault Federal Health Exchange (FHX) |
| PHI Volume | 890,000+ patient records across 47 federal agencies |
| PHI Categories | Demographic, clinical, claims, pharmacy, lab, mental health, substance abuse |
| Covered Entity Status | Business Associate (BA) to 47 CE federal agencies |
| HIPAA Applicability | HIPAA Privacy Rule, Security Rule, Breach Notification Rule, HITECH Act |
| ISSO/ISSM | Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, Security+, CHP, CSCS |
| Privacy Officer | Sandra Voss, Chief Privacy Officer |
| System Owner | Dr. Patricia Owens, Deputy Director, Federal Health Systems |

---

## What This Repository Covers

HIPAA compliance for a federal health exchange involves three distinct regulatory bodies: the HIPAA Privacy Rule (what PHI can be used and disclosed, and patient rights), the HIPAA Security Rule (administrative, physical, and technical safeguards for electronic PHI), and the HITECH Act (breach notification requirements and HIPAA enforcement strengthening). For CloudVault FHX, the Security Rule is the primary technical compliance driver, and every safeguard maps to specific FedRAMP controls.

---

## Repository Deliverables

| # | Document | Folder | HIPAA Reference | Status |
|---|---|---|---|---|
| 1 | PHI Inventory and Data Map | phi-inventory/ | 45 CFR 164.310(d) | In Progress |
| 2 | HIPAA Security Rule Gap Analysis | gap-analysis/ | 45 CFR 164.308-316 | In Progress |
| 3 | Administrative Safeguards Documentation | safeguards/ | 45 CFR 164.308 | In Progress |
| 4 | Physical Safeguards Documentation | safeguards/ | 45 CFR 164.310 | In Progress |
| 5 | Technical Safeguards Documentation | safeguards/ | 45 CFR 164.312 | In Progress |
| 6 | Business Associate Agreement Templates | baa-templates/ | 45 CFR 164.308(b) | In Progress |
| 7 | HIPAA Security Awareness Training Program | training/ | 45 CFR 164.308(a)(5) | In Progress |
| 8 | Breach Response Procedures | breach-response/ | 45 CFR 164.400-414 | In Progress |
| 9 | Risk Analysis and Risk Management | gap-analysis/ | 45 CFR 164.308(a)(1) | In Progress |
| 10 | HIPAA Compliance Metrics Dashboard | gap-analysis/ | Ongoing | Planned |

---

## Folder Structure

```
cloudvault-hipaa/
├── phi-inventory/      # PHI data inventory, data flow map, classification
├── gap-analysis/       # HIPAA Security Rule gap analysis, risk analysis, metrics
├── safeguards/         # Administrative, physical, and technical safeguard documentation
├── baa-templates/      # Business Associate Agreement templates and executed BAA log
├── training/           # HIPAA security awareness training program and completion records
├── breach-response/    # Breach detection, investigation, notification, and reporting procedures
└── diagrams/           # PHI data flow diagram, safeguard coverage map
```

---

## HIPAA Security Rule Safeguard Categories

| Category | CFR Reference | CloudVault FHX Implementation |
|---|---|---|
| Administrative Safeguards | 45 CFR 164.308 | Risk analysis, workforce training, access management procedures, contingency plan, BAA management |
| Physical Safeguards | 45 CFR 164.310 | AWS GovCloud physical security (inherited), workstation use policy, media disposal procedures |
| Technical Safeguards | 45 CFR 164.312 | MFA, audit logs, automatic logoff, PHI encryption at rest (AES-256) and in transit (TLS 1.3) |
| Organizational Requirements | 45 CFR 164.314 | BAAs with all 47 agency partners, group health plan documentation |
| Policies, Procedures, Documentation | 45 CFR 164.316 | All safeguard policies documented, reviewed annually, retained 6 years |

---

## Laws, Regulations, and Standards

| Instrument | Relevance |
|---|---|
| HIPAA Privacy Rule (45 CFR Part 164, Subpart E) | PHI use, disclosure, and patient rights |
| HIPAA Security Rule (45 CFR Part 164, Subparts A and C) | Electronic PHI safeguards |
| HIPAA Breach Notification Rule (45 CFR Part 164, Subpart D) | Breach detection, investigation, and reporting |
| HITECH Act (Pub. L. 111-5, Title XIII) | HIPAA enforcement, breach notification, BA liability |
| NIST SP 800-66 Rev 2 | HIPAA Security Rule implementation guide |
| FISMA (44 U.S.C. § 3551) | Federal information security mandate |
| NIST SP 800-53 Rev 5 | FedRAMP controls that satisfy HIPAA Security Rule requirements |
| HHS OCR Guidance | Enforcement priorities, audit protocols, breach assessment |

---

## Certifications This Portfolio Showcases

| Certification | Issuing Body | Relevance |
|---|---|---|
| CHP (Certified HIPAA Professional) | APHP | Direct HIPAA compliance expertise |
| CGRC (Certified in Governance, Risk, and Compliance) | ISC2 | HIPAA risk analysis and risk management |
| CISA (Certified Information Systems Auditor) | ISACA | HIPAA audit and gap assessment |
| CISM (Certified Information Security Manager) | ISACA | HIPAA program governance |
| PMP (Project Management Professional) | PMI | HIPAA implementation project management |
| CompTIA Security+ SY0-701 | CompTIA | Technical safeguard implementation |
| CISSP (in progress) | ISC2 | PHI security architecture |
Add README.md: cloudvault-hipaa professional landing page---

## Portfolio Status

| Component | Status |
|---|---|
| Repository created | Complete |
| README.md | Complete |
| PHI Inventory folder | In Progress |
| Gap Analysis folder | In Progress |
| Safeguards folder | In Progress |
| BAA Templates folder | In Progress |
| Training folder | In Progress |
| Breach Response folder | In Progress |
| Diagrams folder | In Progress |

---

*Prepared by: Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, CompTIA Security+ SY0-701, CHP, CSCS*
*ISSO and ISSM: CloudVault Federal Health Exchange (FHX)*
*LinkedIn: [Enechi P.C. Njeze](https://www.linkedin.com/in/enechi-njeze)*
*Portfolio: [CloudVault GRC Portfolio](https://github.com/enechi-njeze)*
