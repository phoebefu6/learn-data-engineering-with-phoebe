# Presenter notes - Builder b9: Reliability seams

**Length:** 45 min · **Track:** Builder (b1-b10) · **Running case:** Daybreak coffee

## Preflight (before class)
- Open `courses/b9-reliability-seams.html` and press **Run** once on the Part 2 defensive-extract box to cache the ~8 MB DuckDB engine before class.
- Confirm the demo boxes return `quarantined = 2` (Part 2 / Demo 1) - the two malformed rows are set aside, not fatal. If it errors, re-check the room wifi cached the engine.
- Projector zoom on; verify both SVGs (the three seams; DE-builds-vs-DataOps-operates) read from the back.

## Run of show
1. **0-3 · Recap.** Pipeline works on good days (b2-b8). Today is about the bad days.
2. **3-10 · Part 1, the seams.** Walk the SVG. Tell the silent-rename story - it lands the "fails silently is worse than crashes" point.
3. **10-16 · Part 2, defenses.** Run the TRY_CAST quarantine live; show good vs quarantined counts. Define data contract and idempotency plainly.
4. **16-20 · Part 3, the handoff.** Walk the build-vs-operate SVG. Point explicitly at learn-dataops. No orchestration code here on purpose.
5. **20-32 · Demo 1.** Everyone builds the defensive ingest. Prove the bad row does not kill the run.
6. **32-42 · Demo 2.** Q1 schema/null check, Q2 dedupe hands-on; Q3 is the DE-vs-dataops sorting discussion.
7. **42-45 · Q&A** and tee up b10 (capstone).

## Never cut
- The live quarantine demo (Part 2 or Demo 1). Seeing bad rows set aside instead of crashing is the whole point.
- The DE-builds / DataOps-operates boundary. This is the seam where the course itself hands off.
- The idempotency definition ("twice = once").

## Cut if long
- The data-contract self-study card can be a 60-second mention.
- Demo 2 Q2 (dedupe) can be shown on screen rather than typed by all.

## Likely questions
- *"Should the run crash or quarantine?"* Quarantine the bad rows, keep good data flowing, report the count. Crash only on contract-level breakage (a missing key column).
- *"Who owns schema drift?"* With a data contract, the producer does. Without one, you do - by surprise.
- *"Is a schema check the same as a data contract?"* The check enforces the contract at the seam. The contract is the agreement; the check is the test.
- *"Where do alerts and scheduling live?"* learn-dataops. DE emits the signals; DataOps watches them.
