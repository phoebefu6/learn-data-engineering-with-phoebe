# Presenter notes - Builder session 5: Batch transformation

**Runtime:** 45 min · **Track:** Builder (b5 of 10) · **Chip:** 🟠 · **Live engine:** DuckDB-WASM

## Preflight (do before class)
- Open `courses/b5-batch-transformation.html` and press **▶ Run** on ONE sqlbox. This downloads and caches the ~8 MB DuckDB engine so the first live run in class is instant, not a 20-second wait on the projector.
- Confirm you are online: the engine loads from the jsDelivr CDN on first run only.
- Click "Expand all" once to check every card opens, then collapse before presenting.
- Toggle "Projector zoom: on" if the room is large.

## Run of show
- **0-3 min · Recap (Part 0).** Where the pipeline stands: extract → ingest → land → now transform. Anchor to the amber "what you walk out with" callout.
- **3-9 min · ETL vs ELT (Part 1).** Walk the SVG: the only difference is where the copper transform box sits. Land the flip - engine is now the cheapest compute, so load raw first.
- **9-14 min · Idempotency (Part 2).** Run the daily-orders box, note the count, run it AGAIN live. Count does not move. That is the whole lesson made visible.
- **14-18 min · Compute at scale (Part 3).** The single-node vs distributed SVG + the read-only PySpark snippet. Stress: same logic, different engine; ~100 GB is the rough line.
- **18-32 min · Demo 1.** Everyone builds the three-layer transform (clean → join → aggregate). Re-run to prove idempotency again.
- **32-42 min · Demo 2.** Q1 channel dim (live). Q2 the double-count bug - let them RUN the mistake and read `row_copies = 2`. Q3 discuss aloud.
- **42-45 min · Q&A + homework pointer.**

## Never cut
- The run-it-twice moment in Part 2. It is the emotional core of the session.
- Demo 2 Q2 (the double-count bug). Seeing the bug beats hearing about it.

## Cut if long
- Part 1 self-study card (when ETL still wins) - it is marked self-study, safe to skip live.
- Part 3 PySpark snippet can be pointed at rather than read line by line.

## Likely questions
- *"Is DuckDB really doing ELT?"* Yes - every box loads raw source then transforms in-engine. That is ELT in miniature.
- *"When exactly do I need Spark?"* When one machine can no longer hold or chew the data (~100 GB+), measured, not guessed. Full treatment in b8.
- *"Isn't CREATE OR REPLACE wasteful vs incremental?"* For small/medium tables, rebuild-from-source is simplest and safest. Incremental merges come up in b9's reliability seam.
- *"Where does dbt fit?"* dbt orchestrates and names these layers; the transform logic is exactly what we wrote. Tooling is learn-dataops.
