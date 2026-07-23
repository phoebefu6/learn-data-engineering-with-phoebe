# Presenter notes - Leader session 3: Batch vs streaming

**Audience:** CxO, VPs, managers. 45 min, no code, thinking-mode. This is the first big spending decision of the track - the session that saves budgets.

## Run of show

| Min | Beat | Note |
|-----|------|------|
| 0-3 | Welcome + framing | "This is the decision a sales rep will try to make for you." |
| 3-6 | Part 1 lede + two-clocks SVG | Batch lane vs streaming lane; point at the latency/cost dials. |
| 6-11 | Batch, the sensible default | Land "if nobody can say why batch is insufficient, the answer is batch." |
| 11-14 | Streaming, and why it costs more | Always-on infra + out-of-order/duplicate/late events = 5-10x. |
| 14-20 | Part 2 lede + the honest table | Read each row; make the "in the moment vs slower cadence" split visible. |
| 20-26 | Skepticism: "real-time" + "zero-ETL" | Real-time for what? Zero-ETL = work moved, not gone. |
| 26-32 | Six-months-of-streaming story | The report everyone read once, mid-morning, over coffee. |
| 32-38 | Part 3 + freshness ladder SVG | Daily -> hourly -> micro-batch -> streaming, cost climbing. |
| 38-42 | Micro-batch + the one question | "Who acts on this, how fast, what breaks if it's an hour old?" |
| 42-45 | Q&A + homework handoff | Point to a4 (build vs buy the stack) as next. |

## Preflight
- Open the a3 page, "Expand all" once, then collapse.
- Pre-click the three SVGs (two clocks, freshness ladder) to confirm zoom.
- Have the ~5-10x figure ready and attributed as an industry rule of thumb, not a hard law.
- Line up one real "real-time" request from the room's own backlog to stress-test live.

## Never cut (the load-bearing beats)
- Batch is the default; streaming carries the burden of proof.
- The 5-10x cost premium for streaming.
- The one test: does a fresher number change a decision inside the window?
- Micro-batch as the middle road - most "we need it fresher" requests stop here.

## Cut if running long
- The "streaming, why it costs more" self-study card (name out-of-order/duplicate/late, move on).
- The "honest split in one line" self-study card - it repeats the table's punchline.
- Trim the six-months story to the punchline: "read once, mid-morning, batch would have served everyone."

## Likely exec questions + crisp answers
- **"A competitor advertises real-time - shouldn't we match it?"** Only if a decision on your side changes because the data is seconds old. Matching a feature nobody acts on is paying 5-10x for a light show.
- **"The vendor says zero-ETL means no pipeline cost."** The transform work does not vanish - it moves into their platform, your bill, or a lock-in. Ask where it went before you sign.
- **"Our team says we need streaming - how do I push back without micromanaging?"** Do not argue tech. Ask one question: who acts on this, how fast, and what breaks if it is an hour old? Let the answer decide.
- **"Is micro-batch a real thing or a compromise?"** Real and often the right answer: same cheap batch machinery run every few minutes, minutes-old data, none of streaming's hard problems.
- **"When is streaming genuinely worth it?"** Fraud, live operations, in-session personalization - anywhere the decision is made in the moment and being late makes it worthless.
