# Presenter notes - Builder session 3: Ingestion patterns

**Session:** b3 of b1-b10 · 45 min · builder track
**One-line goal:** learners leave able to choose full vs incremental, write a watermark filter, and explain ELT.

## Run-of-show (45 min)
- **0-3 · Recap.** Callback to b2: "you can land a source once. But pipelines run daily - re-copying everything is wasteful." Frame the efficiency problem.
- **3-9 · Part 1, the continuum.** Walk the two-lane SVG (full vs incremental, cost/complexity). Open the ELT vs ETL card live; land "modern default is ELT, land raw then transform."
- **9-15 · Part 2, watermark.** Run the incremental-pull box. Change the date twice live so they see the count move. Cover the safety-window self-study card.
- **15-20 · Part 3, batch windows.** Run the dated-file box. Define idempotency: re-run must not double-load; one file per window overwrites.
- **20-30 · Demo 1.** Everyone runs full-vs-incremental side by side. Emphasise the gap = bytes not moved = money at scale.
- **30-42 · Demo 2.** Q1 and Q2 hands-on (change watermarks, size windows); Q3 discuss the decision rule out loud.
- **42-45 · Q&A + quiz.**

## Preflight
- Open the page and **press Run once before class** to cache the ~8 MB DuckDB engine before any learner Runs.
- Confirm the watermark boxes return a sensible count (orders span 2026-01 to 2026-06).
- Projector zoom on; expand-all off.
- Have a calculator/mental figure ready for the "1 billion vs 1 million rows" scale example.

## Never cut
- The watermark box with a live date change - it is the aha moment.
- Demo 1 (full vs incremental gap).
- The ELT-is-the-default point.

## Cut if long
- Part 2 safety-window self-study card - mention "late data is real, ask me after."
- Demo 2 Q2 (daily vs monthly window) - homework.
- The Part 1 self-study "cost of full reload" card.

## Likely questions
- *"What if the source has no timestamp to watermark on?"* Then full reload may be the only correct option until they add one (that's Q3's tie-breaker).
- *"How far back should the safety window go?"* Depends on how late data arrives; 1-3 days is a common start. Overlap is cheap, missing data isn't.
- *"Is this streaming?"* No - this is batch/incremental. Continuous + CDC is session b6.
- *"Isn't re-reading the overlap wasteful?"* Cheaper than missing late rows; idempotency (Part 3) makes duplicates harmless.
