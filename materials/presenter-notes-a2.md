# Presenter notes - Leader session 2: Source systems

**Audience:** CxO, VPs, managers. 45 min, no code, thinking-mode. Builds on a1's lifecycle - this session zooms into the "generation" stage.

## Run of show

| Min | Beat | Note |
|-----|------|------|
| 0-3 | Welcome + recap a1 | "Data is born somewhere before it is useful - that somewhere is a source system." |
| 3-6 | Part 1 lede + source-zoo SVG | Walk the five source shapes into the funnel. |
| 6-12 | The shapes, and why they differ | Land that each has its own cadence, structure, reliability. |
| 12-14 | ACID boardroom aside | The system that runs the business is not the system you report from. |
| 14-20 | Cadence / structure / reliability | The three dimensions that predict how hard a source will be. |
| 20-26 | Part 2 lede + schema drift/rate limit/downtime | Three ways an un-owned source turns on you. |
| 26-32 | The rename-that-broke-reports story | Silent failure, two days of bad decisions, months of lost trust. |
| 32-36 | "Just query prod" + the contract conversation | Tie to OLTP vs OLAP (warehouse course). |
| 36-42 | Part 3 + three-question checklist SVG | Contracts / who-gets-paged / replica-not-prod. |
| 42-45 | Q&A + homework handoff | Point to a3 (batch vs streaming) as next. |

## Preflight
- Open the a2 page, "Expand all" once, then collapse.
- Pre-click the two SVGs (source zoo, three-question checklist) to confirm zoom.
- Have one real source-system example from the room's own org ready to name.
- Know the OLTP-vs-OLAP handoff line: depth lives in learn-data-warehouse.

## Never cut (the load-bearing beats)
- "You usually do not own the source" - the permanent condition of the work.
- Schema drift as the classic silent-failure cause.
- The three leader questions (contracts / paged / replica-not-prod).
- The rename-broke-reports story - it makes drift concrete.

## Cut if running long
- The cadence/structure/reliability self-study card (name it, point to the page).
- The "just query prod" self-study card - fold one sentence into the contract beat.
- Trim the ACID aside to "the app's guarantees are why you do not report off it."

## Likely exec questions + crisp answers
- **"Why can't we just read the production database directly?"** Heavy analytics queries fight the live app's writes and can slow the product for real customers. Read a safe replica instead.
- **"Whose job is it to prevent schema drift breaking us?"** Nobody's, unless you fund it. That is what the data contract and the alert (dataops) are for. Right now it is likely an un-owned risk.
- **"We do not control the vendor - so what can we even do?"** Get a written contract on the fields you depend on and a change-notice commitment, and put an alert on the source. You cannot stop change; you can stop being surprised.
- **"How many source systems is normal?"** More than you think - every SaaS tool, payment provider, and app database is one. The homework is to list your top five and mark who owns each.
- **"Is a data contract a legal document?"** No. It is a lightweight shared agreement on fields and change communication. Cheap to write, expensive to skip.
