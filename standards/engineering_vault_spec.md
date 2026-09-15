# Engineering Knowledge Vault & Obsidian Specification

> **The Second Brain:** In a high-velocity 365-day program, your memory will fail you if you don't maintain a networked knowledge system. This vault is your personal engineering operating system.

---

## 📂 Vault Folder Architecture

```text
personal-engineering-vault/
├── 00-Meta/
│   ├── Financial-Ledger.md          <-- Earning vs Certification voucher tracking
│   ├── Sprint-Dashboard.md          <-- Weekly 365-day countdown and tasks
│   └── Certification-Tracker.md     <-- Exam dates, diagnostics, and badges
├── 01-Daily-Logs/                   <-- Daily 30-minute execution check-in
│   └── 2026-W01-D01.md
├── 02-Core-Concepts/                <-- Atomic concept notes linked via [[wikilinks]]
│   ├── Systems/
│   ├── Networking/
│   ├── Cloud-DevOps/
│   ├── Data-AI/
│   └── Cybersecurity/
├── 03-Lab-Reports/                  <-- Hands-on exercises and debugging logs
├── 04-Architecture-ADRs/            <-- Architectural Decision Records for PoW
└── 05-Client-Deals/                 <-- Client scopes, proposals, and deliverables
```

---

## 📝 Template 1: Architecture Decision Record (ADR)

Use this format for every technical decision in your Proof-of-Work capstones:

```markdown
# ADR-001: [Title of Architectural Decision, e.g., Choosing Redis Streams over Kafka for PulseEngine]

**Status:** [Proposed | Accepted | Superseded]  
**Date:** [YYYY-MM-DD]  
**Deciders:** [Your Name]  
**Technical Domain:** [Backend / Distributed Systems / Messaging]

## 1. Context & Problem Statement
[Describe the problem and constraints. What throughput is needed? What are the hosting budget limitations?]

## 2. Decision Drivers
- Need sub-50ms queue latency.
- Must operate within a single $20/mo AWS ElastiCache instance to maintain low operational costs.
- Require consumer group offset tracking and automatic retries.

## 3. Considered Options
1. **Option 1: Apache Kafka:** High throughput, but requires complex multi-broker ZooKeeper/KRaft cluster with high baseline memory (>2GB RAM).
2. **Option 2: AWS SQS:** Serverless, but adds ~30ms network roundtrip latency per poll and lacks flexible fan-out consumer groups.
3. **Option 3: Redis Streams:** Sub-millisecond latency, minimal memory overhead, built-in consumer groups, already used for caching.

## 4. Decision Outcome
**Chosen Option:** Redis Streams.  
**Justification:** Given our Phase 1 scale target of 2,000 events/sec, Redis Streams delivers superior latency while running on our existing Redis cache instance, saving ~$80/month in infrastructure costs compared to managed Kafka.

## 5. Known Trade-Offs & Mitigation
- *Trade-off:* Redis stores streams in RAM; unbounded stream growth can cause OOM.
- *Mitigation:* Configured `MAXLEN ~ 100000` trimming policy on message ingestion to cap stream memory to 250MB.
```

---

## 💰 Template 2: Financial Ledger & Certification Gate Tracker

Keep an active financial ledger tracking your self-funding progress:

```markdown
# Self-Funding Financial Ledger

## 🎯 Target 1: AWS Solutions Architect Associate ($150 USD)
- **Minimum Required Client Earnings:** $300 USD
- **Current Fund Balance:** $0 USD
- **Status:** [Locked 🔒]

| Date | Client / Source | Service Delivered | Gross Revenue | 40% Cert Fund | Running Fund Balance | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| YYYY-MM-DD | Upwork Client A | Postgres Index Optimization | $250.00 | $100.00 | $100.00 | First client win |
| YYYY-MM-DD | Contra Client B | Stripe Webhook Integration | $200.00 | $80.00 | $180.00 | Exam unlocked! |

*Voucher Purchased on:* [Date]  
*Exam Scheduled for:* [Date]  
*Official Score & Badge Link:* [Link]
```

---

## ⏱️ Template 3: Daily Sprint Execution Log

A quick 5-minute markdown entry filled out at the end of each day:

```markdown
# Daily Log: [YYYY-MM-DD] (Day X / 365)

- **Hours of Deep Work:** [e.g., 3.5 hrs]
- **Core Concept Mastered:** [e.g., TCP sliding window & Congestion control algorithms]
- **Code Pushed:** [GitHub Commit URL]
- **Market Outreach Sent:** [e.g., 2 Upwork proposals submitted on query optimization]
- **Daily Bottleneck / Lesson:** [What broke today and how did you resolve it?]
```
