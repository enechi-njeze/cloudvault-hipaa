# HIPAA Diagrams and Visual Documentation

**System:** CloudVault Federal Health Exchange (FHX)
**Repository:** cloudvault-hipaa
**Folder:** diagrams
**Framework Reference:** HIPAA Security Rule 45 CFR 164.308(a)(1)(ii)(A) / NIST SP 800-53 PL-8
**Document ID:** FHX-HIPAA-DIA-001
**Prepared By:** Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, Security+, CHP, CSCS, CISSP (in progress)
**Role:** ISSO / ISSM, CloudVault Federal Health Exchange
**Last Updated:** April 2025
**Status:** Active

---

## Purpose

Visual documentation is a critical component of any HIPAA compliance program. Diagrams make it possible to communicate complex PHI flows, safeguard coverage, and system architecture to diverse audiences: technical engineers who build and maintain the systems, GRC analysts who assess compliance, auditors and OCR investigators who evaluate program adequacy, and executive stakeholders who need to understand risk at a strategic level.

For CloudVault FHX, diagrams support the risk analysis required under 45 CFR 164.308(a)(1)(ii)(A), which mandates an accurate and thorough assessment of all the ways PHI flows through the system. Diagrams provide the visual representation of those flows and the safeguards that protect PHI at each stage.

---

## Documents in This Folder

| Document | Description | Reference | Status |
|---|---|---|---|
| phi-data-flow-diagram.md | Narrative description of the full PHI data flow through FHX with stage-by-stage safeguard mapping | 45 CFR 164.308(a)(1)(ii)(A) | Active |
| safeguard-coverage-map.md | Visual map of HIPAA safeguard coverage across FHX components and data flow stages | 45 CFR 164.308-164.312 | Active |
| phi-lifecycle-diagram.md | PHI lifecycle from ingestion through active use, archival, and secure disposal | 45 CFR 164.310(d) | Active |
| breach-response-flowchart.md | Decision flowchart for breach determination and notification workflow | 45 CFR 164.400-414 | Active |
| hipaa-controls-architecture.md | High-level architecture showing FHX technical controls as they apply to HIPAA requirements | 45 CFR 164.312 | Active |

---

## PHI Data Flow: Stage-by-Stage Description

### Stage 1: Ingestion

PHI enters FHX through three channels: (1) FHIR R4 API from 47 federal agency EHR systems over mutual TLS 1.3; (2) AWS Transfer Family SFTP for batch file transfers; and (3) the FHX patient portal for direct patient submissions. All channels are protected by WAF, API Gateway throttling, and CloudTrail logging.

Active safeguards: TLS 1.3 transmission encryption, mutual TLS authentication, WAF, API Gateway, CloudTrail logging.

### Stage 2: Processing

Ingested PHI is validated and normalized by the FHX processing service on Amazon ECS Fargate within a private VPC subnet. No PHI is persisted to disk during processing. Data moves in memory under VPC isolation with inter-service TLS.

Active safeguards: VPC isolation, no public internet access from processing subnet, container security (no privileged containers, read-only filesystem), AWS Secrets Manager.

### Stage 3: Storage

Validated PHI is stored in Amazon RDS Aurora (PostgreSQL) for structured records, Amazon S3 for clinical documents, and DynamoDB for the fast-access encounter index. All storage uses AES-256 encryption with AWS KMS CMKs under the FHX PHI key policy. Access is restricted to IAM roles following least-privilege principles.

Active safeguards: AES-256 KMS encryption, IAM role-based access, CloudTrail data event logging, automated backups, VPC endpoint access only.

### Stage 4: Exchange

PHI is transmitted to authorized agency partners via FHIR R4 API responses (TLS 1.3), S3 pre-signed URLs with 15-minute expiry (batch exports), and the FHX provider portal. All transmissions are logged with user, time, and data accessed.

Active safeguards: TLS 1.3, MFA-authenticated API access, FHIR scoping, pre-signed URL expiry, complete audit logging.

### Stage 5: Archival

PHI older than 7 years transitions to S3 Glacier with Vault Lock enforcing the retention policy and preventing premature deletion. AES-256 encryption is maintained throughout the archival period.

Active safeguards: S3 Glacier Vault Lock, AES-256 encryption, access limited to archival management role.

### Stage 6: Disposal

At end of retention, PHI is deleted from all storage layers following NIST SP 800-88 Rev 1 procedures. KMS key deletion provides cryptographic destruction assurance. All disposal events are logged and maintained in the PHI disposal log.

Active safeguards: NIST SP 800-88 compliant deletion, KMS key deletion, CloudTrail deletion event logging, disposal log maintained for audit evidence.

---

## Safeguard Coverage Map

| Safeguard | Ingestion | Processing | Storage | Exchange | Archival | Disposal |
|---|---|---|---|---|---|---|
| Access Control (164.312(a)) | IAM, mTLS | IAM, VPC | IAM, RDS roles | IAM, API scopes | IAM, Vault policy | IAM, limited |
| Audit Controls (164.312(b)) | CloudTrail, API GW logs | CloudWatch | CloudTrail data events | CloudTrail, VPC Flow | S3 access logs | CloudTrail delete events |
| Integrity (164.312(c)) | FHIR validation | SHA-256 checksums | RDS constraints | S3 integrity | Glacier integrity | Deletion verification |
| Authentication (164.312(d)) | mTLS, MFA | Service IAM roles | KMS key policy | MFA, PIV/CAC | IAM | IAM |
| Transmission Security (164.312(e)) | TLS 1.3 | VPC (no transit) | Not applicable | TLS 1.3 | Not applicable | Not applicable |
| Encryption at Rest (164.312(a)(2)(iv)) | Not applicable | Not applicable | AES-256 KMS | Not applicable | AES-256 KMS | KMS key deletion |

---

## PHI Lifecycle Summary

| Phase | Duration | Primary PHI Location | Encryption | Access |
|---|---|---|---|---|
| Active use | 0-7 years from last encounter | RDS Aurora, S3, DynamoDB | AES-256 KMS | Role-based, MFA required |
| Archival | Year 7 and beyond | S3 Glacier | AES-256 KMS | Restricted archival role |
| Disposal | End of retention period | Deleted from all systems | KMS key deletion | Authorized disposal role only |

---

## Breach Response Decision Flowchart Summary

When a potential breach is detected:

1. Security incident detected (GuardDuty, CloudTrail anomaly, report)
2. SOC opens incident ticket: Potential PHI Breach
3. ISSO notified within 15 minutes
4. Containment activated (system isolation, credential revocation, log preservation)
5. ISSO conducts four-factor risk assessment within 72 hours
6. Was PHI encrypted throughout? If yes: safe harbor applies, document as not a breach
7. If no: is the probability of compromise demonstrably low? If yes: document as not a breach
8. If no: breach confirmed, proceed to notification
9. Individual notification within 45 days (FHX target)
10. HHS notification simultaneously with individual notification (500+ individuals) or annual log (under 500)
11. Media notification if 500+ residents of a state affected
12. Post-breach review and after-action report within 30 days of notification completion

---

## Related Documents

- [PHI Inventory](../phi-inventory/README.md)
- [HIPAA Gap Analysis](../gap-analysis/README.md)
- [HIPAA Safeguards](../safeguards/README.md)
- [Business Associate Agreements](../baa-templates/README.md)
- [Breach Response Plan](../breach-response/README.md)
- [FedRAMP Architecture Diagrams](https://github.com/enechi-njeze/cloudvault-fedramp-ato/blob/main/ssp-attachments/att-02-data-flow/README.md)
- [NIST RMF Categorization](https://github.com/enechi-njeze/cloudvault-nist-rmf/blob/main/step1-categorize/README.md)

---

*Prepared by Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, CompTIA Security+ SY0-701, CHP, CSCS, CISSP (in progress)*
*ISSO / ISSM, CloudVault Federal Health Exchange (FHX)*
*[LinkedIn](https://www.linkedin.com/in/enechi-njeze) | [Portfolio](https://github.com/enechi-njeze)*
