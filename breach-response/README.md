# HIPAA Breach Response Plan

**System:** CloudVault Federal Health Exchange (FHX)
**Repository:** cloudvault-hipaa
**Folder:** breach-response
**Framework Reference:** HIPAA Breach Notification Rule 45 CFR 164.400-414 / HITECH Act Sec. 13402
**Document ID:** FHX-HIPAA-BR-001
**Prepared By:** Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, Security+, CHP, CSCS, CISSP (in progress)
**Role:** ISSO / ISSM, CloudVault Federal Health Exchange
**Last Updated:** April 2025
**Status:** Active

---

## Purpose

The HIPAA Breach Notification Rule (45 CFR 164.400-414) requires covered entities and business associates to notify affected individuals, HHS, and, in some cases, the media, following a breach of unsecured PHI. For a federal health exchange processing PHI for 890,000+ patients across 47 agencies, a breach event is one of the highest-impact scenarios the program can face. The reputational, legal, and regulatory consequences of a mishandled breach response are severe.

This folder documents the CloudVault FHX Breach Response Plan: the procedures for detecting, containing, and investigating potential breaches; the analysis process for determining whether a reportable breach has occurred; the notification workflows for individuals, HHS, and the media; and the post-breach review process. This plan is tested annually and reviewed after every security incident that meets the initial threshold for breach investigation.

---

## Documents in This Folder

| Document | Description | Reference | Status |
|---|---|---|---|
| breach-response-plan.md | Full FHX Breach Response Plan with detection, investigation, and notification procedures | 45 CFR 164.404-410 | Active |
| breach-determination-worksheet.md | Four-factor risk assessment worksheet for determining whether a security incident constitutes a reportable breach | 45 CFR 164.402 | Active |
| notification-templates.md | Pre-approved notification letter templates for individuals, HHS, and media notifications | 45 CFR 164.404, 164.408 | Active |
| breach-incident-log.md | Register of all security incidents investigated for breach determination since FHX launch | 45 CFR 164.414(b) | Active |
| breach-test-after-action.md | After-action report from the most recent annual breach response tabletop exercise | 45 CFR 164.308(a)(7)(ii)(D) | Active |

---

## Breach Definition and Scope

Under HIPAA, a breach is the acquisition, access, use, or disclosure of PHI in a manner not permitted by the Privacy Rule that compromises the security or privacy of the PHI. For CloudVault FHX, breach analysis applies to all 18 PHI identifier types across all system components.

A security incident is not automatically a breach. HIPAA provides a four-factor risk assessment that must be completed to determine whether a given incident constitutes a reportable breach. If the four-factor assessment demonstrates that the probability of PHI compromise is low, the incident is documented as not constituting a breach, and notification is not required.

**Safe Harbor:** Unsecured PHI that is rendered unusable, unreadable, or indecipherable by encryption (AES-256) is not subject to breach notification. This safe harbor applies to all PHI at rest in CloudVault FHX (AES-256, AWS KMS) and PHI in transit (TLS 1.3). This is a critical risk reduction factor for FHX.

---

## Four-Factor Breach Risk Assessment

When a potential breach is detected, the ISSO conducts a four-factor risk assessment to determine the probability that PHI has been compromised. All four factors must be analyzed.

| Factor | Description | Questions to Answer |
|---|---|---|
| Factor 1: Nature and extent of PHI | What types of PHI were involved? How many individuals? How sensitive is the data? | Were identifiers combined with clinical data? Were financial identifiers (SSN, account numbers) involved? |
| Factor 2: Who accessed or received the PHI | Was the unauthorized access by an authorized user acting outside their scope, or by an external threat actor? | Was the actor inside or outside FHX? Did they have any legitimate healthcare purpose? |
| Factor 3: Whether PHI was actually acquired or viewed | Was the PHI actually viewed, copied, or removed, or was there merely an opportunity for access? | Do logs show data access or exfiltration? Are there indicators of compromise (IOCs) in CloudTrail or GuardDuty? |
| Factor 4: Mitigation | Was the risk to PHI mitigated? For example, was the PHI encrypted? | Was the PHI encrypted at the time of the incident? Was the data returned or destroyed? |

---

## Breach Response Timeline

CloudVault FHX is required to complete breach notifications within the following timeframes. FHX applies more stringent internal timelines to provide adequate preparation time.

| Notification Recipient | HIPAA Deadline | FHX Internal Target | Responsible Party |
|---|---|---|---|
| Initial incident detection to ISSO | N/A (HIPAA) | Within 1 hour of detection | Security Operations Center |
| ISSO completes four-factor assessment | N/A (HIPAA) | Within 72 hours of detection | ISSO (Enechi P.C. Njeze) |
| Affected individuals (if breach confirmed) | Within 60 days of discovery | Within 45 days | Privacy Officer (Sandra Voss) |
| HHS notification (if breach confirmed) | Within 60 days of discovery (500+ individuals) or annually (under 500) | Simultaneous with individual notification | ISSO + Privacy Officer |
| Media notification (if breach affects 500+ in a state or jurisdiction) | Without unreasonable delay | Within 45 days | Privacy Officer + Legal Counsel Marcus Webb |
| Business associate notifies FHX (if BA is the source) | Without unreasonable delay; allows FHX 60 days | BA must notify FHX within 24 hours (per BAA) | Business Associate |
| Post-breach review and after-action report | N/A (HIPAA) | Within 30 days of notification completion | ISSO + Privacy Officer |

---

## Breach Response Procedures

### Phase 1: Detection and Containment (0-4 hours)

When a potential PHI breach is detected through any channel (GuardDuty alert, CloudTrail anomaly, employee report, external notification), the Security Operations Center (SOC) immediately opens an incident ticket in the FHX ITSM system, classifies the incident as "Potential PHI Breach" if PHI exposure is suspected, and notifies the ISSO by PagerDuty within 15 minutes.

The ISSO immediately assesses the incident and activates containment measures: isolating affected systems if warranted (using AWS Security Groups to block ingress/egress), revoking compromised credentials, and preserving logs by disabling log rotation and creating immutable snapshots.

### Phase 2: Investigation (4-72 hours)

The ISSO leads the technical investigation with support from DevOps Lead Trevor L. Abrams and the 3PAO (ClearPath Security Assessors LLC) if needed. The investigation includes: full CloudTrail and CloudWatch log review, GuardDuty finding analysis, DynamoDB and RDS query history review, S3 access log review, and network flow log analysis.


**System:** CloudVault Federal Health Exchange (FHX)
**Repository:** cloudvault-hipaa
**Folder:** breach-response
**Framework Reference:** HIPAA Breach Notification Rule 45 CFR 164.400-414 / HITECH Act Sec. 13402
**Document ID:** FHX-HIPAA-BR-001
**Prepared By:** Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, Security+, CHP, CSCS, CISSP (in progress)
**Role:** ISSO / ISSM, CloudVault Federal Health Exchange
**Last Updated:** April 2025
**Status:** Active

---

## Purpose

The HIPAA Breach Notification Rule (45 CFR 164.400-414) requires covered entities and business associates to notify affected individuals, HHS, and in some cases the media, following a breach of unsecured PHI. For a federal health exchange processing PHI for 890,000+ patients across 47 agencies, a breach event is one of the highest-impact scenarios the program can face. The reputational, legal, and regulatory consequences of a mishandled breach response are severe.

This folder documents the CloudVault FHX Breach Response Plan: the procedures for detecting, containing, and investigating potential breaches; the analysis process for determining whether a reportable breach has occurred; the notification workflows for individuals, HHS, and the media; and the post-breach review process. This plan is tested annually and reviewed after every security incident that meets the initial threshold for breach investigation.

---

## Documents in This Folder

| Document | Description | Reference | Status |
|---|---|---|---|
| breach-response-plan.md | Full FHX Breach Response Plan with detection, investigation, and notification procedures | 45 CFR 164.404-410 | Active |
| breach-determination-worksheet.md | Four-factor risk assessment worksheet for determining whether a security incident is a reportable breach | 45 CFR 164.402 | Active |
| notification-templates.md | Pre-approved notification letter templates for individuals, HHS, and media notifications | 45 CFR 164.404, 164.408 | Active |
| breach-incident-log.md | Register of all security incidents investigated for breach determination since FHX launch | 45 CFR 164.414(b) | Active |
| breach-test-after-action.md | After-action report from the most recent annual breach response tabletop exercise | 45 CFR 164.308(a)(7)(ii)(D) | Active |

---

## Breach Definition and Safe Harbor

Under HIPAA, a breach is the acquisition, access, use, or disclosure of PHI in a manner not permitted by the Privacy Rule that compromises the security or privacy of the PHI.

A security incident is not automatically a breach. HIPAA provides a four-factor risk assessment that must be completed to determine whether a given incident constitutes a reportable breach. If the four-factor assessment demonstrates that the probability of PHI compromise is low, the incident is documented as not constituting a breach, and notification is not required.

**Safe Harbor:** Unsecured PHI that is rendered unusable, unreadable, or indecipherable by encryption (AES-256) is not subject to breach notification. This safe harbor applies to all PHI at rest in CloudVault FHX (AES-256, AWS KMS) and PHI in transit (TLS 1.3). This is a critical risk reduction factor for FHX.

---

## Four-Factor Breach Risk Assessment

| Factor | Description | Key Questions |
|---|---|---|
| Factor 1: Nature and extent of PHI | What types of PHI were involved? How many individuals? | Were identifiers combined with clinical data? Were SSNs or financial IDs involved? |
| Factor 2: Who accessed or received the PHI | Insider acting outside scope, or external threat actor? | Did the actor have any legitimate healthcare purpose? |
| Factor 3: Whether PHI was actually accessed | Was PHI viewed, copied, or removed, or only potentially accessible? | Do CloudTrail/GuardDuty logs show data access or exfiltration? |
| Factor 4: Mitigation | Was the risk mitigated by encryption or other controls? | Was PHI encrypted at time of incident? Was data returned or destroyed? |

---

## Breach Response Timeline

| Notification Recipient | HIPAA Deadline | FHX Internal Target | Responsible Party |
|---|---|---|---|
| Initial detection to ISSO | N/A | Within 1 hour of detection | Security Operations Center |
| ISSO completes four-factor assessment | N/A | Within 72 hours of detection | ISSO (Enechi P.C. Njeze) |
| Affected individuals (if breach confirmed) | Within 60 days of discovery | Within 45 days | Privacy Officer (Sandra Voss) |
| HHS notification (500+ individuals) | Within 60 days of discovery | Simultaneous with individual notification | ISSO + Privacy Officer |
| HHS notification (under 500 individuals) | Annual log, by February 1 | Annual | ISSO + Privacy Officer |
| Media notification (500+ per state) | Without unreasonable delay | Within 45 days | Privacy Officer + Legal Counsel Marcus Webb |
| BA notifies FHX (if BA is source) | Without unreasonable delay | BA BAA requires 24 hours | Business Associate |
| Post-breach after-action report | N/A | Within 30 days of notification completion | ISSO + Privacy Officer |

---

## Breach Response Phase Summary

### Phase 1: Detection and Containment (0-4 hours)

Upon detection of a potential PHI breach through GuardDuty alert, CloudTrail anomaly, employee report, or external notification, the SOC opens an incident ticket, classifies it as Potential PHI Breach, and notifies the ISSO via PagerDuty within 15 minutes. The ISSO activates containment measures: isolating affected systems using AWS Security Groups, revoking compromised credentials, and preserving logs using immutable snapshots.

### Phase 2: Investigation (4-72 hours)

The ISSO leads the technical investigation with support from DevOps Lead Trevor L. Abrams. The investigation covers: CloudTrail and CloudWatch log review, GuardDuty finding analysis, DynamoDB and RDS query history, S3 access logs, and VPC flow logs. The ISSO completes the four-factor breach determination worksheet and reaches one of three conclusions: (1) Safe harbor applies (PHI encrypted), no breach; (2) Breach confirmed, proceed to notification; (3) Inconclusive, escalate to AO (Deputy Director Henry Kline) and legal counsel Marcus Webb.

### Phase 3: Notification (within 45-60 days)

Written notices are sent to affected individuals by first-class mail or email. Each notice includes a description of the breach, PHI types involved, protective steps individuals should take, FHX mitigation actions, and a toll-free contact number. HHS notification is made simultaneously through the HHS Breach Notification Portal. Media notification is provided for any breach affecting 500+ residents of a state.

### Phase 4: Post-Breach Review (within 30 days of notification completion)

The ISSO and Privacy Officer produce a post-breach after-action report covering: root cause analysis, adequacy of the breach response, security control gaps identified, risk register updates, and revised safeguards. The report is presented to the AO and CISO.

---

## Breach Incident Register (Summary)

| Incident ID | Date | Description | PHI Involved | Individuals | Determination | Notification | Status |
|---|---|---|---|---|---|---|---|
| FHX-INC-2023-001 | March 2023 | API query bug inadvertently returned extra patient records | MRN, name, DOB | 14 | Breach confirmed | Yes, completed | Closed |
| FHX-INC-2024-001 | July 2024 | Phishing on agency partner employee; no PHI access confirmed in logs | None confirmed | 0 | Not a breach (encrypted, no access) | No | Closed |
| FHX-INC-2024-002 | November 2024 | Misconfigured S3 bucket in test environment; no PHI present | None | 0 | Not a breach (no PHI) | No | Closed |
| FHX-INC-2025-001 | January 2025 | Unauthorized access attempt blocked by WAF; no PHI accessed | None confirmed | 0 | Not a breach (encrypted, blocked) | No | Closed |

---

## Related Documents

- [PHI Inventory](../phi-inventory/README.md)
- [HIPAA Gap Analysis](../gap-analysis/README.md)
- [HIPAA Safeguards](../safeguards/README.md)
- [Business Associate Agreements](../baa-templates/README.md)
- [Security Training](../training/README.md)
- [FedRAMP IR Controls](https://github.com/enechi-njeze/cloudvault-fedramp-ato/blob/main/README.md)
- [NIST RMF Authorization Package](https://github.com/enechi-njeze/cloudvault-nist-rmf/blob/main/step5-authorize/README.md)

---

*Prepared by Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, CompTIA Security+ SY0-701, CHP, CSCS, CISSP (in progress)*
*ISSO / ISSM, CloudVault Federal Health Exchange (FHX)*
*[LinkedIn](https://www.linkedin.com/in/enechi-njeze) | [Portfolio](https://github.com/enechi-njeze)*
