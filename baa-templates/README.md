# Business Associate Agreements (BAA) Templates and Register

**System:** CloudVault Federal Health Exchange (FHX)
**Repository:** cloudvault-hipaa
**Folder:** baa-templates
**Framework Reference:** HIPAA Security Rule 45 CFR 164.308(b) / 164.314 / HITECH Act Sec. 13401
**Document ID:** FHX-HIPAA-BAA-001
**Prepared By:** Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, Security+, CHP, CSCS, CISSP (in progress)
**Role:** ISSO / ISSM, CloudVault Federal Health Exchange
**Last Updated:** April 2025
**Status:** Active

---

## Purpose

Under the HIPAA Privacy and Security Rules, a covered entity must have a Business Associate Agreement (BAA) in place with every business associate before sharing PHI. HITECH extended this requirement so that business associates must also obtain BAAs from their subcontractors who handle PHI. For CloudVault FHX, which shares PHI with 47 federal agency partners and multiple cloud service providers, BAA management is a critical operational and legal requirement.

A BAA is not just a legal formality. It allocates HIPAA responsibility between parties, specifies permitted uses and disclosures of PHI, requires safeguard commitments, establishes breach notification obligations, and defines what happens to PHI when the agreement terminates. The ISSO and Privacy Officer jointly maintain the BAA program, and the BAA register is reviewed every quarter.

This folder contains the FHX BAA template library, the executed BAA register for all current partners, and the BAA review and renewal workflow.

---

## Documents in This Folder

| Document | Description | Reference | Status |
|---|---|---|---|
| baa-template-standard.md | Standard BAA template for federal agency partners receiving PHI via FHIR API | 45 CFR 164.308(b)(1) | Active |
| baa-template-cloud-provider.md | BAA template for cloud service providers and technology subcontractors | 45 CFR 164.314(a) | Active |
| baa-executed-register.md | Register of all executed BAAs with partner name, effective date, scope, and renewal date | 45 CFR 164.308(b)(1) | Active |
| baa-review-workflow.md | Quarterly BAA review and annual renewal workflow with roles and responsibilities | HHS BAA Guidance | Active |
| baa-subcontractor-addendum.md | Subcontractor BAA addendum for third-party vendors with incidental PHI access | HITECH Sec. 13401 | Active |

---

## BAA Core Requirements

Every BAA executed by CloudVault FHX must contain the following elements per 45 CFR 164.308(b)(3) and 164.504(e):

| Required Element | Description | Included in FHX Template |
|---|---|---|
| Permitted uses and disclosures | Specifies the purposes for which the BA may use or disclose PHI | Yes |
| Prohibited uses | States the BA may not use or disclose PHI other than as permitted or required by the agreement | Yes |
| Safeguards obligation | Requires the BA to implement appropriate safeguards to protect PHI | Yes |
| Breach notification | Requires the BA to report any breach or security incident involving PHI to FHX within 24 hours | Yes (exceeds HIPAA's 60-day requirement) |
| Subcontractor obligation | Requires the BA to obtain BAAs from any subcontractors who handle PHI | Yes |
| PHI access and amendment | Allows FHX to access, correct, or amend PHI held by the BA | Yes |
| PHI return or destruction | Requires the BA to return or destroy all PHI upon termination | Yes |
| Audit and inspection rights | Grants FHX the right to audit the BA's HIPAA compliance | Yes |
| HITECH compliance | Requires the BA to comply with applicable HITECH provisions | Yes |

---

## Executed BAA Register (Sample Entries)

The full register contains entries for all 47 agency partners and all cloud service providers. Representative entries are shown below.

| BAA ID | Partner / Vendor | Partner Type | PHI Shared | Effective Date | Renewal Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| FHX-BAA-001 | Department of Veterans Affairs (VA) | Federal Agency | Patient records, clinical data | January 1, 2023 | December 31, 2025 | Active | Sandra Voss |
| FHX-BAA-002 | Centers for Medicare and Medicaid Services (CMS) | Federal Agency | Beneficiary records, claims data | January 1, 2023 | December 31, 2025 | Active | Sandra Voss |
| FHX-BAA-003 | Indian Health Service (IHS) | Federal Agency | Tribal health records | January 1, 2023 | December 31, 2025 | Active | Sandra Voss |
| FHX-BAA-004 | Defense Health Agency (DHA) | Federal Agency / DoD | Military health records | January 1, 2023 | December 31, 2025 | Active | Sandra Voss |
| FHX-BAA-005 | Amazon Web Services (AWS GovCloud) | Cloud Service Provider | Infrastructure hosting PHI | March 15, 2022 | Perpetual (with notice) | Active | Enechi P.C. Njeze |
| FHX-BAA-006 | ClearPath Security Assessors LLC | 3PAO / Assessor | Incidental access during assessment | February 1, 2025 | January 31, 2026 | Active | Enechi P.C. Njeze |
| FHX-BAA-007 | Apogee Analytics Group | Business Intelligence Vendor | Aggregated, de-identified data only | June 1, 2024 | May 31, 2026 | Active | Sandra Voss |
| FHX-BAA-008 | MedCom Federal Solutions | Health IT Integrator | HL7 FHIR integration services | April 1, 2023 | March 31, 2026 | Active | Enechi P.C. Njeze |
| FHX-BAA-009 | Federal Occupational Health (FOH) | Federal Agency | Employee health records | January 1, 2023 | December 31, 2025 | Active | Sandra Voss |
| FHX-BAA-010 | Substance Abuse and Mental Health Services Administration (SAMHSA) | Federal Agency | Behavioral health records | January 1, 2023 | December 31, 2025 | Active | Sandra Voss |

*Full register: 47 agency BAAs + 18 vendor BAAs = 65 total executed agreements as of April 2025*

---

## BAA Standard Template Structure

The FHX standard BAA template includes the following sections:

**Section 1: Definitions** — Defines Business Associate, Covered Entity, PHI, Protected Health Information, Security Incident, Breach, and all HIPAA/HITECH terms as defined in 45 CFR 160.103.

**Section 2: Obligations of Business Associate** — Specifies permitted uses, prohibited uses, safeguard requirements, incident reporting (24-hour requirement), subcontractor obligations, PHI access and amendment rights, accounting of disclosures support, and audit rights.

**Section 3: Permitted Uses and Disclosures** — Lists specific purposes for which the BA may use or disclose PHI (e.g., treatment, payment, healthcare operations, or specific program purposes).

**Section 4: Security Safeguards** — Requires the BA to implement all applicable HIPAA Security Rule safeguards, maintain a security risk analysis, and remediate identified gaps within 90 days.

**Section 5: Breach and Security Incident Reporting** — Requires notification to FHX Privacy Officer and ISSO within 24 hours of discovery, a written incident report within 72 hours, and full breach notification support within 60 days.

**Section 6: Subcontractors** — Requires the BA to execute a BAA with any subcontractor that creates, receives, maintains, or transmits PHI on behalf of FHX or the BA.

**Section 7: Term and Termination** — Establishes the agreement term, termination rights for HIPAA violations, and the obligation to return or destroy PHI within 30 days of termination.

**Section 8: Miscellaneous** — Governing law, amendment procedure, no third-party beneficiaries, and entire agreement clause.

---

## BAA Review and Renewal Workflow

| Activity | Frequency | Responsible Party | Trigger |
|---|---|---|---|
| BAA register review | Quarterly | Privacy Officer (Sandra Voss) + ISSO | Calendar |
| BAA renewal reminder | 90 days before expiry | Privacy Officer | Automated calendar alert |
| New partner BAA execution | Before any PHI sharing begins | Privacy Officer + Legal Counsel Marcus Webb | New partner onboarding |
| Post-incident BAA review | Within 30 days of breach | ISSO + Privacy Officer | Security incident |
| Annual BAA compliance check | Annually | ISSO | Annual compliance calendar |
| Subcontractor BAA audit | Annually | ISSO | Annual compliance calendar |

---

## Related Documents

- [PHI Inventory](../phi-inventory/README.md)
- [HIPAA Gap Analysis](../gap-analysis/README.md)
- [HIPAA Safeguards](../safeguards/README.md)
- [Breach Response Plan](../breach-response/README.md)
- [Privacy Program](https://github.com/enechi-njeze/cloudvault-privacy/blob/main/README.md)
- [FedRAMP Third-Party Risk Management](https://github.com/enechi-njeze/cloudvault-fedramp-ato/blob/main/README.md)

---

*Prepared by Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, CompTIA Security+ SY0-701, CHP, CSCS, CISSP (in progress)*
*ISSO / ISSM, CloudVault Federal Health Exchange (FHX)*
*[LinkedIn](https://www.linkedin.com/in/enechi-njeze) | [Portfolio](https://github.com/enechi-njeze)*
