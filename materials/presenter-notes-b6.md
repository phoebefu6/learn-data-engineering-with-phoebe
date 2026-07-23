# Presenter notes - Builder session 6: Streaming and CDC

**Runtime:** 45 min · **Track:** Builder (b6 of 10) · **Chip:** 🟠 · **Live engine:** DuckDB-WASM

## Preflight (do before class)
- Open `courses/b6-streaming-and-cdc.html` and press **▶ Run** on ONE sqlbox to download and cache the ~8 MB DuckDB engine before class. First run otherwise stalls ~20s on the projector.
- Confirm you are online: engine loads from the jsDelivr CDN on first run only.
- Click "Expand all", verify every card opens, then collapse.
- Toggle "Projector zoom: on" for large rooms.

## Run of show
- **0-3 min · Recap (Part 0).** Pipeline now does batch end to end; today we add the other clock - streaming.
- **3-9 min · Streaming model + CDC (Part 1).** Walk the SVG: unbounded log, consumer offset, then CDC turning a DB's change log into a stream. Anchor the CDC-beats-re-querying real-world box.
- **9-14 min · Micro-batch (Part 2).** Run the one-window box. Make the point: streaming/micro-batch process "the slice since my last offset," not everything.
- **14-18 min · Tools (Part 3).** Log vs processor vs CDC. Kafka + Kinesis read-only snippets - honestly "needs a cluster, not here." Name Debezium. Point ops to learn-dataops.
- **18-32 min · Demo 1.** Everyone runs the two-window micro-batch and "advances the offset." Tie back to Spark Structured Streaming doing this loop automatically.
- **32-42 min · Demo 2.** Q1 re-window by week (live). Q2 join stream to customers (live). Q3 the latency-changes-a-decision test - discuss aloud.
- **42-45 min · Q&A + homework.**

## Never cut
- Demo 1's two-window "advance the offset" run. It makes the streaming mental model concrete on tools they know.
- Q3's decision test. It is the anti-hype takeaway that keeps them from over-engineering.

## Cut if long
- Either of the two "exactly-once vs at-least-once" self-study cards (Part 1 or Part 2) - marked self-study.
- Kinesis snippet can be skipped if Kafka one already landed the log idea.

## Likely questions
- *"Are we really streaming in DuckDB?"* No - we honestly SIMULATE a stream with windowed batch queries. True streaming needs a cluster; we teach the model, not the ops.
- *"Batch vs micro-batch vs streaming - how do I choose?"* The Q3 test: does lower latency change a decision? Milliseconds → streaming; minutes fine → micro-batch; nobody acts till tomorrow → batch.
- *"Is CDC the same as incremental ingestion (b3)?"* Related but lighter: b3 re-queries changed rows; CDC streams them off the DB's transaction log with near-zero source load.
- *"Why does idempotency keep coming up?"* Retries are routine in streaming (at-least-once), so windows must be safe to re-process - the b5 discipline, now essential.
