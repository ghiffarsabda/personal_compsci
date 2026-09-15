# Phase 1: Systems, Networking & Cloud-Native Engineering

> **Duration:** Weeks 01 – 13 (Quarter 1)  
> **Primary Disciplines:** Computer Science, Software Engineering, Network Engineering, Cloud Infrastructure  
> **Revenue Target:** Earn $\ge \$300 - \$600$ USD  
> **Target Certifications:** **AWS Certified Solutions Architect Associate (SAA-C03)** or **Cisco CCNA (200-301)** / **Linux Foundation LFCS**

---

## 🧠 Part 1: The Production Teaching Plan

### Weeks 01–02: Linux Kernel, OS Internals & Systems Programming
- **Process Architecture:** Process creation (`fork`, `execve`), process states, signals (`SIGTERM`, `SIGKILL`, `SIGHUP`), zombie and orphan processes, PID namespaces.
- **Memory & Storage:** Virtual memory, paging, swap space, page faults, buffer cache, inodes, file descriptors, `/proc` and `/sys` virtual filesystems.
- **Service Management:** Writing custom `systemd` service units, socket activation, logging via `journald`, resource limits with `cgroups` (CPU/Memory quotas).
- **Practical Shell Tooling:** `strace` (syscall tracing), `lsof` (file descriptor inspection), `htop`/`glances`, `awk`, `sed`, `jq`, structured bash scripting.

### Weeks 03–04: Computer Networking & Internet Protocols
- **Network Layering:** Deep dive into the TCP/IP stack vs OSI model. Packet encapsulation and decapsulation.
- **Transport Protocols:** TCP 3-way handshake, SYN floods, TCP sliding window, congestion control algorithms (CUBIC, BBR), UDP vs TCP latency trade-offs.
- **Routing & Subnetting:** IPv4 CIDR notation (`/24`, `/28`, `/16`), subnet masks, default gateways, ARP protocol, VLAN tagging, OSPF and BGP routing fundamentals.
- **Application Protocols:** DNS resolution hierarchy (root, TLD, authoritative nameservers, caching), HTTP/1.1 vs HTTP/2 multiplexing vs HTTP/3 (QUIC/UDP), TLS 1.3 cryptographic handshake (ECDHE, session tickets).
- **Diagnostics:** Live packet analysis using `tcpdump`, `wireshark`, `dig +trace`, `traceroute`, `mtr`, and `curl -v` timing flags.

### Weeks 05–06: High-Concurrency Backend Engineering (Go & PostgreSQL)
- **Go Systems Engineering:**
  - Goroutines vs OS threads, Go runtime M:N scheduler, channel patterns (fan-in, fan-out, worker pools, pipeline pattern).
  - Context package for request timeouts, cancellation propagation, and distributed tracing metadata.
  - Memory allocation (stack vs heap), zero-allocation serializers, profiling with `pprof`.
- **PostgreSQL Database Internals:**
  - Storage engine: Heap tables, WAL (Write-Ahead Logging), MVCC (Multi-Version Concurrency Control) and vacuuming.
  - Indexing: B-Tree internal node structure, composite indexes, partial indexes, GIN indexes for JSONB, index bloat.
  - Query Optimization: Parsing `EXPLAIN (ANALYZE, BUFFERS)` execution plans, detecting sequential scans, fixing nested loops with hash joins.
  - Concurrency: Transaction isolation levels (Read Committed vs Repeatable Read vs Serializable), row-level locking (`SELECT FOR UPDATE`), deadlock mitigation.

### Weeks 07–08: AWS Cloud Architecture Fundamentals
- **Zero-Trust Network Design:** Custom VPC creation from scratch, non-overlapping CIDR blocks, public vs private subnets, Internet Gateways, NAT Gateways, Route Tables.
- **Security & Compute:** IAM Least Privilege policies, Role-based access, Security Groups (stateful) vs Network ACLs (stateless), EC2 vs ECS Fargate serverless containers.
- **High Availability & Storage:** Application Load Balancer (ALB) path-based routing, target groups, health checks, S3 lifecycle policies, RDS Multi-AZ deployments with read replicas.

---

## 🛠️ Part 2: Hands-on Practice Labs

1. **Lab 1.1 (Systems):** Write a production-grade background worker daemon in Go that manages child processes, intercepts `SIGTERM` for graceful connection draining (5s timeout), and is managed via a systemd unit with memory limits (max 128MB).
2. **Lab 1.2 (Networking):** Build a basic raw socket packet sniffer that captures incoming TCP SYN packets, parses the IP/TCP headers, and logs source IPs exhibiting port scanning behavior.
3. **Lab 1.3 (Database Optimization):** Populate a PostgreSQL database with 5,000,000 synthetic e-commerce orders. Write a slow complex analytical query (taking >3.5s), diagnose it with `EXPLAIN ANALYZE`, design a compound index + materialized view, and reduce latency to <15ms.
4. **Lab 1.4 (Cloud Infrastructure):** Deploy a multi-AZ AWS VPC manually using the AWS CLI (no console clicking), complete with private subnets, NAT gateway, and an EC2 instance reachable only through an SSM Session Manager tunnel.

---

## 🏆 Part 3: The Capstone Proof-of-Work Project

### Title: "PulseEngine: High-Throughput Distributed Webhook & Event Dispatcher"

- **Overview:** A multi-tenant SaaS backend service capable of receiving, queueing, retrying, and delivering external webhooks with cryptographic signature verification and Stripe-based metered billing.
- **Architecture Stack:**
  - Language: Go (Fastify/Node.js is an acceptable alternative)
  - Primary DB: PostgreSQL (partitioned event logs by tenant)
  - Queue / Buffer: Redis Streams or RabbitMQ
  - Deployment: AWS ECS Fargate + RDS PostgreSQL + ElastiCache Redis, fronted by ALB
  - Observability: Prometheus `/metrics` endpoint + Grafana Cloud + structured JSON logs with trace IDs.
- **Required Proof-of-Work Standards:**
  - Automated GitHub Actions CI that boots ephemeral Postgres and Redis testcontainers.
  - Exponential backoff retry logic with jitter for dead webhook endpoints.
  - K6 benchmark demonstrating sustained 1,500 requests/second with $p99 < 40\text{ms}$.
  - Architecture Decision Record (ADR) detailing why Redis Streams was selected over Kafka for this throughput tier.

---

## 💰 Part 4: The Monetization Engine (Target: Earn ≥ $300 – $600)

You must secure paying clients or bounties to fund your certification voucher:

### Channel A: Targeted Upwork / Contra Gigs (Fixed Price $150 – $300 each)
- **Niche 1: Database Performance Tuning**
  - Search queries: *"Slow Postgres query", "Fix RDS CPU 100%", "Optimize SQL database"*.
  - Deliverable: Analyze client's slow query log, add indexes, configure PgBouncer connection pooling, deliver before/after latency report.
- **Niche 2: Webhook & Third-Party API Integration**
  - Search queries: *"Stripe webhook failed", "Shopify to Postgres sync", "HubSpot API integration"*.
  - Deliverable: Robust webhook listener with signature verification and retry queue.

### Pitch Template for Database Optimization:
> *"Hi [Client Name], I noticed your PostgreSQL CPU is spiking to 100% during traffic surges. This is almost always caused by missing composite indexes causing sequential table scans, or unbounded database connection spikes.  
> In my recent projects, I routinely optimize query execution plans using EXPLAIN ANALYZE, dropping query latency from seconds to under 20ms. I can inspect your top 5 slowest queries today, add the exact required indexes, and configure connection pooling. If I cannot measurably reduce your query latency, you owe nothing. Available to begin immediately."*

### Channel B: Niche Web Scraping & Pipeline Automation ($200 – $400)
- Find non-technical agencies, realtors, or e-commerce stores needing automated daily data extraction. Deliver automated Python/Go scripts deployed on AWS Lambda with Discord/Slack notifications.

---

## 🎓 Part 5: The Certification Target

### Primary Option: AWS Certified Solutions Architect – Associate (SAA-C03)
- **Exam Cost:** $150 USD (Funded by your first 1–2 freelance gigs).
- **Core Focus Areas:** Resilient architectures (34%), High-performing architectures (24%), Secure architectures (30%), Cost-optimized architectures (12%).
- **Diagnostic Protocol:** Score $\ge 85\%$ across 6 TutorialDojo practice exams before scheduling.

### Alternative Option: Cisco CCNA (200-301) or Linux Foundation LFCS
- **Exam Cost:** $300 – $395 USD (Funded by landing 2–3 freelance contracts).
- **Validation:** Proves deep foundational networking or Linux systems administration to enterprise recruiters.
