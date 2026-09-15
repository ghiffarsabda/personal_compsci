# Phase 2: DevOps, Kubernetes & Platform Engineering

> **Duration:** Weeks 14 – 26 (Quarter 2)  
> **Primary Disciplines:** Information Technology, Platform Engineering, Distributed Systems, Site Reliability Engineering (SRE)  
> **Revenue Target:** Earn $\ge \$600 - \$1,200$ USD  
> **Target Certifications:** **HashiCorp Certified Terraform Associate (003)** + **Certified Kubernetes Administrator (CKA)**

---

## 🧠 Part 1: The Production Teaching Plan

### Weeks 14–15: Container Internals & Advanced OCI Standards
- **Linux Container Foundations:** Kernel namespaces (`pid`, `net`, `mnt`, `ipc`, `uts`, `user`), control groups (`cgroups v2` for memory/CPU capping), Union File Systems (OverlayFS).
- **Hardened Image Architecture:** Multi-stage compilation builds, scratch and distroless images, non-root user execution, vulnerability scanning with `trivy`.
- **Container Runtime Interface:** OCI specifications, `runc`, `containerd`, and high-performance build techniques with Docker Buildx and cache mounts.

### Weeks 16–17: Infrastructure as Code (IaC) with Terraform & OpenTofu
- **State Management:** Remote backends (AWS S3 + DynamoDB state locking), state migration, inspecting state, importing existing unmanaged cloud resources (`terraform import`).
- **Modular Design:** Reusable module architecture, variable validation, outputs, locals, conditional resources (`count` vs `for_each`), dynamic blocks.
- **Production GitOps for IaC:** Terraform Cloud / GitHub Actions automated speculative plans on PRs, drift detection, and automated approval gates.

### Weeks 18–20: Kubernetes Deep Architecture & Cluster Administration
- **Control Plane Anatomy:** `kube-apiserver` request lifecycle (authn, authz, admission control), `etcd` raft consensus protocol and zero-downtime snapshot backups, `kube-scheduler` filtering/scoring, `kube-controller-manager`.
- **Node Level Plumbing:** `kubelet` sync loop, static pods, `kube-proxy` iptables/IPVS modes, container runtime interface (CRI).
- **Core Workloads:** Pod lifecycle (init containers, probes: liveness, readiness, startup), Deployments, StatefulSets (stable network IDs, headless services), DaemonSets, Jobs/CronJobs.
- **Networking & Ingress:** Pod-to-Pod networking (CNI: Calico/Cilium), Services (`ClusterIP`, `NodePort`, `LoadBalancer`), Ingress Controllers (Nginx Ingress, Traefik), `CoreDNS` internal service resolution.
- **Storage Subsystems:** StorageClasses, PersistentVolumes (PV), PersistentVolumeClaims (PVC), access modes (`ReadWriteOnce`, `ReadWriteMany`), CSI volume drivers.

### Weeks 21–22: Cluster Security, Resilience & SRE
- **Identity & RBAC:** User certificates, ServiceAccounts, Roles, ClusterRoles, RoleBindings, ClusterRoleBindings, context switching via `kubectl config`.
- **Traffic Isolation:** NetworkPolicies (default-deny egress/ingress, pod selectors, CIDR blocks).
- **Cluster Stability:** `PodDisruptionBudgets` (PDB), ResourceQuotas, LimitRanges, Horizontal Pod Autoscaler (HPA metrics-server), cluster autoscaling.
- **Incident Troubleshooting:** Diagnosing `CrashLoopBackOff`, `OOMKilled` (exit code 137), `ImagePullBackOff`, `Evicted` pods, Node NotReady states, viewing kubelet system logs via `journalctl -u kubelet`.

### Weeks 23–24: GitOps & Progressive Delivery
- **ArgoCD / FluxCD:** Declarative cluster state synchronized to Git, automated drift reconciliation, multi-cluster management.
- **Progressive Delivery:** Canary releases and Blue/Green rollouts using Argo Rollouts with automated metric analysis (e.g. abort rollout if HTTP 5xx error rate > 1%).
- **Configuration Management:** Helm charts authoring, templating, Chart dependencies, Helm hooks, and secret management using External Secrets Operator (integrating AWS Secrets Manager into K8s Secrets).

### Weeks 25–26: Production Observability Stack
- **Prometheus Core:** Scrape targets, relabeling configurations, custom alerts authoring, PromQL operators (`rate`, `irate`, `histogram_quantile` for p95/p99 latency).
- **Alertmanager:** Deduplication, grouping, routing alerts to PagerDuty/Slack.
- **Grafana Visualization:** Production dashboard construction adhering to the RED method (Rate, Errors, Duration) and USE method (Utilization, Saturation, Errors).

---

## 🛠️ Part 2: Hands-on Practice Labs

1. **Lab 2.1 (Docker Hardening):** Take a bloated 1.2GB legacy Python/Node monolith. Refactor it using multi-stage builds and Google Distroless down to under 80MB. Run a Trivy scan showing zero High/Critical CVEs.
2. **Lab 2.2 (Disaster Recovery Drill):** Spin up a 3-node Kubernetes cluster. Back up the live `etcd` datastore to an encrypted snapshot. Intentionally corrupt the control plane by deleting the etcd data directory. Restore the cluster from snapshot with zero data loss.
3. **Lab 2.3 (IaC Multi-Cloud Module):** Write a production-ready Terraform module that provisions a complete VPC, an EKS cluster with managed node groups, and tags resources dynamically according to enterprise cost-center standards.
4. **Lab 2.4 (Automated Canary Rollout):** Deploy an Argo Rollout pipeline. Simulate a bad release that returns 20% HTTP 500 errors. Verify that Argo Rollouts automatically detects the metric degradation, pauses the canary step, and rolls back to the previous stable release without human intervention.

---

## 🏆 Part 3: The Capstone Proof-of-Work Project

### Title: "ApexPlatform: Production GitOps Platform with Automated Canary Rollouts & Observability"

- **Overview:** A complete, production-grade cloud platform infrastructure managed 100% via code (IaC + GitOps).
- **Architecture Stack:**
  - Provisioning: Terraform / OpenTofu (modular AWS/Hetzner infrastructure)
  - Orchestration: Kubernetes (k3s or EKS)
  - GitOps Controller: ArgoCD
  - Ingress & TLS: Traefik / Nginx Ingress + `cert-manager` (Let's Encrypt automated renewal)
  - Secrets: External Secrets Operator synced with cloud KMS / Vault
  - Monitoring: Prometheus + Alertmanager + Grafana + OpenTelemetry Collector
- **Required Proof-of-Work Standards:**
  - Complete public GitHub repository with zero hardcoded credentials.
  - Video walkthrough simulating a live rolling update, inducing artificial chaos (killing node), and demonstrating automated self-healing.
  - Live Grafana dashboard URL showcasing CPU, memory, and application latency metrics.
  - Architecture Decision Record on selecting ArgoCD over manual Helm CLI deployments.

---

## 💰 Part 4: The Monetization Engine (Target: Earn ≥ $600 – $1,200)

Platform engineering and DevOps skills command immediate high-ticket client budgets:

### Channel A: "AWS Cloud Bill & Infrastructure Audit" ($300 – $500 flat fee)
- Target: Seed/Series A startups with monthly AWS bills between $1,500 and $10,000.
- Pitch: Review their infrastructure for unattached EBS volumes, oversized RDS instances, missing S3 lifecycle policies, and single points of failure.
- Offer: Guaranteed minimum 20% monthly bill reduction, or they pay nothing.

### Channel B: "Dockerizing & CI/CD Migration for Small Dev Teams" ($400 – $750 per repo)
- Target: Agencies or software shops still deploying via manual SSH or FTP.
- Deliverable: Write clean multi-stage Dockerfiles, set up GitHub Actions with automated testing and staging server deployment, and deliver a 10-minute Loom tutorial for their internal devs.

### Pitch Template for CI/CD Automation:
> *"Hi [Founder/CTO], I saw your team is hiring engineers for your web platform. Many teams at your stage lose 5–10 engineering hours each week to manual deployments and broken staging environments.  
> I specialize in setting up automated GitHub Actions pipelines with Docker caching that test, build, and deploy your releases in under 4 minutes with zero manual SSH commands. I can implement this for your main repository in 48 hours for a fixed fee of $450. Here is a link to my public platform architecture repo: [link]. Let's jump on a 10-minute call tomorrow."*

---

## 🎓 Part 5: The Certification Target

### Credential 1: HashiCorp Certified Terraform Associate (003)
- **Exam Cost:** $70 USD.
- **Focus:** Infrastructure as Code concepts, Terraform CLI commands, state manipulation, module architecture.
- **Preparation:** Complete 100 practice questions; pass with $\ge 90\%$.

### Credential 2: Certified Kubernetes Administrator (CKA)
- **Issuing Body:** Linux Foundation & Cloud Native Computing Foundation (CNCF).
- **Exam Cost:** $395 USD (Funded directly by your DevOps client retainers).
- **Exam Format:** 100% hands-on terminal command-line exam (2 hours). No multiple-choice questions.
- **Focus:** Cluster Architecture & Installation (25%), Workloads & Scheduling (15%), Services & Networking (20%), Storage (10%), Troubleshooting (30%).
- **Simulation Protocol:** You must pass the **Killer.sh** mock environment with a score of $\ge 85\%$ before taking the real proctored exam.
