# Presenter notes - Builder session 2: Connect and extract

**Session:** b2 of b1-b10 · 45 min · builder track
**One-line goal:** learners leave able to name the six source shapes and land any of them to a file they control.

## Run-of-show (45 min)
- **0-3 · Recap.** Callback to b1: five stages. "Today we zoom into the first seam: generation into ingestion." Show the Part 0 pipeline recap.
- **3-9 · Part 1, the source zoo.** Walk the SVG. Land the golden rule hard: you extract FROM sources, never change them. Open the first card live.
- **9-15 · Part 2, relational extract.** Run the trimmed-projection box. Contrast with SELECT *. Then run the "dropped file" CSV round trip.
- **15-20 · Part 3, JSON.** Run the customers-to-JSON box. Talk APIs from the self-study card (rate limits, pagination) - concept only, be honest the browser cannot call APIs.
- **20-30 · Demo 1.** Everyone runs the three-shape ingest script. Point at the count summary: "this proves each source landed."
- **30-42 · Demo 2.** Q1 and Q2 hands-on; Q3 discuss out loud (decoupling, replay, not hammering prod).
- **42-45 · Q&A + quiz.**

## Preflight
- Open the page and **press Run once before class** to cache the ~8 MB DuckDB engine - otherwise the first learner Run stalls on download.
- Projector zoom on; expand-all off (reveal cards live).
- Confirm all six sqlboxes run green on your machine first.
- Have b1 open in a tab for the recap callback.

## Never cut
- The golden rule (read, never change the source).
- Demo 1 - it is the whole session's payoff.
- The column-discipline point (don't drag columns you won't use).

## Cut if long
- Part 3 self-study API card - point to it and move on.
- Demo 2 Q2 - assign as homework.
- The Part 1 self-study "why the zoo exists" card.

## Likely questions
- *"Can DuckDB actually call our API?"* No - browsers can't; that's why APIs are concept here. Real pipelines land raw JSON to files first, then parse.
- *"Why not just query the source every time?"* Decoupling, replay, not hammering prod (that is literally Q3).
- *"Is CSV or Parquet better to land in?"* Great question - that's the whole of session b4. Defer.
- *"Where do the tables come from?"* Daybreak's OLTP source, same brand as the SQL and warehouse courses.
