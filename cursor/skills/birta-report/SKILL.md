---
name: birta-report
description: "Write a report — a monthly or quarterly business report, a project status report, an investor or board update, an analytics summary, research results — that puts the verdict first, backs it with numbers against a baseline and names what needs a decision, and publish it to Birta so readers open it at one address period after period and review it on the page. Use whenever the user asks for a report, status update, metrics summary, KPI review, research write-up or \"what happened this month\", even a short one and whether or not they say where to put it: a report is read by people who were not in the chat, so it needs a page they can open. Not for reports generated inside the user's own app."
---

# Reports on Birta

A report is read by someone who stops after the first screen. It must tell them,
in that first screen, how things stand, what changed and what is wanted of them;
everything below exists to back that up for the reader who keeps going. Numbers,
the story and the next steps belong in one place, not three.

## Ask before you build

Ask only what the user has not already said; one short message, then start.

- Who reads it and what will they do with it: a decision, a check-in, an intro,
  reassurance? The reader sets the length and the vocabulary.
- Which period, compared to what: the previous period, the plan, a target? A
  number with no baseline is noise. Confirm where the numbers come from (files,
  a tool, pasted text) and use nothing you were not given.
- What is the verdict, in one sentence, and is there an ask: a decision, money,
  an introduction, a deadline? If the user cannot say, draft a verdict from the
  numbers and show it to them before building.
- Is this recurring? A recurring report lives in one project and gets a new
  version each period, so remarks follow the same sections.

## Structure

| Part | Must contain |
| --- | --- |
| Header | Title, period, "as of" date, data source, author |
| Summary | The verdict first, then three to five points, then the ask |
| Numbers | 3–5 key metrics with value, change against the baseline, period |
| What happened | Wins and misses, each with context, implication and action |
| Risks and decisions | What needs a decision, options, a recommendation, owner, date |
| Next period | 3–5 commitments with owners and dates |
| Detail | Full tables, method, caveats, definitions; folded away |

The summary stands alone: a reader who sees nothing else still knows the state
and whether to worry. A status report keeps the same parts but shorter; an
investor update adds cash, burn and runway to the numbers and a line of thanks
for help received; a research or analytics summary states the question and
method before the findings, and treats "what to do next" as its ask.

## Craft

- One message per section, in its heading. "Signups +40% after the referral
  launch" is a heading; "Signups" is a label.
- Report movement, not activity. Milestones are done or not; no percentages of
  done, no task lists.
- Bad news goes early and in plain words, with the fix or the options beside it.
  Never let a green summary sit above an unresolved critical issue.
- Every ask names the person, the thing and the date. "Would love your thoughts"
  is not an ask.
- Put a caveat next to the number it limits, not in a footnote at the end.
- Separate risks (may happen) from issues (happening now); each has an owner.
- Keep the chart and the sentence about it together; the sentence says what to
  notice, the chart proves it.
- If a section would be empty, drop it rather than fill it. If nothing needs a
  decision, say so in one line.
- No invented numbers, no rounded-up good news, no softened red.

For the text itself, follow `birta-anti-slop-writing`.

## Build it on Birta

- Format: a short status report with no charts is Markdown (`index.md`), with a
  front-matter block for period, as-of date and author. Anything with charts or
  stat tiles is HTML (`index.html`); a board deck follows
  `birta-presentation`.
- For page layout and type, follow `birta-design`; it is a working document, so a
  calm treatment. For charts and KPI tiles, follow `birta-charts`; for a diagram
  of a process or system, follow `birta-diagrams`.
- Give every section and every metric a stable id that names the thing, not its
  position: `id="summary"`, `id="metric-mrr"`, `id="decision-pricing"`. Keep the
  same ids from period to period so remarks on last month's section land on this
  month's.
- Put the detail in `<details>` blocks below the summary, and shared numbers in a
  JSON file next to the page when several charts use them.
- Project and draft work as the `birta-publish` skill describes, access as
  `birta-manage` does. A new period is
  a new version of the same project: edit the numbers and text in place, publish
  with `publish_version`, and the address stays the same.
- Before publishing numbers meant for a closed circle, check the project's access
  with `project_settings` and report it to the user; changing it is the owner's
  call.
- Read `list_version_comments` before writing the next period's report: a thread
  on a metric is often the question the next report must answer.

## Check before publishing

- The first screen gives the verdict, the period and the ask without scrolling.
- Every number shows its baseline and period; every chart's title is a finding.
- Every decision and next step has an owner and a date.
- Misses are stated as plainly as wins, with their consequence.
- The as-of date and data source are on the page, not only in the chat.
- Ids match the previous version where the sections are the same.
- The page reads at phone width and in dark mode.
