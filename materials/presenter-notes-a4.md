# Presenter notes - Leader session 4: Build vs buy the stack

**Audience:** CxO, VPs, managers. No code. 45 min, thinking mode.
**One-line goal:** they leave able to run a build-vs-buy decision and grill a data-tooling vendor.

## Run of show (45 min)
- **0-3 Welcome.** Frame it as a money session, not a tech one. Ask: "How much are we spending on data tools, and could you defend it?" Let the silence land.
- **3-20 The modern data stack (Part 1).** Walk the layer diagram bottom to top. Name the vendor per layer. Land the copper point hard: orchestration = dataops course, not this decision. Open card 1 live.
- **20-42 Managed vs OSS + vendor questions (Parts 2-3).** Teach Reis's "undifferentiated heavy lifting" rule first - it is the spine. Then the tradeoff table. Then the ten questions + the ladder diagram. Tell the "built its own ingestion tool" boardroom story with feeling.
- **42-45 Q&A.** Point to homework: map your own stack as bought/self-run/built.

## Preflight
- Open a4 in projector zoom; test Expand all toggle.
- Have your org's real data-tooling bill (or a rough number) ready as a live anchor.
- Skim the ten questions so you can say them without reading.
- Know which layers YOUR org currently buys vs builds - localize the examples.

## Never cut
- Reis's "avoid undifferentiated heavy lifting" rule (the whole session hangs on it).
- The egress + exit red flag (question set 2). This is the one that saves real money.
- The copper "orchestration = dataops" boundary - keeps scope honest.

## Cut if long
- The "stack that was really a spreadsheet" self-study story (mention in one line).
- The table-format / lakehouse aside can be dropped entirely at exec level.
- Trim the ten questions to the top six (cost, egress, exit, format, fit, references).

## Likely exec questions
- **"Should we just buy everything managed?"** Mostly yes early on. Build only your edge. Managed by default, OSS by justification (scale/cost/control).
- **"Open source is free though, right?"** No - you swap a license fee for engineer salaries, upgrades, and 2am pages. Compare total cost of ownership, not the sticker.
- **"A vendor says we won't need our warehouse anymore - good?"** Red flag. That is a bid to be your single point of failure. Ask about exit and egress before you believe it.
- **"How do we know if something is our 'edge'?"** If a competitor could buy the identical capability off the shelf, it is not your edge - rent it.
- **"Prices/tools changed since this deck?"** Very likely. Everything vendor-specific here is mid-2026; re-verify before signing.
