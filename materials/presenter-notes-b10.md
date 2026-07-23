# Presenter notes - Builder b10: Capstone, the whole pipeline

**Length:** 60 min (capstone) · **Track:** Builder (b1-b10) · **Running case:** Daybreak coffee

## Preflight (before class)
- **Budget 60 min, not 45.** Three build demos plus a wrap. Watch the clock at the 18-min and 48-min marks.
- Open `courses/b10-capstone.html` and press **Run** on Demo 1 once to cache the ~8 MB DuckDB engine before class.
- **Demo 2 re-extracts on purpose:** the database is fresh per box, so Demo 2 lands the Parquet files again before transforming. Say this out loud so nobody thinks Demo 1's files carried over.
- Run Demo 2 twice yourself and confirm `days` and `total_revenue` do not change - that is the idempotency beat.
- Run Demo 3 and confirm the `served_revenue/month=2026-03` partition reads back with rows. Projector zoom on; check the full-pipeline SVG reads from the back.

## Run of show
1. **0-6 · Brief + recap.** State the brief: build the pipeline that feeds the warehouse. Walk the full-pipeline SVG once.
2. **6-18 · Demo 1, extract + land.** Everyone lands three tables to Parquet and reads counts back.
3. **18-33 · Demo 2, transform defensively.** Build the idempotent daily table. Run it twice live - point at the unchanged numbers.
4. **33-48 · Demo 3, serve.** Build the served table, write it partitioned by month, read one partition. This is the handoff line.
5. **48-60 · Wrap.** What they built vs the a-track twin; where next (warehouse, dataops, sql); the honest gap list.

## Never cut
- Running Demo 2 twice. Idempotency is only real when they see the numbers hold.
- Demo 3's partition read-back. That is the literal "warehouse loads this" moment.
- The honest gap list (no orchestration, CI, monitoring, live Spark/Kafka here).

## Cut if long
- The wrap self-study card can be a spoken 2-minute close.
- Demo 1's counts summary can be glanced at rather than dwelt on; the landing is the point.

## Likely questions
- *"Why re-extract in every demo?"* Fresh DB per box, and it mirrors reality - a real run starts from the source too.
- *"Where does the warehouse take over?"* At the served, partitioned Parquet dataset. DE stops; modeling begins (learn-data-warehouse).
- *"Is this production-ready?"* The logic is. It still needs orchestration, monitoring, and CI - that is learn-dataops.
- *"Local files as an object store?"* Swap the local path for an S3/GCS path in real DuckDB; same COPY and read pattern.
