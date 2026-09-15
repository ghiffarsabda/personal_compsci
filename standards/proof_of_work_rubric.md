# Proof-of-Work (PoW) Quality Rubric & Portfolio Standards

> **The Hiring Truth:** Engineering managers and high-paying clients do not read resumes or care about multiple-choice course quizzes. They look for undeniable, reproducible evidence that you can build, operate, troubleshoot, and scale production systems under pressure.

---

## 🏛️ The 6 Pillars of Production-Grade Proof-of-Work

Every capstone project submitted in this curriculum must pass this rigorous rubric to qualify as an accredited milestone.

```
       ┌─────────────────────────────────────────────────────────┐
       │             ENTERPRISE PROOF-OF-WORK PILLARS            │
       └────────────────────────────┬────────────────────────────┘
         ┌───────────────┬──────────┴──────────┬───────────────┐
         ▼               ▼                     ▼               ▼
   [System RFC &]   [Automated CI/CD]    [Live Production] [Observability]
   [Architecture]   [+ IaC Manifests]    [+ Custom Domain] [& Benchmarks]
         │               │                     │               │
         └───────────────┴──────────┬──────────┴───────────────┘
                                    ▼
                      [Hardened Security & IAM]
                      [+ Public Case Study & Video]
```

---

### Pillar 1: Architectural RFC & Decision Records (ADR)
- **Requirement:** The repository must include an `rfc/` or `docs/adr/` directory containing at least 3 formal Architecture Decision Records.
- **Content:**
  - *Context & Problem Statement:* Why was this architecture chosen?
  - *Considered Options:* What alternatives were evaluated (e.g. Postgres vs DynamoDB, REST vs gRPC)?
  - *Decision Outcome & Trade-offs:* What are the known drawbacks, bottlenecks, and costs?
  - *Mermaid.js Diagrams:* Component diagrams, sequence diagrams for critical paths, and data flow charts.

### Pillar 2: Reproducible Infrastructure-as-Code & Multi-Stage Builds
- **Requirement:** Zero manual configuration ("ClickOps") in cloud consoles.
- **Content:**
  - Complete Terraform or OpenTofu manifests for all VPCs, subnets, databases, compute clusters, and DNS records.
  - Multi-stage Dockerfile adhering to distroless or Alpine-based micro-images (final image size < 50MB for Go/Rust, < 150MB for Node/Python).
  - Single-command local spin-up via `docker-compose.yml` that provisions mock S3 (LocalStack), Postgres with seed data, and Redis.

### Pillar 3: Continuous Integration & Automated Delivery (CI/CD)
- **Requirement:** Production-grade GitHub Actions or GitLab CI pipeline.
- **Content:**
  - Automated linting, type-checking, and unit testing on every Pull Request.
  - Integration tests executed against ephemeral Docker database containers (using Testcontainers).
  - Automated security vulnerability scanning (`trivy` for container images, `gitleaks` for credentials, `snyk` or `audit` for dependencies).
  - Automated deployment triggers upon merge to `main` with rollback safety.

### Pillar 4: Live Production Environment & Custom Domain
- **Requirement:** No `localhost:3000` or raw IP addresses (`http://192.241.x.x`).
- **Content:**
  - Deployed to real cloud compute (AWS ECS/EKS, GCP Cloud Run/GKE, Fly.io, or Hetzner VPS).
  - Custom domain with automated TLS/SSL certificate renewal via Cloudflare or Let's Encrypt.
  - Custom HTTP 404/500 error pages and zero exposed stack traces to the public.

### Pillar 5: Observability, Telemetry & Load Stress Testing
- **Requirement:** You must know when the application breaks before a user reports it.
- **Content:**
  - Structured JSON logging with trace correlation IDs injected into request headers.
  - OpenTelemetry / Prometheus metrics endpoint (`/metrics`) instrumented for request rate, error rate, and duration (RED method).
  - Pre-configured Grafana dashboard JSON export committed directly in the repository.
  - Automated K6 or Locust performance test script executing a 1,000-user concurrent spike test, with the resulting latency percentile graph (p50, p95, p99) committed to the repo README.

### Pillar 6: Security Hardening & Zero-Trust Posture
- **Requirement:** Hardened against OWASP Top 10 vulnerabilities.
- **Content:**
  - Zero plain-text credentials; all secrets injected via environment variables, HashiCorp Vault, or AWS Secrets Manager.
  - Strict Content Security Policy (CSP), CORS, Rate Limiting (Redis token bucket algorithm), and SQL injection defenses (parameterized queries).
  - Principle of least privilege enforced for database connection roles and cloud IAM roles.

---

## ⚖️ Toy Project vs. Enterprise Proof-of-Work

| Feature | Junior / Student "Toy Project" | **Enterprise-Grade Proof-of-Work** |
| :--- | :--- | :--- |
| **Authentication** | Basic JWT stored in `localStorage` | HTTP-only encrypted cookies, refresh token rotation, OAuth2/OIDC, CSRF protection |
| **Database** | Raw SQLite or unindexed MongoDB | PostgreSQL with custom B-tree / GIN indexes, connection pooler (PgBouncer), schema migrations |
| **Error Handling** | `try { ... } catch (e) { console.log(e) }` | Centralized middleware, typed error classes, error reporting to Sentry, sanitized client responses |
| **Deployment** | Vercel free tier with default settings | AWS ECS/Fargate or K8s with auto-scaling, health checks (`/healthz`), zero-downtime rolling updates |
| **Testing** | Zero tests or 2 trivial assertion tests | Unit test suite (>80% core logic coverage), end-to-end Playwright tests, load test benchmarks |
| **Documentation** | Default `create-react-app` README | Comprehensive System Architecture, API spec (OpenAPI/Swagger), load test reports, ADRs |

---

---

## 🏛️ The Aether Compounding Suite (Your 365-Day Portfolio)

Instead of 4 random, disconnected toy projects, you build and compound a single enterprise platform:

1. **Q1: AetherCloud** — Multi-AZ AWS infrastructure, custom VPC, private database subnets, ALB, multi-AZ RDS with automated failover.
2. **Q2: AetherFinOps** — Full Terraform modularization of AetherCloud + Infracost CI/CD cost checks + AWS Cost Allocation tag validation rules.
3. **Q3: AetherAudit** — Continuous Cloud Compliance Engine evaluating AetherCloud against AICPA SOC 2 Type II and SOX 404 ITGC controls via AWS Config and OPA.
4. **Q4: AetherEnterprise** — Publication-grade TOGAF 10 Enterprise Architecture Blueprint modeling business capabilities, cloud transition roadmap, and 3-year financial TCO forecast.

