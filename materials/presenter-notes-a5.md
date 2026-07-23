# Presenter notes - Leader session 5: Storage engineering

**Audience:** CxO, VPs, managers. No code. 45 min, thinking mode.
**One-line goal:** they leave knowing storage is two cost levers (format + tier) and how to run the monthly conversation.

## Run of show (45 min)
- **0-3 Welcome.** Hook: "Half your storage bill is probably data nobody has read in years. Let's find it." Promise no byte-level detail.
- **3-20 Formats + why they matter (Part 1).** Show the CSV vs Parquet diagram. Land two ideas: columnar compresses hard, and it reads only needed columns. Stress the "you pay per byte scanned" link to the query bill. Open card 1 live.
- **20-42 Tiers, object storage, cost (Parts 2-3).** Walk the hot/warm/cold ladder - cost down, retrieval time up. Object storage = cheap durable floor (S3). Then the three monthly questions. Tell the "hot-tier prices for 5-year-old logs" story.
- **42-45 Q&A.** Send them to homework: pull the last bill, find the fastest-growing bucket.

## Preflight
- Open a5 in projector zoom; confirm both SVGs render at size.
- Flag the illustrative-figures caveat on the CSV/Parquet diagram (~8x is directional, not a promise).
- Have a rough sense of your own storage bill trend to anchor the tier discussion.
- Be ready to say "table formats" (Iceberg/Delta) in one breath without going down the rabbit hole.

## Never cut
- Format = cost + speed decision, not a technical detail (the whole Part 1 point).
- Hot vs cold tier tradeoff + the "old data on hot tier" waste (biggest easy saving).
- The three monthly questions - this is what they actually take back.

## Cut if long
- The table-formats / lakehouse self-study card (name it, move on).
- The lake-vs-warehouse aside (point to the warehouse course and skip).
- The dashboard-got-cheaper story if the log-archive story already landed.

## Likely exec questions
- **"Why not just keep everything hot for simplicity?"** Because you pay premium price for data no one reads. Auto-tiering rules cool it down with zero downside.
- **"Is Parquet always right?"** No - CSV/JSON win for human-readable, partner handoffs, and one-record-at-a-time writes. Convert to Parquet for repeated analytics.
- **"Should we delete old data to save money?"** Usually tier it cold, not delete - retention rules and legal holds matter. Cold archive is cheap enough that keeping is fine.
- **"Who owns this - do I need a new hire?"** No. Make it a standing monthly review with lifecycle rules, not a person's full-time job.
- **"Are these numbers current?"** Tiers and pricing are mid-2026 and move; re-verify vendor specifics before acting.
