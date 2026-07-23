<!-- learn-with-phoebe hub banner -->
> ### 📚 Part of [**Learn with Phoebe**](https://phoebefu6.github.io/learn-with-phoebe/)
> The shelf of 38 free, hands-on courses on AI, data, and the craft around them. **[Browse every course ↗](https://phoebefu6.github.io/learn-with-phoebe/)**
<!-- /learn-with-phoebe hub banner -->

# learn-data-engineering-with-phoebe

A two-track, interactive data engineering course you run **in your browser**. You learn by building
the pipeline that feeds **Daybreak** - the coffee-subscription brand from
[learn-sql-with-phoebe](https://phoebefu6.github.io/learn-sql-with-phoebe/) and
[learn-data-warehouse-with-phoebe](https://phoebefu6.github.io/learn-data-warehouse-with-phoebe/).
Daybreak has a warehouse now, but nothing reliably feeds it - so its OLTP database plays the source
system, and session by session you connect to it, extract cleanly, choose formats, transform in
batch and stream, engineer storage, and build the reliability seam that serves the warehouse. Every
builder page runs **real DuckDB** via WebAssembly: editable code that reads CSV, JSON, and Parquet,
converts formats, partitions, and moves data over 300,000 rows - a production pipeline in a tab.

**Live site:** https://phoebefu6.github.io/learn-data-engineering-with-phoebe/

By Phoebe Fu.

## Two tracks

### 🤝 Leader track (a1-a6) - execs and managers, no code, 6 x 45 min

| Session | Title | Difficulty |
|---------|-------|------------|
| a1 | What data engineering is | 🟢 easy |
| a2 | Source systems | 🟢 easy |
| a3 | Batch vs streaming | 🟡 medium |
| a4 | Build vs buy the stack | 🟡 medium |
| a5 | Storage engineering | 🟡 medium |
| a6 | The DE org and roadmap | 🟡 medium |

### 🛠️ Builder track (b1-b10) - practitioners, live DuckDB, 45 min each (b10: 60)

| Session | Title | Difficulty |
|---------|-------|------------|
| b1 | The lifecycle in one pipeline | 🟢 easy |
| b2 | Connect and extract | 🟡 medium |
| b3 | Ingestion patterns | 🟡 medium |
| b4 | File and table formats | 🟡 medium |
| b5 | Batch transformation | 🟡 medium |
| b6 | Streaming and CDC | 🟡 medium |
| b7 | Storage engineering | 🟠 hands-on |
| b8 | Distributed processing | 🟠 hands-on |
| b9 | Reliability seams | 🔴 hardest |
| b10 | Capstone: the whole pipeline | 🔴 hardest |

Start at [`index.html`](index.html).

## How the live playground works

`assets/de-live.js` turns every playground on a builder page into an editable box running
**DuckDB-WASM** - real DuckDB, a full analytical engine, compiled to WebAssembly. It reads CSV,
JSON, and Parquet, converts between formats, partitions, and moves data exactly like a production
pipeline. The engine loads **once from a CDN (about 8 MB)** - that is the one network dependency,
stated honestly. After that first load everything runs client-side: the Daybreak source data
(`assets/de-seed.js`) is generated in your browser, every query executes locally, and nothing you
type can break the next example. Where a real stage needs **Spark, Kafka, or Airflow** - which
cannot run in a browser - you see the real code as a clearly marked read-only snippet, never faked.
No install, no cluster, no bill.

## Built from official curricula - honestly

This course is built from the DeepLearning.AI Data Engineering Professional Certificate (Joe Reis)
and Reis & Housley's *Fundamentals of Data Engineering*. It teaches the working core of those
curricula through one running project - the pipeline that feeds Daybreak's warehouse - but it does
not replace them: the certificates, graded labs, AWS exercises, and videos stay on the official
platforms, and if you want the credential, go earn it there. This is the **deng-bucket capstone**:
it deliberately builds only the pipeline. Modeling what the data becomes lives in
learn-data-warehouse; scheduling and monitoring the pipeline in production is handed off to
learn-dataops.

## Prerequisites and siblings

- [learn-sql-with-phoebe](https://phoebefu6.github.io/learn-sql-with-phoebe/) - the query language, and where the Daybreak database comes from; take it first
- [learn-data-warehouse-with-phoebe](https://phoebefu6.github.io/learn-data-warehouse-with-phoebe/) - models what your pipeline serves; runs alongside this course
- [learn-dataops-with-phoebe](https://phoebefu6.github.io/learn-dataops-with-phoebe/) - schedules and monitors what you build; the natural next step

## Structure

```
index.html                     two-track landing + knowledge mindmap
courses/a1..a6-*.html          leader track
courses/b1..b10-*.html         builder track
assets/style.css               design system (teal + copper)
assets/app.js                  engagement layer (progress, quizzes, zoom)
assets/mindmap.js              the knowledge map on the landing page
assets/de-live.js              the live DuckDB pipeline engine
assets/de-seed.js              the Daybreak source data generator
materials/                     source coverage notes
```

## Local preview

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

by Phoebe Fu
