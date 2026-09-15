# Phase 3: Data Engineering, Big Data & Applied AI Systems

> **Duration:** Weeks 27 – 39 (Quarter 3)  
> **Primary Disciplines:** Data Science, Artificial Intelligence, Business Intelligence, Information Systems  
> **Revenue Target:** Earn $\ge \$800 - \$1,500$ USD  
> **Target Certifications:** **Databricks Certified Data Engineer Associate/Professional ($200)** or **Snowflake SnowPro Core ($175)** + **Databricks GenAI Engineer / GCP ML Engineer ($200)**

---

## 🧠 Part 1: The Production Teaching Plan

### Weeks 27–28: Modern Data Warehousing & Dimensional Modeling (dbt & SQL)
- **OLTP vs OLAP:** Row-oriented vs columnar storage formats (Parquet, ORC), compression techniques (Snappy, Zstandard), vectorized query execution.
- **Dimensional Modeling:** Kimball methodology (Fact tables, Dimension tables, Slowly Changing Dimensions Type 1, 2, and 3, Surrogate keys, Star vs Snowflake schema).
- **dbt (data build tool):** Authoring modular SQL transformations, Jinja macros, dbt seeds, incremental models (`is_incremental()`), schema testing, and lineage documentation generation.

### Weeks 29–30: Distributed Data Processing with Apache Spark (PySpark)
- **Spark Internal Engine:** Driver vs Executors, SparkContext, Catalyst Query Optimizer, Tungsten execution engine, DAG execution stages and shuffle boundaries.
- **DataFrames & SQL:** PySpark transformations (`select`, `filter`, `groupBy`, `agg`, `window`), broadcast hash joins vs sort-merge joins, mitigating partition data skew via salting.
- **Performance Tuning:** Managing partitions (`repartition` vs `coalesce`), caching strategies (`MEMORY_AND_DISK`), resolving out-of-memory driver/executor errors.

### Weeks 31–32: Lakehouse Architecture & Table Formats (Delta Lake / Iceberg)
- **The Lakehouse Paradigm:** Combining the reliability of data warehouses with the low cost of object storage.
- **Delta Lake Internals:** The transaction log (`_delta_log` JSON/Parquet checkpointing), ACID compliance on S3/Blob storage, schema enforcement and schema evolution, unified batch and streaming.
- **The Medallion Architecture:** Bronze (raw ingest), Silver (cleaned, deduplicated, enriched), and Gold (business-level aggregations and feature stores). Time-travel queries and data rollback.

### Weeks 33–34: Production Data Orchestration & Streaming (Airflow & Kafka)
- **Workflow Orchestration (Airflow / Dagster):** Writing robust DAGs, tasks, dynamic task mapping, sensors, upstream/downstream triggers, idempotent backfills, and secret management.
- **Real-Time Streaming (Kafka / Redpanda):** Topic partitioning, producer acks, consumer groups, offset commit management, dead letter queues, and exactly-once processing semantics.

### Weeks 35–37: Applied AI Systems, Vector Databases & Production RAG
- **Vector Embeddings:** Semantic search mechanics, cosine similarity vs dot product, distance metrics, dense vs sparse representations.
- **Vector Storage & Indexing:** HNSW (Hierarchical Navigable Small World) graph indexes, IVFFlat, vector indexing with `pgvector`, Qdrant, or Pinecone.
- **Production Retrieval-Augmented Generation (RAG):**
  - Chunking strategies (semantic chunking, recursive character splitting, metadata enrichment).
  - Hybrid Search: Combining BM25 keyword search with dense vector embeddings via Reciprocal Rank Fusion (RRF).
  - Cross-Encoder Reranking: Reranking top-K chunks with Cohere or BGE-reranker for high precision.
  - Multi-hop reasoning with AI Agents (tool calling, structured output extraction via Pydantic).
- **LLM Evaluation & Guardrails:** Automated hallucination detection, context recall, faithfulness scoring using Ragas / TruLens, and NeMo Guardrails.

---

## 🛠️ Part 2: Hands-on Practice Labs

1. **Lab 3.1 (dbt Transformation & Quality Gates):** Build a dbt project transforming raw e-commerce event streams into analytical Kimball Star Schema tables. Write automated tests for uniqueness, non-null, and referential integrity that block pipeline execution if flawed data arrives.
2. **Lab 3.2 (PySpark Medallion Lakehouse):** Process 20GB of raw streaming event logs using PySpark and Delta Lake. Implement schema evolution to handle unexpected incoming columns, optimize storage with `OPTIMIZE` and `Z-ORDER BY`, and demonstrate a time-travel query restoring data to an earlier state.
3. **Lab 3.3 (Enterprise Hybrid RAG System):** Ingest 50 technical PDF manuals. Implement chunking with metadata tagging, embed into `pgvector`, execute hybrid search + reranking, and run an automated evaluation script calculating answer relevancy and faithfulness scores.

---

## 🏆 Part 3: The Capstone Proof-of-Work Project

### Title: "NexusData: Real-Time Streaming Analytics & Enterprise Multimodal RAG Platform"

- **Overview:** An end-to-end data platform combining real-time streaming ingestion, an automated Medallion lakehouse, and an enterprise knowledge retrieval agent with continuous evaluation.
- **Architecture Stack:**
  - Ingestion: Apache Kafka / Redpanda event broker
  - Processing: PySpark / Delta Lake (Medallion architecture)
  - Transformation & Modeling: dbt core
  - Orchestration: Apache Airflow (running in Docker)
  - Vector Engine & LLM: `pgvector` + FastAPI + OpenAI/Anthropic/DeepSeek API + Cohere Reranker
  - Monitoring: Ragas evaluation metrics + Grafana dashboard tracking pipeline lag and LLM token costs.
- **Required Proof-of-Work Standards:**
  - Live deployed query interface with public URL.
  - Public GitHub repository with reproducible `docker-compose` environment.
  - Automated Ragas test report documenting >0.85 faithfulness score across 100 test queries.
  - Architectural RFC documenting cost per 100,000 processed events.

---

## 💰 Part 4: The Monetization Engine (Target: Earn ≥ $800 – $1,500)

Data pipelines and AI integrations are top-priority investments for businesses in 2025/2026:

### Channel A: "Custom Enterprise Internal Document RAG Assistant" ($600 – $1,200)
- Target: Legal firms, accounting agencies, medical clinics, or customer support teams with large volumes of internal documentation.
- Deliverable: A private, secure RAG web app allowing their staff to query internal SOPs and manuals with source citations, deployed to their private cloud.

### Channel B: "Automated Data Ingestion & Reporting Pipeline" ($400 – $800)
- Target: E-commerce brands running multiple Shopify/Amazon stores needing unified sales reporting.
- Deliverable: Automated pipeline extracting data from APIs, transforming with dbt, loading into PostgreSQL/Snowflake, and generating automated daily Google Sheets / Slack summaries.

### Pitch Template for Corporate Document AI:
> *"Hi [Managing Partner / COO], I noticed your team manages extensive compliance documentation and standard operating procedures. In my experience, professionals waste 4–6 hours a week searching through PDFs for specific policy clauses.  
> I build secure, private search assistants that allow your team to instantly query your internal documents and receive exact answers with cited page references, with zero data shared publicly. I can build and deploy a working prototype on your internal documents in 5 days for a fixed fee of $750. Here is a live demo of my document retrieval engine: [link]. Can I show you how it works on Thursday?"*

---

## 🎓 Part 5: The Certification Target

### Track Option 1: Databricks Certified Data Engineer Associate / Professional
- **Exam Cost:** $200 USD.
- **Validation:** Validates enterprise mastery of Apache Spark, Delta Lake, Lakehouse architecture, and data pipelines on Databricks.
- **Preparation:** Complete Databricks Academy labs and achieve $\ge 85\%$ on official practice exam questions.

### Track Option 2: Snowflake SnowPro Core Certification
- **Exam Cost:** $175 USD.
- **Validation:** World standard for cloud data warehousing, virtual warehouses, caching, data sharing, and security.

### Track Option 3: Databricks Generative AI Engineer Associate or GCP ML Engineer
- **Exam Cost:** $200 USD.
- **Validation:** Proves technical capability to build, deploy, evaluate, and monitor production RAG and LLM systems.
