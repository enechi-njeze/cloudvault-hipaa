# HIPAA Security Awareness Training Program

**System:** CloudVault Federal Health Exchange (FHX)
**Repository:** cloudvault-hipaa
**Folder:** training
**Framework Reference:** HIPAA Security Rule 45 CFR 164.308(a)(5) / HITECH Act Sec. 13401
**Document ID:** FHX-HIPAA-TRN-001
**Prepared By:** Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, Security+, CHP, CSCS, CISSP (in progress)
**Role:** ISSO / ISSM, CloudVault Federal Health Exchange
**Last Updated:** April 2025
**Status:** Active

---

## Purpose

HIPAA requires covered entities to implement a security awareness and training program for all workforce members, including management, under 45 CFR 164.308(a)(5)(i). This is a Required specification with no option to implement an equivalent alternative. For CloudVault FHX, whose workforce members and agency partner personnel access PHI belonging to 890,000+ patients across 47 federal agencies, security awareness training is both a compliance obligation and a critical risk reduction control.

The FHX security awareness training program addresses protection from malicious software, login monitoring, password management, and general PHI handling practices. Training is conducted annually for all personnel with access to FHX systems, and within 30 days of hire for new personnel. This folder documents the program curriculum, delivery schedule, completion tracking methodology, and training records management.

---

## Documents in This Folder

| Document | Description | Reference | Status |
|---|---|---|---|
| training-program-overview.md | Full description of the FHX HIPAA security training program including curriculum and delivery | 45 CFR 164.308(a)(5)(i) | Active |
| training-curriculum.md | Module-by-module curriculum with learning objectives, content outline, and assessment criteria | 45 CFR 164.308(a)(5)(ii) | Active |
| training-completion-report.md | FY2025 training completion report with completion rates by organization and role | 45 CFR 164.308(a)(1)(ii)(D) | Active |
| training-policy.md | FHX Security Awareness and Training Policy (FHX-TR-001) | 45 CFR 164.308(a)(5) | Active |
| training-records-register.md | Training records retention register with completion dates and attestation records | OCR Audit Protocol | Active |

---

## Training Program Overview

### Scope

All individuals with access to FHX systems or PHI must complete the FHX HIPAA Security Awareness Training program. This includes: FHX federal workforce members, contractor personnel, agency partner personnel with FHIR API access or portal access, and any third-party vendor personnel with incidental PHI access. As of April 2025, the training program covers 1,247 individuals across 47 agencies and 18 vendor organizations.

### Delivery Method

Training is delivered through the FHX Learning Management System (LMS) hosted on Cornerstone OnDemand (FedRAMP authorized). All modules are available 24/7 and include interactive elements, scenario-based questions, and a final knowledge assessment. Each module requires a passing score of 80% on the assessment. Users who do not pass may retake the assessment after a 24-hour waiting period.

### Training Schedule

| Event | Audience | Frequency | Trigger |
|---|---|---|---|
| Annual HIPAA Security Training | All FHX workforce and authorized users | Annual | January 1 each year; completion required by March 31 |
| New Hire HIPAA Onboarding | New FHX workforce members | Within 30 days of hire | HR new hire notification |
| Role Change Training | Personnel with expanded PHI access | Before access is granted | IAM role change request |
| Incident-Triggered Training | Personnel involved in a PHI security incident | Within 10 days of incident | ISSO incident determination |
| Refresher Training | All workforce | As needed, based on emerging threats | ISSO or CISO directive |
| Phishing Simulation | All workforce | Quarterly | Automated simulation engine |

---

## Training Curriculum

The FHX HIPAA Security Awareness Training program consists of five core modules and two supplemental modules for personnel with elevated PHI access.

### Module 1: HIPAA Foundations (Required, all users, 45 minutes)

This module covers the legal framework and basic requirements of HIPAA and HITECH. Topics include: what PHI is and why it matters, the three rules of HIPAA (Privacy, Security, Breach Notification), the workforce member's individual obligations, and the consequences of HIPAA violations for individuals and the organization. The module uses real-world federal health exchange scenarios throughout.

Learning objectives: Identify the 18 PHI identifiers, describe the three HIPAA rules, explain the difference between permitted and required disclosures, and recognize their personal HIPAA obligations.

### Module 2: Password and Authentication Security (Required, all users, 30 minutes)

This module addresses 45 CFR 164.308(a)(5)(ii)(D) password management and multi-factor authentication requirements. Topics include: creating strong passwords, using the FHX password manager, setting up and using MFA (PIV/CAC for federal staff, TOTP app for contractors), recognizing credential phishing, and what to do if credentials are compromised.

Learning objectives: Set up MFA on the FHX portal, identify credential phishing attempts, report a suspected credential compromise, and comply with FHX password policy requirements.

### Module 3: Malware and Threat Awareness (Required, all users, 30 minutes)

This module addresses 45 CFR 164.308(a)(5)(ii)(B) malware protection requirements. Topics include: common malware types (ransomware, spyware, trojans), how malware enters FHX-connected environments, spotting malicious emails and attachments, safe use of USB devices, and reporting suspected malware infections.

Learning objectives: Recognize signs of a malware infection on a workstation, report a suspected infection to the FHX Security Operations Center, and explain why USB device restrictions exist.

### Module 4: PHI Handling and Data Minimization (Required, all users, 45 minutes)

This module covers the practical rules for handling PHI in the FHX environment. Topics include: minimum necessary standard, secure transmission of PHI (approved channels only), prohibited uses of PHI, secure disposal, physical PHI security (clear desk policy, screen locks), and remote work PHI handling.

Learning objectives: Apply the minimum necessary standard to PHI requests, identify approved versus prohibited PHI transmission channels, and correctly dispose of PHI-containing materials.

### Module 5: Security Incident Reporting (Required, all users, 20 minutes)

This module covers 45 CFR 164.308(a)(6) incident procedures. Topics include: what constitutes a security incident versus a breach, how to report an incident using the FHX Security Operations Center hotline and ticketing system, what information to include in a report, and the non-retaliation policy for good-faith incident reporting.

Learning objectives: Identify events that must be reported as security incidents, submit an incident report through the FHX ITSM system, and understand the non-retaliation protection for reporters.

### Module 6: Advanced PHI Access and API Security (Supplemental, API users, 60 minutes)

Required for all personnel with FHIR API access. Covers: FHIR R4 access authorization scopes, API credential management, detecting and reporting anomalous API behavior, and PHI data handling obligations for system-to-system exchanges.

### Module 7: HIPAA for Supervisors and Managers (Supplemental, management, 45 minutes)

Required for all FHX supervisors and managers. Covers: managerial accountability for workforce HIPAA compliance, conducting HIPAA conversations with workforce members, handling workforce HIPAA complaints, and the sanction policy for HIPAA violations.

---

## FY2025 Training Completion Status (as of April 2025)

| Organization | Total Users | Completed | Completion Rate | Status |
|---|---|---|---|---|
| FHX Core Operations Team | 87 | 87 | 100% | Complete |
| Department of Veterans Affairs | 214 | 209 | 97.7% | In Progress (5 pending) |
| Centers for Medicare and Medicaid Services | 178 | 175 | 98.3% | In Progress (3 pending) |
| Indian Health Service | 92 | 90 | 97.8% | In Progress (2 pending) |
| Defense Health Agency | 143 | 143 | 100% | Complete |
| All other agency partners (43 agencies) | 533 | 498 | 93.4% | In Progress |
| **Total** | **1,247** | **1,202** | **96.4%** | **In Progress** |

All users with a completion rate below 100% will receive a final reminder notice on May 1, 2025. Accounts for users who do not complete training by May 15, 2025 will be suspended pending completion.

---

## Training Records Management

Training records are maintained in the FHX LMS for a minimum of 6 years in accordance with HIPAA records retention requirements. Records include: completion date, module title, assessment score, and attestation confirmation. Records are available for export to the FHX Privacy Officer (Sandra Voss) and ISSO on demand. HHS OCR may request training records as part of a compliance review or breach investigation; records are maintained in a format suitable for immediate production.

---

## Related Documents

- [HIPAA Gap Analysis](../gap-analysis/README.md)
- [HIPAA Safeguards](../safeguards/README.md)
- [Business Associate Agreements](../baa-templates/README.md)
- [Breach Response Plan](../breach-response/README.md)
- [FedRAMP AT Controls (Awareness and Training)](https://github.com/enechi-njeze/cloudvault-fedramp-ato/blob/main/README.md)
- [NIST RMF Step 3: Implementation](https://github.com/enechi-njeze/cloudvault-nist-rmf/blob/main/step3-implement/README.md)

---

*Prepared by Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, CompTIA Security+ SY0-701, CHP, CSCS, CISSP (in progress)*
*ISSO / ISSM, CloudVault Federal Health Exchange (FHX)*
*[LinkedIn](https://www.linkedin.com/in/enechi-njeze) | [Portfolio](https://github.com/enechi-njeze)*
