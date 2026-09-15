# Phase 2: Infrastructure as Code (IaC) & Cloud FinOps

> **Duration:** Weeks 14 – 26 (Quarter 2)  
> **Target Certifications:** **HashiCorp Terraform Associate (003)** ($70 USD) + **FinOps Certified Practitioner (FOCP)** ($300 USD)  
> **Revenue Target:** Earn $\ge \$800$ USD via Cloud Cost Optimization Sprints  
> **The Accounting-Engineering Bridge:** Uniting Infrastructure as Code with financial discipline and cloud unit economics.

---

## 🧠 Part 1: The Production Teaching Plan

### Weeks 14–19: Infrastructure as Code (Terraform / OpenTofu)
- **HCL Syntax & Providers:** Resource blocks, data sources, variables, outputs, and provider configuration.
- **Enterprise State Architecture:** Remote S3 state storage, DynamoDB distributed locking table, state migration, and resolving state drift.
- **Modularization:** Writing composable child modules for VPCs, RDS, and compute clusters. Parameterized inputs and reusable outputs.
- **CI/CD Integration for IaC:** GitHub Actions workflow executing `terraform fmt -check`, `tflint`, speculative `terraform plan` on Pull Requests, and gated `terraform apply` upon merge.

### Weeks 20–24: Cloud Financial Management (The FinOps Framework)
- **The FinOps Lifecycle:** Inform (visibility and allocation), Optimize (rates and usage), Operate (continuous governance).
- **Cost Allocation & Metadata:** AWS Cost Allocation Tags (Environment, CostCenter, Owner, BusinessUnit). Generating and parsing the AWS Cost and Usage Report (CUR).
- **Rate Optimization (Financial Engineering):** Compute Savings Plans vs EC2 Instance Savings Plans vs Standard Reserved Instances (break-even analysis, commitment risk, amortization).
- **Usage Optimization:** Rightsizing compute, unattached EBS volume deletion, S3 Intelligent-Tiering and lifecycle expiration policies, identifying idle RDS instances.
- **Shift-Left Cost Estimation:** Integrating **Infracost** into GitHub Actions to comment estimated monthly cost diffs directly on pull requests before code is merged.

---

## 🏆 Part 2: Capstone Proof-of-Work: "AetherFinOps"

### Title: "AetherFinOps: Modular Terraform Platform with Automated Infracost CI/CD & Cost Governance"
- **Overview:** Refactoring the entire AetherCloud infrastructure into 100% auditable, modular Terraform code equipped with automated budget guardrails.
- **Core Deliverables:**
  1. Complete Terraform repository provisioning VPC, ALB, and RDS across `dev` and `prod` environments with zero manual AWS console clicks.
  2. GitHub Actions PR pipeline running Infracost, posting automated monthly dollar impact directly into PR comments.
  3. Cost Allocation Tagging policy enforced via Terraform validation rules (blocking deployment if `CostCenter` tag is missing).
  4. Executive FinOps Case Study: Demonstrating a 32% simulated cost reduction through automated rightsizing and Savings Plan modeling.

---

## 💰 Part 3: The Monetization Engine (Target: Earn ≥ $800 USD)

### Service Offer: "The 48-Hour Startup AWS Bill Reduction Sprint" ($600 – $1,000)
- **Target Audience:** Startups spending between $3,000 and $20,000/month on AWS who lack a dedicated DevOps or FinOps engineer.
- **Guarantee:** You guarantee to find at least 20% in annual run-rate cloud savings, or the audit is completely free.
- **The Deliverable:** A 6-page FinOps executive presentation breaking down immediate quick wins (unattached storage, idle test databases) and long-term rate optimization (Savings Plans).
- **Proposal Pitch:**
  > *"Hi [Founder/CFO], As an engineer with a background in financial accounting, I routinely see startups overpay AWS by 25–35% due to unattached EBS volumes, oversized RDS instances, and lack of Savings Plans.  
  > I offer a fixed-fee 48-hour Cloud Cost Sprint for $750. I review your AWS billing reports and architecture, and deliver an actionable reduction plan with step-by-step implementation. If I cannot find at least $5,000 in annualized savings for your business, you owe me nothing. Can I inspect your billing dashboard this week?"*

---

## 🎓 Part 4: The Certification Gates: Terraform + FinOps FOCP
- **HashiCorp Terraform Associate (003):** $70 USD.
- **FinOps Certified Practitioner (FOCP):** $300 USD (Administered by the Linux Foundation / FinOps Foundation).
- **Total Voucher Cost:** $370 USD (Funded 100% by your first FinOps consulting client).
