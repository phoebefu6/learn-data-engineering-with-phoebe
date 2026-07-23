# learn-data-engineering-with-phoebe - official course map

Built 2026-07-22. Build-first mode: from verified public syllabi; Phoebe's platform notes slot
in at NOTES-SLOT markers. Re-verify tool/vendor specifics before delivery (fast-moving space).

## Scope contract (locked with Phoebe, 2026-07-22)

- **Lane = ingestion + movement + transform compute + storage engineering + lifecycle framing.**
  This is the deng-bucket capstone (diff 4), the rung ABOVE learn-data-warehouse.
- **Owns:** the DE lifecycle (generate -> ingest -> store -> transform -> serve) + undercurrents;
  source systems (relational / files / APIs / logs / object storage / streams); ingestion
  patterns (batch vs streaming, full vs incremental, CDC, watermarks); file + table formats
  (CSV / JSON / Parquet / Iceberg / Delta); transform compute (ELT-in-engine vs distributed
  Spark); storage engineering (partitioning, tiers, distributed/object storage); distributed
  processing model; the reliability seam that hands off to DataOps.
- **Explicitly NOT here (points out to siblings):**
  - orchestration, CI/CD, monitoring, data-quality testing, IaC, culture -> `learn-dataops`
    (its b2 orchestration, b3 testing/contracts, b6-b8 deploy/observability/IaC already own this;
    note DLAI DE C2 modules 3-4 are literally "DataOps" + "Orchestration" - deliberately ceded).
  - dimensional modeling, star schema, SCD, marts, warehouse tuning -> `learn-data-warehouse`
  - SQL language itself -> `learn-sql`
  - ML feature engineering / serving-for-ML -> ds-bucket courses
- **Running case:** Daybreak coffee (chain: `learn-sql` -> `learn-data-warehouse` ->
  **`learn-data-engineering`**). Daybreak's OLTP tables are the source system being ingested;
  this course builds the pipeline that FEEDS the warehouse built in the sibling course.
- **Live layer:** `de-live.js` + `de-seed.js` (renamed copies of the warehouse course's
  DuckDB-WASM engine; globals still `window.DW_SEED` / `window.DW_SETUPS`). DuckDB genuinely
  runs in-browser: reads CSV/JSON/Parquet, converts formats via COPY round trips, partitions,
  incremental filters, 300k-row scale demos. Spark / Kafka / Kinesis / Airflow / dlt CANNOT run
  in a browser -> shown as READ-ONLY code snippets with an honest "runs on a cluster, not here"
  note. Engine loads once from jsDelivr CDN (~8 MB, cached).
- **Hub:** bucket `deng`, diff 4. Flips the existing `status: planned` placeholder to live.
  Ladder: sql (2) -> data-modeling (3, planned) -> data-warehouse (3, live) ->
  **data-engineering (4)** -> dataops (4, live).

## Source universe (verified syllabi, fetched 2026-07-22)

| # | Source | Role in this course |
|---|--------|---------------------|
| S1 | DLAI **Intro to Data Engineering** (C1, Joe Reis) | lifecycle + undercurrents + architecture + requirements-to-architecture |
| S2 | DLAI **Source Systems, Data Ingestion, and Pipelines** (C2) | source systems (M1), ingestion incl. ETL/ELT + streaming + Kinesis (M2). M3 DataOps + M4 Orchestration deliberately CEDED to learn-dataops |
| S3 | DLAI **Data Storage and Queries** (C3) | storage ingredients + tiers + distributed + row/column (M1), storage abstractions warehouse/lake/lakehouse (M2, light - warehouse owns depth), query life + streaming queries (M3, light) |
| S4 | Reis & Housley **Fundamentals of Data Engineering** (O'Reilly book) | the canonical spine + vocabulary; lifecycle framing throughout |

**Overlap discipline:** S2-M3/M4 (DataOps, orchestration) NOT taught here. S3-M2 (warehouse/
lakehouse) and S3-M3 (advanced SQL/indexes) taught only at the storage-engineering angle
(formats, tiers, physical layout), not the modeling/query-language angle owned by siblings.

## Not covered by design (honest list)

- Airflow/Dagster DAG authoring, CI/CD, monitoring, IaC, Great Expectations -> `learn-dataops`
- Star schema / SCD / marts / warehouse cost tuning -> `learn-data-warehouse`
- SQL syntax -> `learn-sql`; ML feature stores -> ds bucket
- Vendor-specific cloud console depth (AWS VPC/IAM labs from DLAI C2-M1) -> mentioned, not drilled
- Live Spark/Kafka execution (browser can't) -> read-only snippets + honest note

## Session coverage map

Legend: ✓ = taught to ~80% working depth · ◐ = touched, pointer given

### Leader track (a1-a6, 45 min, exec thinking-mode, no code)

| Session | Covers | S1 | S2 | S3 |
|---------|--------|----|----|----|
| a1 What data engineering is | the lifecycle + undercurrents; DE as plumbing under warehouse/ML/AI | ✓ M1-M2 | ◐ | ◐ |
| a2 Source systems | where data is born (DB/API/log/file/stream); you don't own them | ◐ | ✓ M1 | ◐ |
| a3 Batch vs streaming | two clocks; when real-time earns its 5-10x cost | ✓ M3 arch | ✓ M2 | ◐ M3 |
| a4 Build vs buy the stack | modern data stack (ingest/transform/compute tools); managed vs OSS | ◐ | ✓ M2 | ◐ |
| a5 Storage engineering | formats, hot/warm/cold tiers, object storage, cost | ◐ | ◐ | ✓ M1-M2 |
| a6 The DE org + roadmap | DE vs analytics-eng vs DS; feeding warehouse/ML/AI; crawl-walk-run | ✓ M4 | ◐ | ◐ |

### Builder track (b1-b10, 45 min, Daybreak, live DuckDB where runnable)

| Session | Covers | S1 | S2 | S3 |
|---------|--------|----|----|----|
| b1 The lifecycle in one pipeline | 5 stages hands-on; DuckDB reads a raw source and lands it | ✓ M2 | ◐ | ◐ |
| b2 Connect + extract | source types: relational, CSV, JSON, object storage; read each live | ◐ | ✓ M1 | ✓ M1 |
| b3 Ingestion patterns | full vs incremental, watermarks, EL boundary, batch windows | | ✓ M2 | ◐ |
| b4 File + table formats | CSV/JSON/Parquet live conversion + size/speed; Iceberg/Delta concepts | | ◐ | ✓ M1-M2 |
| b5 Batch transformation | transform compute; ELT-in-engine (DuckDB) vs Spark (snippets); idempotent | ◐ | ✓ M2 | ◐ |
| b6 Streaming + CDC | event logs, CDC, micro-batch DuckDB demo; Kafka/Kinesis snippets | ◐ M3 | ✓ M2 | ◐ M3 |
| b7 Storage engineering | partitioning physical layout, tiers, object/distributed storage; partition demo | | | ✓ M1 |
| b8 Distributed processing | the Spark/MPP model, shuffles, partitions; when single-node beats a cluster | ◐ | ◐ | ✓ M1 |
| b9 Reliability seams | schema drift, contracts, idempotency, retries - the handoff to DataOps | ◐ undercurrents | ◐ M3 | |
| b10 Capstone | Daybreak ingest -> store (Parquet) -> transform pipeline feeding the warehouse | ✓ M4 | ✓ | ✓ |

## Fetched syllabi appendix

### S1 - DLAI Introduction to Data Engineering (C1)
- M1 Introduction: lifecycle overview + key undercurrents, stakeholder needs -> requirements, cloud/AWS fundamentals
- M2 The DE Lifecycle and Undercurrents: generation in source systems, ingestion, storage, queries/modeling/transformation, serving; undercurrents = security, data management, data architecture, DataOps, orchestration, software engineering
- M3 Data Architecture: principles, batch + streaming architectures, AWS Well-Architected
- M4 Translating Requirements to Architecture: build end-to-end batch + streaming pipelines

### S2 - DLAI Source Systems, Data Ingestion, and Pipelines (C2)
- M1 Working with Source Systems: source types, relational DBs, SQL, NoSQL, ACID, object storage, logs, streaming systems, connecting to sources, IAM/networking basics
- M2 Data Ingestion: ingestion on a continuum, ETL vs ELT, REST API, streaming ingestion, Kinesis
- M3 DataOps (CEDED -> learn-dataops): automation, IaC/Terraform, observability, Great Expectations, CloudWatch
- M4 Orchestration (CEDED -> learn-dataops): evolution, Airflow DAGs/UI/XCom/Taskflow

### S3 - DLAI Data Storage and Queries (C3)
- M1 Storage Ingredients + Systems: physical components, cloud storage (block/object/file), tiers hot/warm/cold, distributed storage, how DBs store data, row vs column, graph + vector DBs
- M2 Storage Abstractions: warehouse ideas, cloud warehouses, data lakes, lakehouse (light - warehouse course owns depth)
- M3 Queries: life of a query, indexes, joins, aggregates, Redshift, row vs columnar perf, streaming queries (light - sql/warehouse own depth)

## NOTES-SLOT markers
When Phoebe finishes S1-S3 (DLAI DE cert C1-C3) and passes notes: verify each against this map,
correct gaps explicitly (comprehension check), weave her framing into a1/b1 ledes and the
"From your subscriptions" coverage rows.
