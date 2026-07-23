# Presenter notes - Leader session 1: What data engineering is

**Audience:** CxO, VPs, managers. 45 min, no code, thinking-mode. This is the "Start here" session - set the frame for the whole leader track.

## Run of show

| Min | Beat | Note |
|-----|------|------|
| 0-3 | Welcome + why this track | One line: "every number you trust sits on a pipeline someone built." Name Daybreak as the running example. |
| 3-6 | Part 1 lede + lifecycle SVG | Walk the five stages left to right on the diagram. Do not rush the arrows. |
| 6-11 | The five stages in one breath | Land "stages are stable, tools are not." This is the whole session's spine. |
| 11-14 | Undercurrents + which are ours | Point at the copper band: DataOps/orchestration = learn-dataops, not us. |
| 14-20 | Part 2 lede + three-craft table | Read the table row by row against Daybreak. |
| 20-26 | The one-sentence test | Say it out loud, make the room repeat the three verbs. |
| 26-32 | The mis-hire boardroom story | The retail exec who conflated "data engineers" with "dashboards." |
| 32-38 | Part 3 + hierarchy pyramid | Build up from the base. "You cannot buy the top." |
| 38-42 | Cost of not investing | Shadow pipelines, spreadsheet sprawl, nobody trusts the numbers. |
| 42-45 | Q&A + homework handoff | Point to a2 (source systems) as next. |

## Preflight
- Open the a1 page, hit "Expand all" once to confirm cards open, then collapse.
- Test "Projector zoom" toggle for the room size.
- Have the two SVGs (lifecycle, pyramid) pre-zoomed in your head - you will click both.
- Know the three sibling course names cold: learn-dataops, learn-data-warehouse, learn-sql.

## Never cut (the load-bearing beats)
- The five stages named in order.
- "Stages are stable, tools churn" - the reason to fund stages not logos.
- The one-sentence test (get here / shape into facts / run at 2am).
- The hierarchy of needs: foundation before analytics before AI.

## Cut if running long
- The undercurrents self-study card (say one line, point to the page).
- "Confidently wrong downstream" self-study card - fold into the cost beat.
- Trim the mis-hire story to two sentences if needed, but keep the punchline.

## Likely exec questions + crisp answers
- **"Why not just buy a tool that does all this?"** Tools implement stages; they do not remove them. You still own the lifecycle - the tool just runs one part of it.
- **"How is this different from our BI/analytics team?"** BI is the serving stage on top of the warehouse. DE builds the pipes underneath. Different craft, different hire.
- **"We want to do AI this year - why start here?"** Rogati's hierarchy: no trustworthy AI without the data plumbing under it. Fund the base or the AI trains on garbage.
- **"How do I know if our foundation is weak?"** Ask if you would bet a board decision on the top three numbers. Hesitation is your answer.
- **"Isn't 'lifecycle' just consultant-speak?"** It is the one framing that survived every tool change for decades. Hire against it and your investment ports; hire against tools and you rebuild.
