# Presenter notes - Builder session 7: Storage engineering

**Runtime:** 45 min · **Track:** Builder (b7 of 10) · **Chip:** 🔴 · **Live engine:** DuckDB-WASM

## Preflight (do before class)
- Open `courses/b7-storage-engineering.html` and press **▶ Run** on ONE sqlbox to download and cache the ~8 MB DuckDB engine before class. Do this early - the boxes here use `data-setup="big"` (300k rows), so the first run also builds that table; get it warm before the projector is live.
- Confirm you are online: engine loads from the jsDelivr CDN on first run only.
- Run Demo 1 once yourself to confirm the partition write + prune works and to have the ms figures ready to reference.
- Click "Expand all", verify every card opens, then collapse. Toggle "Projector zoom: on" for large rooms.

## Run of show
- **0-3 min · Recap (Part 0).** Data is correct and shaped; now the question is physical layout - fast and cheap, not just right.
- **3-9 min · Partitioning concept (Part 1).** Walk the funnel SVG: unpartitioned reads all, partitioned prunes to one. Land "one big file bad, a million tiny files worse." Anchor the dashboard cost real-world box.
- **9-14 min · Hands-on + tiers (Part 2).** Run the partition-then-read-one-month box on `big_orders`. Show the row count is one month, not 300k. Cover hot/warm/cold in the self-study card.
- **14-18 min · Object storage (Part 3).** The many-engines-one-storage SVG. Land "your laptop's Parquet file IS the S3 object" - same read, longer path.
- **18-32 min · Demo 1.** Everyone partitions and runs the pruned-vs-full-scan comparison. Read the numbers aloud (~38,750 vs 300,000) and connect scanned-bytes to cost.
- **32-42 min · Demo 2.** Q1 partition by channel (live). Q2 rows-per-partition (live). Q3 the over-partitioning / small-files trap - discuss aloud.
- **42-45 min · Q&A + homework.**

## Never cut
- Demo 1's pruned-vs-full-scan number. Bytes-scanned = dollars is the session's punchline.
- Q3 over-partitioning. Without it people leave thinking "more partitions = more speed" and cause the small-files problem.

## Cut if long
- Part 2 storage-tiers self-study card (marked self-study).
- Part 3 distributed-storage read-only snippet can be pointed at, not read line by line.

## Likely questions
- *"Does PARTITION_BY really run in the browser?"* Yes - DuckDB-WASM writes the partitioned folders to its in-browser filesystem. The fallback (separate monthly files) is in the Part 2 tip if the room's browser struggles.
- *"How many partitions is too many?"* Aim for tens-to-hundreds of MB each. Thousands of tiny files = the small-files problem (Q3). Compaction merges shards back up.
- *"Which column do I partition on?"* The one your queries filter on most - usually a date. Match layout to access pattern.
- *"Is this the warehouse's job or DE's?"* DE engineers the physical layout feeding the warehouse; dimensional modeling inside it is learn-data-warehouse. Distributed compute is b8 next.
