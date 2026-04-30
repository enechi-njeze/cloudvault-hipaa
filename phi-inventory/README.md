# PHI Inventory

**System:** CloudVault Federal Health Exchange (FHX)
**Repository:** cloudvault-hipaa
**Folder:** phi-inventory
**Framework Reference:** HIPAA Security Rule 45 CFR 164.310(d)(2)(iii) / HITECH Act
**Document ID:** FHX-HIPAA-PHI-001
**Prepared By:** Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, Security+, CHP, CSCS, CISSP (in progress)
**Role:** ISSO / ISSM, CloudVault Federal Health Exchange
**Last Updated:** April 2025
**Status:** Active

---

## Purpose

Every HIPAA-covered entity and business associate is required to maintain a comprehensive inventory of all Protected Health Information (PHI) it creates, receives, maintains, or transmits. For a federal health data exchange platform like CloudVault FHX, which processes PHI on behalf of 47 federal agencies and 890,000+ patient records, this requirement takes on heightened significance.

This folder documents the PHI data inventory for CloudVault FHX. The inventory identifies where PHI exists across all system components, how it flows between systems and users, what safeguards protect it at each stage, and how its lifecycle is managed from creation through secure disposal. Completing this inventory is a foundational step in conducting the HIPAA-required risk analysis under 45 CFR 164.308(a)(1)(ii)(A).

A real GRC professional uses the PHI inventory to answer three questions regulators and auditors will always ask: What PHI do you have? Where does it go? How is it protected at every point in its lifecycle?

---

## Documents in This Folder

| Document | Description | Reference | Status |
|---|---|---|---|
| phi-inventory-master.md | Master inventory of all PHI data elements by system component | 45 CFR 164.310(d)(2)(iii) | Active |
| phi-data-flow-map.md | End-to-end data flow diagram narrative with ingestion, processing, and egress paths | 45 CFR 164.308(a)(1)(ii)(A) | Active |
| phi-data-classification.md | Classification tiers for PHI, PII, CUI, FTI, and PCI by sensitivity level | NIST SP 800-53 RA-2 | Active |
| phi-disposal-procedures.md | Secure disposal and sanitization procedures for PHI at end of lifecycle | 45 CFR 164.310(d)(2)(i) | Active |
| phi-location-register.md | Registry of all storage locations, repositories, and services where PHI resides | 45 CFR 164.308(a)(1)(ii)(A) | Active |

---

## PHI Data Elements Inventory

The following categories of PHI are created, received, maintained, or transmitted by CloudVault FHX across its integrated AWS GovCloud infrastructure. All 18 HIPAA-defined PHI identifiers are assessed below.

| PHI Identifier | Present in System | Data Elements | Primary Storage Location | Encryption | Retention Period |
|---|---|---|---|---|---|
| Names | Yes | Patient legal name, preferred name | RDS Aurora (encrypted), S3 (SSE-KMS) | AES-256 at rest, TLS 1.3 in transit | 7 years post-encounter |
| Geographic data | Yes | Address, ZIP+4, county, state | RDS Aurora | AES-256 | 7 years |
| Dates (except year) | Yes | DOB, admission date, discharge date, service date | RDS Aurora, DynamoDB | AES-256 | 7 years |
| Phone numbers | Yes | Home, mobile, emergency contact | RDS Aurora | AES-256 | 7 years |
| Fax numbers | Yes | Provider fax numbers linked to patient records | RDS Aurora | AES-256 | 7 years |
| Email addresses | Yes | Patient portal email, provider email | RDS Aurora, SES (transit only) | TLS 1.3 | 7 years |
| Social security numbers | Yes | SSN (partial, last 4 digits for identity matching) | RDS Aurora (tokenized) | AES-256, tokenization | 7 years |
| Medical record numbers | Yes | Agency-assigned MRN, FHX universal patient ID | RDS Aurora, DynamoDB | AES-256 | 7 years |
| Health plan beneficiary numbers | Yes | Federal health plan IDs, Medicaid/Medicare IDs | RDS Aurora | AES-256 | 7 years |
| Account numbers | Yes | Patient billing account, agency billing reference | RDS Aurora | AES-256 | 7 years |
| Certificate/license numbers | Yes | Provider NPI, DEA number | RDS Aurora | AES-256 | 7 years |
| Vehicle identifiers | No | Not collected by FHX | N/A | N/A | N/A |
| Device identifiers | Yes | Medical device IDs linked to patient records | DynamoDB | AES-256 | 7 years |
| Web URLs | Yes | Patient portal activity logs (anonymized in SIEM) | CloudWatch Logs | AES-256 | 2 years |
| IP addresses | Yes | Access logs for audit trail | CloudWatch Logs, S3 | AES-256 | 2 years |
| Biometric identifiers | No | Not collected by FHX | N/A | N/A | N/A |
| Full-face photographs | No | Not collected by FHX | N/A | N/A | N/A |
| Other unique identifiers | Yes | Federal agency enrollment IDs, tribal IDs | RDS Aurora | AES-256 | 7 years |

---

## PHI Data Flow Summary

CloudVault FHX processes PHI across four primary stages. Understanding this flow is required for conducting the HIPAA risk analysis and for mapping safeguard coverage to each stage.

**Stage 1: Ingestion**
PHI enters FHX through three channels: (1) HL7 FHIR R4 API calls from 47 federal agency EHR systems; (2) secure file transfers via SFTP over AWS Transfer Family; and (3) patient portal submissions via the FHX web application. All ingestion channels require mutual TLS authentication and operate over encrypted connections within the AWS GovCloud FedRAMP High boundary.

**Stage 2: Processing and Storage**
Ingested PHI is validated, de-duplicated, and stored in Amazon RDS Aurora (PostgreSQL, encrypted with AWS KMS). Structured clinical data is indexed in DynamoDB for fast retrieval. Audit logs are shipped to CloudWatch Logs and archived to S3 Glacier. All PHI at rest uses AES-256 encryption with keys managed through AWS KMS under a FHX-dedicated Customer Master Key (CMK).

**Stage 3: Exchange and Transmission**
PHI is transmitted to authorized agency partners via FHIR R4 API responses (TLS 1.3), secure messaging through the FHX provider portal, and batch exports to agency data warehouses via encrypted S3 pre-signed URLs with 15-minute expiry. All transmission paths are logged to CloudTrail for audit trail purposes.

**Stage 4: Archival and Disposal**
PHI is retained for a minimum of 7 years per federal records retention requirements. At end of retention, PHI is purged using secure deletion procedures (NIST SP 800-88 Rev 1 Guidelines for Media Sanitization). S3 objects are overwritten and deleted with audit log confirmation. RDS snapshots are destroyed using AWS KMS key deletion procedures. Disposal records are maintained in the PHI disposal log for audit evidence.

---

## PHI Location Register

| System Component | PHI Type | AWS Service | Region | Encryption Key | Data Owner | Backup? |
|---|---|---|---|---|---|---|
| Patient records database | All 18 identifier types except vehicle/biometric/photo | RDS Aurora (PostgreSQL) | us-gov-west-1 | KMS CMK fhx-phi-rds-key | Dr. Patricia Owens | Yes: daily snapshots, 30-day retention |
| Clinical document store | Clinical notes, lab results, imaging metadata | S3 (fhx-clinical-docs-govcloud) | us-gov-west-1 | SSE-KMS fhx-phi-s3-key | Dr. Patricia Owens | Yes: S3 Cross-Region Replication |
| Fast-access clinical index | MRN, dates, encounter IDs | DynamoDB (fhx-clinical-index) | us-gov-west-1 | AWS Managed Key | Dr. Patricia Owens | Yes: point-in-time recovery |
| Audit and access logs | IP addresses, access timestamps, user IDs | CloudWatch Logs | us-gov-west-1 | CloudWatch encryption | Enechi P.C. Njeze | Yes: exported to S3 |
| Long-term archive | All PHI post-active retention | S3 Glacier (fhx-archive) | us-gov-west-1 | SSE-KMS fhx-archive-key | Dr. Patricia Owens | Yes: Vault Lock enabled |
| Temporary processing cache | PHI during API transaction processing | ElastiCache (Redis, in-transit and at-rest encrypted) | us-gov-west-1 | In-transit TLS, at-rest KMS | Enechi P.C. Njeze | No: ephemeral, TTL 30 min |

---

## Data Classification Tiers

CloudVault FHX applies the following data classification tiers to all data elements. PHI is always classified at Restricted or higher.

| Classification | Description | Examples in FHX | Handling Requirement |
|---|---|---|---|
| Top Sensitive | Combined PHI/PII with federal tax information (FTI) or financial account data | SSN + diagnosis, beneficiary number + financial data | Tokenization required, dual-person access for exports, legal hold capable |
| Restricted | Standard PHI, PII, CUI | Patient names, DOB, MRN, diagnoses, prescriptions | AES-256 encryption, role-based access, audit logging mandatory |
| Sensitive | Aggregated or de-identified data, statistical summaries | ZIP-code-level health statistics, anonymized access logs | Encryption at rest, access logging |
| Internal | System configuration, operational metadata | Infrastructure logs, deployment manifests | Access restricted to FHX operations team |
| Public | Published FHX documentation, public health statistics | FHX public API documentation, published metrics | No PHI, no PII, no CUI |

---

## PHI Disposal Procedures

All PHI disposal follows NIST SP 800-88 Rev 1 and HIPAA 45 CFR 164.310(d)(2)(i). The following procedures apply by media type.

| Media Type | Disposal Method | Verification | Documentation |
|---|---|---|---|
| RDS database records | Secure delete via SQL purge + snapshot deletion | KMS key deletion receipt from AWS | Disposal record in PHI disposal log |
| S3 objects | Object overwrite + delete with versioning disabled at time of deletion | S3 deletion confirmation logged to CloudTrail | CloudTrail event ID recorded in disposal log |
| S3 Glacier archives | Vault policy expiry + explicit delete after lock expiry | Glacier inventory report post-deletion | Archive expiry record |
| ElastiCache (Redis) | TTL expiry (30 minutes), flushdb command for manual purge | Cache miss confirmation after purge | Operational log entry |
| Physical media (if applicable) | DoD 5220.22-M standard wipe, certificate of destruction from AWS | AWS certificate of destruction | Certificate retained in disposal log |
| Backup snapshots | AWS KMS CMK deletion after key schedule | KMS key deletion confirmation | KMS deletion event logged to CloudTrail |

---

## Related Documents

- [HIPAA Gap Analysis](../gap-analysis/README.md)
- [HIPAA Safeguards Implementation](../safeguards/README.md)
- [Business Associate Agreement Templates](../baa-templates/README.md)
- [Breach Response Plan](../breach-response/README.md)
- [FHX PHI Data Flow Diagram](../diagrams/README.md)
- [FedRAMP SSP Attachment: Data Flow Diagram](https://github.com/enechi-njeze/cloudvault-fedramp-ato/blob/main/ssp-attachments/att-02-data-flow/README.md)
- [NIST RMF Categorization Package](https://github.com/enechi-njeze/cloudvault-nist-rmf/blob/main/step1-categorize/README.md)

---

## Portfolio Note

This PHI inventory demonstrates competency in HIPAA data governance for a complex federal health exchange environment. It reflects real-world practice for a GRC professional managing PHI across a FedRAMP High, multi-agency cloud platform where data flows cross jurisdictional, regulatory, and organizational boundaries simultaneously.

---

*Prepared by Enechi P.C. Njeze, CGRC, CISA, CISM, PMP, PMI-RMP, CompTIA Security+ SY0-701, CHP, CSCS, CISSP (in progress)*
*ISSO / ISSM, CloudVault Federal Health Exchange (FHX)*
*[LinkedIn](https://www.linkedin.com/in/enechi-njeze) | [Portfolio](https://github.com/enechi-njeze)*
