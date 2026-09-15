# Phase 3: Information Systems Audit, ITGC & SOC 2 Cloud Compliance

> **Duration:** Weeks 27 – 39 (Quarter 3)  
> **Target Certification:** **ISACA CISA (Certified Information Systems Auditor)** ($575 USD) or **CompTIA Security+** ($392 USD)  
> **Revenue Target:** Earn $\ge \$1,200$ USD via SOC 2 / ITGC Readiness Consulting  
> **The Auditor's Domain:** Translating accounting audit methodology into cloud infrastructure controls and regulatory compliance.

---

## 🧠 Part 1: The Production Teaching Plan

### Weeks 27–30: IT General Controls (ITGC) & Financial Statement Auditing (SOX 404)
- **The Audit Process:** Professional audit standards, audit charter, risk-based audit planning, sampling methodology, materiality thresholds, and testing of controls (Design vs Operating Effectiveness).
- **ITGC Core Domains:**
  1. *Access to Programs and Data:* User access provisioning/deprovisioning, quarterly access reviews, privileged access management (PAM), segregation of duties (SoD) between developers and production.
  2. *Program Changes (Change Management):* Formal pull request approvals, automated CI/CD deployment logs, emergency change procedures, and separation of `dev`, `staging`, and `production`.
  3. *Computer Operations:* Automated backup verification, disaster recovery testing, and incident response procedures.
  4. *Program Development:* Secure software development lifecycle (SSDLC) and code reviews.

### Weeks 31–34: SOC 2 Type II & Security Compliance Frameworks
- **AICPA Trust Services Criteria:** Security (common criteria), Availability, Processing Integrity, Confidentiality, and Privacy.
- **Type I vs Type II:** Point-in-time design evaluation vs 6-to-12 month historical operating effectiveness evidence.
- **Automated Cloud Audit Mechanics:**
  - AWS CloudTrail: Multi-region immutable logging, log file integrity validation, S3 bucket lock, and CloudWatch alert alarms for unauthorized API calls.
  - AWS Config & Conformance Packs: Automated drift detection against CIS AWS Foundations Benchmark.
  - AWS Security Hub: Centralized compliance scoring against PCI-DSS and NIST SP 800-53.

---

## 🏆 Part 2: Capstone Proof-of-Work: "AetherAudit"

### Title: "AetherAudit: Automated Cloud Compliance Engine & SOC 2 Evidence Dossier"
- **Overview:** An automated compliance engine that continuously audits the *AetherCloud* AWS infrastructure against SOC 2 Type II controls and generates audit-ready markdown evidence dossiers for external auditors.
- **Core Deliverables:**
  1. Policy-as-Code rules written in Open Policy Agent (OPA) or AWS Config verifying that all S3 buckets are encrypted, all EBS volumes are encrypted with KMS, and zero Security Groups permit open SSH (`0.0.0.0/0`).
  2. Automated Python audit script extracting quarterly IAM access lists, flagging inactive users (>90 days) and users lacking MFA.
  3. Formal "SOC 2 Type II Readiness & ITGC Audit Dossier" (PDF/Markdown) presenting control descriptions, evidence screenshots, testing procedures, and remediation roadmaps.

---

## 💰 Part 3: The Monetization Engine (Target: Earn ≥ $1,200 USD)

### Service Offer: "The Pre-Audit SOC 2 Readiness Assessment" ($1,000 – $2,500)
- **Target Audience:** B2B SaaS startups that must achieve SOC 2 Type II compliance to close six-figure enterprise sales contracts, but cannot afford $25,000 traditional consulting firms.
- **The Deliverable:** A comprehensive gap analysis matrix identifying failed controls, unencrypted data stores, and weak change management policies, accompanied by a 30-day remediation blueprint.
- **Proposal Pitch:**
  > *"Hi [Founder/CTO], Enterprise customers demand SOC 2 Type II certification before signing six-figure contracts, but preparing for a formal audit often stalls engineering teams for months.  
  > Combining an accounting audit background with certified cloud architecture experience, I conduct rapid Pre-Audit SOC 2 Gap Analyses. I review your AWS environment, IAM policies, and GitHub change management workflows, delivering an auditor-ready remediation checklist in 5 business days for a fixed investment of $1,250. Here is a sample audit dossier from my portfolio: [AetherAudit link]. Let's jump on a brief call this week."*

---

## 🎓 Part 4: The Certification Gate: ISACA CISA
- **Cost:** $575 USD (ISACA Member rate).
- **Prestige:** The globally acknowledged gold-standard credential for IT audit and control assurance.
- **Prerequisite:** Funded 100% by your first SOC 2 / ITGC readiness client.
