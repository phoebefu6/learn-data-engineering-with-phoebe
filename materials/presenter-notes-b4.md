# Presenter notes - Builder session 4: File and table formats

**Session:** b4 of b1-b10 · 45 min · builder track
**One-line goal:** learners leave able to choose CSV/JSON/Parquet on purpose and explain what table formats add.

## Run-of-show (45 min)
- **0-3 · Recap.** Callback to b2/b3: "you've been landing data - as CSV, JSON, Parquet - without saying why. Today we make that choice on purpose." Frame it as the storage stage.
- **3-9 · Part 1, row vs columnar.** Walk the comparison SVG (readability/size/scan speed). Open the "why columnar is fast" card; land the 3-of-200-columns image.
- **9-15 · Part 2, round trips.** Run the one-table-three-formats box; point at typeof showing Parquet keeps DATE, CSV doesn't. Run the subset-from-Parquet box.
- **15-20 · Part 3, table formats.** Concept only. ACID + schema evolution + time travel on top of Parquet = lakehouse. Be honest: not live here, DuckDB reads plain Parquet; Iceberg/Delta need engines.
- **20-30 · Demo 1.** Everyone runs the bake-off. Equal row counts, different date type - that's the payoff.
- **30-42 · Demo 2.** Q1 and Q2 hands-on (round-trip + verify, filtered aggregate); Q3 discuss "when JSON is right" out loud.
- **42-45 · Q&A + quiz.**

## Preflight
- Open the page and **press Run once before class** to cache the ~8 MB DuckDB engine before any learner Runs.
- Verify the typeof comparison renders (parquet -> DATE, csv -> VARCHAR) on your machine.
- Projector zoom on; expand-all off.
- Have the learn-data-warehouse link ready for the lakehouse handoff.

## Never cut
- Demo 1 bake-off - the typeof difference is the whole lesson.
- The "format is a cost + speed decision" framing.
- The honest "table formats not live here" note (credibility).

## Cut if long
- Part 3 is already self-study - summarise in 60 seconds if short on time.
- Demo 2 Q2 (filtered aggregate) - homework.
- Part 1 self-study "when readable formats win" card.

## Likely questions
- *"Why did my CSV date come back as text?"* CSV stores no types; everything re-parses on read. That's exactly why Parquet exists for the analytical core.
- *"Can DuckDB read Iceberg/Delta?"* Plain Parquet natively, yes; Iceberg/Delta need extensions or engines like Spark/Trino - not in this browser.
- *"So is JSON always wrong?"* No - it's right for nested, still-changing source data (Q3). JSON at the messy edge, Parquet at the stable core.
- *"Where's the deep dive on lakehouse tables?"* learn-data-warehouse course - this session just names what they do.
