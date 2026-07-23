# Presenter notes - Builder b8: Distributed processing

**Length:** 45 min · **Track:** Builder (b1-b10) · **Running case:** Daybreak coffee

## Preflight (before class)
- Open `courses/b8-distributed-processing.html` and press **Run** on any `data-setup="big"` box once. First run downloads the DuckDB engine (~8 MB) and caches it; do this on the room wifi so class does not wait.
- Confirm the 300k-row boxes return in double- or triple-digit milliseconds. Note the exact ms - you will point at it live.
- Toggle Projector zoom on and check both SVGs (single-node vs cluster; Spark lazy plan) are legible from the back.

## Run of show
1. **0-3 · Recap.** Pipeline stands at b7: extract, move, store partitioned. Today's question: what if it does not fit on one machine?
2. **3-10 · Part 1, why distribute.** Walk the SVG. Land map-shuffle-reduce; make them repeat "the shuffle is the network tax."
3. **10-16 · Part 2, the tradeoff.** Run the 300k aggregate live. Say the ms out loud: "this is a laptop beating a cluster for this size."
4. **16-20 · Part 3, Spark.** Read the PySpark snippet for shape only. Stress lazy vs action. Flag orchestration = dataops.
5. **20-31 · Demo 1.** Everyone runs the three aggregates. Have them read their own ms.
6. **31-42 · Demo 2.** Q1 and Q2 hands-on; Q3 is the cluster-decision discussion.
7. **42-45 · Q&A** and tee up b9 (reliability seams).

## Never cut
- The live 300k timer in Part 2 or Demo 1. The whole session lands on that number.
- The one-line rule: "most data is small; reach for a cluster last."
- The shuffle-is-the-tax mental model.

## Cut if long
- Part 3 Spark snippet can drop to a 60-second mention; the concept matters more than the code.
- Demo 2 Q2 (the window) can be shown on screen instead of typed by everyone.

## Likely questions
- *"So Spark is dead?"* No - it earns its keep at genuine multi-TB scale or in existing Spark shops. It is just reached for too early.
- *"How big is too big for DuckDB?"* Rule of thumb ~100 GB+ on a large box; it streams data bigger than memory off disk. Measure, do not guess.
- *"Where does scheduling Spark jobs live?"* learn-dataops, not here. We build the processing logic; they operate it.
- *"Why is the shuffle so slow?"* It moves data between machines over the network, which is orders of magnitude slower than memory.
