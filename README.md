# Phishing Incident Response Lab

## Overview

This project simulates the investigation and response workflow of a SOC analyst handling phishing-related security incidents. The lab progresses through three investigation scenarios of increasing complexity, including credential phishing, malicious attachment analysis, and a full Microsoft 365 account-compromise investigation.

The investigations demonstrate email-header analysis, SPF/DKIM/DMARC interpretation, IOC identification and enrichment, safe file analysis, Microsoft 365 authentication review, post-compromise activity analysis, data-exfiltration investigation, MITRE ATT&CK mapping, incident classification, containment, and remediation.

All domains, IP addresses, accounts, files, and incident artifacts used throughout this project are simulated or reserved training values. No real credentials, malware, accounts, or organizational data were used.

## Investigation Cases

### [Case 01 — Credential Phishing Investigation](cases/case-01-credential-phishing/)
Investigated a simulated Microsoft 365 credential-phishing email by analyzing sender information, Reply-To discrepancies, SPF/DKIM/DMARC results, phishing indicators, URLs, and other IOCs. The case focused on distinguishing email authentication from actual sender legitimacy and documenting an evidence-based final disposition.

### [Case 02 — Malicious Attachment Investigation](cases/case-02-malicious-attachment/)
Investigated a simulated phishing email containing a suspicious double-extension attachment. Performed safe file-hash comparison, file-signature analysis, readable-content analysis, and simulated sandbox behavior analysis without executing real malware. The investigation mapped observed behaviors to MITRE ATT&CK and developed containment and remediation recommendations.

### [Case 03 — Full Phishing Incident Investigation](cases/case-03-full-incident-investigation/)
Conducted an end-to-end investigation of a simulated credential-phishing incident that progressed to Microsoft 365 account compromise. Correlated reported credential submission with authentication activity, identified a Conditional Access configuration gap, investigated post-compromise mailbox and OneDrive activity, and confirmed the unauthorized download of three Confidential or Restricted financial files.

The incident was classified as **High severity** based on confirmed account compromise and data exfiltration.

## Skills Demonstrated

- Phishing email triage and investigation
- Email header analysis
- SPF, DKIM, and DMARC interpretation
- IOC identification and enrichment
- URL and domain analysis
- Safe file hash and file-signature analysis
- Static malware analysis and simulated sandbox behavior analysis
- Microsoft 365 authentication investigation
- MFA and Conditional Access analysis
- Cloud account compromise investigation
- Post-compromise mailbox and OneDrive analysis
- Data exfiltration investigation
- MITRE ATT&CK mapping
- Incident severity classification
- Containment and remediation planning
- Evidence-based SOC incident reporting

## Repository Structure

```text
Phishing-Incident-Response-Lab/
├── cases/
│   ├── case-01-credential-phishing/
│   ├── case-02-malicious-attachment/
│   └── case-03-full-incident-investigation/
├── iocs/
│   ├── case-01-iocs.txt
│   ├── case-02-iocs.txt
│   └── case-03-iocs.txt
└── reports/
    ├── case-01-incident-report.txt
    ├── case-02-incident-report.txt
    └── case-03-incident-report.txt
```
### Investigation Artifacts

**Indicators of Compromise:** [Case 01](iocs/case-01-iocs.txt) | [Case 02](iocs/case-02-iocs.txt) | [Case 03](iocs/case-03-iocs.txt)

**Incident Reports:** [Case 01](reports/case-01-incident-report.txt) | [Case 02](reports/case-02-incident-report.txt) | [Case 03](reports/case-03-incident-report.txt)
## Key Lessons

- Successful SPF, DKIM, and DMARC authentication does not prove that an email is legitimate. An attacker-controlled lookalike domain can have correctly configured authentication records.
- Email authentication evidence should be evaluated alongside sender identity, Reply-To domains, URLs, message content, and user-reported activity.
- A suspicious attachment should not be executed simply to determine whether it is malicious. Hashing, file-signature analysis, static analysis, and authorized sandboxing provide safer investigation methods.
- Geographic anomalies alone do not prove account compromise. Authentication telemetry, device information, user activity, and subsequent account behavior should be correlated.
- An MFA result of "Not Satisfied" does not automatically indicate MFA bypass. In Case 03, investigation showed that the expected Conditional Access policy was not applied and no MFA challenge was issued.
- File access alone does not establish data exfiltration. Successful file-download audit events provided the evidence needed to confirm transfer of the three identified files.
- Password reset alone may not fully contain a compromised cloud account. Active sessions and authentication tokens should also be revoked.

## Project Outcome

This project demonstrates a structured SOC investigation workflow across three phishing scenarios of increasing complexity. The investigations progressed from email triage and authentication analysis to malicious attachment investigation and finally to a full cloud account-compromise incident involving unauthorized access and confirmed data exfiltration.

The project emphasizes evidence-based analysis, careful distinction between observed and inferred activity, MITRE ATT&CK mapping, appropriate incident classification, and practical containment and remediation decisions.
