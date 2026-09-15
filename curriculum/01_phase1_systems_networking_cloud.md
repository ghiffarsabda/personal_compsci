# Phase 1: Cloud Architecture Foundations, Networking & Resilient Infrastructure

> **Duration:** Weeks 01 – 13 (Quarter 1)  
> **Target Certification:** **AWS Certified Solutions Architect – Associate (SAA-C03)** ($150 USD)  
> **Revenue Target:** Earn $\ge \$400$ USD via Startup Architecture Reviews  
> **Foundation Milestone:** Understanding how modern enterprise cloud infrastructure works under the hood.

---

## 🧠 Part 1: The Production Teaching Plan

### Weeks 01–04: Enterprise Cloud Networking & Linux
- **Linux Operations:** Command-line fluency, SSH key management, systemd services, bash scripting for automated server setup.
- **VPC Network Architecture:** Non-overlapping CIDR block planning (`10.0.0.0/16`), public subnets, private compute subnets, isolated database subnets across 3 Availability Zones (Multi-AZ).
- **Gateways & Routing:** Internet Gateways (IGW), NAT Gateways (and why they cost so much), Route Tables, Elastic IPs, VPC Peering vs AWS Transit Gateway.
- **DNS & Edge Delivery:** Route 53 (latency-based, failover, and weighted routing policies), AWS CloudFront CDN, and SSL/TLS management via AWS Certificate Manager (ACM).

### Weeks 05–08: Identity, Compute & High-Availability Data
- **Identity & Access Management (IAM):** IAM users vs roles, permission boundaries, least privilege policy JSON authoring, cross-account access, and mandatory MFA.
- **Compute Scalability:** EC2 instance families (compute, memory, general purpose), Launch Templates, Application Load Balancer (ALB) health checks, and Auto Scaling Groups (ASG).
- **Persistent Data Tier:** Amazon RDS PostgreSQL Multi-AZ synchronous replication, read replicas, automated snapshots, and Amazon S3 storage classes (Standard, Infrequent Access, Glacier Instant Retrieval).

---

## 🏆 Part 2: Capstone Proof-of-Work: "AetherCloud"

### Title: "AetherCloud: High-Availability Multi-AZ Enterprise Cloud Infrastructure"
- **Architecture Stack:** AWS (VPC, ALB, Auto Scaling EC2/ECS, RDS PostgreSQL Multi-AZ, S3, CloudWatch).
- **Core Deliverables:**
  1. A multi-tier, multi-AZ VPC topology deployed on AWS with zero public access to database subnets.
  2. Automated disaster recovery drill: killing the primary RDS database node and documenting sub-60-second automated failover to the standby replica.
  3. Load-tested ALB setup: scaling compute nodes dynamically from 2 to 6 instances under synthetic HTTP load.
  4. Architecture Decision Record (ADR-001): Network topology, subnet calculation, and security group isolation rules.

---

## 💰 Part 3: The Monetization Engine (Target: Earn ≥ $400 USD)

### Service Offer: "The Startup AWS Architecture & Resilience Audit" ($350 – $500 flat fee)
- **Target Audience:** Seed/Series A B2B startups running on single-instance EC2 or single-AZ RDS who cannot afford downtime.
- **The Deliverable:** A 5-page "Cloud Resilience & High Availability Report" reviewing their VPC, database failover readiness, and single points of failure, delivered in 72 hours.
- **Proposal Pitch:**
  > *"Hi [Founder/CTO], I noticed your platform handles mission-critical transactions for your clients. In early-stage architectures, running on a single AWS availability zone creates a major risk of unexpected outages during AWS regional disruptions.  
  > I conduct rapid, 72-hour AWS Resilience Reviews to identify single points of failure in your VPC, ensure automated database failover, and harden IAM access policies. Here is my public architecture reference: [AetherCloud link]. Can I review your staging setup this week for a flat fee of $400?"*

---

## 🎓 Part 4: The Certification Gate: AWS SAA-C03
- **Cost:** $150 USD (Funded 100% by your first client review).
- **Passing Standard:** Score $\ge 85\%$ across 6 TutorialDojo practice exams before taking the official proctored test.
